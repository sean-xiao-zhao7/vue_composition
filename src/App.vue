<template>
  <section class="container">
    <user-data :firstname="firstname" :lastname="lastname"></user-data>
    <div>
      <input type="text" placeholder="First name" v-model="firstname" />
      <input type="text" placeholder="Last name" ref="lastnameRef" />
      <button @click="setName">Set name</button>
    </div>
  </section>
</template>

<script>
import { reactive, ref, computed, watch, provide } from 'vue';
import UserData from './components/UserData.vue';

export default {
  components: { UserData },
  setup() {
    const user = reactive({ name: 'Test', age: 0 });
    const firstname = ref('');
    const lastname = ref('');
    const lastnameRef = ref(null);

    const changeAge = (age) => {
      user.age = age;
    };

    const fullname = computed(() => {
      return firstname.value + ' ' + lastname.value;
    });

    const setName = () => {
      lastname.value = lastnameRef.value.value;
    };

    watch(lastname, () => {});

    provide('age', 0);

    return {
      user: user,
      changeAge: changeAge,
      firstname,
      lastname,
      lastnameRef,
      fullname,
      setName,
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
