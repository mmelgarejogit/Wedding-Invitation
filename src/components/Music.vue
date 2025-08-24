<template>
  <div class="music-section">
    <div class="music-header">
      <h3 class="music-title">Nuestra Canción</h3>
      <p class="music-text">Presiona el botón para reproducir la melodía de nuestro amor</p>
    </div>
    
    <div class="music-container">
      <audio id="wedding-song" ref="song" @timeupdate="updateProgress">
        <source src="@/assets/wedding-song.m4a" type="audio/mp4" />
        Tu navegador no soporta el elemento de audio.
      </audio>
      <input 
        type="range" 
        :value="progressValue" 
        id="progress" 
        ref="progress" 
        @input="seekAudio"
      />
      <div class="play-button" @click="togglePlay">
        <i 
          class="fas" 
          :class="isPlaying ? 'fa-pause' : 'fa-play'" 
          id="play-icon" 
          ref="playIcon">
        </i>
      </div>
    </div>
    
    <div class="quote-container">
      <p class="quote-text">
        El destino nos unió, el amor nos hizo inseparables
      </p>
      <div class="quote-decoration">
        <span class="heart">♥</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const song = ref(null);
const isPlaying = ref(false);
const progressValue = ref(0);

const togglePlay = () => {
  if (song.value.paused) {
    song.value.play();
    isPlaying.value = true;
  } else {
    song.value.pause();
    isPlaying.value = false;
  }
};

const updateProgress = () => {
  if (song.value) {
    progressValue.value = (song.value.currentTime / song.value.duration) * 100;
  }
};

const seekAudio = (event) => {
  if (song.value) {
    song.value.currentTime = (event.target.value / 100) * song.value.duration;
  }
};
</script>
<style scoped>
.music-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
  padding: 30px 20px;
}

.music-header {
  text-align: center;
  margin-bottom: 30px;
}

.music-title {
  font-size: 2rem;
  font-weight: 500;
  margin-bottom: 15px;
  font-family: 'Edu NSW ACT Cursive', cursive;
  color: var(--primary-color);
}

.music-text {
  font-size: 1.1rem;
  color: #666;
  margin-bottom: 10px;
  font-family: 'Arial', sans-serif;
  line-height: 1.6;
  font-style: italic;
  opacity: 0.9;
}

.music-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  border-radius: 15px;
  padding: 25px;
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255,255,255,0.2);
}

.quote-container {
  text-align: center;
  margin-top: 30px;
  position: relative;
}

.quote-text {
  font-size: 1.2rem;
  color: #444;
  font-family: 'Georgia', 'Times New Roman', serif;
  font-style: italic;
  line-height: 1.7;
  margin: 0;
  padding: 20px 30px;
  position: relative;
  border-radius: 20px;
  border-left: 4px solid var(--secondary-color);
}

.quote-text::before {
  content: '"';
  font-size: 3rem;
  color: var(--accent-color);
  position: absolute;
  top: -10px;
  left: 15px;
  font-family: serif;
}

.quote-text::after {
  content: '"';
  font-size: 3rem;
  color: var(--accent-color);
  position: absolute;
  bottom: -25px;
  right: 15px;
  font-family: serif;
}

.quote-decoration {
  margin-top: 15px;
}

.heart {
  font-size: 1.5rem;
  color: #ff69b4;
  animation: heartbeat 2s ease-in-out infinite;
}

@keyframes heartbeat {
  0%, 100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.1);
  }
}

#progress {
  appearance: none;
  -webkit-appearance: none;
  width: 100%;
  margin-top: 10px;
  height: 12px;
  background: linear-gradient(to right, #FDEFEF, var(--accent-color));
  border-radius: 10px;
  margin: 20px 0px;
  cursor: pointer;
  box-shadow: inset 0 2px 4px rgba(0,0,0,0.1);
}

#progress::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 24px;
  height: 24px;
  background: linear-gradient(135deg, var(--accent-color), var(--primary-color));
  border: 3px solid #fff;
  border-radius: 50%;
  cursor: pointer;
  box-shadow: 0 3px 8px var(--accent-color);
  transition: transform 0.2s ease;
}

#progress::-webkit-slider-thumb:hover {
  transform: scale(1.1);
}

.play-button {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 60px;
  height: 60px;
  background: linear-gradient(135deg, var(--accent-color), var(--primary-color));
  border-radius: 50%;
  cursor: pointer;
  margin-top: 15px;
  transition: all 0.3s ease;
  box-shadow: 0 6px 20px var(--secondary-color);
}

.play-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px var(--accent-color);
}

.play-button:active {
  transform: translateY(0);
}

.play-button i {
  color: white;
  font-size: 24px;
  text-shadow: 0 2px 4px rgba(0,0,0,0.2);
}

@media (max-width: 600px) {
  .music-section {
    padding: 20px 15px;
  }
  
  .music-title {
    font-size: 1.4rem;
  }
  
  .music-text {
    font-size: 1rem;
  }
  
  .quote-text {
    font-size: 1.1rem;
    padding: 15px 20px;
  }
  
  .play-button {
    width: 50px;
    height: 50px;
  }
  
  .play-button i {
    font-size: 20px;
  }
}
</style>