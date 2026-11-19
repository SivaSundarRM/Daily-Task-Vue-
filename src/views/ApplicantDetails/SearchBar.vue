<template>
  <div class="search-container">
    <div class="input-wrapper">
      <input
        type="text"
        v-model="searchQuery"
        @keyup.enter="search"
        placeholder="Search applicants..."
        class="search-input"
      />
      <button @click="search" class="search-btn" aria-label="Search">
        <img
          src="https://media.geeksforgeeks.org/wp-content/uploads/20221210180758/Untitled-design-(28).png"
          class="icnsrchicn"
          alt="search-icon"
        />
      </button>
    </div>
    <div class="items">
      <ul v-if="filteredItems" class="results-list">
        <li v-for="item in filteredItems" :key="item.id" class="result-item">
          {{ item }}
        </li>
      </ul>

      <p v-else-if="submittedQuery" class="no-results">
        No matching applicants found for "{{ submittedQuery }}".
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: [],
      searchQuery: "",
      submittedQuery: "",
    };
  },
  computed: {
    filteredItems() {
      const query = this.submittedQuery.trim().toLowerCase();
      console.log(`Query Type:${typeof query} Query:${query}`);
      console.log(
        this.data.find(
          (item) =>
            String(item.loanId ?? "").toLowerCase() ===
            query.toLowerCase().trim()
        )
      );
      return this.data.find(
        (item) =>
          String(item.loanId ?? "").toLowerCase() === query.toLowerCase().trim()
      );
    },
  },
  methods: {
    async getDetails() {
      try {
        const response = await fetch("http://localhost:3000/applicantDetails");
        if (!response.ok) {
          throw new Error("HTTP Error Occurred");
        }
        this.data = await response.json();
      } catch (err) {
        console.error("Unexpected error:", err);
      }
    },
    search() {
      console.log("Items", typeof this.filteredItems);
      console.log("Data", this.data);
      this.submittedQuery = this.searchQuery;
    },
  },
  mounted() {
    this.getDetails();
  },
};
</script>

<style scoped>
.search-container {
  display: flex;
  flex-direction: column;
  flex: 1;
  gap: 20px;
  min-width: 0;
  max-width: 400px;
  height: 42px;
  align-items: center;
  margin-bottom: 500px;
}

.input-wrapper {
  display: flex;
  flex-direction: row;
}
.search-input {
  width: 100%;
  min-width: 0;
  height: 44px;
  padding: 0 20px;
  border: none;
  outline: none;
  border-radius: 50px 0 0 50px;
  background-color: #e0e0e0;
  font-size: 15px;
}

.search-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #0c007d;
  border-radius: 0 50px 50px 0;
}

.search {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 44px;
  height: 44px;
  padding: 0;
  background-color: #0b0080;
  border: none;
  border-radius: 0px 50px 50px 0px;
  cursor: pointer;
  transition: background-color 0.2s ease, transform 0.15s ease,
    box-shadow 0.2s ease;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.15);
}

.search:hover {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  cursor: pointer;
}

.icnsrchicn {
  width: 22px;
  height: 22px;
  object-fit: contain;
  display: block;
}

.items {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>