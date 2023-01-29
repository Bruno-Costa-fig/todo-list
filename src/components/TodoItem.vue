<template>
  <div>
    <span :class="item.finalizado ? 'finalizado' : ''">{{item.titulo}}</span>
    <box-icon name="check"  
      @click="finalizarItem"></box-icon>
    <box-icon name="trash" @click="$emit('removerItem', item)"></box-icon>
  </div>
</template>

<script>
export default {
  name: "todo-item",
  props: {
    item: {
      type: Object,
      default: {
        titulo: "",
        finalizado: false
      }
    }
  },
  methods: {
    finalizarItem(){
      this.item.finalizado = !this.item.finalizado
    }
  }
}
</script>

<style>
.finalizado {
  text-decoration: line-through;
}
</style>