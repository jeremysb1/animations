<template>
  <button type="button" @click="flag = !flag">Toggle</button>
  
  <button @click="addItem">Add</button>
  <ul>
    <transition-group name="fade">
      <li v-for="(number, index) in mumbers" :key="number"
        @click="removeItem(index)"> {{ number }} 
      </li>
    </transition-group>
  </ul>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      flag: true,
      numbers: [1, 2, 3, 4, 5],
    };
  },
  methods: {
    addItem() {
      const num = Math.floor(Math.random() * 100 + 1);
      const index = Math.floor(Math.random() * this.numbers.length);
      this.numbers.splice(0, index, num);
    },
    removeItem() {
      this.numbers.splice(index, 1);
    }
    beforeEnter(el) {

    },
    enter(el) {
      // const animation = el.animate([{ transform: "scaled3d(0,0,0)" }, {}, {
      //   duration: 1000,
      // }]);

      // animation.onfinish = () => {
      //   done();
      // };
    },
    afterEnter(el) {

    },
    beforeLeave(el) {

    },
    leave(el) {
      // const animation = el.animate([ {}, { transform: "scaled3d(0,0,0)" }, {
      //   duration: 1000,
      // }]);
      // animation.onfinish = () => {
      //   done();
      // };
    afterLeave(el) {

    },
  },
};
</script>

<style>

li {
  font-size: 22px;
  cursor: pointer;
}

h2 {
  width: 400px;
  padding: 20px;
  margin: 20px;
}

.fade-enter-from {
  opacity: 0;
}

.fade-active-enter {
  transition: all 1s linear;
}

.fade-leave-to {
  transition: all 1s linear;
  opacity: 0;
}

.zoom-enter-active {
  animation: zoom-in 1s linear forwards;
  transition: all 2s linear;
}

.zoom-leave-active {
  animation: zoom-out 1s linear forwards;
  transition: all 2s linear;
}

.zoom-enter-from {
  opacity: 0;
}

.zoom-leave-to {
  opacity: 0;
}

@keyframes zoom-in {
  from {
    transform: scale(0, 0);
  }
  to {
    transform: scale(1, 1);
  }
}

@keyframes zoom-out {
  from {
    transform: scale(1, 1);
  }
  to {
    transform: scale(0, 0);
  }
}
</style>