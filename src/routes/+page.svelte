<script lang="ts">
        import { evaluate } from 'mathjs';
let equation:String="";
let answer='';
let sentax='';
function addequation( value:String){
   
    equation += value;
   sentax += mathjs(value);
}
function delet(){
    equation ='';
    sentax ='';

}
function backspace(){
equation=equation.substring(0,equation.length-1);
sentax=sentax.substring(0,sentax.length-1);

}
function mathjs(aa:String):String{
    switch(aa) {
    case '√':
      return 'sqrt(';
    case 'sin':
      return 'sin(';
    case 'cos':
      return 'cos(';
    case 'tan':
      return 'tan(';
    case '^':
      return '^';
      case 'x':
      return '*';
    case '÷':
      return '/';
    case '-':
      return '-';
    case '+':
      return '+';
    default:
      return aa;
    }
}
function Parentheses(sentax: string): string {
    let openParentheses = 0;
    let closeParentheses = 0;

    for (let character of sentax) {
      if (character === '(') {
        openParentheses++;
      } else if (character === ')') {
        closeParentheses++;
      }
    }

    while (openParentheses > closeParentheses) {
      sentax += ')';
      closeParentheses++;
    }

    return sentax;
  }

function solve(){
    let solveEquation = Parentheses(sentax);
      equation = evaluate(solveEquation).toString();
 answer = equation;
}
function ans(){
  equation+=answer;
    sentax+=answer;

}
</script>
<svelte:head>
    <title>
        calculator
    </title>
</svelte:head>
    <div class="   bg-[#736e72] min-h-[39rem] min-w-[21rem] rounded-3xl grid grid-cols-4 gap-1 p-6 font-extrabold shadow-[#eeede5] shadow-2xl text-2xl max-w-[18.75rem]">

<div class="bg-[#eeede5] rounded-2xl col-span-4 min-h-12 mb-1 flex justify-normal items-center px-4  break-all " >
   {equation}
</div>
<button on:click={()=>addequation('/100')}> % </button>
<button on:click={()=>addequation('√')} >√</button>
<button on:click={delet}>CE</button>
<button on:click={backspace} class="bg-[#6a4349]">C</button>
<button type="button" on:click={()=>addequation('sin(')}>sin </button>
<button on:click={()=>addequation('cos(')} >cos</button>
<button on:click={()=>addequation('tan(')}>tan</button>
<button  on:click={()=>addequation('+')} class="bg-[#6a4349]">+</button>
<button  on:click={()=>addequation('7')}>7</button>
<button on:click={()=>addequation('8')}>8</button>
<button on:click={()=>addequation('9')}>9</button>
<button on:click={()=>addequation('-')} class="bg-[#6a4349]">-</button>
<button on:click={()=>addequation('4')}>4</button>
<button on:click={()=>addequation('5')}>5</button>
<button on:click={()=>addequation('6')}>6</button>
<button on:click={()=>addequation('÷')} class="bg-[#6a4349]">÷</button>
<button on:click={()=>addequation('1')}>1</button>
<button on:click={()=>addequation('2')}>2</button>
<button on:click={()=>addequation('3')}>3</button>
<button on:click={()=>addequation('x')} class="bg-[#6a4349]">X</button>
<button  on:click={()=>addequation('.')}>.</button>
<button on:click={()=>addequation('0')}>0</button>
<button on:click={()=>addequation('^')} class="text-base" >^</button>
<button on:click={ans} class="bg-[#6a4349]">Ans</button>
<button  on:click={()=>addequation('(')} class="bg-[#6a4349]">(</button>
<button  on:click={()=>addequation(')')} class="bg-[#6a4349] ">)</button>
<button class="bg-[#a4a4a4] col-span-2  " on:click={solve}>=</button>

</div>

