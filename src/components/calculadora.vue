<template>
    <div id="layoutPrincipal">
        <div id="calculadora">
            <div id="teclasNum">
                <div @click="ativarNum(1)" id="botao1" class="botaoCalc">1</div>
                <div @click="ativarNum(2)" id="botao2" class="botaoCalc">2</div>
                <div @click="ativarNum(3)" id="botao3" class="botaoCalc">3</div>
                <div @click="ativarNum(4)" id="botao4" class="botaoCalc">4</div>
                <div @click="ativarNum(5)" id="botao5" class="botaoCalc">5</div>
                <div @click="ativarNum(6)" id="botao6" class="botaoCalc">6</div>
                <div @click="ativarNum(7)" id="botao7" class="botaoCalc">7</div>
                <div @click="ativarNum(8)" id="botao8" class="botaoCalc">8</div>
                <div @click="ativarNum(9)" id="botao9" class="botaoCalc">9</div>
                <div @click="ativarNum(0)" id="botao0" class="botaoCalc">0</div>
                <div @click="ativarNum('.')" id="botaoPonto" class="botaoCalc">.</div>
            </div>
            <div id="teclasOperacoes">
                <div @click="ativarOperacoes('+')" id="botaoSoma" class="botaoCalc">+</div>
                <div @click="ativarOperacoes('-')" id="botaoSubtracao" class="botaoCalc">-</div>
                <div @click="ativarOperacoes('x')" id="botaoMultiplicacao" class="botaoCalc">x</div>
                <div @click="ativarOperacoes('/')" id="botaoDivisao" class="botaoCalc">/</div>
                <div @click="ativarOperacoes('%')" id="botaoPorcent" class="botaoCalc">%</div>
                <div @click="ativarOperacoes('^')" id="botaoPotencia" class="botaoCalc">^</div>   
            </div>
            <div id="teclasInteracao">
                <div @click="ativarRaiz('√')" id="botaoRaiz" class='botaoCalc'>√x</div>
                <div @click="apagar()" id="botaoApagar" class="botaoCalc">CE</div>
                <div @click="ativarOperacoes(op)" id="botaoIgual" class="botaoCalc">=</div>
            </div>
            <div id="layoutCalc">
                <div id="layoutOp">{{op}}</div>
                <div id="layoutResp">{{resultado}}</div>
                <div id="layoutNumero">{{numerosValor}}</div>
            </div>
        </div>
        <div id="foraCalculadora">
            <div id="botoesFora">
                <div @click="ativarModoEscuro()" id="botaoModoEscuro" class="botaoFora">{{textoModo}}</div>
                <div @click="ativarTesteMesa()" id="botaoTesteMesa" class="botaoFora">{{textoTeste}}</div>
            </div>
            <div id="layoutTeste" v-show="testeMesa==true">
                <div><h3>TESTE DE MESA</h3></div>
                <div>Ultimo valor(valor): {{valor}}</div>
                <div>Valor saida(resultado): {{resultado}}</div>
                <div>Operador(op): {{op}}</div>
                <div>Resul. final (numerosValor): {{numerosValor}}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'calculadora',
    data(){
        return{
            valor: '0',
            op: '0',
            resultado: '0',
            numerosValor: '0', 
            repetePonto: true,
            modoEscuro: false,
            textoModo: "Modo escuro",
            testeMesa: false,
            textoTeste: 'Teste mesa',
        }
    },
    methods: {
        ativarNum: function(valor){
            if(isNaN(valor)==false && valor!=0){
                this.resultado+=String(valor)
                this.resultado=parseFloat(this.resultado)
                    }else
                        if(valor==0){
                            this.resultado+=String(valor)
                            }else
                                if(valor=='.' && this.repetePonto==true){
                                    this.resultado+=String(valor)
                                    this.repetePonto=false
                                }  
            this.valor=valor
        },
        ativarRaiz: function(op){
            if(op=='√' && this.resultado!='0'){
                this.numerosValor=parseFloat(this.resultado)
                this.numerosValor=Math.sqrt(this.resultado)
            }
            if(op!='0' && this.resultado!='0' && this.numerosValor!='0'){
                this.resultado='0'
            }
            this.op=op
        },
        ativarOperacoes: function(op){
            this.repetePonto=true
            if(this.numerosValor!='0' && this.resultado!='0'){
                if(this.op=='+')
                    this.numerosValor=parseFloat(this.numerosValor)+parseFloat(this.resultado)
                    else
                        if(this.op=='-')
                            this.numerosValor=parseFloat(this.numerosValor)-parseFloat(this.resultado)
                            else
                                if(this.op=='x')
                                    this.numerosValor=parseFloat(this.numerosValor)*parseFloat(this.resultado)
                                    else
                                        if(this.op=='/')
                                            this.numerosValor=parseFloat(this.numerosValor)/parseFloat(this.resultado)
                                            else
                                                if(this.op=='%') 
                                                    this.numerosValor=parseFloat(this.numerosValor)*(parseFloat(this.resultado)/100)
                                                    else
                                                        if(this.op=='^')
                                                            this.numerosValor=parseFloat(this.numerosValor)**parseFloat(this.resultado)
                }else
                    if(this.resultado!='0'){
                        this.numerosValor=parseFloat(this.resultado)
                        this.resultado='0'
                    }
            this.resultado='0'
            this.op=op        
        },
        apagar: function(){
            this.op='0'
            this.valor='0'
            this.resultado='0'
            this.numerosValor='0'
            this.repetePonto=true
        },
        
        ativarModoEscuro: function(){
            if(this.modoEscuro==false){
                document.getElementById("layoutPrincipal").style.backgroundColor='rgb(24, 21, 21)'
                document.getElementById("botaoModoEscuro").style.backgroundColor='rgb(24, 21, 21)'
                document.getElementById("botaoModoEscuro").style.color='rgb(255, 255, 255)'
                document.getElementById("botaoModoEscuro").style.border='rgb(255, 255, 255) 2px solid'
                document.getElementById("calculadora").style.border='rgb(255, 255, 255) 2px solid'
                document.getElementById("layoutTeste").style.border='rgb(255, 255, 255) 2px solid'
                document.getElementById("layoutTeste").style.backgroundColor='rgb(0, 0, 0)'
                document.getElementById("layoutTeste").style.color='rgb(255, 255, 255)'
                document.getElementById("botaoTesteMesa").style.backgroundColor='rgb(24, 21, 21)'
                document.getElementById("botaoTesteMesa").style.color='rgb(255, 255, 255)'
                document.getElementById("botaoTesteMesa").style.border='rgb(255, 255, 255) 2px solid'
                document.getElementById("layoutCalc").style.backgroundColor='rgb(24, 21, 21)'
                document.getElementById("layoutCalc").style.color='rgb(255, 255, 255)'   
                this.textoModo='OFF modo'
                this.modoEscuro=true
            }
                else{
                    document.getElementById("layoutPrincipal").style.backgroundColor='rgb(255, 255, 255)'
                    document.getElementById("botaoModoEscuro").style.backgroundColor='rgb(255, 255, 255)'
                    document.getElementById("botaoModoEscuro").style.color='rgb(0, 0, 0)'
                    document.getElementById("botaoModoEscuro").style.border='rgb(0,0,0) 2px solid'
                    document.getElementById("calculadora").style.border='rgb(0,0,0) 2px solid'
                    document.getElementById("layoutTeste").style.border='rgb(0,0,0) 2px solid'
                    document.getElementById("layoutTeste").style.backgroundColor='rgb(255, 255, 255)'
                    document.getElementById("layoutTeste").style.color='rgb(0,0,0)'
                    document.getElementById("botaoTesteMesa").style.backgroundColor='rgb(255, 255, 255)'
                    document.getElementById("botaoTesteMesa").style.color='rgb(0, 0, 0)'
                    document.getElementById("botaoTesteMesa").style.border='rgb(0,0,0) 2px solid'
                    document.getElementById("layoutCalc").style.backgroundColor='rgb(255, 255, 255)'
                    document.getElementById("layoutCalc").style.color='rgb(0, 0, 0)'
                    this.textoModo='Modo escuro'
                    this.modoEscuro=false
                }
        },
        ativarTesteMesa: function(){
            this.testeMesa=!this.testeMesa
        },
    }
}
</script>

