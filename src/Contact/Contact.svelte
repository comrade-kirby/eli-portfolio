<script>
  let name, email, message
</script>

<section class='contact'>
  <h1>GET IN TOUCH</h1>
  <form action="" method="POST">
    <div class='form-input'>
      <input 
        type='text'
        name='name'
        id='name'
        required
        bind:value={name}
        class:filled={name}
        placeholder='NAME' >
      <label for='name'>NAME</label>
    </div>
    <div class='form-input'>
      <input 
        type='email'
        name='email'
        id='email'
        required
        bind:value={email}
        class:filled={email}
        placeholder='EMAIL'>
      <label for='email'>EMAIL</label>
    </div>
    <div class='form-input'>
      <textarea 
        name='message'
        id='message'
        required
        bind:value={message}
        class:filled={message}
        placeholder='MESSAGE' />
      <label for='message'>MESSAGE</label>
    </div>
    <button type="submit">SUBMIT</button>
  </form>
</section>

<style>
  .contact {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    padding: var(--medium-spacing);
  }

  form {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    width: 100%;
    max-width: 700px;
    border: 10px var(--yellow) dotted;
    padding: var(--large-spacing);
    box-sizing: border-box;
  }

  .form-input {
    display: flex;
    flex-direction: column;
    width: 100%;
    margin-bottom: var(--medium-spacing);
  }

  input, textarea {
    margin: 0;
    padding: 4px 0;
    border: none;
    border-radius: 0;
    border-bottom: 1px solid black;
    font-size: var(--medium-font);
    background-color: var(--white);
    transition: 0.2s ease-in-out;
    z-index: 1;
  }

  :focus {
    background-color: white;
    outline: none;
  }

  :focus::placeholder {
    opacity: 0;
  }

  label {
    margin-top: var(--tiny-spacing);
    position: relative;
    text-align: right;
    top: -20px;
    opacity: 0;
    font-size: var(--small-font);
    transition: 0.2s ease-in-out;
  }

  .filled {
    padding: var(--small-spacing) var(--tiny-spacing) 0;
  }

  :focus + label, .filled + label {
    top: 0;
    opacity: 1;
  }

  textarea {
    height: 100px;
    padding: 0;
  }

  textarea:focus {
    height: 300px;
  }

  :required {
    box-shadow: none;
  }

  form:invalid button {
    background-color: grey;
  }

  button {
    background-color: var(--black);
    font-size: var(--medium-font);
    padding: var(--small-spacing);
    color: var(--white);
    border: none;
    transition: 0.2s ease-in-out;
  }

  button:hover, button:focus {
    background-color: var(--yellow);
  }
</style>