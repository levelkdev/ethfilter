# ethfilter

Transaction and event log filtering for Ethereum block data

### Setup

```
npm install
```

### Usage

#### Import and Config

```js
import EthFilter from 'ethfilter'
const ethFilter = EthFilter('http://localhost:8545')

// get the address and abi of the contract you want to filter
// (<myContractAddress> and <myContractAbi>)

const myContractFilter = ethFilter.contract(myContractAddress, myContractAbi)
```

#### Transaction Filter

```js
// this filters all the doThing() transactions that were executed on
// myContractAddress from block 4702800 to 4702900
const doThingTransactions = myContractFilter.transactions({
  fromBlock: 4702800,
  toBlock: 4702900,
  name: 'doThing'
})

console.log(doThingTransactions)
/*
  [
    {
      name: 'doThing',
      input: {
        decoded: <decoded input params>,
        raw: <raw hex data>
      },
      ...<raw transaction receipt data>
    },
    ...
  ]
*/
```

#### Events Filter

```js
const thingHappenedEvents = myContractFilter.events({
  fromBlock: 4702800,
  toBlock: 4702900,
  name: 'ThingHappened'
})

console.log(thingHappenedEvents)
/*
  [
    {
      name: 'ThingHappened',
      arguments: <decoded event arguments>,
      ...<raw event log data>
    },
    ...
  ]
*/
```

### Tests

```
npm test
```
