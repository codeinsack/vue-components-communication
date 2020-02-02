<template>
  <div class="component">
    <h3>You may view the User Details here</h3>
    <p>Many Details</p>
    <p>User name: {{ switchName() }}</p>
    <p>User age: {{ userAge }}</p>
    <button @click="resetName">Reset</button>
  </div>
</template>

<script>
  import { eventBus } from '../main'

  export default {
    props: {
      name: {
        type: String,
        default: 'Melanie',
      },
      userAge: Number,
    },
    methods: {
      switchName() {
        return this.name.split('').reverse().join('')
      },
      resetName() {
        this.myName = 'Abracadabra'
        this.$emit('nameWasReset', this.myName)
      }
    },
    created() {
      eventBus.$on('ageWasEdited', age => {
        this.userAge = age
      })
    }
  }
</script>

<style scoped>
  div {
    background-color: lightcoral;
  }
</style>
