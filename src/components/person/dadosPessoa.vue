<template>
    <div>
        <p v-show="friendAlive">My best friend is: {{friendName}}</p>
        <p v-if="loveSister == true && friendAlive == false">My best friend is: {{sister}}</p>
        <p>The things that i love to do are:</p>
        <ul>
            <li>Explodes everything</li>
            <li>Creates new monkey bombies</li>
            <li>Shots everything i see front on me</li>
            <li v-if="loveSister">Hug my sister</li>
            <li v-else>Try to kill my sister</li>
        </ul>
    </div>
</template>

<script>
    export default{
        name: 'dadosPessoa',
        data(){
            return{
                friendName: 'Silco',
                loveSister: true,
                friendAlive: true,
                sister: 'Vi',
            }
        },
    }
</script>
