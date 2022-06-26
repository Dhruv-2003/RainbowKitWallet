
# RainbowKit 🌈 Wallet Integration

Now you can integrate wallet connection to your Web3 Dapp in just 5 Steps.




## Screenshots

![RainbowKit](https://www.rainbowkit.com/_next/image?url=%2Fhero-docs.png&w=3840&q=75)


## Why should you use 

- Out of the box wallet management 
- Wallet component with address, balance and chain 
- Customizable UI 
- Support of ethers and Wagmi library 

### What else reason do you need to start using it ?



## Let's get to installation

Install a package that has Rainbow Kit🌈, Wagmi and ethers with npm

```bash
npm init @rainbow-me/rainbowkit@latest
# or
yarn create @rainbow-me/rainbowkit@latest
# or
pnpm create @rainbow-me/rainbowkit@latest
```

Enter a project name and you have your basic app ready with all the dependencies . 

\
If you want to add to your current app , then follow the steps below

## Step 1 

Install these packages with npm

```bash
npm install @rainbow-me/rainbowkit wagmi ethers
```

## Step 2

Import RainbowKit, Wagmi and ethers in app.js 

```bash
import '@rainbow-me/rainbowkit/styles.css';
import {
  getDefaultWallets,
  RainbowKitProvider,
} from '@rainbow-me/rainbowkit';
import {
  chain,
  configureChains,
  createClient,
  WagmiConfig,
} from 'wagmi';
import { alchemyProvider } from 'wagmi/providers/alchemy';
import { publicProvider } from 'wagmi/providers/public';
```

## Step 3 

Configure desired Chains and intializing wagmi Client 

```bash

const { chains, provider } = configureChains(
  [chain.mainnet, chain.polygon, chain.optimism, chain.arbitrum],
  [
    alchemyProvider({ alchemyId: process.env.ALCHEMY_ID }),
    publicProvider()
  ]
);
const { connectors } = getDefaultWallets({
  appName: 'My RainbowKit App',
  chains
});
const wagmiClient = createClient({
  autoConnect: true,
  connectors,
  provider
})
```

## Step 4
Wrap your app with WagmiConfig and RainbowKitProvider

```bash
const App = () => {
  return (
    <WagmiConfig client={wagmiClient}>
      <RainbowKitProvider chains={chains}>
        <YourApp />
      </RainbowKitProvider>
    </WagmiConfig>
  );
};
```

## Step 5

Import connect wallet component in the file you want

```bash
import { ConnectButton } from '@rainbow-me/rainbowkit';
export const YourApp = () => {
  return <ConnectButton />;
};
```

💥Boom💥 , The connect wallet component will appear, we can customize the view of component. 

For more customizability and reference : https://www.rainbowkit.com/docs/introduction

![Wallet Connect](https://pbs.twimg.com/media/FVcZcwrUEAEpkOE?format=png&name=small)


    
