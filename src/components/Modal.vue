<template>
  <div class="backdrop" @click.self="closeModal"> //@click.self only work when clicking the div
    <div class="modal" :class="{ sale: theme === 'sale' }"> //:class="{ sale: theme === 'sale' } dynamic classes
      <slot>default content if no slot passed in</slot>
      <div class="actions"> //named slot
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  //props passed from parent
  props: ['theme'],
  //functions
  methods: {
    closeModal() {
      //.$emit('close') to create a custom event named close to be used in the parent
      this.$emit('close')
    }
  }
}
</script>

<style>
  .modal {
    width: 400px;
    padding: 20px;
    margin: 200px auto;
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
  /* sale styles */
  .modal.sale {
    background: crimson;
    color: white;
  }
  .modal.sale h1 {
    color: white;
  }
  .modal.sale .actions {
    color: white;
  }
  .modal.sale .actions a {
    color: white;
  }
</style>