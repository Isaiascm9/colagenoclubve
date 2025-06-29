import React, { useState, useEffect, useRef } from 'react';

// Tailwind CSS CDN - Cargamos Tailwind CSS para estilos modernos y responsivos
// Google Font - Inter - Usamos la fuente Inter para una tipografía limpia y legible
// Estos se incluyen directamente en el JSX para asegurar su carga.

// -----------------------------------------------------------
// Componentes de Iconos SVG
// Estos iconos son SVGs en línea para asegurar la compatibilidad y facilitar la estilización con Tailwind.
// -----------------------------------------------------------

/**
 * Icono de Carrito de Compras (ShoppingCartIcon).
 * @param {object} props - Propiedades del componente.
 * @param {number} [props.size=24] - Tamaño del icono en píxeles.
 * @param {string} [props.className=''] - Clases CSS adicionales para el icono.
 * @param {function} [props.onClick] - Función de controlador de eventos de clic.
 * @returns {JSX.Element} Elemento SVG del icono de carrito.
 */
const ShoppingCartIcon = ({ size = 24, className = '', onClick }) => (
  <svg
    xmlns="http://www.w3.org/2000/svg"
    width={size}
    height={size}
    viewBox="0 0 24 24"
    fill="none"
    stroke="currentColor"
    strokeWidth="2"
    strokeLinecap="round"
    strokeLinejoin="round"
    className={className}
    onClick={onClick}
    style={{ cursor: onClick ? 'pointer' : 'default' }}
  >
    <circle cx="9" cy="21" r="1" />
    <circle cx="20" cy="21" r="1" />
    <path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6" />
  </svg>
);

/**
 * Icono de Instagram (InstagramIcon).
 * @param {object} props - Propiedades del componente.
 * @param {number} [props.size=24] - Tamaño del icono en píxeles.
 * @param {string} [props.className=''] - Clases CSS adicionales para el icono.
 * @returns {JSX.Element} Elemento SVG del icono de Instagram.
 */
const InstagramIcon = ({ size = 24, className = '' }) => (
  <svg
    xmlns="http://www.w3.org/2000/svg"
    width={size}
    height={size}
    viewBox="0 0 24 24"
    fill="none"
    stroke="currentColor"
    strokeWidth="2"
    strokeLinecap="round"
    strokeLinejoin="round"
    className={className}
  >
    <rect width="20" height="20" x="2" y="2" rx="5" ry="5" />
    <path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z" />
    <line x1="17.5" x2="17.51" y1="6.5" y2="6.5" />
  </svg>
);

/**
 * Icono de Cierre/Cruz (XIcon).
 * @param {object} props - Propiedades del componente.
 * @param {number} [props.size=24] - Tamaño del icono en píxeles.
 * @param {string} [props.className=''] - Clases CSS adicionales para el icono.
 * @param {function} [props.onClick] - Función de controlador de eventos de clic.
 * @returns {JSX.Element} Elemento SVG del icono de cierre.
 */
const XIcon = ({ size = 24, className = '', onClick }) => (
  <svg
    xmlns="http://www.w3.org/2000/svg"
    width={size}
    height={size}
    viewBox="0 0 24 24"
    fill="none"
    stroke="currentColor"
    strokeWidth="2"
    strokeLinecap="round"
    strokeLinejoin="round"
    className={className}
    onClick={onClick}
    style={{ cursor: onClick ? 'pointer' : 'default' }}
  >
    <path d="M18 6 6 18" />
    <path d="M6 6 18 18" />
  </svg>
);

/**
 * Icono de Estrella (StarIcon) para calificaciones.
 * @param {object} props - Propiedades del componente.
 * @param {string} [props.fill='currentColor'] - Color de relleno de la estrella.
 * @param {string} [props.className=''] - Clases CSS adicionales para el icono.
 * @returns {JSX.Element} Elemento SVG del icono de estrella.
 */
const StarIcon = ({ fill = 'currentColor', className = '' }) => (
  <svg
    xmlns="http://www.w3.org/2000/svg"
    width="20"
    height="20"
    viewBox="0 0 24 24"
    fill={fill}
    stroke="currentColor"
    strokeWidth="2"
    strokeLinecap="round"
    strokeLinejoin="round"
    className={className}
  >
    <polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2" />
  </svg>
);

// Icono de flecha hacia abajo/arriba para el acordeón FAQ
const ChevronDownIcon = ({ size = 24, className = '', onClick }) => (
    <svg
        xmlns="http://www.w3.org/2000/svg"
        width={size}
        height={size}
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        strokeWidth="2"
        strokeLinecap="round"
        strokeLinejoin="round"
        className={className}
        onClick={onClick}
    >
        <path d="m6 9 6 6 6-6" />
    </svg>
);

// Icono de flecha izquierda para el carrusel
const ChevronLeftIcon = ({ size = 24, className = '', onClick }) => (
    <svg
        xmlns="http://www.w3.org/2000/svg"
        width={size}
        height={size}
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        strokeWidth="2"
        strokeLinecap="round"
        strokeLinejoin="round"
        className={className}
        onClick={onClick}
    >
        <path d="m15 18-6-6 6-6" />
    </svg>
);

// Icono de flecha derecha para el carrusel
const ChevronRightIcon = ({ size = 24, className = '', onClick }) => (
    <svg
        xmlns="http://www.w3.org/2000/svg"
        width={size}
        height={size}
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        strokeWidth="2"
        strokeLinecap="round"
        strokeLinejoin="round"
        className={className}
        onClick={onClick}
    >
        <path d="m9 18 6-6-6-6" />
    </svg>
);

// Icono de flecha hacia arriba para el botón "Volver Arriba"
const ChevronUpIcon = ({ size = 24, className = '', onClick }) => (
    <svg
        xmlns="http://www.w3.org/2000/svg"
        width={size}
        height={size}
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        strokeWidth="2"
        strokeLinecap="round"
        strokeLinejoin="round"
        className={className}
        onClick={onClick}
    >
        <path d="m18 15-6-6-6 6" />
    </svg>
);

// Tasa de cambio constante (1 USD = 120 VES)
const EXCHANGE_RATE_USD_TO_VES = 120;

// Detalles de Pago Móvil
const PAGO_MOVIL_DETAILS = {
    bankNumber: '0102',
    phoneNumber: '04165854321',
    idNumber: '26456876'
};

/**
 * Función de ayuda para calcular la calificación promedio de un conjunto de reseñas.
 * @param {Array<Object>} reviews - Un arreglo de objetos de reseñas, cada uno con una propiedad `rating`.
 * @returns {number} La calificación promedio, o 0 si no hay reseñas.
 */
const getAverageRating = (reviews) => {
    if (!reviews || reviews.length === 0) return 0;
    const total = reviews.reduce((sum, review) => sum + review.rating, 0);
    return (total / reviews.length);
};

