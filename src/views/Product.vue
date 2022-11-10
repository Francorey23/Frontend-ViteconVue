<template>
    <div class="container">
        <h2>Listado de productos</h2>
        <table class="table">
  <thead>
    <tr>
      <th scope="col">Categoria</th>
      <th scope="col">Codigo</th>
      <th scope="col">Nombre</th>
      <th scope="col">Descripcion</th>
      <th scope="col">Precio</th>
      <th scope="col">Cantidad</th>
      <th scope="col">Estado</th>
    </tr>
  </thead>
  <tbody v-if="products">
    <tr v-for="product in products" :key="product.id">
      <th scope="row">{{product.id}}</th>
      <td>{{product.codigo}}</td>
      <td>{{product.nombre}}</td>
      <td>{{product.descripcion}}</td>
    </tr>
    
  </tbody>
</table>
    </div>
    
</template>

<script>
import axios from 'axios'
export default {
    name: "Product",
    data(){
        return{
            products: "",
        }
    },
    mounted() {
        this.getProducts()
    },
    methods: {
        async getProducts(){
            try {
                const response = await axios.get("http://127.0.0.1:8000/api/product")
                //console.log(response)
                this.products = response.data.producto
            } catch (error) {
                console.error(error)
            }
        }
    },
}
</script>