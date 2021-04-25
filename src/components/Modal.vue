<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal">
      <p :class="{green: text === 'Japheth' }">{{text}}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    text: String
  },
  methods:{
    closeModal(){
      this.$emit('closeModal')
    }
  }
}
</script>

<style scoped>
.modal{
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: #fff;
    border-radius: 5px;
}
.backdrop{
    top: 0;
    position: absolute;
    background: rgba(0, 0, 0, 0.5);
    width: 100%;
    height: 100%;
}
.green{
  color: green;
}
</style>