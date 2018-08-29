<template>
  <div class="container">
   <h1>Listado de Productos</h1>
    <div class="container global">
      <div class="row">
          <div id="indicadores">
            <ul>
              <li v-for="info in infos" :info="info" :key="info"></li>
            </ul>
            
          </div>
      </div>
      <div class="row">
        <div class="col-sm-8">
          <div class="prod">
            <producto v-for="producto in productos" :producto="producto" :key="producto.id"></producto>
          </div>
        </div>
        <div class="col-sm-4">
          <div class="carrito">
            <carrito-compra></carrito-compra>
          </div>
        </div>
      </div>
    </div>
  </div>


</template>

<script>
import producto from './components/producto.vue'
import CarritoCompra from './components/carrito.vue'
import axios from 'axios'
export default {
  components:{producto, CarritoCompra},
  data () {
    return {
      infos: [],
      productos: [
        { id:1, nombre:'cuadro uno', precio: 50, img:'producto.jpg' },
         { id:2, nombre:'cuadro dos', precio: 20, img:'producto.jpg' },
         { id:3, nombre:'cuadro tres', precio: 15, img:'producto.jpg' },
         { id:4, nombre:'cuadro cuatro', precio: 25, img:'producto.jpg' }
      ],
      
    }
  },
  mounted () {
    axios
      .get('https://mindicador.cl/api')
      .then(response => (this.infos = response))
      console.log( this.infos );
  }
}

</script>

<style>
body {
  background: #eee;
}
.global {
  display:flex;
  justify-content: space-between
}
.prod {
  display:flex;
  justify-content: space-between;
  flex-wrap:wrap
}
.carrito {
  background-color:#EEEEEE;
}
</style>
