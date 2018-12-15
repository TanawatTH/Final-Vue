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
        { key: "OrderID", sortable: true },
        { key: "CustomerID", sortable: true },
        { key: "EmployeeID", sortable: true },
        { key: "OrderDate", sortable: true },
        { key: "RequiredDate", sortable: true },
        { key: "ShippedDate", sortable: true },
        { key: "ShipVia", sortable: true },
        { key: "Freigth", sortable: true },
        { key: "Shipname", sortable: true },
        { key: "ShipAddress", sortable: true },
        { key: "ShipCity", sortable: true },
        { key: "ShipRegion", sortable: true },
        { key: "PostalCode", sortable: true },
        { key: "ShipCountry", sortable: true },
        { key: "Fax", sortable: true, variant: "danger" }
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