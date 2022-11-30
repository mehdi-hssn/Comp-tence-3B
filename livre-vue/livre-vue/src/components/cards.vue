<template>
<main>

<section class="py-5 text-center container">
  <div class="row py-lg-5">
    <div class="col-lg-6 col-md-8 mx-auto">
      <h1 class="font-weight-light">Nos Livres</h1>
      <p class="lead text-muted">Voici quelque uns de nos livres.<br/>
        Ayez la possibilité de discuter et de commenter les oeuvres avec d'autre lecteurs.
      </p>
    </div>
  </div>
</section>

<div class="album py-5 bg-light">
  <div class="container">

    <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3">
      <div v-for="produit in produits" :key="produit.id" class="col">
        <div class="card shadow-sm">
          <img :src="produit.image" class="bd-placeholder-img card-img-top" width="250" height="500 " xmlns="http://www.w3.org/2000/svg"
            aria-label="Placeholder: Thumbnail" preserveAspectRatio="xMidYMid slice" role="img" focusable="false">
            <title>Placeholder</title>
            <rect width="100%" height="100%" fill="#55595c" /><h3 x="50%" y="50%" fill="#eceeef"
              dy=".3em">{{produit.name}}</h3>
            <img width="100%" height="100%" fill="#55595c" />
          

          <div class="card-body">
            <p class="card-text">{{produit.description}}</p>
            <div class="d-flex justify-content-between align-items-center">
              <div class="btn-group">
                <button type="button" class="btn btn-sm btn-outline-secondary"><img src="../assets/pouceHaut.png" width="25" height="25"></button>
                <button type="button" class="btn btn-sm btn-outline-secondary"><img src="../assets/pouceBas.png" width="25" height="25"></button>
              </div>
              <small class="text-muted">{{produit.time}}</small>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

</main>
</template>

<script>
import axios from 'axios'

export default {
  
  data() {
      return {
      produits: [],
      error: []
    }
  },
  created() {
    axios
      .get(`http://localhost:8080/produit.json`)
      .then(response => {this.produits= response.data.produits})
      .catch(e => {this.errors.push(e)})
   }  
}

</script>

<style scoped>
  h3{
    margin-top: 20px;
  }
</style>  