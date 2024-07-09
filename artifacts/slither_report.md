**THIS CHECKLIST IS NOT COMPLETE**. Use `--show-ignored-findings` to show all the results.
Summary
 - [arbitrary-send-erc20](#arbitrary-send-erc20) (1 results) (High)
 - [arbitrary-send-eth](#arbitrary-send-eth) (1 results) (High)
 - [unused-return](#unused-return) (1 results) (Medium)
 - [missing-zero-check](#missing-zero-check) (1 results) (Low)
 - [reentrancy-events](#reentrancy-events) (1 results) (Low)
 - [assembly](#assembly) (1 results) (Informational)
 - [low-level-calls](#low-level-calls) (1 results) (Informational)
 - [constable-states](#constable-states) (1 results) (Optimization)
 - [immutable-states](#immutable-states) (1 results) (Optimization)
## arbitrary-send-erc20
Impact: High
Confidence: High
 - [ ] ID-0
[L1BossBridge.depositTokensToL2(address,address,uint256)](src/L1BossBridge.sol#L70-L78) uses arbitrary from in transferFrom: [token.safeTransferFrom(from,address(vault),amount)](src/L1BossBridge.sol#L74)

src/L1BossBridge.sol#L70-L78


## arbitrary-send-eth
Impact: High
Confidence: Medium
 - [ ] ID-1
[L1BossBridge.sendToL1(uint8,bytes32,bytes32,bytes)](src/L1BossBridge.sol#L112-L125) sends eth to arbitrary user
	Dangerous calls:
	- [(success,None) = target.call{value: value}(data)](src/L1BossBridge.sol#L121)

src/L1BossBridge.sol#L112-L125


## unused-return
Impact: Medium
Confidence: Medium
 - [ ] ID-2
[L1Vault.approveTo(address,uint256)](src/L1Vault.sol#L20-L22) ignores return value by [token.approve(target,amount)](src/L1Vault.sol#L21)

src/L1Vault.sol#L20-L22


## missing-zero-check
Impact: Low
Confidence: Medium
 - [ ] ID-3
[L1BossBridge.sendToL1(uint8,bytes32,bytes32,bytes).target](src/L1BossBridge.sol#L119) lacks a zero-check on :
		- [(success,None) = target.call{value: value}(data)](src/L1BossBridge.sol#L121)

src/L1BossBridge.sol#L119


## reentrancy-events
Impact: Low
Confidence: Medium
 - [ ] ID-4
Reentrancy in [L1BossBridge.depositTokensToL2(address,address,uint256)](src/L1BossBridge.sol#L70-L78):
	External calls:
	- [token.safeTransferFrom(from,address(vault),amount)](src/L1BossBridge.sol#L74)
	Event emitted after the call(s):
	- [Deposit(from,l2Recipient,amount)](src/L1BossBridge.sol#L77)

src/L1BossBridge.sol#L70-L78


## assembly
Impact: Informational
Confidence: High
 - [ ] ID-5
[TokenFactory.deployToken(string,bytes)](src/TokenFactory.sol#L23-L29) uses assembly
	- [INLINE ASM](src/TokenFactory.sol#L24-L26)

src/TokenFactory.sol#L23-L29


## low-level-calls
Impact: Informational
Confidence: High
 - [ ] ID-6
Low level call in [L1BossBridge.sendToL1(uint8,bytes32,bytes32,bytes)](src/L1BossBridge.sol#L112-L125):
	- [(success,None) = target.call{value: value}(data)](src/L1BossBridge.sol#L121)

src/L1BossBridge.sol#L112-L125


## constable-states
Impact: Optimization
Confidence: High
 - [ ] ID-7
[L1BossBridge.DEPOSIT_LIMIT](src/L1BossBridge.sol#L30) should be constant 

src/L1BossBridge.sol#L30


## immutable-states
Impact: Optimization
Confidence: High
 - [ ] ID-8
[L1Vault.token](src/L1Vault.sol#L13) should be immutable 

src/L1Vault.sol#L13