// Datos de productos con el catálogo ampliado y categorías
const initialProducts = [
    {
        id: 1,
        name: 'Colágeno Hidrolizado Premium',
        price: 28.50,
        originalPrice: 35.00,
        image: 'https://images.pexels.com/photos/7057700/pexels-photo-7057700.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'El colágeno más puro para una piel radiante.',
        longDescription: [
            'Mejora la elasticidad y firmeza de la piel.',
            'Fortalece el cabello y las uñas desde la raíz.',
            'Contribuye a la salud de las articulaciones.',
            'Fácil de disolver y de sabor neutro.',
            'Envase de 300g, ideal para uso diario.'
        ],
        promotionTag: '¡Oferta! 20% OFF',
        upsellProducts: [2, 8],
        reviews: [
            { id: 101, name: 'Ana G.', rating: 5, reviewText: '¡Increíble! Mi piel está más suave y mi cabello luce más brillante. Totalmente recomendado.', date: '2024-06-20' },
            { id: 102, name: 'Sofía L.', rating: 4, reviewText: 'Buen producto, he notado mejoría en la elasticidad de mi piel.', date: '2024-06-22' },
        ],
        category: ['Piel y Cabello', 'Bienestar General']
    },
    {
        id: 2,
        name: 'Flex 500 Colágeno',
        price: 35.00,
        image: 'https://images.pexels.com/photos/7057703/pexels-photo-7057703.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Ayuda a mejorar la movilidad y salud articular.',
        longDescription: [
            'Específico para el soporte de cartílagos y ligamentos.',
            'Reduce la incomodidad articular.',
            'Ideal para deportistas y personas activas.',
            'Contiene colágeno tipo II y otros ingredientes activos.',
            'Presentación en polvo para fácil consumo.'
        ],
        promotionTag: '',
        upsellProducts: [5, 6, 18],
        reviews: [
            { id: 201, name: 'Carlos R.', rating: 4, reviewText: 'Ha mejorado mucho mis rodillas. La entrega fue rápida. ¡Buen producto!', date: '2024-06-18' },
        ],
        category: ['Articulaciones y Huesos']
    },
    {
        id: 3,
        name: 'Pure Wellness Colágeno',
        price: 42.00,
        originalPrice: 48.00,
        image: 'https://images.pexels.com/photos/7057701/pexels-photo-7057701.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Colágeno 5000 MG para tu bienestar general.',
        longDescription: [
            'Contribuye a la regeneración celular.',
            'Mejora la digestión y la salud intestinal.',
            'Apoya el sistema inmunológico.',
            'Con vitaminas y minerales esenciales.',
            'Sabor delicioso y refrescante.'
        ],
        promotionTag: 'Envío Gratis',
        upsellProducts: [1, 7, 11],
        reviews: [
            { id: 301, name: 'Pedro L.', rating: 3, reviewText: 'El sabor no me termina de convencer. Aun así, siento los beneficios.', date: '2024-06-10' },
        ],
        category: ['Bienestar General']
    },
    {
        id: 4,
        name: 'Fine Smooth Colágeno',
        price: 47.50,
        image: 'https://images.pexels.com/photos/7057697/pexels-photo-7057697.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Para una piel suave y elástica. ¡Siente la diferencia!',
        longDescription: [
            'Reduce la apariencia de líneas finas y arrugas.',
            'Aporta un brillo juvenil a la piel.',
            'Hidratación profunda para pieles secas.',
            'Fórmula no grasa, de rápida absorción.',
            'Apto para todo tipo de piel.'
        ],
        promotionTag: '',
        upsellProducts: [1, 5],
        reviews: [],
        category: ['Piel y Cabello']
    },
    {
        id: 5,
        name: 'Colágeno Skin Extra Plus',
        price: 33.00,
        originalPrice: 40.00,
        image: 'https://images.pexels.com/photos/7057694/pexels-photo-7057694.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Fórmula intensiva para la firmeza de tu piel.',
        longDescription: [
            'Mejora significativamente la firmeza de la piel.',
            'Combate los signos del envejecimiento.',
            'Estimula la producción natural de colágeno.',
            'Resultados visibles en pocas semanas.',
            'Libre de parabenos y sulfatos.'
        ],
        promotionTag: '¡25% Descuento!',
        upsellProducts: [4, 8, 16],
        reviews: [
            { id: 501, name: 'Laura P.', rating: 5, reviewText: 'Mi piel se siente mucho más firme, ¡resultados sorprendentes!', date: '2024-06-25' },
        ],
        category: ['Piel y Cabello']
    },
    {
        id: 6,
        name: 'X Ray Colágeno',
        price: 55.00,
        image: 'https://images.pexels.com/photos/7057695/pexels-photo-7057695.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Soporte articular avanzado con colágeno.',
        longDescription: [
            'Formulado para la salud ósea y articular.',
            'Contiene colágeno tipo I y II.',
            'Enriquecido con magnesio y vitamina D.',
            'Promueve la flexibilidad y reduce el dolor.',
            'Ideal para el mantenimiento de la salud musculoesquelética.'
        ],
        promotionTag: '',
        upsellProducts: [2, 19],
        reviews: [],
        category: ['Articulaciones y Huesos']
    },
    {
        id: 7,
        name: 'Mitos y Verdades Colágeno',
        price: 20.00,
        image: 'https://images.pexels.com/photos/7057696/pexels-photo-7057696.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Descubre todo sobre el colágeno y sus beneficios.',
        longDescription: [
            'Guía completa sobre el colágeno.',
            'Desmiente mitos y aclara dudas.',
            'Beneficios reales y cómo incorporarlo a tu vida.',
            'Consejos de expertos para maximizar sus efectos.',
            'Lectura imprescindible para amantes del bienestar.'
        ],
        promotionTag: 'Edición Limitada',
        upsellProducts: [1, 3],
        reviews: [],
        category: ['Bienestar General']
    },
    {
        id: 8,
        name: 'Set Colágeno & Biotina',
        price: 60.00,
        originalPrice: 75.00,
        image: 'https://images.pexels.com/photos/7057698/pexels-photo-7057698.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Combinación perfecta para cabello, piel y uñas.',
        longDescription: [
            'Incluye Colágeno Hidrolizado y Biotina líquida.',
            'Nutrición completa para belleza y salud.',
            'Promueve el crecimiento de cabello fuerte.',
            'Mejora la elasticidad de la piel.',
            'Set ideal para comenzar tu rutina de bienestar.'
        ],
        promotionTag: '¡Ahorra en el Set!',
        upsellProducts: [1, 5],
        reviews: [
            { id: 801, name: 'Sofía M.', rating: 5, reviewText: 'Me encanta el Set de Colágeno y Biotina. Los resultados se ven en pocas semanas. ¡Repetiré!', date: '2024-06-15' },
        ],
        category: ['Piel y Cabello', 'Bienestar General']
    },
    {
        id: 9,
        name: 'Colágeno Geneo',
        price: 45.00,
        image: 'https://images.pexels.com/photos/725997/pexels-photo-725997.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Fórmula avanzada para la regeneración de la piel.',
        longDescription: [
            'Estimula la producción de colágeno y elastina.',
            'Tratamiento facial no invasivo.',
            'Resultados visibles desde la primera sesión.',
            'Aporta luminosidad y unifica el tono de la piel.'
        ],
        promotionTag: '',
        upsellProducts: [4, 5],
        reviews: [
            { id: 901, name: 'Valentina D.', rating: 5, reviewText: 'El tratamiento Geneo es espectacular, mi piel se ve como nueva.', date: '2024-06-19' },
        ],
        category: ['Piel y Cabello']
    },
    {
        id: 10,
        name: 'Colageina 10',
        price: 38.00,
        originalPrice: 45.00,
        image: 'https://images.pexels.com/photos/3683056/pexels-photo-3683056.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Colágeno y antioxidantes para una belleza duradera.',
        longDescription: [
            'Combate los radicales libres y el envejecimiento prematuro.',
            'Piel, cabello y uñas visiblemente más fuertes y saludables.',
            'Enriquecido con Vitamina C para máxima absorción.',
            'Fórmula en cápsulas para un consumo práctico.'
        ],
        promotionTag: 'Más Vendido',
        upsellProducts: [1, 8],
        reviews: [],
        category: ['Piel y Cabello', 'Bienestar General']
    },
    {
        id: 11,
        name: 'Vitalgen Colágeno Bebible',
        price: 52.00,
        image: 'https://images.pexels.com/photos/5612845/pexels-photo-5612845.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Nutrición esencial en un shot diario de sabor delicioso.',
        longDescription: [
            'Alta biodisponibilidad para una rápida absorción.',
            'Delicioso y refrescante sabor a frutos rojos.',
            'Fortalece la piel, articulaciones y huesos desde el interior.',
            'Formato líquido listo para tomar.'
        ],
        promotionTag: '',
        upsellProducts: [3, 7],
        reviews: [
            { id: 1101, name: 'Gabriela V.', rating: 5, reviewText: 'Me encanta el sabor y es muy práctico. He notado mi piel más hidratada.', date: '2024-06-21' },
        ],
        category: ['Piel y Cabello', 'Articulaciones y Huesos', 'Bienestar General']
    },
    {
        id: 12,
        name: 'Colágeno Garden House',
        price: 30.00,
        image: 'https://images.pexels.com/photos/209339/pexels-photo-209339.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'La pureza de la naturaleza para el cuidado de tu piel.',
        longDescription: [
            'Elaborado con ingredientes de origen 100% natural.',
            'Libre de aditivos, colorantes y conservantes.',
            'Brinda soporte estructural para la piel y articulaciones.',
            'Promueve un bienestar integral.'
        ],
        promotionTag: '',
        upsellProducts: [13, 1],
        reviews: [],
        category: ['Piel y Cabello', 'Articulaciones y Huesos', 'Bienestar General']
    },
    {
        id: 13,
        name: 'Simple Colágeno Puro',
        price: 25.00,
        image: 'https://images.pexels.com/photos/5969539/pexels-photo-5969539.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Colágeno hidrolizado sin sabor, 100% puro.',
        longDescription: [
            'Versatilidad total: ideal para mezclar con cualquier bebida.',
            'Sin carbohidratos, sin grasas, sin azúcares.',
            'Fácil disolución en líquidos fríos o calientes.',
            'Mejora la salud general de la piel y tejidos.'
        ],
        promotionTag: '',
        upsellProducts: [1, 12],
        reviews: [],
        category: ['Piel y Cabello', 'Articulaciones y Huesos', 'Bienestar General']
    },
    {
        id: 14,
        name: 'Colágeno Plus con Magnesio',
        price: 39.50,
        image: 'https://images.pexels.com/photos/4198020/pexels-photo-4198020.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'El dúo perfecto para tus músculos y articulaciones.',
        longDescription: [
            'Ayuda a reducir el cansancio y la fatiga muscular.',
            'Contribuye al funcionamiento normal de los músculos y huesos.',
            'Combinación sinérgica con vitamina C y magnesio.',
            'Ideal para deportistas y personas con un estilo de vida activo.'
        ],
        promotionTag: '',
        upsellProducts: [2, 6, 19],
        reviews: [
            { id: 1401, name: 'Ricardo J.', rating: 4, reviewText: 'Lo tomo después de entrenar y me ha ayudado con la recuperación.', date: '2024-06-17' },
        ],
        category: ['Articulaciones y Huesos', 'Bienestar General']
    },
    {
        id: 15,
        name: 'Infiltrex',
        price: 58.00,
        originalPrice: 65.00,
        image: 'https://images.pexels.com/photos/3873177/pexels-photo-3873177.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Soporte intensivo para la salud y flexibilidad articular.',
        longDescription: [
            'Contiene Colágeno tipo II, Glucosamina y Condroitina.',
            'Ayuda a mantener la flexibilidad y lubricación de las articulaciones.',
            'Fórmula especializada para el desgaste articular.',
            'Promueve la regeneración del cartílago.'
        ],
        promotionTag: 'Fórmula Articular',
        upsellProducts: [18, 19],
        reviews: [],
        category: ['Articulaciones y Huesos']
    },
    {
        id: 16,
        name: 'Agial Pro Colágeno',
        price: 49.00,
        image: 'https://images.pexels.com/photos/3998246/pexels-photo-3998246.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Fórmula profesional para una máxima eficacia en tu piel.',
        longDescription: [
            'Contiene péptidos de colágeno bioactivos de alta pureza.',
            'Resultados en la piel probados clínicamente.',
            'Mejora la hidratación, elasticidad y densidad de la piel.',
            'Reduce la profundidad de las arrugas.'
        ],
        promotionTag: '',
        upsellProducts: [5, 9],
        reviews: [],
        category: ['Piel y Cabello']
    },
    {
        id: 17,
        name: 'Colágeno 500 en Cápsulas',
        price: 29.99,
        image: 'https://images.pexels.com/photos/4047069/pexels-photo-4047069.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Dosis precisa de colágeno en cómodas cápsulas.',
        longDescription: [
            'Cada cápsula contiene 500mg de colágeno hidrolizado.',
            'Formato práctico, fácil de incorporar en tu rutina diaria.',
            'Brinda apoyo estructural para la piel y el tejido conectivo.',
            'Ideal para mantener niveles óptimos de colágeno.'
        ],
        promotionTag: '',
        upsellProducts: [10, 13],
        reviews: [],
        category: ['Piel y Cabello', 'Articulaciones y Huesos', 'Bienestar General']
    },
    {
        id: 18,
        name: 'Curflex Colágeno con Cúrcuma',
        price: 44.00,
        image: 'https://images.pexels.com/photos/4113840/pexels-photo-4113840.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'Alivio y bienestar para tus articulaciones.',
        longDescription: [
            'Combina Colágeno Tipo II no desnaturalizado con extracto de Cúrcuma.',
            'Aprovecha las propiedades antiinflamatorias naturales de la cúrcuma.',
            'Contribuye a disminuir la rigidez y el dolor articular.',
            'Mejora la movilidad y calidad de vida.'
        ],
        promotionTag: '¡Nuevo!',
        upsellProducts: [2, 15],
        reviews: [
             { id: 1801, name: 'Marta S.', rating: 5, reviewText: 'Desde que lo tomo, mis articulaciones se sienten mucho mejor. ¡Fantástico!', date: '2024-06-24' },
        ],
        category: ['Articulaciones y Huesos']
    },
    {
        id: 19,
        name: 'Ultra Flex Advanced',
        price: 62.50,
        image: 'https://images.pexels.com/photos/7675419/pexels-photo-7675419.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        shortDescription: 'La máxima protección para tus articulaciones.',
        longDescription: [
            'Fórmula completa con MSM, Glucosamina, Condroitina y Ácido Hialurónico.',
            'Promueve la lubricación y resistencia del cartílago.',
            'Diseñado para atletas y personas con alta exigencia física.',
            'Soporte articular superior y de acción rápida.'
        ],
        promotionTag: '',
        upsellProducts: [6, 14, 15],
        reviews: [],
        category: ['Articulaciones y Huesos']
    }
];

