<script setup>
import { ref } from 'vue';

/* Colores Azules Modernos */
const fechaColor = ref([
  {color: '#00aaff'}, // Azul brillante para UTN (En curso)
  {color: '#41516c'}  // Azul oscuro/elegante para U. Maza (Finalizado)
]);

const educacion = ref([
  {
    fecha: '2025', 
    title: 'Tecnicatura Universitaria en Programación', 
    descripcion: 'Cursando en la Universidad Tecnológica Nacional (UTN) - Facultad Regional Mendoza. Adquiriendo habilidades en desarrollo de software, lenguajes de programación y análisis de sistemas.', 
    enlace:'https://www.frsr.utn.edu.ar/'
  }
]);
</script>

<template>
    <section class="seccion-educacion">
        <ul>
            <li v-for="(item, index) in educacion" :key="index" :style="{ '--fecha-color': fechaColor[index].color}">
            <div class="fecha">{{ item.fecha }}</div>
            <h3 class="title">{{ item.title }}</h3>
            <div class="descripcion">{{ item.descripcion }}</div>
            <a class="enlace" :href="item.enlace" target="_blank">Saber más</a>
        </li>
        </ul>
    </section>
</template>

<style scoped>
/* Estilos generales y variables (Glassmorphism) */
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* --- CONTENEDOR PRINCIPAL (Compacto y Define el fondo) --- */
.seccion-educacion {
    background: linear-gradient(135deg, #0f1c2d, #1a2a3a);
    
    /* 🔥 AJUSTE CLAVE PARA COMPACTAR: Eliminamos 100vh y reducimos padding vertical */
    height: auto; 
    min-height: 50vh; /* Se mantiene un mínimo, pero es ajustable */
    padding: 4rem 1rem; 
    
    display: flex;
    justify-content: center;
    align-items: center;
    
    font-family: 'Inter', sans-serif;
    color: #e0f2f7; 

    /* Variables Glassmorphism */
    --bgColor: #0f1c2d; 
    --cardBgColor: rgba(15, 28, 45, 0.5); 
    --lineColor: rgba(0, 170, 255, 0.2); 
    --shadowColor: rgba(0, 0, 0, 0.37); 
    --hoverShadow: rgba(0, 170, 255, 0.5); 
}


/* Estilos para la lista (timeline) */
ul {
  --col-gap: 1.5rem; 
  --row-gap: 2.5rem; 
  --line-w: 0.2rem; 
  display: grid;
  grid-template-columns: var(--line-w) 1fr; 
  grid-auto-columns: max-content;
  column-gap: var(--col-gap);
  list-style: none;
  width: min(70rem, 100%); 
  margin-inline: auto;
  position: relative;
  margin-top: 0; 
  padding-bottom: 0; 
}

/* Espacio vertical entre ítems */
ul li:not(:last-child) {
    margin-bottom: var(--row-gap);
}

/* Estilo para la línea vertical */
ul::before {
  content: "";
  grid-column: 1;
  grid-row: 1 / span 20;
  background: var(--lineColor);
  border-radius: calc(var(--line-w) / 2);
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0;
  width: var(--line-w);
}

/* Estilo para cada ítem de la lista (tarjeta) */
ul li {
  grid-column: 2;
  --inlineP: 1rem; 
  margin-inline: var(--inlineP); 
  grid-row: span 2;
  display: grid;
  grid-template-rows: min-content min-content min-content auto; 
  
  /* --- Efecto Glassmorphism --- */
  background: var(--cardBgColor);
  backdrop-filter: blur(8px); 
  -webkit-backdrop-filter: blur(8px); 
  border-radius: 12px; 
  border: 1px solid var(--lineColor); 
  box-shadow: 0 4px 16px var(--shadowColor); 
  
  transition: transform 0.3s ease, box-shadow 0.3s ease; 
  padding: 1.5rem; 
  position: relative; 
}

/* Efecto hover */
ul li:hover {
    transform: translateY(-5px); 
    box-shadow: 0 10px 25px var(--hoverShadow); 
}

/* Estilo para la fecha */
ul li .fecha {
  --dateH: 2.5rem; 
  height: var(--dateH);
  line-height: var(--dateH); 
  text-align: center;
  background-color: var(--fecha-color);
  color: white;
  font-size: 0.9rem; 
  font-weight: 600; 
  border-radius: 4px; 
  position: absolute; 
  top: 1.5rem; 
  left: calc(-1 * var(--inlineP)); 
  padding: 0 0.8rem; 
  min-width: 5rem; 
  z-index: 1; 
}

/* Círculo que conecta la fecha con la línea */
ul li .fecha::after {
  content: "";
  position: absolute;
  width: 0.8rem; 
  aspect-ratio: 1;
  background: var(--bgColor); 
  border: 0.2rem solid var(--fecha-color); 
  border-radius: 50%;
  top: 50%;
  transform: translate(-50%, -50%); 
  left: calc(var(--inlineP) * -1 - (var(--line-w) / 2) );
  z-index: 2; 
}

/* Estilos de Contenido */
ul li .title {
  padding-block-start: 0.5rem; 
  padding-block-end: 0.5rem;
  font-weight: 600; 
  font-size: 1.1rem; 
  margin-top: 2rem; 
  color: #00aaff; 
}

ul li .descripcion {
  padding-block-end: 1rem;
  font-weight: 400; 
  line-height: 1.5; 
  color: #c0e6fa; 
  font-size: 0.95rem;
}

/* Enlace "Saber más" */
ul li .enlace {
    display: inline-block; 
    margin-top: 0.8rem;
    padding: 0.4rem 0.8rem; 
    background-color: var(--fecha-color);
    color: white;
    text-decoration: none;
    border-radius: 4px;
    font-size: 0.85rem;
    font-weight: 500;
    transition: filter 0.3s ease, transform 0.2s ease;
    align-self: start; 
    justify-self: start; 
    box-shadow: 0 2px 8px rgba(0, 170, 255, 0.4); 
}

ul li .enlace:hover {
    filter: brightness(1.2); 
    transform: translateY(-2px);
}

ul li .title::before,
ul li .descripcion::before,
ul li .fecha::before {
  content: none;
}


/* --- Media query para pantallas anchas (Desktop Compacto) --- */
@media (min-width: 40rem) {
  ul {
    /* Ajuste clave: Reduce el espacio horizontal entre línea y tarjetas */
    --col-gap: 2rem; 
    
    grid-template-columns: 1fr var(--line-w) 1fr;
    padding: 0; /* Eliminamos padding vertical */
  }
  
  ul li:not(:last-child) {
      margin-bottom: 2rem; /* Espacio vertical reducido */
  }

  ul li {
      padding: 1.5rem; /* Padding interno reducido */
  }

  /* Centramos la línea vertical */
  ul::before {
    grid-column: 2;
    left: 50%; 
    transform: translateX(-50%); 
  }
  
  /* Elementos Impares (Lado Izquierdo) */
  ul li:nth-child(odd) {
    grid-column: 1;
    margin-inline-end: var(--col-gap); 
    margin-inline-start: 0;
    padding-right: 1.5rem;
    padding-left: 2.5rem; 
  }
  
  /* Elementos Pares (Lado Derecho) */
  ul li:nth-child(even) {
    grid-column: 3;
    margin-inline-start: var(--col-gap);
    margin-inline-end: 0;
    padding-left: 1.5rem;
    padding-right: 2.5rem; 
  }

  /* Posicionamiento de fechas (sin cambios en la lógica) */
  ul li:nth-child(odd) .fecha {
    left: auto;
    right: calc(-1 * var(--inlineP)); 
  }

  ul li:nth-child(odd) .fecha::after {
    transform: translate(50%, -50%); 
    left: auto;
    right: calc(var(--inlineP) * -1 - (var(--line-w) / 2) );
  }

  ul li:nth-child(even) .fecha {
    left: calc(-1 * var(--inlineP));
    right: auto;
  }

  ul li:nth-child(even) .fecha::after {
    transform: translate(-50%, -50%); 
    left: calc(var(--inlineP) * -1 - (var(--line-w) / 2) );
    right: auto;
  }
  
  /* Alineación de Contenido */
  ul li:nth-child(odd) .title,
  ul li:nth-child(odd) .descripcion,
  ul li:nth-child(odd) .enlace {
      text-align: right; 
      justify-self: end;
  }

  ul li:nth-child(even) .title,
  ul li:nth-child(even) .descripcion,
  ul li:nth-child(even) .enlace {
      text-align: left; 
      justify-self: start;
  }

  ul li:nth-child(2) {
    grid-row: auto;
  }
}
</style>