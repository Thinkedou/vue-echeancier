<script setup>
// ICI JE SUIS EN JS 
const emprunt = 2000
const dureeEnMois = 10
const mensualite = emprunt/dureeEnMois

console.log('à rembourser chaque mois' , mensualite)

const debut = new Date()
console.log(debut)

const echeancier = []

for (let i = 1; i <= dureeEnMois; i++) {
  echeancier.push({
    dueDate : new Date(debut.setMonth(debut.getMonth()+1)),
    mensualite:mensualite,
    reste: emprunt-(mensualite*i)
  })
}

console.log(echeancier)
</script>

<template>
   <header>
        <h1>écheancier des petits sous €</h1>
   </header>
   <container>
      <div class="form-container">
        <span class="custom-select">
          <label for="duration">Choisir la durée </label>
          <select name="duration" id="duration">
            <option value="">--Merci de choisir une durée--</option>
            <option value="5">5 ans</option>
            <option value="10">10 ans</option>
            <option value="15">15 ans</option>
            <option value="20">20 ans</option>
            <option value="30">30 ans</option>
          </select>
        </span>
        <span class="custom-input">
          <label for="amount">Emprunt </label>
          <input
            type="text"
            id="amount"
            name="amount"
            required />
        </span>
        
      </div>
      <div class="table-container">
        <h4>{{emprunt}} € à rembourser sur {{ dureeEnMois }} mois</h4>
        <div class="table-itself">
          <table>
            <thead>
              <tr>
                <th scope="col">Mois</th>
                <th scope="col">Remboursé</th>
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
        </div>
      </div>
   </container>
</template>

<style scoped>
table {
  font-size: 0.8rem;
  letter-spacing: 1px;
}

caption {
  padding: 10px;
  font-weight: bold;
}

thead,
tfoot {
  background-color: rgb(228 240 245);
}

th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 8px 10px;
}

td:last-of-type {
  text-align: center;
}

tbody > tr:nth-of-type(even) {
  background-color: rgb(237 238 242);
}

tfoot th {
  text-align: right;
}

tfoot td {
  font-weight: bold;
}


</style>
