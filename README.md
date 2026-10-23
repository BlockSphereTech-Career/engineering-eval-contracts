# 15min - timed skill test for smart contract developer

Create your branch from the project root before you change any code:

```bash
git checkout -b John-david-1998-03-01
```

Run the current API from the project root and leave that terminal open:

```bash
cd backend
npm install
npm run dev
```

The API listens on http://localhost:4000.

The quote route also reads the deployed vault, so the local chain has to be up before that URL will answer.

## Task

Buyers ask for a number of shares in a listed property. Finish `quote` in `contracts/contracts/skill/Quote.sol` so it prices that order the same way the marketplace does.

`quote(sharePrice, shares, remaining)` returns:

- `cost` — `sharePrice * shares`, as an integer in wei. Return this cost even when the order cannot be filled.
- `canFill` — `true` only when `remaining` is at least `shares`. An order that takes the last shares still fills. If `shares` is greater than `remaining`, return the cost and set `canFill` to `false`.

Do not change `RealEstateMarketplace.sol`. Stay inside `Quote.sol`.

Run your result from the project root:

```bash
cd contracts
npx hardhat test test/Quote.test.js
```

Read the API result in another terminal, from the project root:

```bash
curl.exe "http://localhost:4000/api/properties/1/quote?shares=4"
```

Pass if `npx hardhat test test/Quote.test.js` passes. That run calls http://localhost:4000/api/properties/1/quote?shares=4 and checks `cost` and `canFill` against it.
