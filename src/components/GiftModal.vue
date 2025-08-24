<template>
  <div class="modal">
    <div 
      v-if="props.modalType === 'transferencia'"
      class="modal-content"
    >
      <span class="close" @click="$emit('close')">&times;</span>
      <h3 class="modal-title">Datos para transferencia</h3>
      <p class="modal-info">
        <i class="fa-solid fa-circle-user modal-icon"></i>
        <label class="modal-label">Alias:</label> 5248119
      </p>
      <p class="modal-info">
        <i class="fa-solid fa-file-contract modal-icon"></i>
        <label class="modal-label">Titular:</label> Liz Genny Pereira Portillo
      </p>
      <p class="modal-info">
        <i class="fa-solid fa-university modal-icon"></i>
        <label class="modal-label">Entidad:</label> Tu Financiera
      </p>
      <p class="modal-info">
        <i class="fa-solid fa-money-check modal-icon"></i>
        <label class="modal-label">Nro de cuenta:</label> 20498942
      </p>
    </div>
    <div 
      v-else-if="props.modalType === 'lista_deseos'"
      class="modal-content"
    >
      <span class="close" @click="$emit('close')">&times;</span>
      <h3 class="modal-title">Lista de deseos</h3>
      <ul class="modal-gift-list">
        <li class="modal-gift-item">🏡 Artículos para el hogar (vajilla, copas de vino, juegos de sábanas o toallas)</li>
        <li class="modal-gift-item">⚡ Electrodomésticos pequeños (cafetera, licuadora, batidora)</li>
        <li class="modal-gift-item">🌍 Experiencias en pareja (cenas, escapadas, entradas a conciertos)</li>
        <li class="modal-gift-item">🍷🥂 Botellas especiales (vino, champagne, licores)</li>
        <li class="modal-gift-item">🌿 Cosas para disfrutar al aire libre (set de picnic, hamaca, parrilla)</li>
        <li class="modal-gift-item">✨ Mimos para consentirnos (velas aromáticas, spa en casa, batas)</li>
      </ul>
    </div>
  </div>
</template>
<script setup lang="ts">
import { defineProps } from 'vue';

const props = defineProps<{
  modalType: string;
}>();
</script>
<style setup>
.modal {
  position: fixed;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal-content {
  background-color: white;
  padding: 25px;
  border-radius: 15px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  position: relative;
  min-height: 300px;
  width: 400px;
}

.close {
  position: absolute;
  top: 10px;
  right: 15px;
  cursor: pointer;
  font-size: 1.5rem;
  color: #444;
}

.modal-title {
  font-size: 1.8rem;
  font-weight: 500;
  font-family: 'Edu NSW ACT Cursive', cursive;
  text-align: center;
  color: var(--primary-color);
  padding: 0 20px;
  margin-bottom: 20px;
}

.modal-info {
  font-size: 1.1rem;
  font-weight: 500;
  font-family: 'Arial', sans-serif;
  color: #444;
  text-align: left;
  padding: 0 20px;
  margin: 0px;
}

.modal-label {
  font-weight: bold;
  color: var(--primary-color);
}

.modal-icon {
  margin-right: 8px;
  color: var(--primary-color);
}

.modal-gift-list {
  list-style-type: disc;
  padding-left: 40px;
  margin-top: 10px;
}

.modal-gift-item {
  font-size: 1rem;
  color: #444;
  margin-bottom: 8px;
  font-family:'Arial', sans-serif;
}

@media (max-width: 600px) {
  .modal-content {
    width: 90%;
    padding: 15px;
  }

  .modal-title {
    font-size: 1.5rem;
    margin-bottom: 15px;
  }

  .modal-info {
    font-size: 1rem;
    margin-bottom: 8px;
  }
}
</style>