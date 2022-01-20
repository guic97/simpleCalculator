<template>
    <div>
        <div id="cadastroUsuario">
            <h3>CADASTRO:</h3>
            <form id="formularioCadastro" action="" @submit="verificarFormulario($event)">
                <div id="cadastroNome" class="labelCadastro">
                    <label for="nome">Nome:</label>
                        <input type="text" id="nome" class="inputCadastro" v-model="nome" name="nome" title="Digite o seu nome">
                </div>
                <div id="cadastroEmail" class="labelCadastro">
                    <label for="email">Email:</label>
                        <input type="text" id="email" class="inputCadastro" v-model="email" name="email" title="Digite o seu email">
                </div>
                <div id="labelDataNascimento" class="labelCadastro">
                    <label for="idade">Idade: </label>
                    <div id="cadastroDataNascimento">
                        <div id='labelDiaNascimento'>
                            <label for="diaNascimento">Dia:</label>
                                <input  class="inputDataNascimento" type="number" v-model="diaNascimento" name="diaNascimento" min="1" max="31">
                        </div>
                        <div id="labelMesNascimento">
                            <label for="mesNascimento">Mês:</label>
                                <input  class="inputDataNascimento" type="text" v-model="mesNascimento" list="mesNascimento">
                                <datalist id="mesNascimento">
                                    <option value="Janeiro"/>
                                    <option value="Fevereiro"/>
                                    <option value="Março"/>
                                    <option value="Abril"/>
                                    <option value="Maio"/>
                                    <option value="Junho"/>
                                    <option value="Julho"/>
                                    <option value="Agosto"/>
                                    <option value="Setembro"/>
                                    <option value="Outubro"/>
                                    <option value="Novembro"/>
                                    <option value="Dezembro"/>
                                </datalist>
                        </div>
                        <div id="labelAnoNascimento">
                            <label  for="anoNascimento">Ano:</label>
                                <input type="number" class="inputAnoNascimento" v-model="anoNascimento" name="anoNascimento" min="1920" max="2022">
                        </div>
                    </div>
                </div>
                <div id="cadastroSenha" class="labelCadastro">
                    <label for="senha">Senha:</label>
                        <input type="password" id="senha" class="inputCadastro" v-model="senha" name="senha" title="Digite a sua senha" min="6">
                </div>
                <div id="confirmarSenha" class="labelCadastro">
                    <label for="csenha">Confirmar senha:</label>
                        <input type="password" id="cSenha" class="inputCadastro" v-model="csenha" name="csenha" title="Confirme sua senha" min="6">
                </div>
                <div>
                    <button style='left:50%' id="botaoEnviarFormulario" class="botao" type="submit">Enviar</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
export default{
    name:'inputCadastro',
    data(){
        return{
            nome:'',
            email:'',
            diaNascimento:'',
            mesNascimento:'',
            anoNascimento:'',
            senha:'',
            csenha:'',

        }
    },
    components:{
      
    },
    methods:{
        verificarFormulario(e){
            if(this.nome=='')
                alert('Preencha o nome')
                else
                    if(this.email=='')
                        alert('Preencha o email')
                        else
                            if(this.diaNascimento=='')
                                alert('Preencha o dia de nascimento')
                                else
                                    if(this.mesNascimento=='')
                                        alert('Preencha o mes de nascimento')
                                        else
                                            if(this.anoNascimento=='')
                                                alert('Preencha o ano de nascimento')
                                                else
                                                    if(this.senha=='')
                                                        alert('Preencha sua senha')
                                                        else
                                                            if (this.csenha=='')
                                                                alert('Confirme a sua senha')
                                                                else
                                                                    if (this.csenha!=this.senha) 
                                                                        alert('Senhas não correspondem')
                                                                        else{
                                                                            e.preventDefault()
                                                                            console.log(this.nome, this.email, this.diaNascimento, this.mesNascimento, this.anoNascimento, this.senha, this.csenha);
                                                                        }
            
        },
        diasMes: function(){
            if (this.mesNascimento=='Abril' || this.mesNascimento=='Junho' || this.mesNascimento=='Setembro' || this.mesNascimento=='Novembro') {
               let min='30'
            }else
                if (this.mesNascimento=='Fevereiro') {
                    let min='29'
                }
        },
    },
    
}
</script>
   
<style scoped>
    #cadastroUsuario{
        position: absolute;
        background-color: lightblue;
        width: 100%;
        height: 430px;
        top: 0%;
        left: 0%;
        
    }
    #cadastroUsuario h3{
        position: relative;
        left: 45%;
        font-size: 30px;
    }
    #formularioCadastro{
        position: absolute;
        width: 600px;
        height: 300px;
        top: 60px;
        left: 320px;
        text-align: left;
    }
    #cadastroNome{
        position: absolute;
        top: 40px;
        left: 40px;
    }
    #cadastroEmail{
        position: absolute;
        top: 40px;
        left: 300px;
    }
    #labelDataNascimento{
        position: absolute;
        top: 90px;
        left: 40px;
      
    }
    #labelDiaNascimento{
        position: absolute;
        top: 0px;
        left: 80px;
    }
    #labelMesNascimento{
        position: absolute;
        top: 0%;
        left: 185px;
    }
    #labelAnoNascimento{
        position: absolute;
        top: 0px;
        left: 390px;
    }
    .botao{
        position: absolute;
        top: 200px;
        left: 40px;
    }
    #cadastroSenha{
        position: absolute;
        top: 150px;
        left: 40px;

    }
    #confirmarSenha{
        position: absolute;
        top: 150px;
        left: 280px;
    }
    .inputCadastro{
        position: relative;
        left: 5px;
    }
</style>
