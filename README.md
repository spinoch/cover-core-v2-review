# cover-core-v2-review

## Design
The essense of Cover is CoverPools. Each CoverPool consists of multiple risky underlying to be covered. If any of the risky underlying of a pool experience an exploit (as per claims guidelines), all active coverages (Cover) of the CoverPool will be paid out up to 100%.

The following are the elements of the V2.
* **CoverPoolFactory** is the contract that creates CoverPools. It also stores information that are common to all V2 contracts, like logic contract implementation addresses, addresses of multi-sigs, claim manager address etc.
* **CoverPool** is the main element of V2. It handles coverage creation and minting, adding/deleting risk covered, stores accepted claims for the pool. A **risk** can be an asset or underlying that is covered in a coverage.
* **Cover** stores the deposited collateral funds for the coverage and handle minting and burning of covTokens, redeeming of collaterals
* **CoverERC20** the ERC20 covToken contract, normal ERC20 funcs with a few Cover specific func.
* **ClaimManagement** (ClaimConfig is part of that) manages the claiming process of Cover Protocol. It may call CoverPool on
..* `enactClaim` when a claim is accepted
..* `setNoclaimRedeemDelay` when a claim is filed or all claims are decided

