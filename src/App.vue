<template>
  <main>
    <h2>Parent form </h2>
    <button @click="setChildValues">Set to Hello World</button>

    <details>
      <summary>Meta</summary>
      <code>
        {{ meta }}
      </code>
    </details>

    <details>
      <summary>Values</summary>
      <code>
          {{ values }}
        </code>
    </details>
    <div>
      <child-form name="childForm"/>
    </div>
  </main>
</template>


<script setup>
import { useForm } from 'vee-validate';
import ChildForm from './ChildForm.vue';


const { values, setFieldValue, meta } = useForm({
  initialValues: {
    childForm: [],
  }
});


function setChildValues(){
  setFieldValue('childForm', [{name: 'hello'}, {name: 'world'}]);
}

</script>
<style>
html{
  font-family: sans-serif;
}
code{
  white-space: pre;
}
main{
  padding: 0 10rem
}
</style>
