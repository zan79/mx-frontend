<template>
  <div>
    <NavBar/>
    <ProductUpdateModal :product="selectedProduct"/>
    <ProductDeleteModal :product="selectedProduct" @onDeleted="getAll" />
    <div class="container mt-5">
      <div>
        <ProductEntryModal class="float-right mt-2" @onAdded="getAll"/>
        <h1 class="text-warning">Products</h1>
      </div>
      <table class="table table-striped table-dark">
        <thead class="bg-warning text-dark">
          <th>Name</th>
          <th>Brand</th>
          <th>Description</th>
          <th>Price</th>
          <th>Stock</th>
          <th>&nbsp;</th>
          <th>&nbsp;</th>
        </thead>
        <tbody>
          <tr v-for="product in products" :key="product.id">
            <td>{{product.name}}</td>
            <td>{{product.brand}}</td>
            <td>{{product.description}}</td>
            <td>{{product.price}}</td>
            <td>{{product.stock}}</td>
            <td>
              <b-button @click="onEdit(product)" variant="info" size="sm">Update</b-button>
            </td>
            <td>
              <b-button @click="onDelete(product)" variant="danger" size="sm">Delete</b-button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>

export default {
  data(){
    return {
      products: [],
      selectedProduct: {}
    }
  },
  methods: {
    async getAll(){
      await this.$axios.get('/api/products')
      .then((res)=>{
        if(res.status==200){
          this.products = res.data
        }
      })
    },
    onEdit(selectedProduct){
      this.selectedProduct = selectedProduct
      this.$bvModal.show('productUpdateModal')
    },
    onDelete(selectedProduct){
      this.selectedProduct = selectedProduct
      this.$bvModal.show('productDeleteModal')
    }
  },
  created(){
    this.getAll()  
  }
}
</script>

<style>
body{
  background-color: #212121;
}
</style>