<template>
  <div>
    <b-button v-b-modal.productEntryModal variant="primary">Add Product</b-button>
    
    <b-modal id="productEntryModal" title="Product Entry Form" ok-title="Save Product" @ok="onAdd"
    ok-variant="success" cancel-variant="danger"
    header-bg-variant="dark"  header-text-variant="warning" header-border-variant="dark" header-close-variant="light"
    body-bg-variant="dark"    body-text-variant="light"
    footer-bg-variant="dark"  footer-border-variant="dark"
    >
      <form action="#">

        <b-form-group label="Name" label-for="name">
          <b-form-input id="name" v-model="product.name" trim></b-form-input>
        </b-form-group>

        <b-form-group label="Brand" label-for="brand">
          <b-form-input id="brand" v-model="product.brand" trim></b-form-input>
        </b-form-group>

        <b-form-group label="Description" label-for="description">
          <b-form-input id="description" v-model="product.description" trim></b-form-input>
        </b-form-group>

        <b-form-group label="Price" label-for="price">
          <b-form-input type="number" id="price" v-model="product.price" trim></b-form-input>
        </b-form-group>

        <b-form-group label="Stock" label-for="stock">
          <b-form-input type="number" id="stock" v-model="product.stock" trim></b-form-input>
        </b-form-group>

        <b-form-group label="Date Acquired" label-for="acquired">
          <b-form-input type="date" id="acquired" v-model="product.acquired_on" trim></b-form-input>
        </b-form-group>

      </form>
    </b-modal>  
  </div>
</template>

<script>
export default {
  data(){
    return {
      product: {}
    }
  },
  methods: {
    async onAdd(){
      this.$axios.post('/api/products', this.product)
      .then((res)=>{
        if(res.status==202){
          alert("Product Added Succesfully")
          this.$emit('onAdded')
        }
      })
    }
  }
}
</script>

<style>

</style>