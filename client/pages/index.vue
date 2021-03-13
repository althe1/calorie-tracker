<template>
  <b-container>
    <h1>Main Page</h1>
    <b-row>
      <b-col>
        <line-chart v-if="data" :data="data" />
      </b-col>
      <b-col>
        <calorie-form v-on:addValue="addValue" />
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  middleware: "auth",
  data() {
    return {
      data: null
    };
  },
  async mounted() {
    this.data = await this.$axios.$get("/calories");
  },
  methods: {
    addValue(entry) {
      this.data.push(entry);
      console.log({ entry });
    }
  }
};
</script>
