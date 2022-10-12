<template>
    <div class="componente">
        <h2>As Informações de Usuário</h2>
        <p>Vários detalhes...</p>
        <p>Nome do Usuário: <strong>{{inverterNome()}}</strong></p>
        <button @click="reiniciarNome">Reiniciar Nome</button>
        <!-- criando um botao que recebe essa propriedade que é uma função -->
        <button @click="reiniciarFn">Reiniciar Nome (call back)</button>
    </div>
</template>

<script>
export default {
    // aceito a propriedade nome
    // só poder ter 1 props ou 1 data com o mesmo nome
    // props: ['nome'],
    //fazendo uma validação de como eu quero receber essas propriedades
    //pode ter varias tipos [tipo1, ...tipox]
    //pode declarar o tipo que vc quer receber da propriedade e deixar como obrigátoria
    // pode declarar um valor default ao invés do required
    //default tambem pode ser uma função
    props: {
        nome: {
            type: String,
            // required: true,
            // default: "Antonio"
            default: function() {
                //10 valores 0 com ','
                return Array(10)
                    .fill(0)
                    .join(',')
            }
        },
        //criando uma propriedade do tipo function (função)
        reiniciarFn: Function
    },
    methods: {
        inverterNome() {
            //quebrando o nome em varias letrar, e transformando e 1 array
            // revertando os valores desse array, e juntando tudo
            return this.nome
                .split('')
                .reverse()
                .join('')
        },
        reiniciarNome() {
            // const nome_antigo = this.nome

            this.nome = 'Pedro'
            //disparando um evento para o componente Pai
            //nome do evento, valor do evento ou varios valores (enviar como objecto dai {})
            // this.$emit('nomeMudou', {
            //     novo: this.nome,
            //     antigo: nome_antigo
            // })
            this.$emit('nomeMudou', this.nome)
        }
    }
}
</script>

<style scoped>
.componente {
    flex: 1;
    background-color: #ec485f;
    color: #fff;
}
</style>
