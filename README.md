# hashed-timelock-contract-ethereum

## How to start
* Install dependencies
npm install
* Start [Ganache]
npm run ganache-start
* Run the tests
npm run test

### HashedTimelock

1.  `newContract(receiverAddress, hashlock, timelock)` create new HTLC with given receiver, hashlock and expiry; returns contractId bytes32
2.  `withdraw(contractId, preimage)` claim funds revealing the preimage
3.  `refund(contractId)` if withdraw was not called the contract creator can get a refund by calling this some time after the time lock has expired.

See [test/helper/utils.js] createContract function for how timeout deadlines are handled

See [test/htlc.js] for examples of interacting with the contract from javascript.