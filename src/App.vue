<template>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
  <div class="cart position-absolute top-0 end-0">
      <p>Корзина: {{this.cart}} рублей</p>
      <button class = 'btn btn-outline-secondary' @click="clearCart">Очистить Корзину</button>
  </div>


  <photo_item 
      :photo_name="'Индивидуальная фотосъемка'" 
      :photo = this.images[0]  
      :description="['Срок выполнения — 7-10 дней.', '20 обработанных снимков', 'Реализация любых творческих идей']"
      :is_avaliable="true"
      @addToCart="addToCart"
      :price = "1500"
  />
  <photo_item 
      :photo_name="'Love-Story'" 
      :photo = this.images[1]  
      :description="['Срок выполнения — 8-14 дней.', 'Публикация фотографий осуществляется с Вашего разрешения.', 'Психологическая поддержка мужчин']"
      :is_avaliable="true"
      :price = "2000"
      @addToCart="addToCart"
      
  />
  <photo_item
      :photo_name="'Фотосессия мероприятия'" 
      :photo = this.images[2]  
      :description="['Срок выполнения — 14 дней.', 'При таинстве крещения, скидка - 500 рублей', 'Цена указана за 1 час']"
      :is_avaliable="true"
      :price = "2000"
      @addToCart="addToCart"
  />

</template>

<script>
import photo_item from './components/photo.vue'
import image1 from './assets/image/photo_1.jpg'
import image2 from './assets/image/photo_2.jpg'
import image3 from './assets/image/photo_3.jpg'


export default {
  name: 'App',
  data(){
    return{
      images: [image1, image2, image3],
      cart: 0
    }
  },
  methods: {
    addToCart: function(value){
      this.cart += value;
    },
    clearCart: function(){
      this.cart = 0;
    }
  },

  components: {
    photo_item
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}

.cart{
  display: block;
  width: 150px;
}

</style>
