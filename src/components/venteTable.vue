<!-- src/components/VenteTable.vue -->
<template>
    <div class="container mt-5">
      <h2>Ventes Enregistrées</h2>
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
          <tr v-for="(vente, index) in ventes" :key="index">
            <td>{{ vente.reference }}</td>
            <td>{{ vente.designation }}</td>
            <td>{{ vente.quantity }}</td>
            <td>{{ vente.price }} €</td>
            <td>{{ vente.quantity * vente.price }} €</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script setup>
  
  </script>
  