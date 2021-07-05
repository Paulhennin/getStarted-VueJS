<template>
  <div>
    <div class="container">
      <div class="row">
        <p class="jumbotron"> Login: <input type="text" v-model="user"/> Vous êtes connectés en tant que {{ user }}</p>
      </div>
      <div v-if="validate">
        <h1> La commance suivante a bien été envoyée : </h1>
        <div>
          <ul v-for="(commande, index) in commandesValidate" :key="index">
            <li class="jumbotron">{{ commande.name }}</li>
          </ul>
        </div>
      </div>
      <h1 class="display-4">Produits Disponibles ! </h1>
      <div class="row">
        <div class="col-2" v-for="(produit, index) in produits" :key="index">
          <p class="jumbotron">
            {{produit.name}}<br>
            <button v-on:click="commander(produit)"> Ajouter à la commande</button>
          </p>
        </div>
      </div>
      <h1 class="display-4" v-if="commandes.length > 0">Votre commande :</h1>
      <div class="row">
        <div v-for="(commande, index) in commandes" :key="index">
          <p class="jumbotron">{{ commande.name }}</p>
          <button v-on:click="enlever(commande)">Supprimer</button>
        </div>
        <div>
            <button v-on:click="valider"> Valider </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Main',
  props: {
    
  },
  data () {
    return { 
      user: "Gracklock",
      produits: [
        { id: 1,
          name:"BigMac",
        }, 
        { id: 2,
          name:"CheeseBurger",
        }, 
        { id: 3,
          name:"Tacos",
        }, 
        { id: 4,
          name:"Pizza",
        }, 
        { id: 5,
          name:"Hamburger",
        }, 
        { id: 6,
          name:"McWrap",
        }
        ],
      commandes: [],
      validate: false,
      commandesValidate: [],
    }
  },
  methods: {
    commander(produit) {
      let list = {...produit};
      list.place = this.commandes.length + 1;
      this.commandes.push(list);
      console.log(list, this.commandes);
    },
    enlever(commande){
      this.commandes.splice(this.commandes.indexOf(commande), 1);
    },
    valider(){
      this.validate = true;
      this.commandesValidate = this.commandes;
        this.commandes = [];
      setTimeout(() => {
        this.validate = false;
      }, 3000);
    }
  },
  components: {
  },
}
</script>

<style>

</style>