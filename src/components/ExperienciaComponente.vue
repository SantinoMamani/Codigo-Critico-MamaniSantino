<script setup>
import icono1 from '/src/assets/agriculture.svg'; 
import icono3 from '/src/assets/bna.webp'; 
import icono5 from '/src/assets/git.svg'; 

import { ref } from 'vue';

const titulo = 'Desarrollador Full Stack';
const fecha = 'Desde Marzo 2025 / Actualidad';
const experiencias = ref([
    { id: 1, src: icono1, parrafo: 'Desarrollé "Agro Gestión Integral", un sistema de escritorio full-stack en Java (con NetBeans) para la gestión agrícola, incluyendo el diseño de la base de datos MySQL.' },
    { id: 2, src: icono3, parrafo: 'Trabajo en el BNA realizando tareas de analisis de datos relacionados con el control y seguimiento de servicion realizando la aplicacion de multas y penalidades y trabajando en el sector de facturacion de servicios' },
    { id: 3, src: icono5, parrafo: 'Gestioné el control de versiones de múltiples proyectos con Git, manejando repositorios, ramas (branching) y colaboración en equipo a través de GitHub.' }
]);
</script>

<template>
    <div class="seccion-experiencia-container">
        <div class="card">
            <h3 class="titulo">{{ titulo.toLocaleUpperCase() }}</h3>
            <p class="fecha">{{ fecha }}</p>
            <ul class="listado">
                <li class="item" v-for="experencia in experiencias" :key="experencia.id">
                    <img class="imagen-svg" :src="experencia.src" alt="Ícono representativo">
                    <p>{{ experencia.parrafo }}</p>
                </li>
            </ul>
        </div>
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

/* Variables de Color (Azul Tech Glassmorphism) */
:root {
    --color-primary-accent: #00aaff; /* Azul brillante para títulos */
    --color-secondary-accent: #FFFFFF; /* Blanco para fecha */
    --bgColor: #0f1c2d; 
    --cardBgColor: rgba(15, 28, 45, 0.5); 
    --lineColor: rgba(0, 170, 255, 0.2); 
    --shadowColor: rgba(0, 0, 0, 0.37); 
    --hoverShadow: rgba(0, 170, 255, 0.5); 
    --color-text-light: #FFFFFF; /* Blanco puro para texto principal */
    --font-sans: 'Inter', sans-serif;
}

/* --- Contenedor principal --- */
.seccion-experiencia-container {
    background: linear-gradient(135deg, #0f1c2d, #1a2a3a);
    height: auto; 
    min-height: 50vh; 
    padding: 4rem 1rem; 
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%; 
}

/* --- Estilos de la Tarjeta (Glassmorphism) --- */
.card {
    display: flex;
    flex-direction: column;
    
    background: var(--cardBgColor);
    backdrop-filter: blur(8px); 
    -webkit-backdrop-filter: blur(8px); 
    border: 1px solid var(--lineColor); 
    box-shadow: 0 10px 30px var(--shadowColor); 

    padding: 1.5rem; 
    border-radius: 12px;
    max-width: 800px; 
    width: 100%; 
    margin: 0; 
    font-family: var(--font-sans);
    color: #FFFFFF; /* 🔥 FORZAMOS el color blanco al contenedor */
}

.titulo {
    font-size: 1.5rem; 
    color: var(--color-primary-accent); /* Mantiene el azul brillante */
    margin-bottom: 0.5rem;
    font-weight: 700;
    letter-spacing: 0.05em;
}

.fecha {
    font-size: 1rem; 
    /* 🔥 FORZAMOS EL BLANCO PURO AQUÍ */
    color: #FFFFFF; 
    margin-bottom: 1.5rem; 
    font-weight: 400; 
}

.listado {
    display: flex;
    flex-direction: column;
    list-style: none;
    padding: 0;
    margin: 0;
}

.item {
    display: flex;
    align-items: flex-start; 
    padding: 1rem 0; 
    gap: 1rem; 
    border-bottom: 1px solid var(--lineColor); 
    transition: background-color 0.3s ease; 
}

.item:last-child {
    border-bottom: none;
}

.item:hover {
    background-color: rgba(0, 170, 255, 0.05); 
    border-radius: 5px; 
}

/* --- Estilos para el Ícono SVG --- */
.imagen-svg {
    width: 42px; 
    height: 42px; 
    flex-shrink: 0; 
    
    filter: drop-shadow(0 0 8px rgba(0, 170, 255, 0.6)); 
    
    margin-top: 0.2rem; 
    transition: transform 0.2s ease, filter 0.2s ease; 
}

.item:hover .imagen-svg {
    transform: translateY(-3px) scale(1.08); 
    filter: drop-shadow(0 0 12px rgba(0, 170, 255, 0.9)); 
}


.item p {
    font-size: 0.95rem; 
    /* 🔥 FORZAMOS EL BLANCO PURO AQUÍ TAMBIÉN */
    color: #FFFFFF; 
    line-height: 1.6; 
    margin: 0; 
}


/* --- Media Query para Desktop (Tablet en adelante) --- */
@media (min-width: 600px) {
    .seccion-experiencia-container {
        padding: 5rem 1rem; 
    }

    .card {
        padding: 2.5rem; 
        width: 90%; 
    }

    .titulo {
        font-size: 1.8rem;
    }

    .fecha {
        font-size: 1.1rem;
        color: #FFFFFF; /* Reafirmamos el blanco */
        margin-bottom: 2rem;
    }
    
    .item {
        padding: 1.2rem 0; 
        gap: 1.5rem; 
    }
    
    .item p {
        font-size: 1rem;
        color: #FFFFFF; /* Reafirmamos el blanco */
    }

    .imagen-svg {
        width: 48px; 
        height: 48px;
    }
}
</style>