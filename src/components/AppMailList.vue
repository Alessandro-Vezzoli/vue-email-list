<template>
  <h1>LISTA EMAIL</h1>
  <ul v-if="listmail.length == 10">
    <li v-for="email in listmail" :key="email">{{ email }}</li>
  </ul>
</template>
<script>
export default {
  name: "AppMailList",

  data() {
    return {
      listmail: [],
    };
  },
  created() {
    for (let index = 0; index < 10; index++) {
      axios
        .get("https://flynn.boolean.careers/exercises/api/random/mail")
        .then((responde) => {
          const mail = responde.data.response + index;
          this.listmail.push(mail);
          console.log(mail);
        })
        .catch(() => {});
    }
  },
};
</script>
<style scoped></style>
