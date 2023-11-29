# Article summary
[Nakamoto (2008)](https://bitcoin.org/bitcoin.pdf) presented an alternative to centralized financial industries/actors. Instead of relying on trusted third party to prevent double-spending peer-to-peer network could be used to form a trusted source. This electric payment system would be based on cryptography instead of trust, making it accessible for every willing to participate. Transactions are verified and long chain provides proof-of-work making it hard (should I say almost impossible) to make changes to the past. Timestamps are used for hashes, but time itself is not relevant information. In peer-to-peer network longest chain is master and nodes can come and go as they want. This makes Bitcoin easy to maintain, because there isn't need for centralized party to be a master.

# Bitcoin testnet wallet
Firstly I just followed instruction from the course page [Trust to Blockchain 2023 autumn](https://terokarvinen.com/2023/trust-to-blockchain/#h5-not-byzantine) and ramped up the electrum client using testnet. I initialized a new wallet with default settings and created a new seed.

After everything was ready I went on to find some fake Bitcoins online. I found few options and decided to try out https://coinfaucet.eu/en/btc-testnet so I requested some fake money to my address tb1q75edjdlt5tevwpvug9g852j85yk2whhjslugyk.

![Fake money waiting for confirmation](/Fake_money.png)

I had to wait a pretty long time before I got enough confirmations for the money transfer in the testnet, but eventually I was able to send some fake money to Tero to his address published on the course page.

![Send money to Tero](/send_money.png)

For the end of this excercise I sended all the remaining Bitcoins back to where I got them.

# Exploring Bitcoin
Quick search for bitcoin explorer provided lots of good options and I decided to check Blockstream Explorer and more explicitly [block #819014](https://blockstream.info/block/000000000000000000016bdb94e2cb5f53c63b5254cfbf2931d5edf9223c10b9) from it.

The image below contains details of the block. Details include height, status, timestamp, size, virtual size, weight units, version, Merkle root, bits, difficulty and nonce. Height is basically just the number which identifies the block. Status tells how many confirmations does the block have which in the end tells how valid it is. Timestamp refers to time when block had its last edit (when last transaction of that block was made). Size, virtual size and weight units are basic information of the block (like file size on a disk). Version is self explanatory, because it is a version number used to check for changes. Merkle root is the root hash of the all the hashed that belong to this block. Bits and difficulty relate to calculating Merkle root has. Nonce refers to the nonsense input used to calculate the hash with as many starting zeros as possible for the hash of the block.
![Block details](/block_details.png)

Image below contains transaction details. Those details include status (how many confirmations), block (where this transaction belongs to), block height (human readable identification number of the block), block timestamp (latest update of the block), transaction fees (how much it costed to make this transaction), size, virtual size and weight (different size details of the transaction, like file details), version, lock time, segwit fee savings and privacy analysis. Most interesting things are basically status, block information and transaction fees.
![Transaction details](/transaction.png)
