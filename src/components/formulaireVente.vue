<template>
  <div class="container">
    <h1 style="text-align: center">Enregistrer de vente</h1>
    <form @submit.prevent="validation">
      <div class="mb-3">
      <label for="reference" class="form-label">Réference</label>
      <input
        type="text"
        class="form-control"
        id="reference"
        v-model="reference"
        @blur="valReference"
        placeholder="reference"
      />
      <span v-if="error.reference" class="text-danger">{{ error.reference }}</span>
    </div>
    <div class="mb-3">
      <label for="designation" class="form-label">Désignation</label>
      <input
        class="form-control"
        id="designation"
        v-model="designation"
        @blur="valDesignation"
        placeholder="Désignation"
      />
      <span v-if="error.designation" class="text-danger">{{ error.designation }}</span>
    </div>
    <div class="mb-3">
      <label for="quantite" class="form-label">Quantité</label>
      <input
        type="number"
        class="form-control"
        id="quantite"
        v-model="quantite"
        @blur="valQuantite"
        placeholder="Quantite"
      />
      <span v-if="error.quantite" class="text-danger">{{ error.quantite }}</span>
    </div>
    <div class="mb-3">
      <label for="prix" class="form-label">Prix</label>
      <input
        type="number"
        class="form-control"
        id="prix"
        v-model="prix"
        @blur="valPrix"
        placeholder="Prix de vente"
      />
      <span v-if="error.prix" class="text-danger">{{ error.prix }}</span>
    </div>
    <div class="mb-3">
      <button class="btn btn-primary" type="submit">Enregistrer</button>
    </div>
    </form>
    <div class="container mt-5">
      <h2 style="text-align: center">Liste des ventes</h2>
      <table class="table table-striped">
        <thead>
          <tr>
            <th>Référence</th>
            <th>Désignation</th>
            <th>Quantité</th>
            <th>Prix</th>
            <th>Total</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(vente, ventes) in ventes" :key="index">
            <td>{{ vente.reference }}</td>
            <td>{{ vente.designation }}</td>
            <td>{{ vente.quantite }}</td>
            <td>{{ vente.prix }} MRU</td>
            <td>{{ vente.quantite * vente.prix }} MRU</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';


const reference = ref('');
const designation = ref('');
const quantite = ref('');
const prix = ref('');
const ventes = ref([]);

const error = ref({
  reference : '',
  designation : '',
  quantite : '',
  prix : ''
});

function validation(){
  
  try{
    valReference()
    valDesignation()
    valQuantite()
    valPrix()
    if(reference.value && designation.value && quantite.value && prix.value){
      ventes.value.push({
        reference : reference.value,
        designation : designation.value,
        quantite : quantite.value,
        prix : prix.value
      })
    }
  }catch(e){
        return e;
  }

  reference.value = '';
  designation.value = '';
  quantite.value = '';
  prix.value = '';
}

function valReference(){
  if(!reference.value){
    error.value.reference = 'reference est requis'
  }
}
function valDesignation(){
  if(!designation.value){
    error.value.designation = 'designation est requis'
  }
}
function valQuantite(){
  if(!quantite.value){
    error.value.quantite = 'Quantite est requis'
  }
}
function valPrix(){
  if(!prix.value){
    error.value.prix = 'Prix est requis'
  }
}
</script>

<style scoped>

</style>
