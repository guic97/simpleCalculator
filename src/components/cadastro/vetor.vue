<template>
    <div>
        <div id="exemplosFor">
            <div id="forEmpresas">
                <h2>Empresas</h2>
                <ul>
                    <li v-for="(empresa,index) in empresas" :key="index">{{empresa}}</li>
                </ul>
            </div>
            <div id="forPessoas">
                <h2>Pessoas:</h2>
                <ul>
                    <li v-for="pessoa in pessoas" :key="pessoa.id">{{pessoa.nome}}</li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name: 'vetor',
    data(){
        return{
            empresas: ['Microsoft', 'Apple', 'Meta', 'Adidas', 'McDonalds'],
            pessoas: [
                {nome: 'Ana', id: 1, idade:'20'},
                {nome: 'Guilherme', id: 2, idade:'25'},
                {nome: 'João', id: 3, idade:'30'},
                {nome: 'Claudia', id: 4, idade:'50'},
                {nome: 'Vanessa', id: 5, idade:'34'},
            ],
        }
    },  
}
</script>

<style scoped>
    #exemplosFor{
        position: absolute;
        background-color: brown;
        bottom: 0px;
        right: 0px;
        height: 200px;
        width: 30%;
        border: rgb(0,0,0) 3px solid;
    }
    #forEmpresas{
        position: absolute;
        top: 10px;
        left: 10px;
    }
    #forPessoas{
        position: absolute;
        top: 10px;
        left: 50%;
    }
</style>
