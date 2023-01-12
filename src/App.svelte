<script>
    import { get } from 'svelte/store';
  import EightBall from './assets/8_Ball.svg'
  import LordPepe from './assets/Lord_Pepe.svg'

  let question = null;
  let clicked = false;

  let tempval = null;

  let firstFilter = null;

  let secondRandom = null;
  let secondFilter = null;

  let answer = null;

  function turnClicked() {
    clicked = true;

    tempval = question;

    firstFilter = getRandomAnswer();
    secondRandom = getRandomAnswer();

    if (firstFilter >=0 && firstFilter <=0.3999 && clicked && question == tempval){

        secondFilter = "positive";
    }



      else if (firstFilter >=0.4 && firstFilter <=0.7999 && clicked && question == tempval){
        secondFilter = "negative";
      }



      else if (firstFilter >=0.8 && firstFilter <=0.9499 && clicked && question == tempval){
        secondFilter = "uncertain";
      }


      else if (firstFilter >=0.95 && firstFilter <=1 && clicked && question == tempval){
        secondFilter = "meme";
      }

  

  }

  function getRandomAnswer() {

    return Math.random();

  }

</script>

<main>

  <h1>Magic 8 Ball</h1>


  <div>
    <img src={EightBall} alt =" Eight Ball"/>
  </div>

  <!-- <div> 
    <img src={LordPepe} alt =" Pepe"/>
  </div>
  -->
 
  <div>

    <div>
      <input type="text" bind:value={question} >
    </div>

    <div>
      <button id="button" on:click={turnClicked}>
        {#if clicked && question == tempval} Pergunta de novo!
        {:else if !clicked} Pergunta! 
        {/if}
      </button>
    </div>

    {#if question != null && question != "" && clicked && question == tempval}
      
    
      

      {#if secondFilter == "positive" && clicked && question == tempval}
        {#if secondRandom >= 0 && secondRandom <= 0.1110}
          {answer = "Sim, com toda a certeza."}

        {:else if secondRandom >= 0.1111 && secondRandom <= 0.2220}
          {answer = "Decididamente."}

        {:else if secondRandom >= 0.2222 && secondRandom <= 0.3330}
          {answer = "Claro! Sem dúvida nenhuma!"}

        {:else if secondRandom >= 0.3333 && secondRandom <= 0.4440}
          {answer = "Definitivamente sim."}

        {:else if secondRandom >= 0.4444 && secondRandom <= 0.5550}
          {answer = "Podes contar com isso!"}

        {:else if secondRandom >= 0.5555 && secondRandom <= 0.6660}
          {answer = "Ah, sim. Eu consigo ver isso a acontecer..."}

        {:else if secondRandom >= 0.6666 && secondRandom <= 0.7770}
          {answer = "Parece-me que sim..."}

        {:else if secondRandom >= 0.7777 && secondRandom <= 0.8880}
          {answer = "Sim."}

        {:else if secondRandom >= 0.8888 && secondRandom <= 1}
          {answer = "Tudo aponta para que sim."}
        {/if}
      {/if}

      {#if secondFilter == "uncertain" && clicked && question == tempval}
        {#if secondRandom >= 0 && secondRandom <= 0.1999}
          {answer = "A comunicação está interrompida, tenta de novo..."}

        {:else if secondRandom >= 0.2 && secondRandom <= 0.3999}
          {answer = "Pergunta de novo mais tarde."}

        {:else if secondRandom >= 0.4 && secondRandom <= 0.5999}
          {answer = "É melhor que não saibas isso agora..."}

        {:else if secondRandom >= 0.6 && secondRandom <= 0.7999}
          {answer = "Não consigo decifrar isso neste momento..."}

        {:else if secondRandom >= 0.8 && secondRandom <= 1}
          {answer = "Concentra-te e pergunta de novo!"}
        {/if}
      {/if}

      {#if secondFilter == "negative" && clicked && question == tempval}
        {#if secondRandom >= 0 && secondRandom <= 0.1999}
          {answer = "A minha resposta final é não!"}

        {:else if secondRandom >= 0.2 && secondRandom <= 0.3999}
          {answer = "Se eu fosse a ti, eu não contava com isso..."}

        {:else if secondRandom >= 0.4 && secondRandom <= 0.5999}
          {answer = "De acordo com as minhas fontes, não."}

        {:else if secondRandom >= 0.6 && secondRandom <= 0.7999}
          {answer = "Não me parece... Não..."}

        {:else if secondRandom >= 0.8 && secondRandom <= 1}
          {answer = "Tenho as minhas dúvidas..."}
        {/if}
      {/if}

      {#if secondFilter == "meme" && clicked && question == tempval}
        {#if secondRandom >= 0 && secondRandom <= 0.2499}
          {answer = "POG  :O"}

        {:else if secondRandom >= 0.2500 && secondRandom <= 0.4999}
          {answer = "F CRINGE LOL"}

        {:else if secondRandom >= 0.5 && secondRandom <= 0.7499}
          {answer = "You sound like Genshit Impact Enjoyer"}

        {:else if secondRandom >= 0.75 && secondRandom <= 1}
        <div> 
          <img src={LordPepe} alt =" Pepe"/>
        </div>
        {/if}
      {/if}
  {/if}


</main>

<style>


</style>
