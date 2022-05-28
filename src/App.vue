<template>
  <div class="content">
    <h1>Step 1: Check if terra has already been added</h1>
    <p>
      If you already have terra or Testnet configured in Keplr you will
      need to remove it first, or this tool will do nothing.
    </p>

    <ol class="guide">
      <li>
        Open and unlock Keplr, then click the name of the currently selected
        chain at the top
      </li>
      <img alt="Vue logo" src="./assets/chainname.png" />
      <li>
        Scroll to the bottom, and check terra or Testnet are not listed
        under Beta Support
      </li>
      <img alt="Vue logo" src="./assets/betasupport.png" />
      <li>If they are, click the X next to the chain name to remove it</li>
    </ol>
    
    <h1>Step 2: Add terra to Keplr</h1>

    <ol class="guide">
      <li>Open and unlock Keplr.</li>

      <li>
        Click the add button below. If nothing happens it means that you already
        have a terra chain installed. Either use it, or follow the
        instructions in Step 1 to remove it.
      </li>

      <button class="button" @click="addNetwork()">Add terra</button>

      <li>Keplr will open an approval window. Read it, then click Approve</li>

      <img alt="Vue logo" src="./assets/keplrapprove.png" />

      <li>
        If no error appears then terra was successfully added to Keplr.
      </li>
    </ol>

    <h1>Step 3: Switch from Mainnet to terra in Keplr</h1>

    <ol class="guide">
      <li>
        Open and unlock Keplr, then click the name of the currently selected
        chain at the top
      </li>
      <img alt="Vue logo" src="./assets/chainname.png" />
      <li>
        Scroll to the bottom then click Secure Secrets terra under Beta Support
      </li>
      <img alt="Vue logo" src="./assets/securesecretsconnect.png" />
      <li>
        Congrats! Keplr is now using the terra or testnet
        chain via Secure Secrets
      </li>
    </ol>
    <br />

  </div>
</template>

<script>
export default {
  methods: {
    addNetwork() {
      window.keplr.experimentalSuggestChain({
        chainId   : "phoenix-1",
        chainName : "TerraV2",
        rpc       : "https://rpc.terrav2.ccvalidators.com/",
        rest      : "https://fcd.terrav2.ccvalidators.com/",
        bip44     : {
          coinType : 529,
        },
        coinType      : 529,
        stakeCurrency : {
          coinDenom        : "LUNA",
          coinMinimalDenom : "uluna",
          coinDecimals     : 6,
        },
        bech32Config : {
          bech32PrefixAccAddr  : "terra",
          bech32PrefixAccPub   : "terrapub",
          bech32PrefixValAddr  : "terravaloper",
          bech32PrefixValPub   : "terravaloperpub",
          bech32PrefixConsAddr : "terravalcons",
          bech32PrefixConsPub  : "terravalconspub",
        },
        currencies : [ {
          coinDenom        : "LUNA",
          coinMinimalDenom : "uluna",
          coinDecimals     : 6,
        } ],
        feeCurrencies : [ {
          coinDenom        : "LUNA",
          coinMinimalDenom : "uluna",
          coinDecimals     : 6,
        } ],
        gasPriceStep : {
          low     : 0.15,
          average : 0.25,
          high    : 0.4,
        },
        features : [ ],
      });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

#app .content {
  width: 800px;
  margin: 0 auto;
}

ol.guide li {
  padding: 1em 0;
}

h3 {
  margin: 40px 0 0;
}

a {
  color: #42b983;
}
</style>
