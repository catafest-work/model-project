<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <!-- <h1>{{ header }}</h1>
      <p>{{ text }}</p> -->
      <!-- use slot from App.vue  slot has a wrapper div class modal , in App.vue toggleModal button ALT used in "methods" toggle the dialog  -->
      <!-- the text "default content<" is show only if on App.js has only the tag template in tag "Modal" without any tags -->
      <slot>default content</slot> 
      <div class="actions">
        <!-- baset of definition of <template v-slot:links> from App.vue will parse all slots and will use the next source code :  -->
        <slot name="links"></slot> 
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    // using props 
    //props: ['header', 'text', 'theme'], 
    props: ['theme'], 
    methods: {
      closeModal() {
        this.$emit('close'); // emit event  this is colected by   <div class="backdrop" @click="closeModal"> and reflect in App.vue , see <div v-if="showModal">, and can be used like @close !
      }
    }
  }
</script>
<style> 
.modal 
{ 
  width: 400px; 
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.backdrop { 
  top: 0;
  position: fixed;
  background: rgba(0,0,0,0.5);
  width: 100%;
  height: 100%;
} 
.modal h1 {
  color: #03cfb4;
  border: none;
  padding: 0;
}
.modal p {
  font-style: normal;
}
.modal .actions {
  text-align: center;
  margin: 30px 0 10px 0;
}
.modal .actions a {
  color: #333;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}
.modal.sale {
  background-color: crimson;
  color: white;
}
.modal.sale h1 {
    color: white;
}
</style>