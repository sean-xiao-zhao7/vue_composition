<template>
  <h2>{{ fullname }}</h2>
  <h3>{{ age }}</h3>
</template>

<script>
import { computed, inject } from '@vue/runtime-core';
export default {
  props: ['firstname', 'lastname'],
  setup(props, context) {
    console.log(context);
    const fullname = computed(() => {
      return props.firstname + ' / ' + props.lastname;
    });

    const age = inject('age');

    return {
      fullname: fullname,
      age,
    };
  },
};
</script>
