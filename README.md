# hashed-timelock-contract-ethereum

## How to start
* Install dependencies
* Start [Ganache]
* Run the tests

$ npm install
$ npm run ganache-start
$ npm run test

Compiling your contracts...
===========================
> Compiling ./contracts/HashedTimelock.sol
> Compiling ./contracts/Migrations.sol
> Artifacts written to /var/folders/5h/gdwfp6292y5g8zn5yzg4j1cw0000gn/T/test--41449-jO0raVUR0iyW
> Compiled successfully using:
   - solc: 0.5.16+commit.9c3226ce.Emscripten.clang



  Contract: HashedTimelock
    ✓ newContract() should create new contract and store correct details (75ms)
    ✓ newContract() should fail when no ETH sent
    ✓ newContract() should fail with timelocks in the past (41ms)
    ✓ newContract() should reject a duplicate contract request (88ms)
    ✓ withdraw() should send receiver funds when given the correct secret preimage (104ms)
    ✓ withdraw() should fail if preimage does not hash to hashX (79ms)
    ✓ withdraw() should fail if caller is not the receiver (80ms)
    ✓ withdraw() should fail after timelock expiry (1107ms)
    ✓ refund() should pass after timelock expiry (58ms)
    ✓ refund() should fail before the timelock expiry (62ms)
    ✓ getContract() returns empty record when contract doesn't exist

11 passing (2s)

### HashedTimelock

1.  `newContract(receiverAddress, hashlock, timelock)` create new HTLC with given receiver, hashlock and expiry; returns contractId bytes32
2.  `withdraw(contractId, preimage)` claim funds revealing the preimage
3.  `refund(contractId)` if withdraw was not called the contract creator can get a refund by calling this some time after the time lock has expired.

See [test/helper/utils.js] createContract function for how timeout deadlines are handled

See [test/htlc.js] for examples of interacting with the contract from javascript.