<template>
  <div class="flash" v-bind:class="{flashIsHidden: showMessage}">
    <h3>{{ msg }}</h3>
  </div>
  <div>
    <div class="connect row" v-if="!isLogged">
      <p class="label"> Entrez votre nom: <input class="login" type="text" v-model="user"/></p>
      <button class="btn" v-on:click="connecter()"> Connexion </button>
    </div>

    <div class="row" v-if="isLogged">
      <p class="label">Bonjour {{ user }} </p>
      <button class="btn btn-log" v-on:click="logout()"> Déconnexion </button>
    </div>

    <div class="flash flash-command" v-bind:class="{flashIsHidden: !validate}">
      <div>

      <h3> La commance suivante a bien été envoyée : </h3>
      <div>
        <ul v-for="(commande, index) in commandesValidate" :key="index">
          <li class="label">{{ commande.name }}</li>
        </ul>
      </div>
      </div>
      <span>
      <h4> Pour un prix de : {{commandesPrice.toFixed(2)}} € </h4>
      </span>
    </div>

    <div class="cards">
      <h1 class="cards-title">Produits Disponibles ! </h1>
      <div class="cards-deck">
        <div class="card" v-for="(produit, index) in produits" :key="index">
          <div class="card-content">
            <span class="card-title">
            {{produit.name}}
            </span>
            <span class="card-price">
              {{produit.prix}}€
            </span>
          </div>
          <button class="btn" v-on:click="commander(produit)"> Ajouter à la commande</button>
        </div>
      </div>
    </div>

    <div class="cards">
      <h1 class="cards-title" v-if="commandes.length">Votre commande :</h1>
      <div class="cards-deck">
        <div class="card" v-for="(commande, index) in commandes" :key="index">
          <div class="card-content">
            <span class="card-title">
              {{commande.name}}
            </span>
            <span class="card-price">
              {{commande.prix}}€
            </span>
          </div>
          <button class="btn" v-on:click="enlever(commande)">Supprimer</button>
        </div>
      </div>
      <h2 v-if="commandes.length">Prix total : {{commandesPrice.toFixed(2)}}</h2>
      <button class="btn" v-on:click="valider" v-if="commandes.length"> Valider la commande</button>
    </div>
      <div>
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
      user: "",
      msg: "",
      produits: [
        { id: 1,
          name:"BigMac",
          prix: 5.99,
        }, 
        { id: 2,
          name:"CheeseBurger",
          prix: 2.99,
        }, 
        { id: 3,
          name:"Tacos",
          prix: 3.99,
        }, 
        { id: 4,
          name:"Pizza",
          prix: 9.99,
        }, 
        { id: 5,
          name:"Hamburger",
          prix: 1.99,
        }, 
        { id: 6,
          name:"McWrap",
          prix: 4.99,
        }
        ],
      commandes: [],
      validate: false,
      commandesValidate: [],
      isLogged: false,
      showMessage: true,
      flash: "flash flash-isHidden",
      commandesPrice: 0,
    }
  },
  methods: {
    connecter() {
      if (this.user === "") {
        this.msg = "Le champs Login ne peut être vide !"
        this.showMessage = false;
        setTimeout(() => {
          this.showMessage = true;
        }, 3000)
      } else {
        this.isLogged = true;
      }
    },
    logout() {
      this.isLogged = false;
    },
    commander(produit) {
      let list = {...produit};
      list.place = this.commandes.length + 1;
      this.commandes.push(list);
      this.commandesPrice = 0;
      for(let obj of this.commandes) {
        console.log(`obj`, obj)
        this.commandesPrice = (this.commandesPrice + obj.prix);
      }
      console.log(list, this.commandes, this.commandesPrice);
    },
    enlever(commande){
      this.commandes.splice(this.commandes.indexOf(commande), 1);
      this.commandesPrice = 0;
      for(let obj of this.commandes) {
        console.log(`obj`, obj)
        this.commandesPrice = (this.commandesPrice + obj.prix);
      }
    },
    valider(){
      if (this.isLogged) {
        this.validate = true;
        this.commandesValidate = this.commandes;
          this.commandes = [];
        setTimeout(() => {
          this.validate = false;
        }, 3000);
      } else {
        this.msg = "Pour valider votre commande vous devez être connecté !"
        this.showMessage = false;
        setTimeout(() => {
          this.showMessage = true;
        }, 3000)
      }
    }
  },
  components: {
  },
}
</script>

<style>

</style>