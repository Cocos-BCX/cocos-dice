<template>
  <section class="slider-container">
    <div class="slider">
      <!-- <div ref="slide" @click="slide" class="slider-bg">
        <div ref="range" :style="{'right': rangeDistance}" class="slider-range"></div>
        <div :style="{'right': rangeDistance}" ref="tooltip" class="slider-tooltip">{{current}}</div>
        <div
          @mousedown="dragStart"
          :class="{'active': isDraging}"
          :style="{'right': rangeDistance}"
          ref="handle"
          class="slider-handle"
        ></div>
      </div>-->
    </div>
    <div class="range">
      <span>1</span>
      <el-slider v-model="initial" @change="slide" :show-tooltip="true"></el-slider>
      <span class="all">100</span>
    </div>
  </section>
</template>

<script>
import eventHub from "@/utils/event";

export default {
  props: {
    // initial: {
    //   type: Number,
    //   default: 50
    // },
    max: {
      type: Number,
      default: 100
    },
    min: {
      type: Number,
      default: 1
    },
    result: {}
  },
  data() {
    return {
      isDraging: false,
      left: 0,
      slideWidth: 0,
      initial: 50
    };
  },

  methods: {
    slide() {
      switch (true) {
        case this.initial < this.min:
          this.initial = this.min;
          break;
        case this.initial > this.max:
          this.initial = this.max;
          break;
      }
      eventHub.$emit("ROLLUNDER_CHANGE", this.initial);
    }
  },
  destroyed() {
    document.removeEventListener("mousemove", this.drag);
    document.removeEventListener("mouseleave", this.dragEnd);
    document.removeEventListener("mouseup", this.dragEnd);
  }
};
</script>

<style scoped>
.range {
  display: flex;
  align-items: center;
  color: #fff;
  font-size: 18px;
  font-weight: 600;
}
.el-slider {
  flex: 1;
  margin-left: 0.15rem;
}
.range span {
  margin: 0 0.07rem 1px;
}
.range .all {
  margin-left: 0.15rem;
}

.slider-container {
  background-color: #4b484888;
  border-radius: 50px;
  height: 0.84rem;
  margin: 0 auto;
  width: 6.55rem;
  padding: 0.3rem;
  user-select: none;
}

.slider {
  position: relative;
  display: flex;
  align-items: center;
}

.slider > span {
  color: #fff;
  font-weight: 600;
  padding: 0 10px;
  letter-spacing: 0.5px;
  font-size: 16px;
}

.slider-bg {
  background-color: #de3162;
  height: 10px;
  border-radius: 5px;
  width: 100%;
  position: relative;
  cursor: pointer;
}

.slider-range {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  background-color: #6eed9b;
  box-shadow: 0 0 20px #02f292;
  border-radius: 5px;
  transition: right ease 200ms;
}

.slider-handle {
  border: 1px solid #c5c5c5;
  background: #f6f6f6;
  cursor: grabbing;
  width: 1.2em;
  height: 1.2em;
  position: absolute;
  z-index: 1;
  top: -0.3em;
  margin-right: -0.6em;
  transition: right ease 200ms;
  border-radius: 4px;
}

.slider-handle.active {
  background-color: #3d91e7;
}

.slider-tooltip {
  width: 0.25rem;
  text-align: center;
  position: absolute;
  margin-top: -0.3rem;
  background: #000;
  padding: 0.04rem;
  border-radius: 0.05rem;
  color: #fff;
  font-size: 0.8em;
  margin-right: -1em;
  transition: right ease 200ms;
}
@media screen and (max-width: 720px) {
  .slider-container {
    background-color: #4b484888;
    border-radius: 0.5rem;
    height: 0.84rem;
    margin: 0 auto;
    width: 100%;
    padding: 0.3rem;
    user-select: none;
  }

  .slider {
    position: relative;
    display: flex;
    align-items: center;
  }

  .slider > span {
    color: #fff;
    font-weight: 600;
    padding: 0 0.1rem;
    letter-spacing: 0.5px;
    font-size: 0.16rem;
  }

  .slider-bg {
    background-color: #de3162;
    height: 0.1rem;
    border-radius: 5px;
    width: 100%;
    position: relative;
    cursor: pointer;
  }

  .slider-range {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    background-color: #6eed9b;
    box-shadow: 0 0 20px #02f292;
    border-radius: 5px;
    transition: right ease 200ms;
  }

  .slider-handle {
    border: 1px solid #c5c5c5;
    background: #f6f6f6;
    cursor: grabbing;
    width: 1.2em;
    height: 1.2em;
    position: absolute;
    z-index: 1;
    top: -0.3em;
    margin-right: -0.6em;
    transition: right ease 200ms;
    border-radius: 4px;
  }

  .slider-handle.active {
    background-color: #3d91e7;
  }

  .slider-tooltip {
    width: 0.5rem;
    text-align: center;
    position: absolute;
    margin-top: -0.3rem;
    background: #000;
    padding: 0.04rem;
    border-radius: 5px;
    color: #fff;
    font-size: 0.8em;
    margin-right: -1em;
    transition: right ease 200ms;
  }
}
</style>

