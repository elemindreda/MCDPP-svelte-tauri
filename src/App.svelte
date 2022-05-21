<script lang="ts">
  import logo from './assets/logo_hoslab.png'
  import Filedrop from './lib/filedrop.svelte';
  import github_icon from 'svelte-awesome/icons/github';
  import bug_icon from 'svelte-awesome/icons/bug'
  import Icon from 'svelte-awesome/components/Icon.svelte';
  // import {read, writeFileXLSX} from 'xlsx';
function doNothing(){
  return;
}



</script>
  <div class = "main">
    <div class="header">
      <img src={logo} alt="Hoslab Logo" />
      <a href="mailto:swaghulde@hoslab.com.au" target="_blank">
        <Icon data={bug_icon} style = {"height: 2rem; width:2rem;"}/>
      </a>
      <a href="http://github.com/elemindreda/" target="_blank">
        <Icon data={github_icon} style = {"height: 2rem; width:2rem;"}/>
      </a>
    </div>
    <Filedrop />
    <button on:click={doNothing}>
    boom
    </button>
    <p>
      Check out my github <a href="http://github.com/elemindreda/" target="_blank">repo</a> for the source code.

    </p>
  </div>
 
<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    background: linear-gradient(to right, #4568dc, #b06ab3);
  }

  .header {
    display: grid;
    grid-template-columns: [row1-s] 80% [row1-e row2-s] 10% [row2-e row3-s] 10% [row3-e];
    width: 100%;
  }


  .main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  color: #D7D7EF;
  font-family: 'Lato', sans-serif;
  width: 500px;
  position: fixed;
  }

  img {
    grid-column-start: row1-s;
    grid-column-end: row1-e;
    justify-self: left;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  button {
    font-family: inherit;
    font-size: inherit;
    padding: 1em 2em;
    color: #ff3e00;
    background-color: rgba(255, 62, 0, 0.1);
    border-radius: 2em;
    border: 2px solid rgba(255, 62, 0, 0);
    outline: none;
    width: 200px;
    font-variant-numeric: tabular-nums;
    cursor: pointer;
  }
  button:focus {
    border: 2px solid #ff3e00;
  }

  button:active {
    background-color: rgba(255, 62, 0, 0.2);
  }


  @media (min-width: 480px) {

    p {
      max-width: none;
    }
  }
</style>
