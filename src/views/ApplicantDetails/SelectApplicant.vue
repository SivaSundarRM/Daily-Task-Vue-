<template>
  <div class="applicant">
    <div class="">
      <label for="applicant-select">Type of Update:</label>
      <select
        id="applicant-select"
        v-model="applicantSelect"
        @change="onUpdateTypeChange"
      >
        <option disabled value="">Please select one</option>
        <option
          v-for="option in applicantSelectOptions"
          :key="option"
          :value="option"
        >
          {{ option }}
        </option>
      </select>
    </div>

    <div class="">
      <label for="applicant-type">Sub Type:</label>
      <select
        id="applicant-type"
        v-model="applicantType"
        @change="logSelection"
      >
        <option disabled value="">Please select one</option>
        <option
          v-for="option in applicantTypeOptions"
          :key="option"
          :value="option"
        >
          {{ option }}
        </option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      applicantSelect: "",
      applicantType: "",
      applicantSelectOptions: [
        "Update Applicant Details",
        "Update Co-Applicant Details",
      ],
      applicantTypeOptions: ["Applicant", "Co-Applicant"],
    };
  },
  watch: {
    applicantSelect(newVal) {
      if (newVal === "Update Applicant Details") {
        this.applicantType = "Applicant";
      } else if (newVal === "Update Co-Applicant Details") {
        this.applicantType = "Co-Applicant";
      }
      this.logSelection();
    },
    applicantType(newVal) {
      if (newVal === "Applicant") {
        this.applicantSelect = "Update Applicant Details";
      } else if (newVal === "Co-Applicant") {
        this.applicantSelect = "Update Co-Applicant Details";
      }
    },
  },
  methods: {
    logSelection() {
      console.log("Type of Update:", this.applicantSelect);
      console.log("Sub Type:", this.applicantType);
    },
  },
};
</script>
<style scoped>
.applicant {
  display: flex;
  gap: 20px;
  padding: 20px;
}


</style>