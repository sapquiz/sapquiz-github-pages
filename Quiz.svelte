<script>
  let questions = [
    {
      question: "Was ist SAP?",
      options: ["Software", "Hardware", "Dienstleistung"],
      answer: "Software"
    },
    {
      question: "Was bedeutet ERP?",
      options: ["Enterprise Resource Planning", "Enterprise Resource Program", "Enterprise Resource Project"],
      answer: "Enterprise Resource Planning"
    },
    // Füge hier weitere Fragen hinzu
  ];

  let currentQuestionIndex = 0;
  let score = 0;
  let selectedOption = '';

  function submitAnswer() {
    if (selectedOption === questions[currentQuestionIndex].answer) {
      score++;
    }
    selectedOption = '';
    currentQuestionIndex++;
  }

  function resetQuiz() {
    currentQuestionIndex = 0;
    score = 0;
  }
</script>

<main>
  {#if currentQuestionIndex < questions.length}
    <h1>{questions[currentQuestionIndex].question}</h1>
    {#each questions[currentQuestionIndex].options as option}
      <label>
        <input type="radio" bind:group={selectedOption} value={option} />
        {option}
      </label>
    {/each}
    <button on:click={submitAnswer}>Antwort einreichen</button>
  {:else}
    <h1>Quiz beendet!</h1>
    <p>Dein Punktestand: {score} von {questions.length}</p>
    <button on:click={resetQuiz}>Nochmal spielen</button>
  {/if}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
  }
</style>
