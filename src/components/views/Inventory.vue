

<template>
        <div v-if="!loading" class="row">
                <div v-for="(item, index) in items" class="card" style="width: 17rem;">
                  <router-link tag="div" :to="{ path: '/item/' + item.id }" >
                    <img class="card-img-top" :src="item.photo" alt="Card image cap">
                  <div class="card-body">
                    <h5 class="card-title"> {{ item.title }} </h5>
                  </div>
                  </router-link>                    
                  <div class="card-footer">
                    <p class="card-text"> {{ item.price }} </p>
                    <a @click="addToCart(item)" class="btn btn-primary"> + Add </a>
                  </div>
                </div>              
            </div>
            <h1 v-else>Loading...</h1>
</template>
<script>
import axios from 'axios'
export default {
data(){
  return {
    loading: true,
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
        this.items = response.data
        this.loading = false        
   })
  }
 }
}
</script>

<style>

</style>
            