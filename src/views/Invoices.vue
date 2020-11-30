<template>
  <div class="invoices">
    <h1 class="subheading grey--text">Invoices</h1>

    <v-container class="my-5">

     <v-layout row justify-center class="mb-3">
        <v-card>
        <v-card-title>
            <v-text-field
            v-model="search"
            append-icon="mdi-magnify"
            label="Search"
            single-line
            hide-details
            ></v-text-field>
        </v-card-title>
        <v-data-table
            :headers="headers"
            :items="invoices"
            :search="search"
        >
              <template v-slot:no-data>
        <v-alert :value="true" color="error" icon="warning">
          Sorry, nothing to display here
        </v-alert>
      </template>
        </v-data-table>
        </v-card>
      </v-layout>

    </v-container>
  </div>
</template>

<script>
export default {
 data() {
   return {
    search: '',
    loading: true,
    headers: [
        {
          text: 'Id',
          align: 'start',
          sortable: false,
          value: 'id',
        },
        { text: 'Title', value: 'title' },
        { text: 'Body', value: 'body' },
        { text: 'User Id', value: 'userId' },
      ],
      invoices: [
      ],
    }
  },
    watch: {
    options: {
      handler() {
        this.readDataFromApi();
      },
    },
    deep: true,
  },
  methods: {
    getInvoices() {
        const baseURI = 'https://jsonplaceholder.typicode.com/posts/'
        this.$http.get(baseURI)
          .then(response => {
              this.loading = false;
              console.log(response.data)
              this.invoices = response.data;
              console.log(this.invoices)
          })
          .catch(error => {
            console.log(error)
          })
          .finally(() => console.log("Done"))
        }
  },
  mounted () {
      this.getInvoices();
     }
  }
</script>