// Datos de reseñas de clientes (para la sección general de reseñas)
const customerReviews = [
    {
        id: 1,
        name: 'Ana G.',
        rating: 5,
        reviewText: '¡Increíble! Mi piel está más suave y mi cabello luce más brillante. Totalmente recomendado.',
        date: '2024-06-20'
    },
    {
        id: 2,
        name: 'Carlos R.',
        rating: 4,
        reviewText: 'El colágeno Flex 500 ha mejorado mucho mis rodillas. La entrega fue rápida. ¡Buen producto!',
        date: '2024-06-18'
    },
    {
        id: 3,
        name: 'Sofía M.',
        rating: 5,
        reviewText: 'Me encanta el Set de Colágeno y Biotina. Los resultados se ven en pocas semanas. ¡Repetiré!',
        date: '2024-06-15'
    },
    {
        id: 4,
        name: 'Pedro L.',
        rating: 3,
        reviewText: 'El Pure Wellness Colágeno es bueno, pero el sabor no me termina de convencer. Aun así, siento los beneficios.',
        date: '2024-06-10'
    },
    {
        id: 5,
        name: 'María F.',
        rating: 5,
        reviewText: 'El colágeno hidrolizado premium es una maravilla. Lo tomo todos los días y mi piel se ve fabulosa.',
        date: '2024-06-05'
    },
];

// Datos para la sección de Preguntas Frecuentes
const faqData = [
    {
        question: '¿Qué es el colágeno y por qué es importante?',
        answer: 'El colágeno es la proteína más abundante en nuestro cuerpo y es esencial para la estructura de la piel, huesos, músculos, tendones y ligamentos. Su producción disminuye con la edad, lo que puede llevar a la aparición de arrugas, pérdida de elasticidad y problemas articulares. Suplementar con colágeno ayuda a reponerlo.'
    },
    {
        question: '¿Cuáles son los beneficios de tomar suplementos de colágeno?',
        answer: 'Tomar colágeno puede mejorar la elasticidad e hidratación de la piel, reducir la apariencia de arrugas, fortalecer el cabello y las uñas, apoyar la salud de las articulaciones y los huesos, y contribuir a la salud intestinal.'
    },
    {
        question: '¿Cómo debo tomar el colágeno?',
        answer: 'La forma de tomarlo depende del tipo de suplemento. Generalmente, el colágeno en polvo se mezcla con agua, jugos, batidos o café. Las cápsulas o gomitas se toman según las indicaciones del fabricante, usualmente con las comidas. Es recomendable seguir las instrucciones específicas de cada producto.'
    },
    {
        question: '¿A qué edad debo empezar a tomar colágeno?',
        answer: 'La producción natural de colágeno comienza a disminuir alrededor de los 25-30 años. Muchas personas optan por empezar a tomar suplementos en esta etapa para prevenir los signos del envejecimiento y mantener la salud general. Sin embargo, no hay una edad "correcta" fija; se puede iniciar cuando se desee apoyar la producción de colágeno del cuerpo.'
    },
    {
        question: '¿Tiene el colágeno efectos secundarios?',
        answer: 'El colágeno es generalmente seguro para la mayoría de las personas. Los efectos secundarios son raros y suelen ser leves, como hinchazón, acidez estomacal o sensación de saciedad. Si tienes alguna condición médica o estás tomando otros medicamentos, consulta a un profesional de la salud antes de empezar a tomar suplementos.'
    }
];

// -----------------------------------------------------------
// Componente ProductCard
// Muestra un producto individual con su imagen, nombre, precio y un botón para añadir al carrito.
// Incluye una animación al desplazarse usando Intersection Observer.
// -----------------------------------------------------------

/**
 * Componente ProductCard.
 * Muestra un producto individual con su imagen, nombre, precio, calificación promedio
 * y un botón para añadir al carrito. Incluye una animación de aparición al desplazarse.
 * @param {object} props - Propiedades del componente.
 * @param {object} props.product - Objeto del producto a mostrar.
 * @param {function} props.addToCart - Función para añadir el producto al carrito.
 * @param {function} props.openProductDetail - Función para abrir el modal de detalles del producto.
 * @returns {JSX.Element} Elemento de tarjeta de producto.
 */
const ProductCard = ({ product, addToCart, openProductDetail }) => {
    const cardRef = useRef(null);
    const [isVisible, setIsVisible] = useState(false);

    // useEffect para observar la visibilidad del componente en el viewport
    useEffect(() => {
        const observer = new IntersectionObserver(
            ([entry]) => {
                // Si el elemento está intersectando (en el viewport) y aún no es visible
                if (entry.isIntersecting && !isVisible) {
                    setIsVisible(true);
                    observer.unobserve(entry.target); // Dejar de observar una vez que es visible
                }
            },
            {
                root: null, // El viewport como raíz
                rootMargin: '0px',
                threshold: 0.1 // Activar cuando el 10% del elemento es visible
            }
        );

        if (cardRef.current) {
            observer.observe(cardRef.current);
        }

        // Función de limpieza para desobservar cuando el componente se desmonta
        return () => {
            if (cardRef.current) {
                observer.unobserve(cardRef.current);
            }
        };
    }, [isVisible]); // Se vuelve a ejecutar si isVisible cambia (aunque el desobservador lo evita después del primer disparo)

    // Calcula la calificación promedio para el producto
    const averageRating = getAverageRating(product.reviews);

    return (
        <div
            ref={cardRef} // Referencia al div para el Intersection Observer
            className={`bg-white rounded-lg shadow-lg overflow-hidden flex flex-col items-center p-4 border border-purple-100 relative cursor-pointer
                        transform transition-all duration-700 ease-out
                        ${isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'}`} // Clases para la animación
            onClick={() => openProductDetail(product)} // Abre el modal de detalles al hacer clic en la tarjeta
        >
            {/* Etiqueta de promoción, si existe */}
            {product.promotionTag && (
                <span className="absolute top-2 left-2 bg-pink-500 text-white text-xs font-bold px-3 py-1 rounded-full shadow-md z-10">
                    {product.promotionTag}
                </span>
            )}
            <img
                src={product.image}
                alt={product.name}
                className="w-full h-48 object-cover rounded-md mb-4"
                // Manejo de errores para imágenes: muestra una imagen de placeholder si la carga falla
                onError={(e) => { e.target.onerror = null; e.target.src = `https://placehold.co/300x300/ece9f4/4b5563?text=Imagen+No+Disponible`; }}
            />
            <h3 className="text-xl font-semibold text-purple-800 text-center mb-2">{product.name}</h3>
            {/* Mostrar estrellas de calificación si hay reseñas */}
            {product.reviews && product.reviews.length > 0 ? (
                <div className="flex items-center mb-2">
                    {[...Array(5)].map((_, i) => (
                        <StarIcon
                            key={i}
                            fill={i < Math.round(averageRating) ? 'rgb(251 191 36)' : 'none'} // Rellena la estrella según la calificación
                            className="text-yellow-400 w-4 h-4"
                        />
                    ))}
                    <span className="ml-1 text-gray-600 text-sm">({product.reviews.length})</span> {/* Número de reseñas */}
                </div>
            ) : (
                <div className="h-6 mb-2"></div> // Espacio en blanco para mantener el diseño si no hay reseñas
            )}
            <p className="text-gray-600 text-sm text-center mb-4 flex-grow">{product.shortDescription}</p>
            <div className="flex flex-col items-center mb-4"> {/* Muestra el precio original y el actual */}
                {product.originalPrice && (
                    <span className="text-gray-400 line-through text-lg">${product.originalPrice.toFixed(2)}</span>
                )}
                <p className="text-pink-600 text-2xl font-bold">${product.price.toFixed(2)}</p>
                <p className="text-purple-500 text-sm font-medium mt-1">
                    ~ {((product.price * EXCHANGE_RATE_USD_TO_VES)).toFixed(2)} Bs {/* Precio en Bolívares */}
                </p>
            </div>
            <button
                onClick={(e) => { e.stopPropagation(); addToCart(product); }} // Evita que el clic en el botón abra el modal
                className="bg-purple-600 text-white px-6 py-3 rounded-full hover:bg-purple-700 transition duration-300 ease-in-out transform hover:scale-105 shadow-md hover:shadow-lg focus:outline-none focus:ring-2 focus:ring-purple-500 focus:ring-opacity-75 w-full"
            >
                Agregar al Carrito
            </button>
        </div>
    );
};

// -----------------------------------------------------------
// Componente ProductDetailModal
// Muestra los detalles completos de un producto en un modal.
// Incluye descripción larga, reseñas, productos relacionados y un botón de compra animado.
// -----------------------------------------------------------

/**
 * Componente ProductDetailModal.
 * Muestra los detalles completos de un producto en un modal. El botón "Agregar al Carrito"
 * tiene una animación de temblor que se activa periódicamente para llamar la atención.
 * @param {object} props - Propiedades del componente.
 * @param {object} props.product - El producto seleccionado para mostrar.
 * @param {function} props.addToCart - Función para añadir el producto al carrito.
 * @param {function} props.closeModal - Función para cerrar el modal.
 * @param {Array<Object>} props.allProducts - Todos los productos disponibles para filtrar los de venta adicional.
 * @returns {JSX.Element|null} Elemento modal de detalles del producto o null si no hay producto.
 */