<style scoped>
    #layoutTeste{
        position: absolute;
        background-color: rgb(255, 255, 255);
        height: 180px;
        width: 290px;
        top: 50px;
        left: 100px;
        color: rgb(0, 0, 0);
        font-size: 17px;
        border: black 2px solid;
        text-align: right;
        padding-right: 15px;
    }
    #layoutTeste h3{
        text-align: center;
    }
    #calculadora{
        position: relative;
        background-color: rgb(121, 29, 86);
        height: 505px;
        width: 315px;
        left: 500px;
        border: rgb(0, 0, 0) 3px solid;
    }
    .botaoCalc{
        position: absolute;
        background-color: rgb(255, 255, 255);
        height: 65px;
        width: 65px;
        font-size: 50px;
        border: black 2px solid;
        text-align: center;
        cursor: pointer;
    }
    #layoutCalc{
        position: absolute;
        background-color: rgb(255, 255, 255);
        height: 90px;
        width: 275px;
        top: 20px;
        left: 15px;
        color: rgb(0, 0, 0);
        font-size: 40px;
        border: black 2px solid;
        text-align: right;
        padding-right: 10px;
    }
    #layoutOp{
        position: absolute;
        top: 25px;
        left: 10px;
    }
    .botaoFora{
        position: absolute;
        background-color: rgb(255, 255, 255);
        left: 850px;
        top: 20px;
        height: 65px;
        width: 65px;
        font-size: 20px;
        border: black 2px solid;
        text-align: center;
        cursor: pointer;
    }
    #botaoModoEscuro{
        left: 850px;
        top: 20px;
    }
    #botaoTesteMesa{
        left: 850px;
        top: 95px;
    }
    #botaoIgual{
        top: 125px;
        left: 10px;
    }
    #botaoApagar{
        top: 125px;
        left: 85px;
    }
    #botaoRaiz{
        top: 125px;
        left: 160px;
    }
    #botaoPotencia{
        top: 125px;
        left: 235px;
    }
    #botao1{
        top: 200px;
        left: 10px;
    }
    #botao2{
        top: 200px;
        left: 85px;
    }
    #botao3{
        top: 200px;
        left: 160px;
    }
    #botao4{
        top: 275px;
        left: 10px;
    }
    #botao5{
        top: 275px;
        left: 85px;
    }
    #botao6{
        top: 275px;
        left: 160px;
    }
    #botao7{
        top: 350px;
        left: 10px;
    }
    #botao8{
        top: 350px;
        left: 85px;
    }
    #botao9{
        top: 350px;
        left: 160px;
    }
    #botao0{
        top: 425px;
        left: 10px;
    }
    #botaoPorcent{
        top: 425px;
        left: 85px;
    }
    #botaoPonto{
        top: 425px;
        left: 160px;
    }
    #botaoDivisao{
        top: 425px;
        left: 235px;
    }
    #botaoSoma{
        top: 200px;
        left: 235px;
    }
    #botaoSubtracao{
        top: 275px;
        left: 235px;
    }
    #botaoMultiplicacao{
        top: 350px;
        left: 235px;
    }
</style>