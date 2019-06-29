

<template>
        <div class="row">
                <div v-for="(item, index) in items" class="card" style="width: 17rem;">
                  <img class="card-img-top" :src="item.photo" alt="Card image cap">
                  <div class="card-body">
                    <h5 class="card-title"> {{ item.title }} </h5>
                    <p class="card-text"> {{ item.price }} </p>
                    <a @click="addToCart(item)" class="btn btn-primary"> + Add </a>
                  </div>
                </div>

                

              
            </div>
</template>
<script>
import axios from 'axios'
export default {
data(){
  return {
    items: []
  }
},
mounted(){
  this.fechInventory()
},
methods: {
  addToCart(item){
   this.$emit('newItemAdded', item)
  },
  fechInventory(){
   axios.get('http://localhost:3000/items').then(response => {
     console.log(response)
   })
  }
 }
}
</script>

<style>

</style>
            