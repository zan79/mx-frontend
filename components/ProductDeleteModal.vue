<template>
   <div>    
    <b-modal id="productDeleteModal" title="Delete Product" ok-title="Delete Product" @ok="onDelete"
    ok-variant="danger" cancel-variant="secondary"
    header-bg-variant="dark"  header-text-variant="warning" header-border-variant="dark" header-close-variant="light"
    body-bg-variant="dark"    body-text-variant="light"
    footer-bg-variant="dark"  footer-border-variant="dark"
    >
      Do you really want to delete this product? <br>
      {{product.name}} - {{product.description}}
    </b-modal>  
  </div>
</template>

<script>
export default {
  props: {
    product: {}
  },
  methods: {
    async onDelete(){
      this.$axios.delete('/api/products/' + this.product.id)
      .then((res)=>{
        if(res.status==202){
          alert("Product Deleted Succesfully")
          this.$emit('onDeleted')
        }
      })
    }
  }
}
</script>

<style>

</style>