const ProductDetailModal = ({ product, addToCart, closeModal, allProducts }) => {
    if (!product) return null; // No renderizar si no hay producto seleccionado

    // Estado para controlar la animación de temblor del botón
    const [isShaking, setIsShaking] = useState(false);
    
    // useEffect para activar la animación del botón cada 4 segundos
    useEffect(() => {
        const intervalId = setInterval(() => {
            setIsShaking(true);
            // La clase de animación se quita después de 500ms para permitir que se reinicie
            setTimeout(() => {
                setIsShaking(false);
            }, 500);
        }, 4000); // Repetir cada 4 segundos

        // Limpiar el intervalo cuando el modal se cierra o el producto cambia
        return () => clearInterval(intervalId);
    }, [product]); // El efecto se reinicia si se abre un modal de un producto diferente

    // Filtra los productos de venta adicional basados en los IDs en el objeto del producto
    const upsellProducts = allProducts.filter(p => product.upsellProducts && product.upsellProducts.includes(p.id));
    const averageRating = getAverageRating(product.reviews);

    return (
        <div className="fixed inset-0 bg-black bg-opacity-70 flex items-center justify-center z-50 p-4">
            <div className="bg-gradient-to-br from-white to-purple-50 rounded-lg shadow-2xl p-6 w-full max-w-4xl max-h-[90vh] overflow-y-auto relative animate-fadeInUp">
                <button
                    onClick={closeModal}
                    className="absolute top-4 right-4 text-gray-500 hover:text-gray-800 transition duration-200"
                    aria-label="Cerrar"
                >
                    <XIcon size={30} />
                </button>

                <div className="flex flex-col md:flex-row gap-6">
                    <div className="md:w-1/2 flex justify-center items-center">
                        <img
                            src={product.image}
                            alt={product.name}
                            className="max-w-full max-h-72 object-contain rounded-lg shadow-md border border-purple-100"
                            onError={(e) => { e.target.onerror = null; e.target.src = `https://placehold.co/400x400/ece9f4/4b5563?text=Imagen+No+Disponible`; }}
                        />
                    </div>
                    <div className="md:w-1/2">
                        <h2 className="text-3xl font-bold text-purple-800 mb-2">{product.name}</h2>
                        {product.promotionTag && (
                            <span className="bg-pink-500 text-white text-sm font-bold px-3 py-1 rounded-full shadow-md mb-3 inline-block">
                                {product.promotionTag}
                            </span>
                        )}
                        {product.reviews && product.reviews.length > 0 && (
                            <div className="flex items-center mb-3">
                                {[...Array(5)].map((_, i) => (
                                    <StarIcon
                                        key={i}
                                        fill={i < Math.round(averageRating) ? 'rgb(251 191 36)' : 'none'}
                                        className="text-yellow-400"
                                    />
                                ))}
                                <span className="ml-2 text-gray-600 text-base">({product.reviews.length} opiniones)</span>
                            </div>
                        )}
                        <div className="flex flex-col items-start mt-2 mb-4">
                            {product.originalPrice && (
                                <span className="text-gray-400 line-through mr-2 text-xl">${product.originalPrice.toFixed(2)}</span>
                            )}
                            <p className="text-pink-600 text-4xl font-extrabold">${product.price.toFixed(2)}</p>
                            <p className="text-purple-500 text-lg font-medium mt-1">
                                ~ {((product.price * EXCHANGE_RATE_USD_TO_VES)).toFixed(2)} Bs
                            </p>
                        </div>
                        {/* Título y lista de descripción larga */}
                        <h3 className="text-xl font-semibold text-purple-700 mt-4 mb-2">Descripción:</h3>
                        <ul className="list-disc list-inside text-gray-700 text-base space-y-1">
                            {product.longDescription.map((item, index) => (
                                <li key={index}>{item}</li>
                            ))}
                        </ul>
                        
                        {/* Botón de "Agregar al Carrito" con animación de temblor y ícono */}
                        <button
                            onClick={() => { addToCart(product); closeModal(); }} // Añade al carrito y cierra el modal
                            className={`w-full bg-purple-600 text-white px-6 py-3 rounded-full text-lg font-semibold
                                        flex items-center justify-center space-x-2 hover:bg-purple-700 transition-all duration-300
                                        ease-in-out transform hover:scale-105 shadow-md hover:shadow-lg focus:outline-none
                                        focus:ring-2 focus:ring-purple-500 focus:ring-opacity-75 mt-6 ${isShaking ? 'animate-shake' : ''}`}
                        >
                            <ShoppingCartIcon size={20} className="text-white" />
                            <span>Agregar al Carrito</span>
                        </button>
                    </div>
                </div>

                {/* Sección de Reseñas de Productos en el Modal (con scroll horizontal) */}
                {product.reviews && product.reviews.length > 0 && (
                    <div className="mt-8 border-t border-purple-200 pt-6">
                        <h3 className="text-2xl font-bold text-purple-800 mb-4 text-center">Opiniones de Clientes:</h3>
                        <div
                            className="flex overflow-x-auto snap-x snap-mandatory pb-4 hide-scrollbar"
                            style={{ scrollPaddingLeft: '1rem', scrollPaddingRight: '1rem' }} // Añade padding para el efecto de "snap"
                        >
                            {product.reviews.map(review => (
                                <div key={review.id} className="min-w-[280px] sm:min-w-[320px] flex-shrink-0 snap-center
                                                                bg-white p-4 rounded-lg shadow-sm border border-purple-100 mx-2">
                                    <div className="flex items-center mb-2">
                                        {[...Array(5)].map((_, i) => (
                                            <StarIcon
                                                key={i}
                                                fill={i < review.rating ? 'rgb(251 191 36)' : 'none'}
                                                className="text-yellow-400 w-5 h-5"
                                            />
                                        ))}
                                        <span className="ml-3 font-semibold text-purple-700 text-lg">{review.name}</span>
                                    </div>
                                    <p className="text-gray-700 italic mb-2">"{review.reviewText}"</p>
                                    <span className="text-sm text-gray-500">{review.date}</span>
                                </div>
                            ))}
                        </div>
                    </div>
                )}

                {/* Sección de Upsell (productos relacionados) */}
                {upsellProducts.length > 0 && (
                    <div className="mt-8 border-t border-purple-200 pt-6">
                        <h3 className="text-2xl font-bold text-purple-800 mb-4 text-center">También te podría interesar:</h3>
                        <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4">
                            {upsellProducts.map(upsellProduct => (
                                <div key={upsellProduct.id} className="bg-white rounded-lg shadow-md p-4 flex flex-col items-center cursor-pointer transition-transform duration-200 hover:scale-105">
                                    <img
                                        src={upsellProduct.image}
                                        alt={upsellProduct.name}
                                        className="w-24 h-24 object-cover rounded-md mb-2"
                                        onError={(e) => { e.target.onerror = null; e.target.src = `https://placehold.co/96x96/ece9f4/4b5563?text=N/A`; }}
                                    />
                                    <p className="font-semibold text-purple-700 text-center">{upsellProduct.name}</p>
                                    <p className="text-pink-600 font-bold mb-1">${upsellProduct.price.toFixed(2)}</p>
                                    <p className="text-purple-500 text-xs font-medium mb-3">
                                        ~ {((upsellProduct.price * EXCHANGE_RATE_USD_TO_VES)).toFixed(2)} Bs
                                    </p>
                                    <button
                                        onClick={() => { addToCart(upsellProduct); closeModal(); }}
                                        className="bg-pink-500 text-white text-sm px-4 py-2 rounded-full hover:bg-pink-600 transition duration-200 shadow-sm hover:shadow-md w-full"
                                    >
                                        <ShoppingCartIcon size={16} className="inline-block mr-1" /> Agregar
                                    </button>
                                </div>
                            ))}
                        </div>
                    </div>
                )}
            </div>
        </div>
    );
};

// -----------------------------------------------------------
// Componente CartOverlay
// Muestra el contenido del carrito de compras en una superposición lateral.
// Permite ajustar cantidades, eliminar productos y proceder al pedido por WhatsApp.
// Incluye opciones de entrega y métodos de pago condicionales.
// -----------------------------------------------------------

/**
 * Componente CartOverlay.
 * Muestra el contenido del carrito en una superposición lateral. Permite al usuario
 * actualizar cantidades, eliminar productos y seleccionar opciones de envío y pago
 * antes de generar un pedido por WhatsApp.
 * @param {object} props - Propiedades del componente.
 * @param {Array<Object>} props.cart - El arreglo de elementos en el carrito.
 * @param {function} props.updateQuantity - Función para actualizar la cantidad de un producto en el carrito.
 * @param {function} props.removeFromCart - Función para eliminar un producto del carrito.
 * @param {function} props.calculateTotal - Función para calcular el total del carrito.
 * @param {function} props.handleWhatsAppOrder - Función para generar el pedido por WhatsApp.
 * @param {function} props.closeCart - Función para cerrar el carrito.
 * @param {string} props.selectedDeliveryOption - Opción de entrega seleccionada ('caracas' o 'nacional').
 * @param {function} props.setSelectedDeliveryOption - Función para actualizar la opción de entrega.
 * @param {string} props.selectedPaymentMethod - Método de pago seleccionado.
 * @param {function} props.setSelectedPaymentMethod - Función para actualizar el método de pago.
 * @param {string} props.selectedShippingCompany - Compañía de envío seleccionada ('MRW' o 'Zoom').
 * @param {function} props.setSelectedShippingCompany - Función para actualizar la compañía de envío.
 * @param {string} props.shippingAddress - Dirección de la agencia de envío.
 * @param {function} props.setShippingAddress - Función para actualizar la dirección de la agencia.
 * @param {string} props.shippingState - Estado de la agencia de envío.
 * @param {function} props.setShippingState - Función para actualizar el estado de la agencia.
 * @returns {JSX.Element} Elemento de superposición del carrito.
 */
