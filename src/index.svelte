<script>
  let min = 0;
  let max = 10;
  let operator = "+"

  let questions = []

  const createQuestions = () => {
    questions = [];
    for (let i = 0; i < 10; i++) {
      let num1 = Math.floor((Math.random() * max) + min)
      let num2 = Math.floor((Math.random() * max) + min)
      let question
      if (operator === "+") {
        question = {
                first: ` ${num1} + ${num2} = `,
                second: ` ${num1} - ${num2} = `,
                third: `-${num1} + ${num2} = `,
                fourth: `-${num1} - ${num2} = `
              }
      } else if (operator === "*") {
        question = {
                first: ` ${num1} x ${num2} = `,
                second: ` ${num1} ÷ ${num2} = `,
                third: `-${num1} x ${num2} = `,
                fourth: `-${num1} ÷ ${num2} = `
              }
      }
      questions = [...questions, question]
    }
  }
</script>

<style>
  section {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    height: 500px;
  }
</style>

<h1 class="title">Maths Worksheet Generator</h1>

<div>
  <div>
    <label class="label">
      Min:
      <input type="number" bind:value={min}>
    </label>

    <label class="label">
      Max:
      <input type="number" bind:value={max}>
    </label>
  </div>

  <div>
    <label class="label">
      Add/Subtract:
      <input type="radio" bind:group={operator} value={"+"}>
    </label>

    <label class="label">
      Multiply/Divide:
      <input type="radio" bind:group={operator} value={"*"}>
    </label>
  </div>
</div>


<button class="button" on:click={createQuestions}>Generate</button>

<section class="section">
  {#each questions as question}
    <div>
      <pre><p>{question.first}</p></pre>
      <pre><p>{question.second}</p></pre>
      <pre><p>{question.third}</p></pre>
      <pre><p>{question.fourth}</p></pre>
    </div>
    <hr>
  {/each}
  <div>
  
  </div>
  
</section>
