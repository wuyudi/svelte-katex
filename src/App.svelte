<script>
  import katex from "katex";
  let formula = "\\int_a^b f(x)\\,dx";
  var is_display = true;
  const render = (formula, is_display) =>
    katex.renderToString(formula, {
      displayMode: is_display,
      throwOnError: false,
    });
</script>

<svelte:head>
  <link
    rel="stylesheet"
    href="https://cdn.jsdelivr.net/npm/katex@0.12.0/dist/katex.min.css"
    integrity="sha384-AfEj0r4/OFrOo5t7NnNe46zW/tFgW6x/bCJG8FqQCEo3+Aro6EYUG4+cU+KJWu/X"
    crossorigin="anonymous"
  />
  <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
  <script
    id="MathJax-script"
    async
    src="https://cdn.jsdelivr.net/npm/mathjax@3.0.1/es5/tex-mml-chtml.js"></script>
</svelte:head>

<main>
  <div><textarea bind:value={formula} /></div>
  <button on:click={() => (is_display = !is_display)}>
    {is_display ? "inline" : "displayMode"} -> {is_display
      ? "displayMode"
      : "inline"}
  </button>
  <div>
    {@html render(formula, is_display)}
  </div>
  <h3>inline</h3>
  {@html render(formula, false)}
  <h3>block</h3>
  {@html render(formula, true)}
</main>
