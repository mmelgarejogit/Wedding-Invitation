<template>
  <div class="info-container">
    <div class="info-item">
      <img class="info-icon" src="@/assets/location-img.png" alt="Location Icon" />
      <h3 class="info-title">Ceremonia Civil y Recepción</h3>
      <p class="info-description">Hora: 20:00 p.m.</p>
      <p class="info-description">Salón de Eventos Las Hermanas</p>
      <p class="info-description">Loma Clavel, San Lorenzo</p>
      <button class="info-button" @click="openMap">Ver Mapa</button>
    </div>
    <div class="info-item">
      <img class="info-icon" src="@/assets/gift-logo.png" alt="Location Icon" />
      <h3 class="info-title">Regalos</h3>
      <p class="info-description">
        El mejor regalo es que estés presente en este día tan esperado, pero si deseas hacernos un obsequio, tenemos estas opciones:
      </p>
      <div class="gift-options">
        <button class="info-button" @click="openModal('transferencia')">Transferencia</button>
        <button class="info-button" @click="openModal('lista_deseos')">Lista de deseos</button>
      </div>
    </div>
    <div class="info-item">
      <img class="info-icon" src="@/assets/dresscode.png" alt="Dresscode" />
      <h3 class="info-title">Dresscode</h3>
      <p class="info-description">Elegante.</p>
      <p class="info-description">
        Prepárense para una fiesta llena de colores, dejen el blanco, rosa y lila para los novios.
      </p>
    </div>
  </div>
  <div 
    v-if="!mobileView" 
    class="info-img-container"
  >
    <div class="info-decoration">
      <img src="@/assets/eucalipto-side.png" alt="Eucalipto" class="eucalipto-left"/>
      <img src="@/assets/eucalipto-side.png" alt="Eucalipto" class="eucalipto-right"/>
    </div>
    <div class="info-img-body">
      <img class="info-img" src="@/assets/couple-real-img.jpg" alt="couple" />
    </div>
  </div>
  <img 
    v-else 
    class="info-img" 
    src="@/assets/couple-real-img.jpg"
    alt="wedding" 
  />
  <GiftModal 
    v-if="showGiftModal" 
    @close="showGiftModal = false" 
    :modalType="modalType"
  />
  <div class="info-container">
    <div class="info-item">
      <h3 class="info-title">Pases</h3>
      <p class="info-description">Hemos reservado</p>
      <div class="number-tickets-circle">
        <p class="number-tickets">2</p>
      </div>
      <p class="info-description">Lugares en tu honor.</p>
    </div>
    <div class="info-item">
      <h3 class="info-title">No niños</h3>
      <p class="info-description">Por favor, comprenda que esta es una celebración exclusiva para adultos.
      </p>
    </div>
    <div class="info-item">
      <h3 class="info-title">Confirmar asistencia</h3>
      <p class="info-description">Por favor, confirma tu asistencia a este evento tan especial hasta el 15 de Noviembre.
      </p>
       <button 
        class="info-button" 
        @click="openForm">
        Confirmar Asistencia
      </button>
    </div>
  </div>
  <div 
    v-if="!mobileView" 
    class="info-img-container"
  >
    <div class="info-decoration">
      <img src="@/assets/eucalipto-side.png" alt="Eucalipto" class="eucalipto-left"/>
      <img src="@/assets/eucalipto-side.png" alt="Eucalipto" class="eucalipto-right"/>
    </div>
    <div class="info-img-body">
      <img class="info-img" src="@/assets/LizyJoel2.jpg" alt="wedding" />
    </div>
  </div>
  <img 
    v-else 
    class="info-img" 
    src="@/assets/LizyJoel2.jpg" 
    alt="couple" 
  />
  <h2 class="couple-names">
    Joel y Liz
  </h2>
  <div class="flowers-decoration">
    <img src="@/assets/flowers-top.png" alt="Flores" class="flowers-top-left"/>
    <img src="@/assets/flowers-top.png" alt="Flores" class="flowers-top-right"/>
  </div>
</template>
<script setup lang="ts">
import GiftModal from './GiftModal.vue';
import { ref } from 'vue';

const showGiftModal = ref(false);
const modalType = ref('');
const mobileView = ref(false);

