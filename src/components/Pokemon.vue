<template>
    <li class="info" v-bind:style="{color:pokemon.color_1}">
        <div>
            <img v-bind:src="pokemon.url_image"/>
            <h3> {{ pokemon.pokemon }}</h3>
            <p> type: {{pokemon.type_1}}
            <p> ability: {{ pokemon.ability_1}}</p>
            <p> attack: {{ pokemon.attack}}</p>
            <p> weight: {{ pokemon.weight}}</p>
            <p> speed: {{ pokemon.speed }} </p>
        </div>
        <span>
            <button class="detail-button" @click="show = true"> More Details </button>
            <Modal :pokemon="pokemon" v-if="show" :onClose="() => show = false">
            </Modal>               
        </span>
    </li>
</template>

<script>
import Modal from '../shared/Modal'; 

export default {
    props: {
        pokemon: Object
    },
    components: {
        Modal
    },
    data() {
        return {      
            show: false
        };
    }
};
</script>

<style scoped lang="postcss">
li {
  position:relative;
  text-align: center; 
    border: 1px solid black;
    margin: 10px;
    background-color:grey; 
    text-shadow: 1px 1px 1px black;
    border-radius: 10pt;
    box-shadow: 1pt 5pt 5pt; 
&:hover {
    img{
        transform: scale(1.7);
        filter: grayscale(0)    
        }
}
}
img {
  top: 0;
  left: 0;
  width: 100px;
  height: 100px;
  z-index: 4;
  object-fit: cover;
  display: block;
  margin-left: auto; 
  margin-right: auto; 
  transition: 500ms;
  filter: grayscale(1);
}
h3, p {
  margin: 0;
}
.detail-button {
    border-radius: 10pt;
    font-size: 10pt 
}
</style>