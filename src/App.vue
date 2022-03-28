<template>
  <section class="container">
    <h2>{{ fullname }}</h2>
    <h3>{{ user.age }}</h3>
    <button @click="changeAge(3)">Change age</button>
    <div>
      <input type="text" placeholder="First name" v-model="firstname" />
      <input type="text" placeholder="Last name" v-model="lastname" />
    </div>
  </section>
</template>

<script>
import { reactive, ref, computed, watch } from 'vue';

export default {
  setup() {
    const user = reactive({ name: 'Test', age: 0 });
    const firstname = ref('');
    const lastname = ref('');

    const changeAge = (age) => {
      user.age = age;
    };

    const fullname = computed(() => {
      return firstname.value + ' ' + lastname.value;
    });

    watch(lastname, () => {});

    return {
      user: user,
      changeAge: changeAge,
      firstname,
      lastname,
      fullname,
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>
