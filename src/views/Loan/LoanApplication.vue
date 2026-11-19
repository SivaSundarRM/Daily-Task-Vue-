<template>
  <div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      data: [],
    };
  },
  methods: {
    async getDetails() {
      try {
        const response = await fetch("http://localhost:3000/applicantDetails");
        if (!response.ok) {
          throw new Error("Http Error occured");
        }
        const details = await response.json();
        this.data = details;
        console.log(this.data);
      } catch (error) {
        console.log("Error occured:", error);
      }
    },
  },
  mounted() {
    this.getDetails();
  },
};
</script>

<style>
</style>