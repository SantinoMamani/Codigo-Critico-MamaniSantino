<script setup>
// Asegúrate de que estas rutas sean correctas en tu proyecto
import linkedin from '/src/assets/linkedin_icon.svg';
import instagram from '/src/assets/instagram_icon.svg';
import github from '/src/assets/github_icon.svg';
// IMPORTANTE: La ruta de la foto se mantiene
import fotoPerfil from '/src/assets/santino-mamani-photo.jpg'; 

const title = 'Santino Mamani';
const descripcion = 'Estudiante en Técnicatura Universitaria en Programación - UTN';
const residencia = 'Burzaco, Buenos Aires, Argentina';
const presentacion = 'Hola, Bienvenido a mi portafolio. Soy estudiante de la Tecnicatura Universitaria en Programación, enfocado en aprender sobre el desarrollo de software.';
const redesSociales = [
  { id: 1, name: 'linkedin', src: linkedin, url: 'https://www.linkedin.com/in/santino-mamani-1b7743319/' },
  { id: 2, name: 'Instagram', src: instagram, url: 'https://www.instagram.com/santii.mamani/' },
  { id: 3, name: 'github', src: github, url: 'https://github.com/SantinoMamani' },
  
];
const telefono = '+54 9 11 2676-1564';
</script>

<template>
  <section class="datos-personales">
    <div class="card">
      <img :src="fotoPerfil" alt="Foto de Perfil de Santino Mamani" class="perfil-img">
      
      <h1>{{ title }}</h1>
      <h2>{{ descripcion }}</h2>
      <p>{{ presentacion }}</p>
      
      <ul class="container-lista">
        <li v-for="red in redesSociales" :key="red.id">
          <a :href="red.url" target="_blank"><img class="icon-redsocial" :src="red.src" width="35rem" :alt="red.name"></a>
        </li>
      </ul>
      
      <h3>☎ Mi Teléfono personal: {{ telefono }}</h3>
      <h4>{{ residencia }}</h4>
    </div>
  </section>
</template>

<style scoped>
/* Estilo Sugerido para el fondo del cuerpo (si lo pones en un CSS global) */
/* Este fondo oscuro y dinámico es CLAVE para que el efecto de transparencia se note */
.datos-personales {
    min-height: 100vh; 
    display: flex;
    justify-content: center;
    align-items: center;
    /* Fondo con degradado tech */
    background: linear-gradient(135deg, #0f1c2d, #1a2a3a);
}

/* --- Ajustes Glassmorphism (Transparencia) --- */
.card {
  /* Fondo moderno y elegante: Azul oscuro con 50% de transparencia (RGBA) */
  background: rgba(15, 28, 45, 0.5); 
  
  /* Efecto de cristal esmerilado/Glassmorphism */
  backdrop-filter: blur(10px); 
  -webkit-backdrop-filter: blur(10px); /* Compatibilidad con Safari */
  
  border-radius: 15px; /* Bordes más redondeados */
  border: 1px solid rgba(0, 170, 255, 0.3); /* Borde de luz sutil */
  box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37); /* Sombra elevada */
  
  /* Responsividad */
  width: 90%; 
  max-width: 450px; 
  margin: 20px auto; 
  padding: 25px; 
  text-align: center;
  color: #e0f2f7; /* Texto blanco-azulado */
}

/* Estilos de Tipografía y Foto */
.perfil-img {
    width: 140px; 
    height: 140px;
    border-radius: 50%; 
    object-fit: cover; 
    margin-bottom: 20px;
    /* Borde de luz brillante */
    border: 4px solid #00aaff; 
    box-shadow: 0 0 15px rgba(0, 170, 255, 0.6); 
}

h1 {
  font-size: 2.2rem; 
  margin-top: 0.8rem;
  color: #00aaff; /* Azul brillante para el título */
  text-shadow: 0 0 8px rgba(0, 170, 255, 0.4);
}

h2 {
    font-size: 1.3rem;
    font-weight: 300; 
    color: #90d8f0; 
}

h3 {
  font-size: 1.1rem;
  font-weight: 500;
  margin-top: 1.8rem;
  color: #e0f2f7;
}

h4 {
    font-size: 1rem;
    font-weight: 300;
    color: #b3e0ed;
}

p {
  font-size: 1.05rem;
  font-weight: 400;
  margin: 1.2rem 0 1.8rem 0; 
  line-height: 1.6; 
  color: #c0e6fa;
}

/* Redes Sociales */
.container-lista {
  display: flex;
  justify-content: center;
  list-style: none;
  padding: 0;
  margin: 0;
}

.icon-redsocial {
  width: 40px; 
  height: 40px;
  background-color: #00aaff; 
  border-radius: 50%;
  padding: 6px; 
  margin: 0 10px; 
  box-shadow: 0 0 12px rgba(0, 170, 255, 0.7); 
  transition: transform 0.3s ease, background-color 0.3s ease; 
}

.icon-redsocial:hover {
  background-color: #e0f2f7; 
  box-shadow: 0 0 18px rgba(255, 255, 255, 0.8); 
  transform: scale(1.15); 
}

/* --- MEDIA QUERY para tabletas y escritorio (pantallas >= 768px) --- */
@media (min-width: 768px) {
    .card {
        max-width: 650px; 
        padding: 50px; 
    }
    
    h1 {
        font-size: 3.5rem;
    }
    
    h2 {
        font-size: 1.6rem;
    }

    p {
        font-size: 1.2rem;
    }
}
</style>