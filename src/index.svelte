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
  #questions {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    height: 500px;
  }
</style>

<svelte:head>
  <title>Maths Generator</title>
</svelte:head>

<section class="hero is-primary">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Maths Worksheet Generator
      </h1>
      <h2 class="subtitle">
        Time to git gud!
      </h2>
    </div>
  </div>
</section>

<section class="section">
  <label class="label">
    Min:
    <input type="number" bind:value={min}>
  </label>

  <label class="label">
    Max:
    <input type="number" bind:value={max}>
  </label>

  <label class="label">
    <input type="radio" bind:group={operator} value={"+"}>
    Add/Subtract
  </label>

  <label class="label">
    <input type="radio" bind:group={operator} value={"*"}>
    Multiply/Divide
  </label>

  <button class="button" on:click={createQuestions}>Generate</button>
</section>

<section class="section" id="questions">
  {#each questions as question}
    <div>
      <pre><p>{question.first}</p></pre>
      <pre><p>{question.second}</p></pre>
      <pre><p>{question.third}</p></pre>
      <pre><p>{question.fourth}</p></pre>
    </div>
  {/each}
  <div>
  
  </div>
  
</section>
