<template>
  <div class="main">
    <div class="layoutPrincipal flexWrap">
      <div class="calculator">
        <div class="layoutCalc flexWrap">
          <div>{{resultado}}</div>
          <div>{{op}}</div>
          <div>{{numerosValor}}</div>
        </div>
        <div class="teclas flexWrap">
          <div @click="ativarOperacoes(op)" id="botaoIgual">=</div>
          <div @click="apagar()" id="botaoApagar">CE</div>
          <div @click="ativarRaiz('√')" id="botaoRaiz">√x</div>
          <div @click="ativarOperacoes('^')">^</div>
          <div @click="ativarNum(1)">1</div>
          <div @click="ativarNum(2)">2</div>
          <div @click="ativarNum(3)">3</div>
          <div @click="ativarOperacoes('+')">+</div>
          <div @click="ativarNum(4)">4</div>
          <div @click="ativarNum(5)">5</div>
          <div @click="ativarNum(6)">6</div>
          <div @click="ativarOperacoes('-')">-</div>
          <div @click="ativarNum(7)">7</div>
          <div @click="ativarNum(8)">8</div>
          <div @click="ativarNum(9)">9</div>
          <div @click="ativarOperacoes('x')">x</div>
          <div @click="ativarNum(0)">0</div>
          <div @click="ativarOperacoes('%')">%</div>       
          <div @click="ativarNum('.')">.</div>
          <div @click="ativarOperacoes('/')">/</div>
        </div>
      </div>
      <div class="foraCalculadora flexWrap">
        <div class="botoesFora">
          <div @click="ativarTesteMesa()">{{textoTeste}}</div>
        </div>
        <div class="layoutTeste flexWrap" v-show="testeMesa==true">
          <div><h3>TESTE DE MESA</h3></div>
          <div>Ultimo valor(valor): {{valor}}</div>
          <div>Valor saida(resultado): {{resultado}}</div>
          <div>Operador(op): {{op}}</div>
          <div>Resul. final (numerosValor): {{numerosValor}}</div>
        </div>
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
      ativarTesteMesa: function(){
        this.testeMesa=!this.testeMesa
      },
    }
}
</script>

<style scoped>
    *{
      margin: 0px;
      padding: 0px;
    }
    .layoutPrincipal div{  
      align-items: center;
    }
    .flexWrap{
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
    }
    .calculator{
      margin-top: 50px;
      background-color: rgb(121, 29, 86);
      height: 550px;
      width: 330px;
      border: rgb(0, 0, 0) 3px solid;
    }
    .calculator div{
      margin: 5px;
      justify-items: center;
      align-items: center;
    }
    .layoutCalc{
      background-color: rgb(255, 255, 255);
      padding: 5px 0;
      text-align: end;
      color: rgb(0, 0, 0);
      font-size: 30px;
      border: black 2px solid;
      justify-items: end;
      flex-direction: column;
    }
    .layoutTeste{
      background-color: rgb(255, 255, 255);
      color: rgb(0, 0, 0);
      flex-direction: column;
      font-size: 18px;
      border: black 2px solid;
      padding: 10px;
    }
    .layoutTeste div{
      text-align: end;
    }
    .layoutTeste div:first-child{
      margin-bottom: 10px;
    }
    .teclas div, .botoesFora div{
      background-color: rgb(255, 255, 255);
      height: 65px;
      width: 65px; 
      border: black 2px solid;
      text-align: center;
      cursor: pointer;
    }
    .teclas div{
      font-size: 50px;
    }
    .foraCalculadora div{
      margin-right: 20px;
    }
    .botoesFora div{
      margin: 10px;
      font-size: 20px;
    }
</style>