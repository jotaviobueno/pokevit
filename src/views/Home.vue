<script>
  import ListPokemons from '../components/ListPokemons.vue';
  import CardPokemonSelected from '../components/CardPokemonSelected.vue'
  import { ref, onMounted, reactive, computed } from 'vue';
  import axios from 'axios';

  export default {
    components: {
      ListPokemons,
      CardPokemonSelected
    },
    setup() {
      const results = ref([]);
      const pokemonSelected = ref([]);
      const state = reactive({
        baseurl: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/"
      });
      const search = ref("");

      onMounted(async () => {
        const response = await axios.get(
          "https://pokeapi.co/api/v2/pokemon?limit=151&offset=0"
        );
        results.value = response.data.results;
      });

      const pokemonsFiltered = computed(() => {
        if (results.value && search.value) {
          const query = search.value.toLowerCase();
          return results.value.filter((pokemon) => pokemon.name.toLowerCase().includes(query));
        }
        return results.value;
      });

      async function selectPokemon(pokemon) {
        const response = await axios.get(pokemon.url)

        
        console.log(response.data)

        pokemonSelected.value = response.data;
      }

      return { results, state, pokemonsFiltered, search, selectPokemon, pokemonSelected};
    }
  };
</script>

<template>
  <main>
    <div class="container text-body-secondary">
      
      <div class="row mt-4">
        <div class="col-sm-12 col-md-6">
          
          <CardPokemonSelected 
            :name="pokemonSelected.name"
            :baseurl="state.baseurl + pokemonSelected.id + '.svg'"
            :experience="pokemonSelected.base_experience"
            :weight="pokemonSelected.weight"
            :abilities="pokemonSelected.abilities"
            />
        </div>
  
        <div class="col-sm-12 col-md-6">
          <div class="card card-list">
            <div class="card-body row">
              
              <div class="mb-3">
                <label 
                hidden 
                for="searchPokemonField" 
                class="form-label">
                Pesquisar...
                </label>
                <input 
                v-model="searchPokemonField"
                type="text" 
                class="form-control" 
                id="searchPokemonField" 
                placeholder="Pesquisar...">
              </div>
              <ListPokemons
                v-for="pokemon in pokemonsFiltered" :key="pokemon.name" 
                :name="pokemon.name" 
                :baseurl="state.baseurl + pokemon.url.split('/')[6] + '.svg'"
                @click="selectPokemon(pokemon)"/>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style>
.card-list{
  max-height: 450px;
  overflow-y: scroll;
  overflow-x: hidden;
}
</style>
