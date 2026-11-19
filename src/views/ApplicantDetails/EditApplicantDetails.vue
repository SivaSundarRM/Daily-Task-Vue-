<template>
  <div>
    <div>
      <SelectApplicant />
    </div>
    <div>
      <table border="1">
        <thead>
          <tr>
            <th>Field Name</th>
            <th>Original</th>
            <th>L1</th>
            <th>L2</th>
            <th>L3</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th scope="row">First Name</th>
            <td>Siva</td>
            <td>Siva | <button>update</button></td>
            <td><button>update</button></td>
            <td></td>
          </tr>
          <tr>
            <th scope="row">Last Name</th>
            <td>Sundar</td>
            <td><button>update</button></td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <th scope="row">Email</th>
            <td>sivaramachandran242@gmail.com</td>
            <td><button>update</button></td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <th scope="row">Mobile Number</th>
            <td>8309940289</td>
            <td><button>update</button></td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <th scope="row">Date of Birth</th>
            <td>04/12/2004</td>
            <td><button>update</button></td>
            <td></td>
            <td></td>
          </tr>
          <tr class="table-second__header">
            <th scope="row" colspan="5">Installation Address</th>
          </tr>
          <tr>
            <th scope="row">Street 1</th>
            <td>8-11 govt hospital road</td>
            <td><button>update</button></td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <th scope="row">Street 2</th>
            <td>8-11 govt hospital road</td>
            <td><button>update</button></td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <th scope="row">City</th>
            <td>---</td>
            <td></td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <th scope="row">State</th>
            <td>---</td>
            <td></td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <th scope="row">Zipcode</th>
            <td>---</td>
            <td></td>
            <td></td>
            <td></td>
          </tr>
          <tr class="table-third__header">
            <th scope="row" colspan="5">Billing Address</th>
          </tr>
          <tr>
            <th scope="row">Street 1</th>
            <td>8-11 govt hospital road</td>
            <td><button>update</button></td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <th scope="row">Street 2</th>
            <td>8-11 govt hospital road</td>
            <td><button>update</button></td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <th scope="row">City</th>
            <td>---</td>
            <td></td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <th scope="row">State</th>
            <td>---</td>
            <td></td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <th scope="row">Zipcode</th>
            <td>---</td>
            <td></td>
            <td></td>
            <td></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import SelectApplicant from "./SelectApplicant.vue";

export default {
  components:{
    SelectApplicant
  },
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
table {
  border-collapse: separate;
  border-spacing: 0;
  border: 1px solid #ccc;
  border-radius: 10px;
  overflow: hidden;
  width: 100%;
}
th,
td {
  border-top: none;
  border-bottom: none;
  border-left: 1px solid black;
  border-right: 1px solid black;
  padding: 8px;
}

.table-second__header {
  border: 1px solid black;
  background-color: #000000;
}

tr.table-second__header th {
  color: #ffffff;
  font-weight: bold;
  text-align: left;
  padding-left: 20px;
}

tr.table-third__header {
  border: 1px solid yellow;
  background-color: #000000;
}

tr.table-third__header th {
  color: #ffffff;
  font-weight: bold;
  text-align: left;
  padding-left: 20px;
}
</style>