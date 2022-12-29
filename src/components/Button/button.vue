<template>
  <a :href="link" v-if="link" class="link"><slot /></a>
  <button
    :class="['button', color, time && 'button--time', icon && 'button--icon']"
    :disabled="disabled"
    :type="type"
    @click="countDown"
    v-else
  >
    <img :src="icon" :alt="icon" v-if="icon" />
    <slot v-else></slot>
    <div class="timer" v-if="time">
      {{ displayMinutes }}:{{ displaySeconds }}
    </div>
  </button>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "Button-component",
  props: {
    disabled: Boolean,
    color: String,
    time: Number,
    icon: String,
    link: Boolean,
    type: String,
    content: String,
  },
  data() {
    return {
      counter: this.time,
      displaySeconds: 0,
      displayMinutes: 0,
    };
  },
  mounted() {
    (this.displayMinutes = Math.floor(this.counter / 60)),
      (this.displaySeconds = this.counter % 60);
    if (this.displaySeconds <= 9) {
      this.displaySeconds = "0" + Math.floor(this.displaySeconds);
    }
    if (this.displayMinutes <= 9) {
      this.displayMinutes = "0" + this.displayMinutes;
    }
  },
  methods: {
    countDown() {
      if (this.counter && this.counter > 0) {
        return setTimeout(() => {
          this.displayMinutes = Math.floor(this.counter / 60);
          this.displaySeconds = this.counter % 60;
          if (this.displaySeconds <= 9) {
            this.displaySeconds = "0" + Math.floor(this.displaySeconds);
          }
          if (this.displayMinutes <= 9) {
            this.displayMinutes = "0" + this.displayMinutes;
          }
          --this.counter;
          this.countDown();
        }, 1000);
      } else if (this.counter === 0) {
        this.counter = this.time;
      }
    },
  },
});
</script>

<style setup>
.button {
  border-radius: 17px;
  display: flex;
  padding: 14px 46px;
  margin-bottom: 20px;
  font-family: Phosphate;
  font-style: normal;
  font-weight: 400;
  font-size: 18px;
  line-height: 24px;
  text-align: center;
  color: #ffffff;
}

.link {
  font-family: "Nunito";
  font-style: normal;
  font-weight: 700;
  font-size: 16px;
  line-height: 18px;
  transition: color 0.3s;
  color: #fff;
}
.link:hover {
  color: #767679;
}
.link:active {
  color: #c4296c;
}

.button--icon {
  width: 60px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0;
  border-radius: 21px;
}

.button--time {
  background: #efefef;
  color: #767679;
  font-family: "Phosphate";
  font-style: normal;
  font-weight: 400;
  font-size: 18px;
  line-height: 24px;
  text-align: center;
}

.danger {
  background-color: #df3f3e;
}
.primary {
  background-color: #702c7e;
}
.secondary {
  background-color: #c4296c;
}
.warning {
  background-color: #f4ba46;
}
.disabled {
  background-color: #efefef;
}
.info {
  background-color: #0083b6;
}
.action {
  background-color: #ed732e;
}
.button:disabled {
  background-color: #efefef;
  color: #767679;
}

.timer {
  background-color: #df3f3e;
  border-radius: 12px;
  padding: 1px 6px 3px;
  margin-left: 6px;
  color: #fff;
}

@media screen and (max-width: 640px) {
  .button--icon {
    width: 52px;
    height: 52px;
  }
  .button {
    padding: 12px 26px;
    font-size: 16px;
  }
}
</style>
