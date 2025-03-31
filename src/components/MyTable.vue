<template>

<table>
  <caption>
    Emprunt: {{ emprunt }}€, sur {{ dureeEnMois }} mois
  </caption>
  <thead>
    <tr>
      <th scope="col">Mois</th>
      <th scope="col">à rembourser</th>
      <th scope="col">Reste du</th>
    </tr>
  </thead>
  <tbody >
    <tr v-for="monthly in echeancier">
      <th scope="row">{{monthly.dueDate}}</th>
      <td>{{monthly.mensualite}}</td>
      <td>{{ monthly.reste }}</td>
    </tr>
  </tbody>
</table>
</template>