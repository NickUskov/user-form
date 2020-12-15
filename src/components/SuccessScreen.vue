<template>
  <div class="success-wrapper">
    <div class="success">
      <h2>Клиент успешно добавлен!</h2>
      <button @click="fireClick">Ок</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "SuccessScreen",
  methods: {
    fireClick() {
      this.$emit("fire-click");
    },
  },
};
</script>

<style lang='sass'>
.success-wrapper
    display: flex
    justify-content: center
    align-items: center
    width: 100vw
    height: 100vh

.success
    text-align: center
    margin: 3rem
    background-color: rgba(255, 255, 255, 1)
    border-radius: 5px
    padding: 2rem
    width: 500px
    height: 200px
    display: flex
    flex-direction: column
    align-items: center
    justify-content: center
    box-shadow: 0 3px 3px rgba(0,0,0,0.5)
    button
        background-color: #0984e3
        font-size: 16px
        cursor: pointer
        border-radius: 2px
        margin: 1rem auto
        margin-bottom: 0
        padding: 10px
        width: 200px
        color: white
        border: none
        transition: 0.1s
        &:hover
            background-color: #2980b9
</style>