<template>
<div class="main-container">
  <div class="container">
    <div class="user" :class="isSelected(index)" v-for="user, index in users" :key="index">
      {{ user }}
    </div>
  </div>
  <div class="spin-button">
    <button  @click="spinRoulette">Lanzar ruleta!</button>
  </div>
</div>
</template>

<script>
export default {
  name: 'BaseRoulette',
  data () {
    return {
      users: ['bruno', 'jose javier', 'carmen', 'juan pablo', 'roberto', 'adrian antonio', 'simon', 'sergio', 'ismael', 'irina', 'ricardo adrian', 'dario', 'lucia', 'carlos', 'antonio', 'mathias', 'nestor', 'aythami'],
      userSelected: -1
    };
  },
  methods: {
    getRandom () {
      return Math.floor(Math.random() * this.users.length);
    },
    spinRoulette () {
      this.userSelected = this.getRandom();
    },
    isSelected (index) {
      return (index === this.userSelected) ? 'selected' : '';
    }
  },
  mounted () {
    console.log('mounted');
  },
  updated () {
    console.log('updated');
  }

};
</script>

<style lang="postcss" scoped>

.main-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  & .container {

    border: 2px solid red;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    width: 900px;
    margin: auto;

    & .user {
      border: 2px solid black;
      padding: 6px;
      font-size: 2em;

      &.selected {
        background: red;
      }
    }
  }
  & .spin-button {
    margin-top: 20px;
  }

  & button {
    width: 100vw;
    height: 200px;
  }
}

</style>
