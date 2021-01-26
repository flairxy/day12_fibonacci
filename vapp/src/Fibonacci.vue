<template>
  <div>
    <h1>Fibinacci</h1>
    <form @submit.prevent="getFib">
      <input type="number" v-model="number" placeholder="Enter a number" />
      <button>submit</button>
    </form>
    <p>{{ fib_value }}</p>
  </div>
</template>
<script>
import { mapGetters } from "vuex";
export default {
  data: () => ({
    fib_value: "",
    number: 0,
  }),
  computed: {
    ...mapGetters("drizzle", ["drizzleInstance"]),
  },
  methods: {
    getFib() {
      this.drizzleInstance.contracts.Fibonacci.methods
        .fib(this.number)
        .call()
        .then((res) => {
          this.fib_value = `The fibonacci of ${this.number} is ${res}`;
        });
    },
  },
};
</script>
