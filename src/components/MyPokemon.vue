<template>
 
    <div id="pokemon">
        
        <div class="card">
            <div class="card-image">
                <figure >
                <img :src="currentImg" alt="Placeholder image">
                </figure>
            </div>
            <div class="card-content">
                <div class="media">
                <div class="media-content">
                    <p class="title is-4">{{num}} - {{ upper(name) }}</p>
                    <span class="type subtitle is-6">{{ pokemon.type }}</span>
                </div>
                </div>

                <div class="content">
                    <button class="button is-medium is-halfwidth" @click="mudarSprite">Change sprite</button>
                </div>
            </div>
        </div>
    </div>

</template>

<script>

import axios from 'axios';
export default {
    created: function(){
        axios.get(this.url).then(res => {
            this.pokemon.type = res.data.types[0].type.name
            this.pokemon.front = res.data.sprites.front_default
            this.pokemon.back = res.data.sprites.back_default
            this.currentImg = this.pokemon.front
        })
    },
    data(){
        return {
            isFront: true,
            currentImg: '',
            pokemon: {
                type: '',
                front: '',
                back: ''
            }
        }
    },
    props: {
        num: Number,
        name: String,
        url: String
    },
    methods: {
        upper: function(value){
            var newName = value[0].toUpperCase() + value.slice(1)
            return newName
        },
        mudarSprite: function(){
            if(this.isFront){
                this.isFront = false
                this.currentImg = this.pokemon.back
            }else{
                this.isFront = true
                this.currentImg = this.pokemon.front
            }
        },
        pokemonType: function(value){
            console.log(value)
            return value
        }
    },
   
}
</script>

<style>
    #pokemon{
        margin-top: 2%
    }

    #span.type {
        border: 2px solid #000;
        border-radius: 20px;
        padding: 4px 16px;
        color: #fff;

    }

    span.type.normal {
        background-color: #A8A878;
        border-color: #6D6D4E;
        content: 'Normal';
    }

    span.type.fire {
        background-color: #F08030;
        border-color: #9C531F;
        content: 'Fire';
    }

    span.type.water {
        background-color: #6890F0;
        border-color: #445E9C;
        content: 'Water';
    }

    span.type.electric {
        background-color: #F8D030;
        border-color: #A1871F;
        content: 'Electric';
    }

    span.type.grass {
        background-color: #78C850;
        border-color: #4E8234;
        content: 'Grass';
    }

    span.type.ice {
        background-color: #98D8D8;
        border-color: #638D8D;
        content: 'Ice';
    }

    span.type.fighting {
        background-color: #C03028;
        border-color: #7D1F1A;
        content: 'Fighting';
    }

    span.type.poison {
        background-color: #A040A0;
        border-color: #682A68;
        content: 'Poison';
    }

    span.type.ground {
        background-color: #E0C068;
        border-color: #927D44;
        content: 'Ground';
    }

    span.type.flying {
        background-color: #A890F0;
        border-color: #6D5E9C;
        content: 'Flying';
    }

    span.type.psychic {
        background-color: #F85888;
        border-color: #A13959;
        content: 'Psychic';
    }

    span.type.bug {
        background-color: #A8B820;
        border-color: #6D7815;
        content: 'Bug';
    }

    span.type.rock {
        background-color: #B8A038;
        border-color: #786824;
        content: 'Rock';
    }

    span.type.ghost {
        background-color: #705898;
        border-color: #493963;
        content: 'Ghost';
    }

    span.type.dragon {
        background-color: #7038F8;
        border-color: #4924A1;
        content: 'Dragon';
    }

    span.type.dark {
        background-color: #705848;
        border-color: #49392F;
        content: 'Dark';
    }

    span.type.steel {
        background-color: #B8B8D0;
        border-color: #787887;
        content: 'Steel';
    }
</style>