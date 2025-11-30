<script setup>
// Se importa ref de vue para poder usarlo
import { ref } from 'vue';

// --- Imports de iconos (Solo los que usás en tu lista) ---
import img1 from '@/components/icons/js.svg';
import img2 from '@/components/icons/python.svg';
import img3 from '@/components/icons/html-css.svg';
import img4 from '@/components/icons/java.svg';
import img5 from '@/components/icons/sql.svg';
import img7 from '@/components/icons/vue.svg';
import img8 from '@/components/icons/node.svg';
import img11 from '@/components/icons/git.svg';
import img15 from '@/components/icons/visual.svg';
import img17 from '@/components/icons/mysql.svg';
import img19 from '@/components/icons/arg.svg';
import img20 from '@/components/icons/eeuu.svg';


//Se crea un array de objetos con TUS habilidades
const habilidades = ref([
    {// Se crea un objeto con id, nombre y habilidades
        id: 1, nombre: 'Lenguajes de Programación', habilidades: [
            { id: 1, nombre: 'JavaScript', nivel: 'Básico', icono: img1 },
            { id: 2, nombre: 'Python', nivel: 'Básico', icono: img2 },
            { id: 3, nombre: 'HTML/CSS', nivel: 'Básico', icono: img3 },
            { id: 4, nombre: 'Java', nivel: 'Básico', icono: img4 },
            { id: 5, nombre: 'SQL', nivel: 'Básico', icono: img5 }
        ]
    },
    {
        id: 2, nombre: 'Frameworks y Librerías', habilidades: [
            { id: 1, nombre: 'Vue.js', nivel: 'Básico', icono: img7 },
            { id: 2, nombre: 'Node.js', nivel: 'Básico', icono: img8 },
        ]
    },
    {
        id: 3, nombre: 'Herramientas y Software', habilidades: [
            { id: 1, nombre: 'Git', nivel: 'Intermedio', icono: img11 },
            { id: 2, nombre: 'Visual Studio Code', nivel: 'Básico', icono: img15 }
        ]
    },
    {
        id: 4, nombre: 'Bases de Datos', habilidades: [
            { id: 1, nombre: 'MySQL', nivel: 'Básico', icono: img17 },
        ]
    },
    {
        id: 5, nombre: 'Idiomas', habilidades: [
            { id: 1, nombre: 'Español', nivel: 'Nativo', icono: img19 },
            { id: 2, nombre: 'Inglés', nivel: 'Elemental (A2)', icono: img20 }
        ]
    }
]);

</script>


<template>
    <div class="seccion-skills-container">
        <div class="skills-wrapper">
            <div v-for="habilidad in habilidades" :key="habilidad.id" class="skills-categoria">
                <h3>{{ habilidad.nombre }}</h3>
                <ul class="skills">
                    <li v-for="skill in habilidad.habilidades" :key="skill.id" class="skill">
                        <img :src="skill.icono" :alt="skill.nombre">
                        <span>{{ skill.nombre }}</span>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

/* Variables de Color (Azul Tech Glassmorphism) */
:root {
    --color-primary-accent: #00aaff; /* Azul brillante */
    --color-text-light: #FFFFFF; /* Blanco puro */
    --color-text-description: #c0e6fa; /* Azul claro para descripciones */
    --bgColor: #0f1c2d; 
    --cardBgColor: rgba(15, 28, 45, 0.5); 
    --lineColor: rgba(255, 255, 255, 0.4); /* Línea BLANCA semitransparente */
    --shadowColor: rgba(0, 0, 0, 0.5); 
    --hoverShadow: rgba(0, 170, 255, 0.6); 
    --font-sans: 'Inter', sans-serif;
}

/* --- Contenedor Principal (Fondo Animado Restaurado) --- */
.seccion-skills-container {
    /* Fondo Animado */
    background: linear-gradient(-45deg, #001f3f, #0074D9, #001f3f, #1a1a1a);
    background-size: 400% 400%;
    animation: gradientBG 30s ease infinite;

    /* 🔥 COMPACTADO: Eliminamos min-height y ajustamos padding */
    height: auto;
    padding: 3rem 1rem;
    
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: var(--font-sans); 
}

/* Keyframes para la animación */
@keyframes gradientBG {
    0% {
        background-position: 0% 50%;
    }
    50% {
        background-position: 100% 50%;
    }
    100% {
        background-position: 0% 50%;
    }
}


.skills-wrapper {
    width: 100%;
    max-width: 900px; 
    padding: 1rem;
}

.skills-categoria {
    margin-bottom: 2rem; /* 🔥 COMPACTADO */
}

.skills-categoria h3 {
    display: flex;
    justify-content: left; 
    margin-bottom: 1.2rem; /* 🔥 COMPACTADO */
    font-size: 1.4em; /* 🔥 COMPACTADO */
    color: #FFFFFF !important; /* Texto del título en blanco brillante */
    font-weight: 600;
    border-bottom: 2px solid var(--lineColor); /* Línea blanca visible */
    padding-bottom: 0.5rem;
}

/* 🔥 CAMBIO A DISEÑO DE TABLA/GRID */
.skills {
    display: grid;
    /* 🔥 COMPACTADO: Columnas más pequeñas (mínimo 120px) */
    grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
    gap: 12px; /* 🔥 COMPACTADO */
    list-style: none;
    padding: 0;
}

/* Tarjeta de habilidad individual */
.skill {
    display: flex;
    flex-direction: column; 
    justify-content: center;
    align-items: center;
    gap: 8px; /* 🔥 COMPACTADO */
    
    /* Efecto "GLASSMORPHISM" con tu paleta */
    background: var(--cardBgColor);
    backdrop-filter: blur(8px); 
    -webkit-backdrop-filter: blur(8px); 
    border: 2px solid rgba(0, 170, 255, 0.4); 
    
    padding: 1rem 0.5rem; /* 🔥 COMPACTADO */
    border-radius: 10px; /* Bordes más sutiles */
    
    transition: all 0.3s ease;
    text-align: center;
}

.skill:hover {
    transform: scale(1.05); 
    box-shadow: 0 8px 25px var(--hoverShadow); 
    border-color: var(--color-primary-accent); 
}

.skill img {
    width: 32px; /* 🔥 COMPACTADO */
    height: 32px; /* 🔥 COMPACTADO */
}

.skill span {
    font-size: 1em; /* 🔥 COMPACTADO */
    color: #FFFFFF !important; 
    font-weight: 500; /* Un poco más ligero que el 600 anterior */
}

/* --- RESPONSIVIDAD PARA MÓVIL --- */
@media (max-width: 768px) {
    .skills-wrapper {
        padding: 0.5rem; 
    }

    .skills-categoria h3 {
        justify-content: center; 
        font-size: 1.2em; /* 🔥 COMPACTADO */
    }

    /* Ajustamos el grid para móviles */
    .skills {
        /* 🔥 COMPACTADO: Columnas aún más pequeñas */
        grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
        gap: 8px; 
    }

    .skill {
        padding: 0.8rem 0.4rem; /* 🔥 COMPACTADO */
        gap: 6px; /* 🔥 COMPACTADO */
    }

    .skill img {
        width: 28px; /* 🔥 COMPACTADO */
        height: 28px; /* 🔥 COMPACTADO */
    }

    .skill span {
        font-size: 0.9em; /* 🔥 COMPACTADO */
    }

    .skill:hover {
        transform: scale(1);
        box-shadow: none;
        border-color: var(--color-primary-accent);
    }
}
</style>