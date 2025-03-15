<template>
  <div class="form__group field">
    <input
      v-bind="$attrs"
      :placeholder="label"
      @input="$emit('update:modelValue', $event.target.value)"
      type="input"
      class="form__field"
    />
    <label for="name" class="form__label">{{ label }}</label>
  </div>
</template>

<script setup>
defineProps({
  label: {
    type: String,
    required: true,
    default: "My Label",
  },
});
</script>

<style scoped>
.form__group {
  position: relative;
  padding: 20px 0 0;
  width: 100%;
  max-width: 250px;
}

.form__field {
  font-family: inherit;
  width: 100%;
  border: none;
  border-bottom: 2px solid var(--gray-color);
  outline: 0;
  font-size: 17px;
  color: var(--white-color);
  padding: 7px 0;
  background: transparent;
  transition: border-color 0.2s;
}

.form__field::placeholder {
  color: transparent;
}

.form__field:placeholder-shown ~ .form__label {
  font-size: 17px;
  cursor: text;
  top: 20px;
}

.form__label {
  position: absolute;
  top: 0;
  display: block;
  transition: 0.2s;
  font-size: 17px;
  color: var(--gray-color);
  pointer-events: none;
}

.form__field:focus {
  padding-bottom: 6px;
  font-weight: 700;
  border-width: 3px;
  border-image: linear-gradient(
    to right,
    var(--secondary-color),
    var(--primary-color)
  );
  border-image-slice: 1;
}

.form__field:focus ~ .form__label {
  position: absolute;
  top: 0;
  display: block;
  transition: 0.2s;
  font-size: 17px;
  color: var(--primary-color);
  font-weight: 700;
}

.form__field:required,
.form__field:invalid {
  box-shadow: none;
}
</style>
