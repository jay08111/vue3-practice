<template>
  <div class="backdrop">
    <div
      class="modal"
      :class="{ sale: theme === 'sale' }"
      @click.self="closeModal"
    >
      <h1>{{ header }}</h1>
      <p>modal content {{ text }}</p>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    header: {
      type: String,
    },
    text: {
      type: String,
    },
    theme: {
      type: String,
    },
    showModal: {
      type: Boolean,
    },
  },
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>
<style>
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: #fff;
  border-radius: 10px;
}
.modal h1 {
  color: #03fcb4;
  border: none;
  padding: 0;
}
.modal p {
  font-style: normal;
}
.modal.sale {
  background: crimson;
  color: white;
}
.modal.sale h1 {
  color: #fff;
}
.none {
  display: none;
}
</style>
