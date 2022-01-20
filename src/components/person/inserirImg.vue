<template>
    <div>
        <div><img style="width:150px;" :src="imagem" :alt="descricao"></div>
    </div>
</template>

<script>
export default {
    name: 'imagemJinx',
    data(){
        return{
            imagem: '/imagens/jinx.jpg',
            descricao: 'Jinx (Powder)',
        }
    },
}
</script>