const CartOverlay = ({
    cart,
    updateQuantity,
    removeFromCart,
    calculateTotal,
    handleWhatsAppOrder,
    closeCart,
    selectedDeliveryOption,
    setSelectedDeliveryOption,
    selectedPaymentMethod,
    setSelectedPaymentMethod,
    selectedShippingCompany,
    setSelectedShippingCompany,
    shippingAddress,
    setShippingAddress,
    shippingState,
    setShippingState
}) => {
    const isCaracas = selectedDeliveryOption === 'caracas';
    const totalUSD = calculateTotal();
    const totalVES = totalUSD * EXCHANGE_RATE_USD_TO_VES;

    /**
     * Función envoltorio para handleWhatsAppOrder.
     * Asegura que las opciones de entrega y pago estén seleccionadas antes de proceder.
     */
    const handleWhatsAppOrderWrapper = () => {
        // Validación para asegurar que se hayan seleccionado todas las opciones necesarias
        if (!selectedDeliveryOption) {
            console.log('Por favor, selecciona una opción de entrega.');
            // Aquí podrías mostrar un mensaje al usuario en la UI
            return;
        }
        if (!selectedPaymentMethod) {
            console.log('Por favor, selecciona un método de pago.');
            // Aquí podrías mostrar un mensaje al usuario en la UI
            return;
        }

        // Si la entrega es nacional, también se debe seleccionar una compañía de envío y proporcionar dirección/estado
        if (selectedDeliveryOption === 'nacional') {
            if (!selectedShippingCompany) {
                console.log('Por favor, selecciona una compañía de envío.');
                // Aquí podrías mostrar un mensaje al usuario en la UI
                return;
            }
            if (!shippingAddress.trim() || !shippingState.trim()) {
                console.log('Por favor, ingresa la dirección de la agencia y el estado.');
                // Aquí podrías mostrar un mensaje al usuario en la UI
                return;
            }
        }

        // Si todas las validaciones pasan, procede con el pedido de WhatsApp
        handleWhatsAppOrder(selectedDeliveryOption, selectedPaymentMethod, selectedShippingCompany, shippingAddress, shippingState);
    };

    return (
        <div className="fixed inset-0 bg-black bg-opacity-50 flex justify-end z-50">
            {/* El contenedor principal del carrito ahora usa max-h-screen y overflow-y-auto */}
            <div className="bg-gradient-to-br from-purple-100 to-pink-50 w-full md:w-1/2 lg:w-1/3 max-h-screen overflow-y-auto shadow-2xl p-6 flex flex-col rounded-l-lg animate-slideIn">
                <div className="flex justify-between items-center mb-6 border-b pb-4 border-purple-300">
                    <h2 className="text-3xl font-bold text-purple-800">Tu Carrito</h2>
                    <XIcon
                        className="text-purple-600 hover:text-purple-800 cursor-pointer transition duration-200"
                        onClick={closeCart}
                        size={30}
                    />
                </div>

                <div className="flex-grow overflow-y-auto pr-2">
                    {cart.length === 0 ? (
                        <p className="text-gray-600 text-center py-8 text-lg">Tu carrito está vacío.</p>
                    ) : (
                        cart.map(item => (
                            <div key={item.product.id} className="flex items-center justify-between bg-white p-4 rounded-lg shadow-md mb-4 border border-pink-100">
                                <img
                                    src={item.product.image}
                                    alt={item.product.name}
                                    className="w-16 h-16 object-cover rounded-md mr-4"
                                    onError={(e) => { e.target.onerror = null; e.target.src = `https://placehold.co/64x64/ece9f4/4b5563?text=N/A`; }}
                                />
                                <div className="flex-grow">
                                    <h3 className="font-semibold text-lg text-purple-700">{item.product.name}</h3>
                                    <p className="text-gray-600">${item.product.price.toFixed(2)}</p>
                                    <p className="text-purple-500 text-sm font-medium mt-1">
                                        ~ {((item.product.price * item.quantity) * EXCHANGE_RATE_USD_TO_VES).toFixed(2)} Bs
                                    </p>
                                </div>
                                <div className="flex items-center space-x-2">
                                    <button
                                        onClick={() => updateQuantity(item.product.id, item.quantity - 1)}
                                        className="bg-purple-500 text-white w-8 h-8 rounded-full flex items-center justify-center hover:bg-purple-600 transition duration-200 text-lg font-bold disabled:opacity-50 disabled:cursor-not-allowed"
                                        disabled={item.quantity === 1}
                                    >
                                        -
                                    </button>
                                    <span className="text-xl font-semibold text-gray-800 w-8 text-center">{item.quantity}</span>
                                    <button
                                        onClick={() => updateQuantity(item.product.id, item.quantity + 1)}
                                        className="bg-purple-500 text-white w-8 h-8 rounded-full flex items-center justify-center hover:bg-purple-600 transition duration-200 text-lg font-bold"
                                    >
                                        +
                                    </button>
                                    <button
                                        onClick={() => removeFromCart(item.product.id)}
                                        className="bg-red-500 text-white w-8 h-8 rounded-full flex items-center justify-center hover:bg-red-600 transition duration-200 ml-2 text-sm"
                                        title="Eliminar"
                                    >
                                        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className="lucide lucide-trash-2"><path d="M3 6h18"/><path d="M19 6v14c0 1-1 2-2 2H7c-1 0-2-1-2-2V6"/><path d="M8 6V4c0-1 1-2 2-2h4c1 0 2 1 2 2v2"/><line x1="10" x2="10" y1="11" y2="17"/><line x1="14" x2="14" y1="11" y2="17"/></svg>
                                    </button>
                                </div>
                            </div>
                        ))
                    )}
                </div>

                <div className="border-t pt-6 mt-6 border-purple-300">
                    <div className="flex justify-between items-center mb-2">
                        <span className="text-2xl font-bold text-purple-800">Total:</span>
                        <span className="text-3xl font-extrabold text-pink-700">${totalUSD.toFixed(2)}</span>
                    </div>
                    <p className="text-right text-purple-600 text-xl font-semibold mb-4">~ {totalVES.toFixed(2)} Bs</p>

                    {/* Opciones de entrega */}
                    <div className="mb-4">
                        <h3 className="text-xl font-semibold text-purple-800 mb-2">¿Dónde deseas recibir tu pedido?</h3>
                        <div className="flex flex-col space-y-2">
                            <label className="inline-flex items-center">
                                <input
                                    type="radio"
                                    name="deliveryOption"
                                    value="caracas"
                                    checked={selectedDeliveryOption === 'caracas'}
                                    onChange={() => {
                                        setSelectedDeliveryOption('caracas');
                                        setSelectedPaymentMethod(''); // Resetear método de pago al cambiar opción
                                        setSelectedShippingCompany('');
                                        setShippingAddress('');
                                        setShippingState('');
                                    }}
                                    className="form-radio text-purple-600 h-5 w-5"
                                />
                                <span className="ml-2 text-gray-700 text-lg">En Caracas</span>
                            </label>
                            <label className="inline-flex items-center">
                                <input
                                    type="radio"
                                    name="deliveryOption"
                                    value="nacional"
                                    checked={selectedDeliveryOption === 'nacional'}
                                    onChange={() => {
                                        setSelectedDeliveryOption('nacional');
                                        setSelectedPaymentMethod(''); // Resetear método de pago al cambiar opción
                                        setSelectedShippingCompany('');
                                        setShippingAddress('');
                                        setShippingState('');
                                    }}
                                    className="form-radio text-purple-600 h-5 w-5"
                                />
                                <span className="ml-2 text-gray-700 text-lg">En el resto del país</span>
                            </label>
                        </div>
                    </div>

                    {/* Opciones de envío (solo si la opción de entrega es 'nacional') */}
                    {selectedDeliveryOption === 'nacional' && (
                        <div className="mb-4">
                            <h3 className="text-xl font-semibold text-purple-800 mb-2">Selecciona tu compañía de envío:</h3>
                            <div className="flex flex-col space-y-2">
                                <label className="inline-flex items-center">
                                    <input
                                        type="radio"
                                        name="shippingCompany"
                                        value="MRW"
                                        checked={selectedShippingCompany === 'MRW'}
                                        onChange={() => {
                                            setSelectedShippingCompany('MRW');
                                            setShippingAddress('');
                                            setShippingState('');
                                        }}
                                        className="form-radio text-purple-600 h-5 w-5"
                                    />
                                    <span className="ml-2 text-gray-700 text-lg">MRW</span>
                                </label>
                                <label className="inline-flex items-center">
                                    <input
                                        type="radio"
                                        name="shippingCompany"
                                        value="Zoom"
                                        checked={selectedShippingCompany === 'Zoom'}
                                        onChange={() => {
                                            setSelectedShippingCompany('Zoom');
                                            setShippingAddress('');
                                            setShippingState('');
                                        }}
                                        className="form-radio text-purple-600 h-5 w-5"
                                    />
                                    <span className="ml-2 text-gray-700 text-lg">Zoom</span>
                                        </label>
                            </div>
                        </div>
                    )}

                    {/* Campos de dirección y estado */}
                    {selectedDeliveryOption === 'nacional' && selectedShippingCompany && (
                        <div className="mb-4 space-y-4">
                            <div>
                                <label htmlFor="shippingAddress" className="block text-lg font-medium text-purple-800 mb-2">
                                    Dirección de la Agencia:
                                </label>
                                <input
                                    type="text"
                                    id="shippingAddress"
                                    value={shippingAddress}
                                    onChange={(e) => setShippingAddress(e.target.value)}
                                    placeholder="Ej: Av. Principal, C.C. El Sol, Local 10"
                                    className="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-500 focus:border-transparent transition duration-200"
                                    required
                                />
                            </div>
                            <div>
                                <label htmlFor="shippingState" className="block text-lg font-medium text-purple-800 mb-2">
                                    Estado:
                                </label>
                                <input
                                    type="text"
                                    id="shippingState"
                                    value={shippingState}
                                    onChange={(e) => setShippingState(e.target.value)}
                                    placeholder="Ej: Miranda"
                                    className="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-500 focus:border-transparent transition duration-200"
                                    required
                                />
                            </div>
                        </div>
                    )}

                    {/* Opciones de pago */}
                    {selectedDeliveryOption && (
                        <div className="mb-6">
                            <h3 className="text-xl font-semibold text-purple-800 mb-2">Selecciona tu método de pago:</h3>
                            <div className="flex flex-col space-y-2">
                                {isCaracas ? (
                                    <>
                                        <label className="inline-flex items-center">
                                            <input
                                                type="radio"
                                                name="paymentMethod"
                                                value="pago_movil"
                                                checked={selectedPaymentMethod === 'pago_movil'}
                                                onChange={() => setSelectedPaymentMethod('pago_movil')}
                                                className="form-radio text-pink-600 h-5 w-5"
                                            />
                                            <span className="ml-2 text-gray-700 text-lg">Pago Móvil</span>
                                        </label>
                                        <label className="inline-flex items-center">
                                            <input
                                                type="radio"
                                                name="paymentMethod"
                                                value="efectivo_contra_entrega"
                                                checked={selectedPaymentMethod === 'efectivo_contra_entrega'}
                                                onChange={() => setSelectedPaymentMethod('efectivo_contra_entrega')}
                                                className="form-radio text-pink-600 h-5 w-5"
                                            />
                                            <span className="ml-2 text-gray-700 text-lg">Efectivo contra entrega</span>
                                        </label>
                                    </>
                                ) : (
                                    <>
                                        <label className="inline-flex items-center">
                                            <input
                                                type="radio"
                                                name="paymentMethod"
                                                value="pago_movil_nacional"
                                                checked={selectedPaymentMethod === 'pago_movil_nacional'}
                                                onChange={() => setSelectedPaymentMethod('pago_movil_nacional')}
                                                className="form-radio text-pink-600 h-5 w-5"
                                            />
                                            <span className="ml-2 text-gray-700 text-lg">Pago Móvil (para envíos nacionales)</span>
                                        </label>
                                        <label className="inline-flex items-center">
                                            <input
                                                type="radio"
                                                name="paymentMethod"
                                                value="transferencia"
                                                checked={selectedPaymentMethod === 'transferencia'}
                                                onChange={() => setSelectedPaymentMethod('transferencia')}
                                                className="form-radio text-pink-600 h-5 w-5"
                                            />
                                            <span className="ml-2 text-gray-700 text-lg">Transferencia (para envíos nacionales)</span>
                                        </label>
                                        <p className="text-sm text-gray-500 mt-2">Envíos a todo el país por MRW o Zoom (cobro a destino).</p>
                                    </>
                                )}
                            </div>
                        </div>
                    )}

                    {/* Botón de Realizar Pedido por WhatsApp */}
                    <button
                        onClick={handleWhatsAppOrderWrapper}
                        // Deshabilitar el botón si el carrito está vacío o faltan selecciones
                        disabled={
                            cart.length === 0 ||
                            !selectedDeliveryOption ||
                            !selectedPaymentMethod ||
                            (selectedDeliveryOption === 'nacional' && (!selectedShippingCompany || !shippingAddress.trim() || !shippingState.trim()))
                        }
                        className="w-full bg-green-500 text-white py-4 rounded-full text-xl font-semibold
                                    flex items-center justify-center space-x-3 hover:bg-green-600 transition duration-300
                                    ease-in-out transform hover:scale-105 shadow-lg hover:shadow-xl
                                    focus:outline-none focus:ring-2 focus:ring-green-400 focus:ring-opacity-75
                                    disabled:opacity-50 disabled:cursor-not-allowed"
                    >
                        <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className="lucide lucide-whatsapp"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path></svg>
                        <span>Realizar Pedido por WhatsApp</span>
                    </button>
                </div>
            </div>
        </div>
    );
};

