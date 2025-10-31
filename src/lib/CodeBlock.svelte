<script>
  export let code;
  export let lang = 'text';

  let copied = false;

  function copyCode() {
    if (navigator.clipboard) {
      navigator.clipboard.writeText(code);
    } else {
      // Fallback for older browsers
      const textArea = document.createElement('textarea');
      textArea.value = code;
      document.body.appendChild(textArea);
      textArea.select();
      document.execCommand('copy');
      document.body.removeChild(textArea);
    }
    copied = true;
    setTimeout(() => copied = false, 5000);
  }
</script>

<div class="code-block">
  <pre><code class="language-{lang}">{code}</code></pre>
  <button on:click={copyCode} class="copy-btn">{copied ? 'Copied' : '📋 Copy'}</button>
</div>

<style>
  .code-block {
    position: relative;
  }
  .copy-btn {
    position: absolute;
    top: 0.5rem;
    right: 0.5rem;
    background: #000;
    color: #fff;
    border: none;
    padding: 0.25rem 0.5rem;
    cursor: pointer;
    border-radius: 4px;
    font-size: 0.8rem;
  }
  .copy-btn:hover {
    background: #333;
  }
</style>