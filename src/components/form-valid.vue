<template>
  <div class="form">
    <div class="form__header">Parola Yenileme</div>
    <div class="form__body">
      <div class="form__group" :class="{ 'form-group--error': $v.name.$error }">
        <div class="form__groupRow">
          <label>Name:</label>
          <input v-model.trim="name" @input="setName($event.target.value)" />
        </div>
        <div v-if="!$v.name.required">Field is required</div>
        <div v-if="!$v.name.minLength">
        Name must have at least {{ $v.name.$params.minLength.min }} letters.
    </div>
      </div>

      <div class="form__group" :class="{ 'form-group--error': $v.age.$error }">
        <div class="form__groupRow">
        <label>Age:</label>
        <input :value="age" @change="setAge($event.target.value)" />
    </div>
    <div v-if="!$v.age.between">
        Must be between {{ $v.age.$params.between.min }} and
        {{ $v.age.$params.between.max }}
      </div>
      </div>
      
    </div>
  </div>
</template>

<script>
import { required, minLength, between } from "vuelidate/lib/validators";

export default {
  data() {
    return {
      name: "",
      age: 0,
    };
  },
  validations: {
    name: {
      required,
      minLength: minLength(4),
    },
    age: {
      between: between(20, 30),
    },
  },

  methods: {
    setName(value) {
      this.name = value;
      this.$v.name.$touch();
    },
    setAge(value) {
      this.age = value;
      this.$v.age.$touch();
    },
  },
};
</script>
<style>
.form {
  width: 80vh;
  background-color: white;
  border: 2px solid black;
  border-radius: 10px;
}

.form__header {
  background-color: black;
  color: white;
  padding: 20px 40px;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
}

.form__body {
  padding: 20px 40px;
}

.form__group {
  margin-top: 30px;
  display: flex;
  flex-direction: column;
}

.form__groupRow {
  display: flex;
  justify-content: space-between;
}
</style>
