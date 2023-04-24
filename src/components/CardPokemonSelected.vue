<template>
  <div class="card cardPokemonSelected">
      <img :src="baseurl" class="mx-auto d-block mt-5" height="200" alt="">
    
    <div class="card-body">
      <h5>abilities</h5>
      <ul v-for="abilitie in abilities" :key="abilitie">
          name: {{ abilitie.ability.name }}
      </ul>
      <hr>
      <p class="card-text"></p>

      <div class="row">

        <section class="col">
          <strong>XP:</strong>
          <span>{{ experience }}</span>
        </section>

        <section class="col">
          <strong>Peso:</strong>
          <span>{{ weight }}</span>
        </section>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      name: {
        type: String,
      },
      baseurl: {
        type: String,
      },
      experience: {
        type: Number
      },
      weight: {
        type: Number
      },
      abilities: {
        type: [String]
      }
    },
  };
</script>

<style scoped>

.cardPokemonSelected{
  height: 450px;
  background: rgb(131, 118, 212);
  background: linear-gradient(90deg, rgba(238, 235, 122, 0.816) 0%, rgba(227, 132, 88, 0.597) 100%);
  cursor: pointer;
}

.cardPokemonSelected img:hover {
  padding: .3rem;
}

</style>
