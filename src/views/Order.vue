<template>
    <div>
        <h1>customers</h1>
 <b-table striped hover :items="products" :fields="fields" :per-page="pagesize" :current-page="pageindex"></b-table>
  <b-pagination size="lg" :total-rows="products.length" v-model="pageindex" :per-page="pagesize">  </b-pagination>
    </div>
</template>
<script>
import axios from "axios";
export default {
  name: "customers",
  components: {},
  data() {
    return {
      message: "Project 2 By Tong",
      products: [],
      pagesize:5,
      pageindex:1,
      fields: [
        { key: "order_id", sortable: true },
        { key: "customer_id", sortable: true },
        { key: "employee_id", sortable: true },
        { key: "order_date", sortable: true },
        { key: "required_date", sortable: true },
        { key: "shipped_date", sortable: true },
        { key: "ship_via", sortable: true },
        { key: "freight", sortable: true },
        { key: "ship_name", sortable: true },
        { key: "ship_address", sortable: true },
        { key: "ship_city", sortable: true },
        { key: "ship_region", sortable: true },
        { key: "ship_postal_code", sortable: true },
        { key: "ship_country", sortable: true, variant: "danger" }
      ]
    };
  },
  mounted() {
    var instace = this;
    axios
      .get("https://quiet-chamber-68969.herokuapp.com/api/order/")
      .then(function(response) {
        console.log(response.data);
        instace.products = response.data.data;
      });
  }
};
</script>