<template>
   <div>
      <div class="container">
          <div class="row">
              
              <div class="col-4">
                <img :src="photo" />
              </div>
  
              <div class="col-8">
                <h3> {{ photo_name }} </h3>

                <ul>
                  <li v-for="descr in description" v-bind:key="descr">
                      {{ descr }}
                  </li>
                </ul>
                
                 
                <button 
                    type="button" 
                    class="btn"
                    @click="this.Cart"
                    :disabled="!is_avaliable" 
                    :class="buttonClass">
                    <div v-if="is_avaliable">Купить</div>
                    <div v-else>Недоступно</div>
                </button>
                 
               

              </div>

          </div>

      </div> 
 
   </div>
</template>

<script>
export default {
  name: 'photo_item',
  props: {
    photo_name: String,
    photo: String,
    description: Object, 
    is_avaliable: Boolean,
    price: Number
  },
  methods:{
    Cart: function(){
      this.$emit('addToCart', this.price)
    }
  },
  computed: {
    buttonClass(){
      if (this.is_avaliable){
        return "btn btn-outline-success";
      }
      return "btn btn-outline-danger"
    }
  } 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.container{
  display: block;
  margin: 0px auto;
  padding: 10px;
}

h3 {
  margin: 20px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
  display: block;
  margin: 0 auto;
}
li {
  display: block;
  margin: 2px 10px;
}
img{
  display: block;
  width: 100%;
  height: 100%;
}
a {
  color: #42b983;
}

 


</style>
