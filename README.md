# Off Chain Workers

Substrate node with `off-chain-workers` demo is in this repo.

There is often a need to query and/or process off-chain data before it can be included in the on-chain state. 

The conventional way of doing this is through oracles. Oracles are external services that typically listen to blockchain events and trigger tasks accordingly. When these tasks complete, their results are submitted back to the blockchain using transactions. 

While this approach works, it still has several flaws with respect to security, scalability, and infrastructure efficiency.

To make the off-chain data integration secure and more efficient, Substrate provides off-chain workers. The off-chain worker subsystem allows execution of long-running and possibly non- deterministic tasks(e.g. web requests, encryption/decryption and signing of data, random number generation, CPU-intensive computations, enumeration/aggregation of on-chain data, etc.) that could otherwise require longer than the block execution time.

Off-chain workers have their own Wasm execution environment outside of the Substrate runtime. This separation of concerns is to make sure that the block production is not impacted by the long-running tasks. 

However, as the off-chain workers are declared in the same code as the runtime, they can easily access on-chain state for their computations.
