# zkVerify Relayer Demo

## 🔑 Using your zkVerify API Key

To link submissions with your EVM wallet for points/rewards, you need an API key issued by the zkVerify team.

1. Request an API key from the zkVerify team. It will be tied to your wallet address.
2. Create a `.env` file in the project root with your key:

```env
ZKVERIFY_API_KEY=your_api_key_here
```

3. The relayer script (`index.js`) automatically attaches this key when submitting proofs:

```js
const res = await fetch("https://api.zkverify.io/v1/submit", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    "Authorization": `Bearer ${process.env.ZKVERIFY_API_KEY}`
  },
  body: JSON.stringify({
    proof,
    publicSignals
  })
});
```

4. That’s it — every finalized proof is now linked to your wallet address on zkVerify.