// -----------------------------------------------------------
// Componente CustomerReviews
// Muestra una sección de testimonios de clientes con desplazamiento horizontal.
// -----------------------------------------------------------

/**
 * Componente CustomerReviews.
 * Muestra una sección de testimonios de clientes con desplazamiento horizontal, con flechas de navegación.
 * @param {object} props - Propiedades del componente.
 * @param {Array<Object>} props.reviews - El arreglo de objetos de reseñas a mostrar.
 * @returns {JSX.Element} Elemento de la sección de reseñas de clientes.
 */
const CustomerReviews = ({ reviews }) => {
    const scrollContainerRef = useRef(null);
    const [canScrollLeft, setCanScrollLeft] = useState(false);
    const [canScrollRight, setCanScrollRight] = useState(false);

    // Función para desplazarse a la izquierda
    const scrollLeft = () => {
        if (scrollContainerRef.current) {
            scrollContainerRef.current.scrollBy({
                left: -scrollContainerRef.current.offsetWidth / 2, // Desplazarse media anchura del contenedor
                behavior: 'smooth'
            });
        }
    };

    // Función para desplazarse a la derecha
    const scrollRight = () => {
        if (scrollContainerRef.current) {
            scrollContainerRef.current.scrollBy({
                left: scrollContainerRef.current.offsetWidth / 2, // Desplazarse media anchura del contenedor
                behavior: 'smooth'
            });
        }
    };

    // Función para actualizar el estado de las flechas de desplazamiento
    const checkScrollability = () => {
        if (scrollContainerRef.current) {
            const { scrollLeft, scrollWidth, clientWidth } = scrollContainerRef.current;
            setCanScrollLeft(scrollLeft > 0);
            setCanScrollRight(scrollLeft + clientWidth < scrollWidth);
        }
    };

    // Efectos para inicializar el estado de las flechas y reaccionar a cambios de tamaño/scroll
    useEffect(() => {
        checkScrollability(); // Comprobar al montar el componente
        const currentRef = scrollContainerRef.current;
        if (currentRef) {
            currentRef.addEventListener('scroll', checkScrollability); // Comprobar al hacer scroll
            window.addEventListener('resize', checkScrollability); // Comprobar al redimensionar la ventana
        }

        // Limpieza de event listeners
        return () => {
            if (currentRef) {
                currentRef.removeEventListener('scroll', checkScrollability);
            }
            window.removeEventListener('resize', checkScrollability);
        };
    }, [reviews]); // Re-ejecutar si las reseñas cambian (aunque no deberían cambiar en este caso)

    return (
        <section className="container mx-auto p-4 md:p-8 my-12 bg-white rounded-xl shadow-lg relative">
            <h2 className="text-4xl font-bold text-center text-purple-800 mb-10">Lo que dicen nuestros clientes</h2>
            <div className="relative">
                {/* Flecha izquierda */}
                {canScrollLeft && (
                    <button
                        onClick={scrollLeft}
                        className="absolute left-0 top-1/2 -translate-y-1/2 bg-white p-2 rounded-full shadow-md z-10
                                   hover:bg-purple-100 transition duration-200 focus:outline-none focus:ring-2 focus:ring-purple-500"
                        aria-label="Desplazar reseñas a la izquierda"
                    >
                        <ChevronLeftIcon size={30} className="text-purple-600" />
                    </button>
                )}

                {/* Contenedor de reseñas con desplazamiento */}
                <div
                    ref={scrollContainerRef}
                    className="flex overflow-x-auto snap-x snap-mandatory pb-4 hide-scrollbar"
                    style={{ scrollPaddingLeft: '1rem', scrollPaddingRight: '1rem' }}
                >
                    {reviews.map(review => (
                        <div key={review.id} className="min-w-[calc(100%-2rem)] sm:min-w-[300px] lg:min-w-[350px] flex-shrink-0 snap-center
                                                        bg-gradient-to-br from-purple-50 to-pink-50 p-6 rounded-lg shadow-md
                                                        border border-purple-100 mx-2">
                            <div>
                                <div className="flex items-center mb-3">
                                    {[...Array(5)].map((_, i) => (
                                        <StarIcon
                                            key={i}
                                            fill={i < review.rating ? 'rgb(251 191 36)' : 'none'} // Tailwind yellow-400
                                            className="text-yellow-400"
                                        />
                                    ))}
                                </div>
                                <p className="text-gray-700 text-lg italic mb-4">"{review.reviewText}"</p>
                            </div>
                            <div className="flex justify-between items-center text-sm text-gray-500">
                                <span className="font-semibold text-purple-700">- {review.name}</span>
                                <span>{review.date}</span>
                            </div>
                        </div>
                    ))}
                </div>

                {/* Flecha derecha */}
                {canScrollRight && (
                    <button
                        onClick={scrollRight}
                        className="absolute right-0 top-1/2 -translate-y-1/2 bg-white p-2 rounded-full shadow-md z-10
                                   hover:bg-purple-100 transition duration-200 focus:outline-none focus:ring-2 focus:ring-purple-500"
                        aria-label="Desplazar reseñas a la derecha"
                    >
                        <ChevronRightIcon size={30} className="text-purple-600" />
                    </button>
                )}
            </div>
        </section>
    );
};

// -----------------------------------------------------------
// Componente FAQItem
// Muestra una pregunta y respuesta FAQ con funcionalidad de acordeón.
// -----------------------------------------------------------

/**
 * Componente FAQItem.
 * Muestra una pregunta frecuente con su respuesta, permitiendo expandir y colapsar la respuesta.
 * @param {object} props - Propiedades del componente.
 * @param {string} props.question - La pregunta.
 * @param {string} props.answer - La respuesta.
 * @param {boolean} props.isOpen - Si la respuesta está visible.
 * @param {function} props.setIsOpen - Función para cambiar el estado de visibilidad.
 * @returns {JSX.Element} Elemento de pregunta frecuente.
 */
const FAQItem = ({ question, answer, isOpen, setIsOpen }) => {
    return (
        <div className="border border-purple-200 rounded-lg overflow-hidden shadow-sm mb-4 bg-white">
            <button
                className="flex justify-between items-center w-full p-5 text-left text-lg font-semibold text-purple-800
                           bg-purple-50 hover:bg-purple-100 transition duration-300 focus:outline-none"
                onClick={() => setIsOpen(!isOpen)}
                aria-expanded={isOpen}
            >
                {question}
                <ChevronDownIcon
                    className={`transform transition-transform duration-300 ${isOpen ? 'rotate-180' : 'rotate-0'}`}
                    size={24}
                />
            </button>
            <div
                className={`overflow-hidden transition-all duration-300 ease-in-out ${isOpen ? 'max-h-screen opacity-100' : 'max-h-0 opacity-0'}`}
                style={{
                    // Hack para animar la altura sin conocerla
                    maxHeight: isOpen ? '1000px' : '0px',
                    padding: isOpen ? '1.25rem' : '0rem', // py-5 px-5
                }}
            >
                <p className="text-gray-700 leading-relaxed">
                    {answer}
                </p>
            </div>
        </div>
    );
};

// -----------------------------------------------------------
// Componente NewsletterSignup
// Formulario de suscripción a boletín.
// -----------------------------------------------------------

/**
 * Componente NewsletterSignup.
 * Proporciona un formulario para que los usuarios se suscriban a un boletín.
 * Muestra un mensaje de confirmación tras el envío.
 * @returns {JSX.Element} Elemento del formulario de suscripción al boletín.
 */
