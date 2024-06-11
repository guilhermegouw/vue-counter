<template>
    <p>{{ total }}</p>
    <button @click="calcula('-')">Decrement</button>
    <button @click="calcula('+')">Increment</button>

    <p>Nome Computado: {{ nomeFormatado }}</p>
    <label>Input a computar</label>
    <input v-model="nome" type="text"><br>

    <label>Input a observar</label>
    <input v-model="busca" type="text">
    <p v-text="resultado"></p>
</template>

<script>
    export default {
        name: 'lv-contador',
        data() {
            return {
                total: 10,
                nome: 'jose antonio',
                resultado: "",
                busca: "",
            }
        },
        computed: {
            nomeFormatado: {
                get: function() {
                    return this.nome.toUpperCase()
                },
                set: function( novoValor ) {
                    this.nome = novoValor.substring(0, 3)
                }
            }
        },
        watch: {
            busca: function() {
                this.resultado = 'Aguardando o término de digitação...'
                this.recolheResposta()
            }
        },
        methods: {
            calcula( sinal ) {
                this.total = (sinal == '-') ? this.total -1: this.total + 1
            },
            recolheResposta() {
                let valor = this.busca
                setTimeout(() => {
                    if (valor == this.busca) 
                    this.resultado = 'Terminou de digitar...'
                }, 500)
            }
        }
    }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
