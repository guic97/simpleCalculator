<template>
  <main>
    <div class="mainLayout flexWrap">
      <div class="calculator flexWrap">
        <div class="calculatorLayout">
          <div>{{result}}</div>
          <div>{{op}}</div>
          <div>{{numberValue}}</div>
        </div>
        <div class="keys flexWrap">
          <div @click="activateOp(op)">=</div>
          <div @click="erase()">CE</div>
          <div @click="activateRoot('√')">√x</div>
          <div @click="activateOp('^')">^</div>
          <div @click="activateNumber(1)">1</div>
          <div @click="activateNumber(2)">2</div>
          <div @click="activateNumber(3)">3</div>
          <div @click="activateOp('+')">+</div>
          <div @click="activateNumber(4)">4</div>
          <div @click="activateNumber(5)">5</div>
          <div @click="activateNumber(6)">6</div>
          <div @click="activateOp('-')">-</div>
          <div @click="activateNumber(7)">7</div>
          <div @click="activateNumber(8)">8</div>
          <div @click="activateNumber(9)">9</div>
          <div @click="activateOp('x')">x</div>
          <div @click="activateNumber(0)">0</div>
          <div @click="activateOp('%')">%</div>       
          <div @click="activateNumber('.')">.</div>
          <div @click="activateOp('/')">/</div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
    name: 'calculator',
    data(){
      return{
        value: '0',
        op: '0',
        result: '0',
        numberValue: '0', 
        repeatDot: true,
      }
    },
    methods: {
      activateNumber: function(value){
        if(isNaN(value)==false && value!=0){
          if (this.op=='-' && this.numberValue=='0') {
          this.result=String(this.op+value);
          this.op='0';
          }else
            this.result+=String(value);
            this.result=parseFloat(this.result);
            }else
              if(value==0){
                this.result+=String(value);
                }else
                  if(value=='.' && this.repeatDot==true){
                    this.result+=String(value);
                    this.repeatDot=false;
                  }  
        this.value=value;
      },
      activateOp: function(op){
        this.repeatDot=true;
        if(this.numberValue!='0' && this.result!='0'){
          if(this.op=='+')
            this.numberValue=parseFloat(this.numberValue)+parseFloat(this.result);
            else
              if(this.op=='-')
                this.numberValue=parseFloat(this.numberValue)-parseFloat(this.result);
                else
                  if(this.op=='x')
                    this.numberValue=parseFloat(this.numberValue)*parseFloat(this.result);
                    else
                      if(this.op=='/')
                        this.numberValue=parseFloat(this.numberValue)/parseFloat(this.result);
                        else
                          if(this.op=='%') 
                            this.numberValue=parseFloat(this.numberValue)*(parseFloat(this.result)/100);
                            else
                              if(this.op=='^')
                                this.numberValue=parseFloat(this.numberValue)**parseFloat(this.result);
              }else
                if(this.result!='0'){
                  this.numberValue=parseFloat(this.result);
                }
        this.result='0';
        this.op=op;    
      },
      activateRoot: function(op){
        if(op=='√' && this.result!='0'){
          this.numberValue=parseFloat(this.result);
          this.numberValue=Math.sqrt(this.result);
        }
        if(op!='0' && this.result!='0' && this.numberValue!='0'){
          this.result='0';
        }
        this.op=op;
      },
      erase: function(){
        this.op='0';
        this.value='0';
        this.result='0';
        this.numberValue='0';
        this.repeatDot=true;
      },
    }
}
</script>

<style scoped>
  main{
    background-color: var(--color5);
  }
  .mainLayout{
    padding: 30px 0px;
    background-color: var(--color1);
    min-width: 200px;
    max-width: 800px;
    margin: auto;
    justify-content: center;
  }
  .calculator{
    background-color: var(--color4);
    height: 550px;
    width: 330px;
    border: rgb(0, 0, 0) 3px solid;
    align-content: center;
  }
  .calculator div{
    margin: 5px;
  }
  .calculatorLayout{
    width: 100%;
    background-color: var(--color1);
    padding: 5px 0;
    border: black 2px solid;
  }
  .calculatorLayout div{
    max-width: 95%;
    display: flex;
    flex-wrap: wrap;
    color: rgb(0, 0, 0);
    font-size: 30px;
    justify-content: flex-end;
  }
  .keys{
    justify-content: center;
  }
  .keys div{
    background-color: var(--color1);
    height: 65px;
    width: 65px; 
    border: black 2px solid;
    text-align: center;
    cursor: pointer;
    padding-top: 10px;
    font-size: 40px;
    transition: .2s;
  }
  .keys div:hover{
    background-color: var(--color2);
  }
</style>