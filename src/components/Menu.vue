<template>
  <div class="hello">

    <h1>Coffee Liège</h1>
    <p class="titleMenu">{{message}}</p>

      <div class="containerPrincipale">
        <div class="menuContainer" v-for="(item, index) in simpleMenu" :key="index">
          <div class="menu" v-if="item.disponible == true" v-on:click="addProduit(item) in simpleMenu">
              <img v-if="item.disponible == true" class="pictureMenu" v-bind:src="item.url" alt="item.alt"/>
              {{item.label}} : <br/> {{item.cost}} $
          </div>
        </div>  
      </div>

      <div v-if="shop.length > 0">

        <div id="panier" v-for="item in shop" :key="item">
            {{ item.label }} : {{ item.cost }} $
            
        </div>
      <!-- <div id="panier" v-for="item in shop" :key="item">
            TOTAL = {{  totalCofee }} $
        </div> -->
        <p>TOTAL = {{  totalCofee }} $</p>
        
      </div>

    </div>

</template>

<script>
export default {
  name: 'Menu',
   data: () => {
        return {
            message : "Menu de saison : ",
          
             simpleMenu: [
                { label: 'Black Coffee', cost: 3, disponible:true, url: require('@/assets/coffeeblack.jpg'), alt: "Black Coffee"},
                { label: 'Milk Coffee', cost: 3 ,disponible:true, url: require('@/assets/coffeemilk.jpg'), alt: "Milk Coffee"},
                { label: 'Hot Chocolate', cost: 4 ,disponible:true, url: require('@/assets/hotchoco.jpg'), alt: "Hot chocolate"},
                { label: 'Ice Chocolate', cost: 4 ,disponible:true, url: require('@/assets/chocoice.jpg'), alt: "Ice chocolate"},
                { label: 'Cappuccino', cost: 3 ,disponible:true, url: require('@/assets/cappuccino.jpg'), alt: "Cappuccino"},
                { label: 'Gourmet coffee', cost: 10 ,disponible:true, url: require('@/assets/cafe-gourmand.jpg'), alt: "Gourmet Cofee"},
                { label: 'Water', cost: 3 ,disponible:true, url: require('@/assets/water.jpg'), alt: "Water"},
                { label: 'Orange juice', cost: 10 ,disponible:false, url: require('@/assets/orangejuice.jpg'), alt: "Orange juice"}
            ],

              shop : [],
        }
    },

    methods: {

    addProduit(simpleMenu){

      this.shop.push({
        label: simpleMenu.label,
        cost: simpleMenu.cost
      })
    },
    },

    computed: {

      totalCofee() {
          let total = 0

          this.shop.forEach(item => {
            total += item.cost
          })
          return  total
        },
      
      }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1{
  font-size: 4rem;
  color: rgb(188, 211, 226);
}

a {
  color: #42b983;
}

.containerPrincipale{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.menuContainer {
  max-width: 100%;
  display: flex;
  justify-content: center;
}
.menu {
  margin: 10px 10px;
  font-size: 1.4rem;
  color: white;
  width: 200px;
  height: 200px;
  background-color: black;
  border-radius: 10px;
}

.titleMenu{
  margin-top: 60px;
  margin-bottom: 60px;
  font-size: 2rem;
   color: rgb(233, 222, 222);
}

.pictureMenu{
  width: 200px;
  height: 100px;
}

#panier{
  margin-top: 10px;
  font-size: 2rem;
  color: white;
}
</style>
