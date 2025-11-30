<script setup>
import { ref } from 'vue';

// --- Importa el nuevo FondoMatrix ---
// (Asegúrate que la ruta './FondoMatrix.vue' sea correcta)
import FondoMatrix from './FondoMatrix.vue'; 

// Arreglo reactivo (ref) con tus intereses personalizados
const intereses = ref([
    'Tecnología y Desarrollo de Software: Apasionado por la programación, la resolución de problemas complejos y la exploración de nuevas tecnologías.',
    'Analisis de datos: Apasionado por el analisis de datos, realizando actividades laborales relacionadas y enfocado en potenciar mi carrera con mi experiencia laboral',
]);
</script>

<template>
    <div class="seccion-intereses-container">
        
        <FondoMatrix class="fondo-matrix-bg" /> 
        
        <div class="intereses-contenedor">
            <ul class="contenedor-lista">
                <li class="item" v-for="interes in intereses" :key="interes">
                    {{ interes }}
                </li>
            </ul>
        </div>

    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

/* Variables de Color (Azul Tech Glassmorphism) */
:root {
    --color-primary-accent: #00aaff;
    --color-text-light: #FFFFFF;
    --cardBgColor: rgba(15, 28, 45, 0.5); 
    --lineColor: rgba(0, 170, 255, 0.4); 
    --shadowColor: rgba(0, 0, 0, 0.5); 
    --font-sans: 'Inter', sans-serif;
}

/* --- Contenedor Principal (Compacto) --- */
.seccion-intereses-container {
    position: relative; 
    overflow: hidden; 
    
    /* 🔥 AJUSTE CLAVE: Se elimina min-height para que la altura se ajuste al contenido */
    height: auto;
    
    display: flex;
    justify-content: center;
    align-items: center;
    /* Dejamos padding vertical para que no quede pegado */
    padding: 3rem 1rem; 
    font-family: var(--font-sans); 
}

/* --- Estilo para el componente de fondo --- */
.fondo-matrix-bg {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 0; 
    object-fit: cover; 
}


/* --- Tarjeta Glassmorphism (Tu contenedor original) --- */
.intereses-contenedor {
    position: relative; 
    z-index: 1; 
    margin: 0 auto;
    max-width: 85%;
    padding: 1rem; 
    overflow: hidden; 
    border-radius: 12px; 
    
    /* Estilos Glassmorphism */
    background: var(--cardBgColor);
    backdrop-filter: blur(8px); 
    -webkit-backdrop-filter: blur(8px); 
    border: 2px solid var(--lineColor); 
    box-shadow: 0 10px 30px var(--shadowColor); 
}

.contenedor-lista {
    list-style-type: none;
    padding: 0.5rem; 
    margin: 0;
    
    /* Texto blanco brillante */
    color: #FFFFFF !important; 
    
    font-size: 1.1rem; 
    font-weight: 400;
    line-height: 1.5; 
    text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.6); 
}

.item {
    margin-bottom: 1rem; 
}

.item:last-child {
    margin-bottom: 0;
}

/* --- Responsividad para Móvil --- */
@media (max-width: 768px) {
    .intereses-contenedor {
        max-width: 95%;
        padding: 0.8rem; 
    }
    .contenedor-lista {
        font-size: 0.95rem; 
        padding: 0.5rem;
        line-height: 1.4; 
    }
}
</style>