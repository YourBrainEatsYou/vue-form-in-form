<template>
  <div>
    <hr >
    <h2>Child Field Array</h2>
    <div v-for="(field, idx) in fields" :key="idx">
      <Field :name="`${name}[${idx}].name`" v-slot="{value, handleInput, meta}" rules="required">
        <input type="text" :value="value" @input="handleInput" :style="{background: !meta.valid ? 'red' : 'transparent'}">
      </Field>
      <button @click="remove(idx)">Remove</button>
    </div>
    <button @click="push({name: ''})">Add Field</button>
  </div>
</template>

<script setup>
import { Field, useFieldArray, defineRule} from 'vee-validate';
import {required} from '@vee-validate/rules';
import { toRef } from 'vue';

defineRule('required', required)

const props = defineProps({
  name: {
    required: true,
    type: String,
  }
});

const name = toRef(props, 'name');

// I/O
const {remove, push, fields} = useFieldArray(name);
</script>
