<template>
    <div class="componente">
        <h2>As Informações de Usuário</h2>
        <p>Vários detalhes...</p>
        <p>Nome do Usuário: <strong>{{inverterNome()}}</strong></p>
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
            default: function(){
                //10 valores 0 com ','
                return Array(10).fill(0).join(',')
            }
        }
    },
    methods: {
        inverterNome(){
            //quebrando o nome em varias letrar, e transformando e 1 array
            // revertando os valores desse array, e juntando tudo 
            return this.nome.split('').reverse().join('')
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
