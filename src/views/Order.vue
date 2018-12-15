<template>
    <div>
        <h1>Google Store</h1>
        <b-form-group horizontal label="Search" class="mb-0">
          <b-input-group>
            <b-form-input v-model="filter" placeholder="Type to Search" />
            <b-input-group-append>
              <b-btn :disabled="!filter" @click="filter = ''">Clear</b-btn>
            </b-input-group-append>
          </b-input-group>
        </b-form-group>
        <b-table striped hover :items="products" :fields="fields" :filter="filter" :per-page="10" :current-page="pageIndex" @filtered="onFiltered">
        <template slot="actions" slot-scope="row">
        <!-- We use @click.stop here to prevent a 'row-clicked' event from also happening -->
        <b-button size="sm" @click.stop="info(row.item, row.index, $event.target)" class="mr-1">
          Info modal
        </b-button>
        
      </template>
   

        </b-table>
        <b-pagination size="md" :total-rows="products.length" v-model="pageIndex" :per-page="pageSize"></b-pagination>

    </div>
</template>
<script>
import axios from "axios";
export default {
  name: "product",
  components: {},
  data() {
    return {
      message: "Project 2",
      products: [],
      pageSize: 10,
      pageIndex: 1,
      fields: [
        {
          key: "order_id",
          sortable: true
        },
        {
          key: "customer_id",
          sortable: true
        },
        {
          key: "employee_id",
          sortable: true,
          
        },
        {
          key: "order_date",
          sortable: true,
          
        },
        {
          key: "required_date",
          sortable: true,
          
        },
        {
          key: "shipped_date",
          sortable: true,
          
        },
        {
          key: "ship_via",
          sortable: true,
          
        },
        {
          key: "freight",
          sortable: true,
          
        },
        {
          key: "ship_name",
          sortable: true,
         
        },
        {
          key: "ship_address",
          sortable: true,
         
        },
        {
          key: "ship_city",
          sortable: true,
          
        },
         {
          key: "ship_region",
          sortable: true,
          
        },
         {
          key: "ship_postal_code",
          sortable: true,
          
        },
         {
          key: "ship_country",
          sortable: true,
         
        },
        {
          key: "product_id",
          sortable: true,
          
        },
         {
          key: "unit_price",
          sortable: true,
          
        },
         {
          key: "quantity",
          sortable: true,
          
        },
         {
          key: "discount",
          sortable: true,
          
        },
         {
          key: "company_name",
          sortable: true,
          
        },
         {
          key: "contact_name",
          sortable: true,
          
        },
         {
          key: "contact_title",
          sortable: true,
          
        },
         {
          key: "address",
          sortable: true,
          
        },
         {
          key: "city",
          sortable: true,
          
        },
         {
          key: "region",
          sortable: true,
          
        },
        {
          key: "postal_code",
          sortable: true,
         
        },
        {
          key: "country",
          sortable: true,
         
        },
        {
          key: "phone",
          sortable: true,
          
        },
        {
          key: "fax",
          sortable: true,
          
        },
          {
          key: "fax",
          sortable: true,
          
        },
          {
          key: "fax",
          sortable: true,
          
        },
           {
          key: "title_of_courtesy",
          sortable: true,
          
        },
        {
          key: "first_name",
          sortable: true,
          
        },
          {
          key: "last_name",
          sortable: true,
          
        },
        {
          key: "title",
          sortable: true,
          
        },

          {
          key: "birth_date",
          sortable: true,
         
        },
        {
          key: "hire_date",
          sortable: true,
          
        },
        {
          key: "home_phone",
          sortable: true,
          
        },
          {
          key: "extension",
          sortable: true,
          
        },
         {
          key: "reports_to",
          sortable: true,
         
        },
         {
          key: "photo_path",
          sortable: true,
        }
      ],
      filter: null,
    };
  },
  methods: {
    onFiltered (filteredItems) {
      // Trigger pagination to update the number of buttons/pages due to filtering
      this.totalRows = filteredItems.length
      this.currentPage = 1
    }
  },
  mounted() {
    var instance = this;
    axios
      .get("https://afternoon-sands-15941.herokuapp.com/api/products")
      .then(function(response) {
        console.log(response.data);
        instance.products = response.data.data;
      });
  }
};
</script>