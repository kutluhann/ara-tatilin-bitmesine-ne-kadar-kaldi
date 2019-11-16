<template>
  <div class="container" v-if="!loading">
    <div class="countdown" v-if="!finished">
      <span>ara tatilin bitmesine ne kadar kaldı?</span>
      <span class="fields">
        <span class="field">{{days}}g</span>
        <span class="field">{{hours}}s</span>
        <span class="field">{{minustes}}d</span>
        <span class="field">{{seconds}}s</span>
      </span>
    </div>
    <div v-else>
      <span>ara tatil bitti, okullara devam :(</span>
    </div>
  </div>
</template>

<script>

export default {
  name: 'app',
  components: {
  },
  data() {
    return {
      loading: true,
      days: 0,
      hours: 0,
      minustes: 0,
      seconds: 0,
      finished: false
    }
  },
  computed: {
  },
  mounted() {
    setTimeout(() => {
      this.loading = false
    }, 2000)
    setInterval(() => {
      let finalDate = new Date("Nov 25, 2019 00:00:00").getTime()
      let now = Date.now()
      let distance = finalDate - now
      if(distance > 0){
        this.days = Math.floor(distance / (1000 * 60 * 60 * 24))
        this.hours = Math.floor(distance % (1000 * 60 * 60 * 24) / (1000 * 60 * 60))
        this.minustes = Math.floor(distance % (1000 * 60 * 60) / (1000 * 60))
        this.seconds = Math.floor(distance % (1000 * 60) / (1000))
      }else{
        this.finished = true
      }
    }, 1000)
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
html{
  font-size: 16px;
}
body{
  height: 100vh;
  width: 100vw;
  font-family: 'Open Sans', sans-serif;
  text-align: center;
  overflow: hidden;
}
@media (max-width: 1024px){
  html{
    font-size: 8px;
  }
}
span{
  font-size: 2rem;
  font-weight: bold;
}
.container{
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.countdown{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.fields{
  padding: 4rem;
}
.field{
  padding: 1rem;
  font-size: 4rem;
}
</style>