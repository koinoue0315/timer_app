<template>
  <v-container>
    <v-row
      class="ma-4 text-center"

    >
      <v-col cols="12">
        <p><span class="text-h2">{{timeCount}}</span><span> 秒</span></p>
      </v-col>
    </v-row>
    <v-row
      class="ma-4 text-center"
      align="center"
      justify="space-around"
    >
      
        <v-btn
          color="primary"
          @click="timeCountUp"
          :disabled="isCountup"
        >
          スタート
        </v-btn>

        <v-btn
          @click="stop"
        >
          リセット
        </v-btn>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data: () => ({
      timeCount: 0,
      isCountup: false,
      timerFunc: null,
      stopTimerFlag: false,
    }),

    methods: {
      timeCountUp () {
        this.isCountup = true;
        this.stopTimerFlag = false;
        this.timerFunc = setInterval(() => {
          this.timeCount = this.timeCount + 1;
          if (this.stopTimerFlag) {
            this.isCountup = false;
            clearInterval(this.timerFunc);
            this.timeCount = 0;
          }
        }, 1000);
      },
      stopOrRestart () {
        this.isCountup = !this.isCountup;
      },
      stop () {
        this.stopTimerFlag = true;
      }
    }
  }
</script>
