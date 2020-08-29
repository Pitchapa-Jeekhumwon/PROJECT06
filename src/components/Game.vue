<template>
  <div>
    <div class="col">
      <button @click="start()" class="btn btn-primary mr-5 mb-4">Start</button>
      <button v-bind:disabled="end" @click="attack()" class="btn btn-warning mr-2 mb-4">Attack</button>
      <button
        v-bind:disabled="end"
        @click="specialattack()"
        class="btn btn-danger mr-5 mb-4"
      >Special Attack</button>
      <button @click="reset()" class="btn btn-light mb-4">Reset</button>
    </div>

    <div class="row">
      <div class="col-6 alert alert-danger" role="alert">
        <h5>Player : {{aPlayer.name}}, HP : {{aPlayer.hp}}</h5>
      </div>
      <div class="col-6 alert alert-danger" role="alert">
        <h5>Monster : {{aMonster.name}}, HP : {{aMonster.hp}}</h5>
      </div>
    </div>

    <div class="row">
      <div class="col-5">
        <br />
        <div style="position: absolute; z-index: 2;">
          <img style="width:100%" :src="aPlayer.img" />
        </div>
      </div>

      <div class="col-2">
        <br />
        <div v-if="aMonster.hp <=0 ">
          <br /><br /><br /><br /><br />
          <img
            src="img/13.png"
            width="100%"
          />
        </div>
        <div v-else-if="aPlayer.hp <= 0 ">
          <br /><br /><br /><br /> <br />
          <img
            src="img/12.png"
            width="100%"
          />
        </div>
        <br /><br /><br /><br /><br /><br />
        <img src="img/11.png" width="80%"
        />
      </div>

      <div class="col-5">
        <div style="position: absolute; z-index: 4;">
          <img style="width:100%" :src="aMonster.img" />
        </div>
      </div>
    </div>
    <br /><br /><br /><br />
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      vs1: "",
      playmax: "",
      monsmax: "",
      end: false,
      aPlayer: { name: "", hp: 1, img: "", hp1: "" },

      player: [
        {
          name: "Yuta",
          hp: 500,
          img :"./img/1.png",
        },
        {
          name: "Saito",
          hp: 450,
          img:"./img/2.png",
        },
        {
          name: "Kyoshin",
          hp: 350,
          img:"./img/3.png",
        },
        {
          name: "ํYukari",
          hp: 300,
          img:"./img/4.png",
        },
        {
          name: "Saya",
          hp: 250,
          img:"./img/5.png",
        },
      ],
      aMonster: { name: "", hp: 1, img: "", hp2: "" },
      monster: [
        {
          name: "Yoshitaka",
          hp: 480,
          img:"./img/6.png",
        },
        {
          name: "Sugiyama",
          hp: 430,
          img:"./img/7.png",
        },
        {
          name: "Nakahara",
          hp: 320,
          img:"./img/8.png",
        },
        {
          name: "Okazaki",
          hp: 240,
          img:"./img/9.png",
        },
        {
          name: "Igaarashi",
          hp: 220,
          img:"./img/10.png",
        },
      ],
    };
  },
  methods: {
    random: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },

    start: function () {
      this.aPlayer = this.player[this.random(1, 5) - 1];
      this.aMonster = this.monster[this.random(1, 5) - 1];
    },
    attack: function () {
      this.playmax = Math.floor(Math.random() * 15 + 5);
      this.aPlayer.hp = this.aPlayer.hp - this.playmax;
      this.monsmax = Math.floor(Math.random() * 15 + 5);
      this.aMonster.hp = this.aMonster.hp - this.monsmax;
      if (this.aPlayer.hp <= 0) {
        this.aPlayer.hp <= 0;
        this.end = true;
      } else if (this.aMonster.hp <= 0) {
        this.aMonster.hp <= 0;
        this.end = true;
      }
    },
    specialattack: function () {
      this.playmax = Math.floor(Math.random() * 30 + 5);
      this.aPlayer.hp = this.aPlayer.hp - this.playmax;
      this.monsmax = Math.floor(Math.random() * 30 + 5);
      this.aMonster.hp = this.aMonster.hp - this.monsmax;
      if (this.aPlayer.hp <= 0) {
        this.aPlayer.hp = 0;
        this.end = true;
      } else if (this.aMonster.hp <= 0) {
        this.aMonster.hp = 0;
        this.end = true;
      }
    },
    reset: function () {
      window.location.reload();
    },
  },
};
</script>

