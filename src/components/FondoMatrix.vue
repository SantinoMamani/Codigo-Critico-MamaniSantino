<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

// Referencia al elemento <canvas>
const canvasEl = ref(null);

onMounted(() => {
    const canvas = canvasEl.value;
    if (!canvas) return;
    
    const ctx = canvas.getContext('2d');
    
    // Paleta de colores de tu portafolio
    const backgroundColor = 'rgba(15, 28, 45, 0.1)'; // Fondo oscuro con desvanecimiento
    const textColor = '#00aaff'; // Tu azul brillante

    // Caracteres para la lluvia
    const chars = '0123456789ABCDEFアァカサタナハマヤャラワガザダバパイィキシチニヒミリヰギジヂビピウゥクスツヌフムユュルグズブヅプエェケセテネヘメレヱゲゼデベペオォコソトノホモヨョロヲゴゾドボポヴッン';
    const fontSize = 16;
    let columns = 0;
    let drops = [];

    let animationFrameId;

    function initializeCanvas() {
        // Asegurarse de que el canvas tenga un tamaño inicial
        canvas.width = window.innerWidth || document.documentElement.clientWidth;
        canvas.height = window.innerHeight || document.documentElement.clientHeight;
        
        columns = Math.floor(canvas.width / fontSize);
        drops = [];
        for (let x = 0; x < columns; x++) {
            drops[x] = Math.floor(Math.random() * canvas.height / fontSize);
        }
    }

    // Función para dibujar un frame
    function draw() {
        // Fondo semi-transparente para el efecto de "estela"
        ctx.fillStyle = backgroundColor;
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        
        ctx.fillStyle = textColor;
        ctx.font = fontSize + 'px monospace';

        for (let i = 0; i < drops.length; i++) {
            const text = chars[Math.floor(Math.random() * chars.length)];
            ctx.fillText(text, i * fontSize, drops[i] * fontSize);
            
            // Reiniciar la gota si se va de la pantalla
            if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
                drops[i] = 0;
            }
            
            // Mover la gota
            drops[i]++;
        }
        
        animationFrameId = requestAnimationFrame(draw);
    }

    // Iniciar
    initializeCanvas();
    draw();

    // Limpiar en resize
    const handleResize = () => {
        if (animationFrameId) {
            cancelAnimationFrame(animationFrameId);
        }
        initializeCanvas();
        draw();
    };
    
    window.addEventListener('resize', handleResize);

    // Limpiar al desmontar el componente
    onUnmounted(() => {
        if (animationFrameId) {
            cancelAnimationFrame(animationFrameId);
        }
        window.removeEventListener('resize', handleResize);
    });
});
</script>

<template>
  <canvas ref="canvasEl" class="fondo-matrix"></canvas>
</template>

<style scoped>
.fondo-matrix {
    /* Asegura que el canvas cubra todo */
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 0;
    background-color: #0f1c2d; /* Fondo base oscuro */
}
</style>