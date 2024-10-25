
# Memecoin Tapp Concept for Twitter via Tlink

## Overview

This tapp allows memecoin owners to post on Twitter with an auto-rendered Tlink that includes three interactive buttons: 
1. **Buy $1 of Memecoin**.
2. **Share to Earn**.
3. **Open Coingecko**.

### Key Features
- **Auto-rendered Tlink**: The moment the Tlink is embedded in a tweet, it will render as a picture with interactive buttons.
- **Buy $1 Memecoin**: Users can purchase $1 of the memecoin via Uniswap with a 10% fee.
- **Share to Earn**: Users can share the Tlink and earn from successful referral transactions.
- **Open Coingecko**: Directs users to the memecoin's page on Coingecko.

---

## User Flow

### 1. Memecoin Owner Posting:
   1. The memecoin owner creates a Tlink via the tapp.
   2. The tapp generates an image with text and three buttons: **Buy $1 Memecoin**, **Share to Earn**, **Open Coingecko**.
   3. The owner posts the tweet with the Tlink, which automatically renders as the image with the buttons.

### 2. Users Engaging with the Tlink:
When users see the tweet, they interact with the Tlink rendered as a card with the following options:
   1. **Buy $1 of Memecoin**: 
      - Clicking the "Buy" button opens a Uniswap interface to purchase $1 worth of the memecoin.
      - A 10% fee applies (50% to the owner, 50% to the share-to-earn pool).
   2. **Share to Earn**: 
      - Clicking "Share to Earn" generates a personalized Tlink for the user to share.
      - Referrals through this link allow the sharer to earn a portion from the share-to-earn pool.
   3. **Open Coingecko**: 
      - Clicking this button opens the memecoin's Coingecko page in a new tab.

---

## Share-to-Earn Mechanism

1. A user clicks "Share to Earn" to generate their personalized Tlink.
2. The user shares the link with their followers. 
3. When someone buys via the shared Tlink, the original user earns from the share-to-earn pool.
4. The tapp tracks and rewards users based on successful referrals.

---

## Technical Overview

### Frontend:
- **Twitter API and Tlink Rendering**: The tapp auto-generates a card (image) from the Tlink with interactive buttons.
- **Web3 Integration**: To connect wallets and handle Uniswap transactions.
- **UI for Cards**: A clean design that auto-renders when the Tlink is shared.

### Smart Contracts:
- **Fee Distribution Contract**: Splits the 10% transaction fee between the memecoin owner and the share-to-earn pool.
- **Share-to-Earn Contract**: Tracks referrals and distributes rewards based on successful transactions.(can use database+ manmully instead of smart contract )
- **Uniswap Integration**: Ensures seamless purchases of $1 worth of memecoin.

---

## TokenScript Design

Here's an example of the TokenScript XML defining the actions and rendering the Tlink.

```xml
<action id="render-tlink">
  <label xml:lang="en">Tlink Memecoin Interaction</label>
  <card>
    <title>Memecoin Name</title>
    <description>Buy, Share, or Learn more about Memecoin</description>
    <buttons>
      <button id="buy-memecoin">
        <label>Buy $1 Memecoin</label>
        <transaction>
          <contract>uniswap-contract</contract>
          <method name="buyTokens">
            <inputs>
              <input name="amount" type="uint256">1000000000000000000</input>
            </inputs>
          </method>
        </transaction>
      </button>
      <button id="share-tlink">
        <label>Share to Earn</label>
        <custom> <!-- Share-to-earn logic --> </custom>
      </button>
      <button id="open-coingecko">
        <label>Open Coingecko</label>
        <url>https://www.coingecko.com/en/coins/memecoin</url>
      </button>
    </buttons>
  </card>
</action>
```

---

## Next Steps

- **Mockup Creation**: A clickable TokenScript mockup can be developed to simulate this tapp’s user experience and functionalities. (Done)
- **Product Documentation**: Developers can use detailed documentation outlining the smart contracts, frontend components, and tapp integration with Uniswap and Twitter.
