<script>
// @ts-nocheck

  import { onMount } from 'svelte';
  import { chainData,chainId,connected,defaultEvmStores,selectedAccount,web3 } from 'svelte-web3';
//   export let message
//   export let tipAddress
//   const enable = () => defaultEvmStores.setProvider('https://sokol.poa.network')
 
const enableBrowser = () => defaultEvmStores.setBrowserProvider()
  $: checkAccount = $selectedAccount || '0x0000000000000000000000000000000000000000'
  $: balance = $connected ? $web3.eth.getBalance(checkAccount) : ''

//   free eligibility NFT

let sendTipFreeNFT = true;
   
    onMount(async () => {
        await fetch(`https://rocket-elevators-express-api.herokuapp.com/NFT/gift/${checkAccount}`)
    .then(response => response.json())
    .then(data => {
            sendTipFreeNFT = data;
    }).catch(error => {
        // return [];

  });
  });

// NOT ELIGIBILITY FREE, HERE TO BUY ROCKET 

let buyWithRocket = {};
  onMount(async () => {
    await fetch(`https://rocket-elevators-express-api.herokuapp.com/NFT/buyWithRocket/${checkAccount}`)
      .then((response) => response.json())
      .then((data) => {
        buyWithRocket = data;
      })
      .catch((error) => {
        // return [];
      });
  });

  function buy() {
    return buyWithRocket;
  }
</script>


<svelte:head>
	<title>Rocket Elevators</title>
	<meta name="description" content="Wallet app" />
</svelte:head>

<main>

<h1> * Welcome to your wallet *</h1>

  {#if $web3.version}

  <div > 
    <a href="/mint" class="btn"on:click="{enableBrowser}">CLICK HERE TO CONNECT TO WALLET</a>
   </div>
  {/if} 

  {#if $connected}
  <p>
    Connected chain: chainId = {$chainId}
  </p>
  <p>
    Your account adress = {$selectedAccount || 'not connected'}
  </p>

  <p>
    {checkAccount} Balance on {$chainData.name}=
    {#await balance}
    <span>waiting...</span>
    {:then value}
    <span>{value}</span>
    {/await} {$chainData.nativeCurrency.symbol}
  </p>
  
  {#if sendTipFreeNFT === "false"}

  <div> 
    <a href="/mint" class="btn" onClick={() => buy()}>CLICK HERE TO GET FREE NFT</a>
   </div>
    {/if}
  {/if}
</main>


<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin-top: 80px;
	}

    h1{
        color: red;
        font-weight: bolder;
        text-decoration: underline;
       text-transform: uppercase;
    }
    a.btn { 
    width: 400px;
    padding: 10px 25px 10px 25px;
    font-family: Arial; 
    font-size: 16px;
    text-decoration: none;
    color: #ffffff; 
    background-color: red;
    margin-bottom: 60px;
    margin-top:16%;
}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>