const NewsletterSignup = () => {
    const [email, setEmail] = useState('');
    const [message, setMessage] = useState('');
    const [isSuccess, setIsSuccess] = useState(false);

    const handleSubmit = (e) => {
        e.preventDefault();
        if (email && email.includes('@') && email.includes('.')) {
            // Simulación de envío
            console.log(`Email suscrito: ${email}`);
            setMessage('¡Gracias por suscribirte a nuestro boletín! Mantente al tanto de nuestras novedades.');
            setIsSuccess(true);
            setEmail('');
            setTimeout(() => setMessage(''), 5000); // Borra el mensaje después de 5 segundos
        } else {
            setMessage('Por favor, introduce un correo electrónico válido.');
            setIsSuccess(false);
        }
    };

    return (
        <section className="bg-purple-700 text-white py-12 px-6 md:px-12 mt-12">
            <div className="max-w-3xl mx-auto text-center">
                <h2 className="text-4xl font-bold mb-4">¡Mantente Conectado!</h2>
                <p className="text-xl mb-8 opacity-90">
                    Sé el primero en enterarte de nuevas ofertas, productos y consejos de bienestar.
                </p>
                <form onSubmit={handleSubmit} className="flex flex-col sm:flex-row items-center justify-center gap-4">
                    <input
                        type="email"
                        placeholder="Introduce tu correo electrónico"
                        value={email}
                        onChange={(e) => setEmail(e.target.value)}
                        className="w-full sm:w-2/3 px-5 py-3 rounded-full text-gray-900 border border-transparent
                                   focus:outline-none focus:ring-2 focus:ring-pink-300 focus:border-transparent transition-all duration-300"
                        required
                    />
                    <button
                        type="submit"
                        className="w-full sm:w-1/3 bg-pink-500 text-white px-6 py-3 rounded-full text-lg font-bold
                                   hover:bg-pink-600 transition duration-300 ease-in-out transform hover:scale-105
                                   shadow-lg focus:outline-none focus:ring-2 focus:ring-pink-300"
                    >
                        Suscribirme
                    </button>
                </form>
                {message && (
                    <p className={`mt-4 text-lg ${isSuccess ? 'text-green-300' : 'text-red-300'}`}>
                        {message}
                    </p>
                )}
            </div>
        </section>
    );
};

/**
 * Componente MarqueeText.
 * Muestra un texto que se desplaza horizontalmente para anunciar promociones.
 * @param {object} props - Propiedades del componente.
 * @param {string} props.text - El texto a mostrar en el marquee.
 * @returns {JSX.Element} Elemento del texto deslizante.
 */
const MarqueeText = ({ text }) => {
    return (
        <div className="bg-pink-500 text-white text-center py-2 px-4 overflow-hidden whitespace-nowrap shadow-md">
            <p className="inline-block text-lg font-semibold animate-marquee">
                {text}
            </p>
        </div>
    );
};


// -----------------------------------------------------------
// Componente principal de la aplicación (App)
// -----------------------------------------------------------

/**
 * Componente principal de la aplicación "Colágeno Club VE".
 * Gestiona el estado del carrito, la visibilidad de los modales y las opciones de pedido.
 * Renderiza el encabezado, la sección principal de productos, las reseñas de clientes,
 * y los modales condicionales del carrito y detalle de producto.
 * @returns {JSX.Element} El elemento raíz de la aplicación.
 */
