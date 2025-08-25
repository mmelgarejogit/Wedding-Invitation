<template>
  <div class="wedding-container">
    <div class="decorations">
      <img 
        src="@/assets/eucalipto-side.png"
        class="eucalipto-left"
        alt="flowers"
      />
      <img 
        src="@/assets/eucalipto-side.png"
        class="eucalipto-right"
        alt="flowers"
      />
      <img 
        src="@/assets/flowers-top.png"
        class="flowers-top-left"
        alt="flowers"
      />
      <img 
        src="@/assets/flowers-top.png"
        class="flowers-top-right"
        alt="flowers"
      />
    </div>
    <div class="presentation">
      <img
        src="@/assets/wedding-logo.png"
        class="wedding-logo"
        alt="bride and groom logo"
      />
      <div class="presentation-body">
        <img 
          src="@/assets/couple-img-second.jpg"
          class="couple-img"
          alt="couple image"
        />
        <img
          src="@/assets/cursive-names.png"
          class="couple-names"
          alt="couple names"
        />
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">

</script>
<style scoped>
.wedding-container {
  position: relative;
  width: 100%;
  min-height: 100vh;
  overflow: hidden; 
}

.decorations {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}

.presentation {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: start;
  width: 100%;
  min-height: 100vh;
  padding: 20px;
  gap: 25px;
  box-sizing: border-box;
  z-index: 0; 
}

.wedding-logo {
  max-width: 350px;
  width: 100%;
  height: auto;
  border-radius: 50%;
  margin: 0 auto;
}

.couple-img {
  max-width: 500px;
  width: 100%;
  height: auto;
  border-radius: 50%;
  margin: 0 auto;
}

.couple-names {
  max-width: 350px;
  width: 100%;
  height: auto;
  margin: 0 auto;
}

.eucalipto-left {
  position: absolute;
  left: 0;
  bottom: 0;
  height: 100vh;
  width: auto;
  opacity: 0.8;
}

.eucalipto-right {
  position: absolute;
  right: 0;
  bottom: 0;
  transform: rotate(180deg);
  height: 100vh;
  width: auto;
  opacity: 0.7;
}

.flowers-top-left {
  position: absolute;
  top: 0;
  left: 0;
  width: 150px;
  height: auto;
}

.flowers-top-right {
  position: absolute;
  top: 0;
  right: 0;
  width: 150px;
  height: auto;
  transform: rotate(110deg);
}

.presentation-body {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 20px;
  margin-top: 50px;
}

@media (max-width: 768px) {
  .presentation {
    padding: 15px;
    gap: 20px;
    min-height: 80vh;
  }

  .wedding-container {
    min-height: 80vh;
  }

  .decorations {
    height: 80vh;
  }
  
  .wedding-logo {
    max-width: 220px;
    margin-top: 20px;
  }
  
  .couple-img {
    max-width: 270px;
  }
  
  .couple-names {
    max-width: 220px;
  }

  .eucalipto-left, 
  .eucalipto-right {
    height: 70vh;
    opacity: 0.5;
  }

  .flowers-top-left {
    width: 120px;
    top: -10px;
    left: -10px;
  }

  .flowers-top-right {
    width: 120px;
    top: -10px;
    right: -10px;
  }

  .presentation-body {
    margin-top: 120px;
  }
}

@media (max-width: 480px) {
  .presentation {
    padding: 10px;
    gap: 15px;
  }
  
  .wedding-logo {
    max-width: 150px;
  }
  
  .couple-img {
    max-width: 200px;
  }
  
  .couple-names {
    max-width: 180px;
  }

  .eucalipto-left,
  .eucalipto-right {
    height: 60vh;
    opacity: 0.5;
    top: 225px;
  }

  .flowers-top-left,
  .flowers-top-right {
    width: 90px;
  }

  .presentation-body {
    margin-top: 80px;
  }
}
</style>