const openMap = () => {
  window.open('https://www.google.com/maps?q=-25.3629665374756,-57.4661750793457', '_blank');
};

const openModal = (modalTypeArg: string) => {
  modalType.value = modalTypeArg;
  showGiftModal.value = true;
};

const openForm = () => {
  window.open('https://forms.gle/YEJ41MZeuciT1kZM8', '_blank');
};

const checkMobileView = () => {
  mobileView.value = window.innerWidth <= 768;
};

window.addEventListener('resize', checkMobileView);
</script>
<style scoped>
.info-container {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.info-button {
  background-color: var(--primary-color);
  color: white;
  border: none;
  border-radius: 20px;
  padding: 12px 20px;
  cursor: pointer;
  font-size: 1rem;
  font-family: 'Georgia', 'Times New Roman', serif;
  font-weight: 500;
  margin: 10px 0;
  margin: 10px 5px;
  min-width: 180px;
  transition: all 0.3s ease;
}

.info-button:hover {
  opacity: 0.9;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(174, 156, 143, 0.3);
}

.info-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 60px;
}

.info-icon {
  max-width: 200px;
  max-height: 200px;
}

.info-title {
  font-size: 2rem;
  font-weight: 500;
  font-family: 'Edu NSW ACT Cursive', cursive;
  text-align: center;
  color: var(--primary-color);
  padding: 0 20px;
  margin-bottom: 15px;
}

.info-description {
  font-size: 1rem;
  font-weight: 400;
  font-family: 'Georgia', 'Times New Roman', serif;
  color: #444;
  text-align: center;
  padding: 0 20px;
  margin: 0px;
  max-width:500px;
}

.gift-options {
  display: flex;
  justify-content: center;
  align-items: center;
  min-width: 100%;
}

.info-img-container {
  position: relative;
  width: 100%;
  min-height: 100vh;
}

.info-decoration {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}

.info-img {
  border-radius: 15px;
  justify-content: center;
}

.eucalipto-left {
  position: absolute;
  left: 0;
  bottom: 0;
  height: 70vh;
  width: auto;
  opacity: 0.8;
}

.eucalipto-right {
  position: absolute;
  right: 0;
  bottom: 0;
  transform: rotate(180deg);
  height: 70vh;
  width: auto;
  opacity: 0.8;
}

.info-img-body{
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  min-height: 100vh;
  padding: 20px;
  z-index: 0; 
}

.number-tickets {
  font-size: 2rem;
  font-weight: 700;
  color: var(--primary-color);
  font-family: 'Georgia', 'Times New Roman', serif;
  margin: 10px 0;
}

.number-tickets-circle{
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  width: 60px;
  height: 60px;
  border: 4px solid var(--primary-color);
  margin: 10px 0;
}

.couple-names {
  font-size: 4rem;
  font-weight: 600;
  font-family: 'Beau Rivage', cursive;
  text-align: center;
  color: var(--primary-color);
  margin: 40px;
}

.flowers-top-left {
  position: absolute;
  bottom: 0px;
  left: 0px;
  width: 150px;
  height: auto;
  transform: rotate(270deg);
}

.flowers-top-right {
  position: absolute;
  bottom: 0px;
  right: 0px;
  width: 150px;
  height: auto;
  transform: rotate(190deg);
}

.flowers-decoration {
  position: relative;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.dresscode-icon {
  max-width: 200px;
  max-height: 200px;
}

@media (max-width: 768px) {
  .info-icon {
    max-width: 90px;
    max-height: 90px;
  }

  .info-title {
    font-size: 1.4rem;
    margin: 10px 0;
  }

  .info-description {
    font-size: 0.9rem;
    padding: 0 15px;
  }

  .info-button {
    padding: 8px 16px;
    font-size: 0.9rem;
    margin-bottom: 0px;
    min-width: 150px;
  }

  .gift-options {
    flex-direction: column;
    align-items: center;
  }

  .info-img {
    width: 100%;
    margin-bottom: 40px;
  }

  .flowers-top-left, .flowers-top-right {
    width: 90px;
  }

  .couple-names {
    font-size: 2.8rem;
    margin: 20px;
  }
}

</style>