export default function App() {
    // Estado para los productos en el carrito
    const [cart, setCart] = useState([]);
    // Estado para controlar la visibilidad de la superposición del carrito
    const [showCart, setShowCart] = useState(false);
    // Estado para almacenar el producto seleccionado para el modal de detalles
    const [selectedProduct, setSelectedProduct] = useState(null);
    // Estado para controlar la visibilidad del modal de detalles del producto
    const [showProductModal, setShowProductModal] = useState(false);

    // Estados para búsqueda y filtrado
    const [searchTerm, setSearchTerm] = useState('');
    const [selectedCategories, setSelectedCategories] = useState([]);
    const [filteredProducts, setFilteredProducts] = useState(initialProducts);

    // Nuevos estados para las opciones de entrega y pago del carrito
    const [selectedDeliveryOption, setSelectedDeliveryOption] = useState(''); // 'caracas' o 'nacional'
    const [selectedPaymentMethod, setSelectedPaymentMethod] = useState(''); // 'pago_movil', 'efectivo_contra_entrega', 'transferencia'
    const [selectedShippingCompany, setSelectedShippingCompany] = useState(''); // 'MRW' o 'Zoom'
    const [shippingAddress, setShippingAddress] = useState('');
    const [shippingState, setShippingState] = useState('');

    // Estado para controlar qué pregunta FAQ está abierta
    const [openFAQIndex, setOpenFAQIndex] = useState(null);

    // Estado para controlar la visibilidad del botón "Volver Arriba"
    const [showBackToTop, setShowBackToTop] = useState(false);

    // Lógica de búsqueda y filtrado
    useEffect(() => {
        let currentFilteredProducts = initialProducts.filter(product =>
            product.name.toLowerCase().includes(searchTerm.toLowerCase()) ||
            product.shortDescription.toLowerCase().includes(searchTerm.toLowerCase()) ||
            product.longDescription.some(desc => desc.toLowerCase().includes(searchTerm.toLowerCase()))
        );

        if (selectedCategories.length > 0) {
            currentFilteredProducts = currentFilteredProducts.filter(product =>
                product.category && product.category.some(cat => selectedCategories.includes(cat))
            );
        }

        setFilteredProducts(currentFilteredProducts);
    }, [searchTerm, selectedCategories]);

    // Efecto para controlar la visibilidad del botón "Volver Arriba"
    useEffect(() => {
        const handleScroll = () => {
            if (window.pageYOffset > 300) { // Mostrar el botón después de 300px de scroll
                setShowBackToTop(true);
            } else {
                setShowBackToTop(false);
            }
        };

        window.addEventListener('scroll', handleScroll);

        return () => {
            window.removeEventListener('scroll', handleScroll);
        };
    }, []);

    // Función para desplazar la página hacia arriba
    const scrollToTop = () => {
        window.scrollTo({
            top: 0,
            behavior: 'smooth' // Desplazamiento suave
        });
    };


    /**
     * Añade un producto al carrito o incrementa su cantidad si ya existe.
     * @param {object} product - El producto a añadir.
     */
    const addToCart = (product) => {
        setCart(prevCart => {
            const existingItemIndex = prevCart.findIndex(item => item.product.id === product.id);
            if (existingItemIndex > -1) {
                const newCart = [...prevCart];
                newCart[existingItemIndex].quantity += 1;
                return newCart;
            } else {
                return [...prevCart, { product, quantity: 1 }];
            }
        });
        setShowCart(true); // Abrir el carrito automáticamente al añadir un producto
    };

    /**
     * Actualiza la cantidad de un producto específico en el carrito.
     * @param {number} productId - El ID del producto a actualizar.
     */
    const updateQuantity = (productId, newQuantity) => {
        setCart(prevCart => {
            if (newQuantity <= 0) {
                // Si la nueva cantidad es 0 o menos, eliminar el producto del carrito
                return prevCart.filter(item => item.product.id !== productId);
            }
            return prevCart.map(item =>
                item.product.id === productId
                    ? { ...item, quantity: newQuantity }
                    : item
            );
        });
    };

    /**
     * Elimina un producto del carrito.
     * @param {number} productId - El ID del producto a eliminar.
     */
    const removeFromCart = (productId) => {
        setCart(prevCart => prevCart.filter(item => item.product.id !== productId));
    };

    /**
     * Calcula el precio total de todos los productos en el carrito.
     * @returns {number} El total del carrito en USD.
     */
    const calculateTotal = () => {
        return cart.reduce((total, item) => total + item.product.price * item.quantity, 0);
    };

    /**
     * Genera y abre un enlace de WhatsApp con el pedido.
     * @param {string} deliveryOption - Opción de entrega seleccionada.
     * @param {string} paymentMethod - Método de pago seleccionado.
     * @param {string} shippingCompany - Compañía de envío seleccionada (si aplica).
     * @param {string} shippingAddress - Dirección de la agencia (si aplica).
     * @param {string} shippingState - Estado de la agencia (si aplica).
     */
    const handleWhatsAppOrder = (deliveryOption, paymentMethod, shippingCompany, shippingAddress, shippingState) => {
        if (cart.length === 0) {
            console.log("El carrito está vacío, no se puede realizar el pedido.");
            return;
        }

        const phoneNumber = '584165853210'; // Número de WhatsApp para el pedido (ejemplo)
        let message = "¡Hola Colágeno Club VE! Me gustaría realizar el siguiente pedido:\n\n";

        cart.forEach(item => {
            message += `${item.product.name} (x${item.quantity}) - $${(item.product.price * item.quantity).toFixed(2)} (${((item.product.price * item.quantity) * EXCHANGE_RATE_USD_TO_VES).toFixed(2)} Bs)\n`;
        });

        message += `\nTotal: $${calculateTotal().toFixed(2)} (${(calculateTotal() * EXCHANGE_RATE_USD_TO_VES).toFixed(2)} Bs)\n`;

        message += `\nOpción de entrega: ${deliveryOption === 'caracas' ? 'En Caracas' : 'En el resto del país'}\n`;
        if (deliveryOption === 'nacional' && shippingCompany) {
            message += `Compañía de envío: ${shippingCompany}\n`;
            if (shippingAddress.trim() && shippingState.trim()) {
                message += `Dirección de la Agencia: ${shippingAddress}\n`;
                message += `Estado: ${shippingState}\n`;
            }
        }
        message += `Método de pago: ${paymentMethod.replace(/_/g, ' ')}\n`;

        if (paymentMethod.includes('pago_movil')) {
            message += `\nDetalles de Pago Móvil:\n`;
            message += `Banco: ${PAGO_MOVIL_DETAILS.bankNumber}\n`;
            message += `Teléfono: ${PAGO_MOVIL_DETAILS.phoneNumber}\n`;
            message += `Cédula: ${PAGO_MOVIL_DETAILS.idNumber}\n`;
        }

        if (deliveryOption === 'nacional') {
            message += `(Cobro a destino)\n`;
        }
        message += `\n¡Gracias!`;

        const encodedMessage = encodeURIComponent(message);
        const whatsappUrl = `https://wa.me/${phoneNumber}?text=${encodedMessage}`;
        window.open(whatsappUrl, '_blank');

        // Después de generar el pedido por WhatsApp, podrías limpiar el carrito
        setCart([]);
        setShowCart(false); // Cerrar el carrito
        setSelectedDeliveryOption(''); // Resetear opciones
        setSelectedPaymentMethod('');
        setSelectedShippingCompany('');
        setShippingAddress('');
        setShippingState('');
    };


    const openProductDetail = (product) => {
        setSelectedProduct(product);
        setShowProductModal(true);
    };

    const closeProductDetail = () => {
        setSelectedProduct(null);
        setShowProductModal(false);
    };

    const handleCategoryChange = (category) => {
        setSelectedCategories(prevCategories =>
            prevCategories.includes(category)
                ? prevCategories.filter(cat => cat !== category)
                : [...prevCategories, category]
        );
    };

    const availableCategories = [...new Set(initialProducts.flatMap(p => p.category || []))];


    return (
        <div className="min-h-screen bg-gradient-to-br from-purple-50 to-pink-50 font-sans text-gray-800">
            {/* CDN para Tailwind CSS y Google Font Inter */}
            <script src="https://cdn.tailwindcss.com"></script>
            <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet" />

            {/* Estilos CSS personalizados para animaciones y scrollbar */}
            <style>
                {`
                .animate-slideIn {
                    animation: slideIn 0.3s forwards ease-out;
                }
                @keyframes slideIn {
                    from {
                        transform: translateX(100%);
                    }
                    to {
                        transform: translateX(0);
                    }
                }
                .animate-fadeInUp {
                    animation: fadeInUp 0.3s forwards ease-out;
                }
                @keyframes fadeInUp {
                    from {
                        opacity: 0;
                        transform: translateY(20px);
                    }
                    to {
                        opacity: 1;
                        transform: translateY(0);
                    }
                }
                /* Animación de temblor para el botón */
                @keyframes shake {
                    10%, 90% { transform: translateX(-1px); }
                    20%, 80% { transform: translateX(2px); }
                    30%, 50%, 70% { transform: translateX(-3px); }
                    40%, 60% { transform: translateX(3px); }
                }
                .animate-shake {
                    animation: shake 0.5s ease-in-out;
                }

                /* Ocultar scrollbar pero mantener funcionalidad de scroll */
                .hide-scrollbar::-webkit-scrollbar {
                    display: none;
                }
                .hide-scrollbar {
                    -ms-overflow-style: none;  /* IE and Edge */
                    scrollbar-width: none;  /* Firefox */
                }

                /* Marquee Animation */
                .animate-marquee {
                    display: inline-block;
                    white-space: nowrap;
                    animation: marquee 15s linear infinite; /* Ajusta la duración para controlar la velocidad */
                }

                @keyframes marquee {
                    0% { transform: translateX(100%); }
                    100% { transform: translateX(-100%); }
                }
                `}
            </style>

            {/* Encabezado */}
            <header className="bg-white shadow-lg py-4 px-6 md:px-12 flex justify-between items-center sticky top-0 z-40 rounded-b-xl">
                <div className="flex items-center space-x-4">
                    {/* Logo actualizado según el screenshot del usuario */}
                    <img
                        src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhW464vcduASiIK4VNGeWCb6UVElpnqbnMcKGJiVQyqNU9QqE1CW2js0oACUuFM1FrW4rNfx-WhjVBPDKUGdpmks5aal_gV4QKYo3k6Zye1PuwpZhT1IWv6b6eHVcsGz-W_Gv58Afu8wrlQt19OdvPVEjEcPvwcyEDAgFBoaLqsTPhn3UtC6ZQvOnXyEw/s320/IMG_1754.jpeg"
                        alt="Colageno Club VE Logo"
                        className="h-12 object-contain"
                        onError={(e) => { e.target.onerror = null; e.target.src = `https://placehold.co/100x50/ffffff/4b5563?text=Logo`; }} // Fallback en caso de error
                    />
                    {/* El título "Collagen Store" se elimina si el logo ya incluye texto como en el screenshot */}
                </div>
                <nav className="flex items-center space-x-6">
                    <a href="https://www.instagram.com/colagenoclub.ve/" target="_blank" rel="noopener noreferrer"
                       className="text-gray-600 hover:text-pink-600 transition duration-300 transform hover:scale-110 flex items-center space-x-2"
                       aria-label="Visita nuestra página de Instagram">
                        <InstagramIcon size={28} className="text-pink-600" />
                        <span className="hidden md:inline text-lg font-medium">Instagram</span>
                    </a>
                    <button
                        onClick={() => setShowCart(true)}
                        className="relative p-2 rounded-full bg-purple-100 hover:bg-pink-100 transition duration-300 transform hover:scale-110
                                   focus:outline-none focus:ring-2 focus:ring-purple-500"
                        aria-label="Ver carrito de compras"
                    >
                        <ShoppingCartIcon size={28} className="text-pink-600" />
                        {cart.length > 0 && (
                            <span className="absolute -top-1 -right-1 bg-purple-500 text-white text-xs font-bold rounded-full h-5 w-5 flex items-center justify-center">
                                {cart.reduce((total, item) => total + item.quantity, 0)}
                            </span>
                        )}
                    </button>
                </nav>
            </header>

            {/* Marquee Text - Texto Deslizante */}
            <MarqueeText text="¡ENVÍO GRATIS POR COMPRAS MAYORES A $30! " />

            {/* Sección Hero */}
            <section
                className="relative w-full bg-cover bg-center h-96 flex items-center justify-center text-center px-4
                           rounded-xl my-8 mx-auto max-w-7xl" // Asegura bordes redondeados y ancho controlado
                style={{ backgroundImage: "url('https://i.blogs.es/20c7b9/istock-1060929022/840_560.jpeg')" }}
            >
                {/* Overlay ajustado para coincidir con el screenshot */}
                <div className="absolute inset-0 bg-gradient-to-t from-purple-800 to-transparent opacity-60 rounded-xl"></div>
                <div className="relative z-10 text-white">
                    <h2 className="text-4xl md:text-6xl font-extrabold mb-4 drop-shadow-lg">
                        La Belleza y el Bienestar en Cada Gota
                    </h2>
                    <p className="text-xl md:text-2xl font-light drop-shadow-md">
                        Tu secreto para una vida más plena y radiante.
                    </p>
                </div>
            </section>

            {/* Sección de Búsqueda y Filtro */}
            <section className="container mx-auto p-4 md:p-8 bg-white rounded-xl shadow-lg mb-12">
                <h2 className="text-3xl font-bold text-purple-800 mb-6 text-center">Encuentra tu Colágeno Ideal</h2>
                <div className="mb-6">
                    <input
                        type="text"
                        placeholder="Buscar productos por nombre o descripción..."
                        className="w-full p-4 border border-purple-300 rounded-full focus:outline-none focus:ring-2 focus:ring-pink-500 focus:border-transparent transition duration-200 shadow-sm"
                        value={searchTerm}
                        onChange={(e) => setSearchTerm(e.target.value)}
                    />
                </div>
                <div className="mb-6">
                    <h3 className="text-xl font-semibold text-purple-800 mb-3">Filtrar por Categoría:</h3>
                    <div className="flex flex-wrap gap-4 justify-center">
                        {availableCategories.map(category => (
                            <label key={category} className="inline-flex items-center bg-purple-100 px-4 py-2 rounded-full cursor-pointer hover:bg-purple-200 transition duration-200">
                                <input
                                    type="checkbox"
                                    value={category}
                                    checked={selectedCategories.includes(category)}
                                    onChange={() => handleCategoryChange(category)}
                                    className="form-checkbox h-5 w-5 text-pink-600 rounded focus:ring-pink-500"
                                />
                                <span className="ml-2 text-gray-700 font-medium">{category}</span>
                            </label>
                        ))}
                    </div>
                </div>
            </section>

            {/* Listado de Productos */}
            <main className="container mx-auto p-4 md:p-8">
                <h2 className="text-4xl font-bold text-center text-purple-800 mb-10 mt-6">Nuestros Productos</h2>
                {filteredProducts.length === 0 ? (
                    <p className="text-center text-gray-600 text-xl py-10">No se encontraron productos que coincidan con tu búsqueda.</p>
                ) : (
                    <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8">
                        {filteredProducts.map(product => (
                            <ProductCard
                                key={product.id}
                                product={product}
                                addToCart={addToCart}
                                openProductDetail={openProductDetail}
                            />
                        ))}
                    </div>
                )}
            </main>

            {/* Sección de Reseñas de Clientes (con desplazamiento horizontal) */}
            <CustomerReviews reviews={customerReviews} />

            {/* Sección de Preguntas Frecuentes (FAQ) */}
            <section id="faq" className="container mx-auto p-4 md:p-8 my-12 bg-white rounded-xl shadow-lg">
                <h2 className="text-4xl font-bold text-center text-purple-800 mb-10">Preguntas Frecuentes</h2>
                <div className="max-w-3xl mx-auto">
                    {faqData.map((faq, index) => (
                        <FAQItem
                            key={index}
                            question={faq.question}
                            answer={faq.answer}
                            isOpen={openFAQIndex === index}
                            setIsOpen={() => setOpenFAQIndex(openFAQIndex === index ? null : index)}
                        />
                    ))}
                </div>
            </section>

            {/* Newsletter / Suscripción para Novedades */}
            <NewsletterSignup />

            {/* Superposición del Carrito (CartOverlay) */}
            {showCart && (
                <CartOverlay
                    cart={cart}
                    updateQuantity={updateQuantity}
                    removeFromCart={removeFromCart}
                    calculateTotal={calculateTotal}
                    handleWhatsAppOrder={handleWhatsAppOrder}
                    closeCart={() => setShowCart(false)}
                    selectedDeliveryOption={selectedDeliveryOption}
                    setSelectedDeliveryOption={setSelectedDeliveryOption}
                    selectedPaymentMethod={selectedPaymentMethod}
                    setSelectedPaymentMethod={setSelectedPaymentMethod}
                    selectedShippingCompany={selectedShippingCompany}
                    setSelectedShippingCompany={setSelectedShippingCompany}
                    shippingAddress={shippingAddress}
                    setShippingAddress={setShippingAddress}
                    shippingState={shippingState}
                    setShippingState={setShippingState}
                />
            )}

            {/* Modal de Detalles del Producto */}
            {showProductModal && (
                <ProductDetailModal
                    product={selectedProduct}
                    addToCart={addToCart}
                    closeModal={closeProductDetail}
                    allProducts={initialProducts} // Pasamos todos los productos para los "upsell"
                />
            )}

            {/* Botón "Volver Arriba" flotante */}
            {showBackToTop && (
                <button
                    onClick={scrollToTop}
                    className="fixed bottom-6 right-6 bg-purple-600 text-white p-3 rounded-full shadow-lg
                               hover:bg-purple-700 transition-all duration-300 ease-in-out transform hover:scale-110
                               focus:outline-none focus:ring-2 focus:ring-purple-500 z-50"
                    aria-label="Volver arriba"
                >
                    <ChevronUpIcon size={28} />
                </button>
            )}

            {/* Pie de página */}
            <footer className="bg-purple-800 text-white py-6 px-4 text-center rounded-t-xl">
                <p className="text-lg">&copy; {new Date().getFullYear()} Colágeno Club VE. Todos los derechos reservados.</p>
                <div className="flex justify-center items-center space-x-4 mt-3">
                    <a href="https://www.instagram.com/colagenoclub.ve/" target="_blank" rel="noopener noreferrer"
                       className="text-white hover:text-pink-300 transition duration-300 transform hover:scale-125"
                       aria-label="Visita nuestra página de Instagram">
                        <InstagramIcon size={30} />
                    </a>
                </div>
            </footer>
        </div>
    );
}
