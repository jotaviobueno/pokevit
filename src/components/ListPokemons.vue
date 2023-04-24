<template>
  <div class="col-4">
    <div class="card p-2 mb-4 cardListPokemon">
      <p class="text-center">{{ name }}</p>
      <img :src="baseurl" class="card-img-top" height="80" alt="...">

    </div>
  </div>
</template>

<script>
  export default {
    props: {
      name: {
        type: String,
        required: true
      },
      baseurl: {
        type: String,
      }
    },
  };
</script>

<style scoped>
.cardListPokemon{
  background: rgb(151,118,212);
  background: linear-gradient(90deg, rgba(151,118,212,0.8155637254901961) 0%, rgba(96,168,166,0.5970763305322129) 100%);
  cursor: pointer;
}

.cardListPokemon:hover{
  background: rgb(151,118,212);
  cursor: pointer;
}

.cardListPokemon img:hover {
  padding: .3rem;
}

</style>
