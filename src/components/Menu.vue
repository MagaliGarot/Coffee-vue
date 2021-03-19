<template>
  <div class="hello">

    <h1>Coffee Liège</h1>

    <p class="intro"> Curabitur lacus ligula, ullamcorper aliquet vulputate quis, dignissim vitae justo. 
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
      <br/>
      Aenean hendrerit quis lorem et commodo. 
      Integer fringilla velit eget dui sodales aliquet. 
      <br/>
      Vestibulum et magna lobortis justo sodales placerat at vel nunc. 
    </p>
    <p class="titleMenu">{{message}}</p>

      <div class="containerPrincipale">

        <div class="menuContainer" v-for="(item, index) in simpleMenu" :key="index">

          <div class="menu" v-if="item.disponible == true">

              <img v-if="item.disponible == true" class="pictureMenu" v-bind:src="item.url" alt="item.alt"/>


             <div class="icon" v-if="showIcons">
                <button class="button" v-on:click="addProduit(item) in simpleMenu">
                    <img class="sizeIcon" src="../assets/heart-regular.svg"/>   
                </button>
              </div>  

              <div class="icon" v-if="!showIcons">
                <button v-on:click="human">
                    <img class="sizeIcon" src="../assets/heart-solid.svg"/>  
                </button>
              </div>

              {{item.label}} : <br/> {{item.cost}} $
          </div>

        </div>  

      </div>

      <div class="containerFavoriteMenu" v-if="shop.length > 0">
        <p class="titleMenu">My favorite Menu</p>
        <div id="panier" v-for="item in shop" :key="item">
            ○ {{ item.label }} : {{ item.cost }} $
        </div>
        <p class="priceTotal">Total = {{  totalCofee }} $</p>
        
      </div>

    </div>

</template>

<script>


export default {
  name: 'Menu',
   data: () => {
        return {
            message : "Menu",

            showIcons: true,
          
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
              like: [],
        }
    },

    methods: {

    addProduit(simpleMenu){

      this.shop.push({
        label: simpleMenu.label,
        cost: simpleMenu.cost
      })
      this.showIcons= false
    },

 
    human() {
    this.showIcons = true
  }

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

/* ================================
    TITLE PAGE
   ================================ */

h1{
  font-size: 4.4rem;
  color: rgb(201, 228, 246);
  font-family: 'Fredericka the Great', cursive;

  margin-bottom:60px;
}

.titleMenu{
  margin-top: 60px;
  margin-bottom: 60px;

  font-size: 3rem;
  font-weight: 800;
  color: rgb(233, 222, 222);
}

.intro{
  width: 80%;
  margin-right: auto;
  margin-left: auto;

  color:white;
  line-height: 2em;
  font-size: 1.5rem;
}


/* ================================
    CONTAINER
   ================================ */

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

/* ================================
    MENU -> LIST COFFEE
   ================================ */

.menu {
  margin: 15px 10px;

  font-size: 1.5rem;
  color: white;
  
  width: 200px;
  height: 240px;

  background-color: black;
  border-radius: 10px;
}

.pictureMenu{
  margin-bottom : 10px;
  width: 200px;
  height: 100px;
}

/* ================================
    Favorite MENU
   ================================ */

.containerFavoriteMenu{
  width: 87%;
  height: 100%;

  padding: 20px 20px;

  margin-right: auto;
  margin-left: auto;
  margin-top: 60px;
  margin-bottom: 60px;

  background: rgb(0,0,0);
  background: linear-gradient(180deg, rgba(0,0,0,1) 0%, rgba(49,49,74,1) 51%, rgba(93,130,138,1) 100%);

  border-radius: 40px;
}

#panier{
  font-size: 2rem;
  color: white;
}

.priceTotal{
  margin-top: 40px;
  font-size: 2rem;
  color: rgb(167, 167, 167);
}

/* ================================
    ICON
   ================================ */

button{
  border: 1px solid white;
  background: linear-gradient(180deg, rgba(0,0,0,1) 0%, rgba(49,49,74,1) 51%, rgba(93,130,138,1) 100%);
  border-radius: 4px;
  padding: 5px 5px;

  margin-bottom: 15px;

  transition: all 5s ease-out;
}   

button:hover{
  background: linear-gradient(180deg, rgba(0,0,0,1) 0%, rgba(49,49,74,1) 51%, rgba(223,43,214,1) 100%);
}     

button:focus{
  background: linear-gradient(180deg, rgba(0,0,0,1) 0%, rgba(49,49,74,1) 51%, rgba(223,43,214,1) 100%);
}

.sizeIcon{
  width: 20px;
}

</style>
