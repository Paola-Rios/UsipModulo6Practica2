<template>
  <div class="home">
    <div class="container">
        <div class="row">
            <h3>{{producto.nombre}}</h3>
        </div>
        <div class="row">
            <div class="col-12 col-sm-6 col-md-4 ">
                <img :src="`${producto.imagen}`" alt="" width="100%">
            </div>
            <div class="col-12 col-sm-6  col-md-8">
                <h6>{{producto.descripcion}}</h6>
                <div class="p-3 mb-2 text-white" v-bind:style="precioEstilos">
                    Precio: {{producto.precio}} BOB
                </div>
                <h5>Color</h5>
                <div>
                    <div v-for="color of producto.colores" class="color-box clic" v-on:click="actualizarColor(`${color}`)" :style="`background: ${color};`"/>
                </div>
                <h5>Cantidad</h5>
                <div class="quantity">
                    <button v-on:click='this.pedido.cantidad--'>-</button>
                    <div>{{pedido.cantidad}}</div>
                    <button v-on:click='this.pedido.cantidad++'>+</button>
                </div>
                <div class="buy-box">
                    <button type="button" class="btn btn-primary" v-on:click="eventoComprar()">Comprar</button>
                </div>
            </div>
        </div>
    </div>
  </div>

  <div class="container ">
    <div class="row">
        <h4>Productos relacionados</h4>
    </div>
    <div class="row">
        <div v-for="prodRel of productosRelacionados" class="col">
            <div class="card" style="width: 18rem;">
                <div class="card-body">
                    <h5 class="card-title">{{prodRel.nombre}}</h5>
                    <img :src="prodRel.imagen" alt="" width="100%">
                        <p class="card-text">{{prodRel.descripcion}}</p>
                        <div class="producto-relacionado-precio">Precio:{{prodRel.precio}} BOB</div>
                        <div>
                            <div>
                                <div v-for="color of prodRel.colores" class="color-box" :style="`background: ${color};`"/>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
  </div>
  <footer :style="`background-color: ${footerColor};`"></footer>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  data() {
    return{
      footerColor: "slategrey",
      precioEstilos: "background: orangered; color: white; font-weight: bold",
      producto: {
                    id:1,
                    imagen: "https://ae01.alicdn.com/kf/Sc3cc58f2a441419f970cc01f9e5358fbw/Dron-LU3-MAX-GPS-8K-HD-profesional-con-c-mara-Dual-card-n-autoestabilizador-Motor-sin.jpg_Q90.jpg_.webp",
                    nombre: "Dron LU3 MAX GPS 8K HD",
                    descripcion: "Dron LU3 MAX GPS 8K HD profesional con <b>cámara Dual</b>, cardán autoestabilizador, Motor sin escobillas para evitar obstáculos, cuadricóptero plegable",
                    precio: "620",
                    colores: ["red", "blue", "black", "yellow", "pink"]
                },
      productosRelacionados : [
                {
                    id:2,
                    imagen: "https://ae01.alicdn.com/kf/Hd59f72dd965d467dbbd499275a70b1d4z/Dron-plegable-KF102-con-Gps-8K-c-mara-Dual-HD-2-ejes-card-n-Motor-sin.jpg_Q90.jpg_.webp",
                    nombre: "KF102",
                    descripcion: "Dron plegable KF102 con Gps, 8K, cámara Dual HD, 2 ejes, cardán, Motor sin escobillas, fotografía aérea, 1200M de distancia, novedad de 2022",
                    precio:"1180",
                    colores: ["orange", "blue"]
                },
                {
                    id:3,
                    imagen:"https://ae01.alicdn.com/kf/S947d9284b5ea4531a1bec599a09a1f49K/KBDFA-Dron-E888-RC-cuadric-ptero-profesional-FPV-4K-HD-fotograf-a-a-rea-evitaci-n.jpg_Q90.jpg_.webp",
                    nombre: "KBDFA-Dron E888 RC",
                    descripcion: "KBDFA-Dron E888 RC, cuadricóptero profesional FPV, 4K HD, fotografía aérea, evitación de obstáculos, helicóptero, juguetes de distancia",
                    precio:"154",
                    colores: ["black", "midnightblue"]
                },
                {
                    id:4,
                    imagen:"https://ae01.alicdn.com/kf/S552326188797415ab6c729f850ab2639R/Dron-Profesional-4K-con-GPS-8K-c-mara-HD-3-ejes-card-n-antivibraci-n-evitaci.jpg_Q90.jpg_.webp",
                    nombre: "Dron Profesional 4K con GPS",
                    descripcion: "Dron Profesional 4K con GPS, 8K, cámara HD, 3 ejes, cardán antivibración, evitación de obstáculos, fotografía aérea, Quadcopter, nuevo",
                    precio:"1800",
                    colores: ["teal", "blue", "slategrey", "navy"]
                }
        ],
        pedido: {
          id: 123,
          cantidad: 1,
          color:"red"
        }
    }
  },
  components: {
     //HelloWorld
  },
  methods: {
    eventoComprar: function(){
      alert(`Id: ${this.pedido.id} - Cantidad: ${this.pedido.cantidad} - Color: ${this.pedido.color}`);
    },
    actualizarColor: function(nuevoColor) {
      this.pedido.color = nuevoColor;
    }
  }
}
</script>
<style>
            .color-box {
                width: 40px;
                height: 40px;
                border-radius: 50%;
                margin: 7px;
                display: inline-block;
            }

            .clic{
                cursor: pointer;
            }

            .quantity button{
                border-radius: 50%;
                display: inline-block;
                width: 30px;
            }
            .quantity div{
                text-align: center;
                min-width: 30px;
                display: inline-block;
                font-weight: bold;
            }
            .buy-box{
                margin: 20px;
            }
            footer {
                
                text-align: center;
                padding: 30px 10px;
                margin-top: 50px;
                min-height: 100px;
            }
            .container{
                margin-top: 50px;
            }
            .producto-relacionado-precio{
                background: orangered;
                color: white;
                text-align: center;
                padding: 10px; 
            }
</style>
