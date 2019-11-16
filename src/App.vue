<template>
  <div class="countdown">
    <span>ara tatilin bitmesine ne kadar kaldı?</span>
    <span class="fields">
      <span class="field">{{days}}g</span>
      <span class="field">{{hours}}s</span>
      <span class="field">{{minustes}}d</span>
      <span class="field">{{seconds}}s</span>
    </span>
  </div>
</template>

<script>

export default {
  name: 'app',
  components: {
  },
  data() {
    return {
      days: 0,
      hours: 0,
      minustes: 0,
      seconds: 0,
    }
  },
  computed: {
  },
  mounted() {
    setInterval(() => {
      let finalDate = new Date("Nov 25, 2019 00:00:00").getTime()
      let now = Date.now()
      let distance = finalDate - now
      this.days = Math.floor(distance / (1000 * 60 * 60 * 24))
      this.hours = Math.floor(distance % (1000 * 60 * 60 * 24) / (1000 * 60 * 60))
      this.minustes = Math.floor(distance % (1000 * 60 * 60) / (1000 * 60))
      this.seconds = Math.floor(distance % (1000 * 60) / (1000))
      /*
      this.days = days < 10 ? '0' + days : days
      this.hours = hours < 10 ? '0' + hours : hours
      this.minustes = minustes < 10 ? '0' + minustes : minustes
      this.seconds = seconds < 10 ? '0' + seconds : seconds
      */
    }, 1000)
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
body{
  height: 100vh;
  width: 100vw;
  font-size: 1rem;
  font-family: 'Open Sans', sans-serif;
}
span{
  font-size: 2rem;
}
.countdown{
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-weight: bold;
}
.fields{
  margin-top: 4rem;
}
.field{
  margin: 1rem;
  font-size: 4rem;
}
</style>