<template>
  <div class="date-container">
    <h3 class="date-title">
      Tenemos el agrado de invitarlos a nuestra boda
    </h3>
    <span class="date-month">
      Diciembre
    </span>
    <div class="full-date">
      <div class="date-day">
        Sábado
      </div>
      <h3>20</h3>
      <div class="date-year">
        2025
      </div>
    </div>
    <h3 class="date-title">
      Faltan ...
    </h3>
    <div class="countdown-container">
      <div class="countdown-item">
        <span class="countdown-number">{{countdown.days}}</span>
        <span class="countdown-label">Días</span>
      </div>
      <span class="countdown-separator">:</span>
      <div class="countdown-item">
        <span class="countdown-number">{{countdown.hours}}</span>
        <span class="countdown-label">Horas</span>
      </div>
      <span class="countdown-separator">:</span>
      <div class="countdown-item">
        <span class="countdown-number">{{countdown.minutes}}</span>
        <span class="countdown-label">Minutos</span>
      </div>
      <span class="countdown-separator">:</span>
      <div class="countdown-item">
        <span class="countdown-number">{{countdown.seconds}}</span>
        <span class="countdown-label">Segundos</span>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
  import { ref } from 'vue';

  const countdown = ref({
    days: 0,
    hours: 0,
    minutes: 0,
    seconds: 0
  })

  const targetDate = new Date('2025-12-20T00:00:00');

  const updateCountdown = () => {
    const now = new Date();
    const timeDiff = targetDate.getTime() - now.getTime();

    if (timeDiff > 0) {
      countdown.value.days = Math.floor(timeDiff / (1000 * 60 * 60 * 24));
      countdown.value.hours = Math.floor((timeDiff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      countdown.value.minutes = Math.floor((timeDiff % (1000 * 60 * 60)) / (1000 * 60));
      countdown.value.seconds = Math.floor((timeDiff % (1000 * 60)) / 1000);
    } else {
      countdown.value.days = 0;
      countdown.value.hours = 0;
      countdown.value.minutes = 0;
      countdown.value.seconds = 0;
    }
  }

  setInterval(updateCountdown, 1000);
</script>
<style scoped>
.date-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-bottom: 40px;
}

.date-title {
  font-size: 2rem;
  font-weight: 500;
  font-family: 'Edu NSW ACT Cursive', cursive;
  margin: 20px 0;
  text-align: center;
  color: var(--primary-color);
  padding: 0 20px;
}

.date-month {
  margin-top: 30px;
  text-align: center;
  font-size: 1.3rem;
  font-family: 'Georgia', 'Times New Roman', serif;
  color: #333;
}

.full-date {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  margin-bottom: 30px;
  min-width: 150px;
}

.date-day,
.date-year {
  color: #333;
  font-size: 1.3rem;
  font-family: 'Georgia', 'Times New Roman', serif;
  border-top: 2px solid var(--primary-color);
  border-bottom: 2px solid var(--primary-color);
  text-align: center;
  padding: 10px 30px;
  margin-inline: 10px;
  width: 150px;
  box-sizing: border-box;
}

.full-date h3 {
  font-size: 2.1rem;
  font-weight: bold;
  color: var(--primary-color);
  margin: 0;
  font-family: 'Georgia', 'Times New Roman', serif;
}

.countdown-container {
  display: flex;
  justify-content: center;
  gap: 20px;
}

.countdown-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: 'Georgia', 'Times New Roman', serif;
  box-sizing: border-box;
  min-width: 60px;
}

.countdown-number {
  font-size: 1.8rem;
  font-weight: 500;
  color: #333;
}

.countdown-label {
  font-size: 0.8rem;
  color: #666;
  font-style: italic;
}

.countdown-separator {
  font-size: 1.5rem;
  color: #333;
  font-weight: 500;
  margin: 5px 0;
}

@media (max-width: 600px) {
  .date-title {
    font-size: 1.4rem;
    margin: 15px 0;
    padding: 0 10px;
  }

  .date-month {
    font-size: 1.1rem;
  }

  .full-date {
    gap: 15px;
  }

  .date-day,
  .date-year {
    font-size: 1.1rem;
    padding: 8px 15px;
    width: 100px;
  }

  .full-date h3 {
    font-size: 1.8rem;
  }

  .countdown-container {
    gap: 10px;
  }
}
</style>