<template>
  <div id="app">
    <Game />
  </div>
</template>

<script>
import Game from "./components/Game.vue";

export default {
  name: "App",
  components: {
    Game,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  padding: 3em;
}

body { 
  background-image: url(https://lh3.googleusercontent.com/Vv815O_yWVLw-VZyjOhGX2W_EfZyQTLtCt7Iy0ih882oQoHAsDOmz0LNiPpexVDKhuMAZOkCQ8h--ZNGTGSpfbbOEOuAkrzOc9AqSknhJRizNw70zojQGexNSgFBG18zE3D97fyXymEDyjRbvyVi9m7KURrRMokYx7vLg1Gv7fd3zhRZHkD_uSWoiyGMCn5awMo4TzfE8kIgMigF7iPt0ipsU20AjHKyatCAIjE5if1BHmmXBBl6f-vS5MbSKu3z4hzLdYgeTmdqCWzLQVEbIMS6Gdu9-e9JBrYUgf_qq8otQzLevxwOz7r1qKoxlcWgqHw1pfpTmtBwpqUse5Fe4zloAIWp83yBa-46E60r6uaqt_AymYt1_l_o9GbQeXzkflB2tWklqQ6pZ57Ku3ZHmcqC6-UP1XW1vUHCGVyUDgjpeqAmxC1RPTj--NQ3B2rrdHlSqDMdPu3Hf9lIaydlEkg6tP5Vhao_pFgEHzRPgQS75zqTbUSxYhIj1drU2_84UInDBMIhSLA0S1vqmtzPRNqYrbvecXdWaySRMTw0ZPDnXLaNFeT6RUGyFBbSiKiC-ntjTCKcubBQjvcNMB-lQQYIwD_1m_YUamORpa78jh26ZwIrcTcbz5nBKrqpEDevVmkmWLZ1V6RkTpHzSc4gG0hRKB--MpCdZweew22ZtTk_5wb4OGVmEb1O-SDHFg=w500-h265-no?authuser=0);
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

</style>
