# Slither over SKALE
Results of running slither on the main contracts of SKALE

## Compilation warnings/errors 

/share/contracts/SkaleDKG.sol:21:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
pragma experimental ABIEncoderV2;

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Migrations.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Parameter Migrations.upgrade(address).new_address (../../share/contracts/Migrations.sol#20) is not in mixedCase
Variable Migrations.last_completed_migration (../../share/contracts/Migrations.sol#6) is not in mixedCase

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

## INFO:Detectors:
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) is declared view but contains assembly code
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) is declared view but contains assembly code
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) is declared view but contains assembly code
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) is declared view but contains assembly code
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) is declared view but contains assembly code
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) is declared view but contains assembly code

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state

## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#254)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#330)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-1

## INFO:Detectors:
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#322)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-2

## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	Event emitted after the call(s):
	- AllDataReceived(groupIndex,fromNodeIndex) (../../share/contracts/SkaleDKG.sol#245)
	- SuccessfulDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#255)
Reentrancy in SkaleDKG.complaint(bytes32,uint256,uint256) (../../share/contracts/SkaleDKG.sol#178-203):
	External calls:
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#196)
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#201)
	Event emitted after the call(s):
	- ComplaintSent(groupIndex,fromNodeIndex,toNodeIndex) (../../share/contracts/SkaleDKG.sol#190)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleDKG.broadcast(bytes32,uint256,bytes,bytes) (../../share/contracts/SkaleDKG.sol#136-176) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#157-163)
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#433-437)
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#704-707)
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#714-717)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#718-721)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#722-725)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#726-729)
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#772-775)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#800-803)
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#810-815)
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#824-831)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

##  INFO:Detectors:
Different versions of Solidity is used in :
	- Version used: ['ABIEncoderV2', '^0.5.0']
	- ^0.5.0 (../../share/contracts/ContractManager.sol#20)
	- ^0.5.0 (../../share/contracts/Ownable.sol#1)
	- ^0.5.0 (../../share/contracts/Permissions.sol#20)
	- ^0.5.0 (../../share/contracts/SkaleDKG.sol#20)
	- ABIEncoderV2 (../../share/contracts/SkaleDKG.sol#21)
	- ^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#different-pragma-directives-are-used

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleDKG.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ECDH.sol#20) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: ! groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i_scope_0]) && nodesData.isNodeActive(nodesWithFreeSpace[i_scope_0]) (../../share/contracts/SchainsFunctionalityInternal.sol#158)
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i]) || ! nodesData.isNodeActive(nodesWithFreeSpace[i]) (../../share/contracts/SchainsFunctionalityInternal.sol#150)
SchainsFunctionalityInternal.findSchainAtSchainsForNode(uint256,bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#172-181) has external calls inside a loop: ISchainsData(dataAddress).schainsForNodes(nodeIndex,i) == schainId (../../share/contracts/SchainsFunctionalityInternal.sol#176)
SchainsFunctionalityInternal.selectNodeToGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#188-209) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodeIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#203)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: groupsData.setException(groupIndex,node) (../../share/contracts/SchainsFunctionalityInternal.sol#239)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: schainsData.addSchainForNode(node,groupIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#240)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop

## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in SchainsFunctionalityInternal.createGroupForSchain(string,bytes32,uint256,uint8) (../../share/contracts/SchainsFunctionalityInternal.sol#61-77):
	External calls:
	- addGroup(schainId,numberOfNodes,bytes32(uint256(partOfNode))) (../../share/contracts/SchainsFunctionalityInternal.sol#68)
	- numberOfNodesInGroup = generateGroup(schainId) (../../share/contracts/SchainsFunctionalityInternal.sol#69)
	- ISchainsData(dataAddress).setSchainPartOfNode(schainId,partOfNode) (../../share/contracts/SchainsFunctionalityInternal.sol#70)
	Event emitted after the call(s):
	- SchainNodes(schainName,schainId,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#71-76)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251):
	External calls:
	- groupsData.setNodesInGroup(groupIndex,nodesInGroup) (../../share/contracts/SchainsFunctionalityInternal.sol#245)
	Event emitted after the call(s):
	- GroupGenerated(groupIndex,nodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#246-250)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionalityInternal.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

##  INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

##  INFO:Detectors:
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external

## INFO:Detectors:
NodesData.isLeavingPeriodExpired(uint256) (../../share/contracts/NodesData.sol#368-370) uses timestamp for comparisons
	Dangerous comparisons:
	- block.timestamp - nodes[nodeIndex].leavingDate >= leavingPeriod (../../share/contracts/NodesData.sol#369)
NodesData.isTimeForReward(uint256) (../../share/contracts/NodesData.sol#377-380) uses timestamp for comparisons
	Dangerous comparisons:
	- nodes[nodeIndex].lastRewardDate + IConstants(constantsAddress).rewardPeriod() <= block.timestamp (../../share/contracts/NodesData.sol#379)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

## INFO:Detectors:
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) is declared view but contains assembly code
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) is declared view but contains assembly code

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#141-144)
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#253-256)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleVerifier.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
addGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146)
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractReceiver.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsData.isTimeExpired(bytes32) (../../share/contracts/SchainsData.sol#291-293) uses timestamp for comparisons
	Dangerous comparisons:
	- schains[schainId].startDate + schains[schainId].lifetime < block.timestamp (../../share/contracts/SchainsData.sol#292)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: schain = ISchainsData(schainsDataAddress).schainsAtSystem(i) (../../share/contracts/Pricing.sol#89)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: numberOfNodesInGroup = IGroupsData(schainsDataAddress).getNumberOfNodesInGroup(schain) (../../share/contracts/Pricing.sol#90)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: part = ISchainsData(schainsDataAddress).getSchainsPartOfNode(schain) (../../share/contracts/Pricing.sol#91)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Pricing.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:

Pragma version^0.5.0 (../../share/contracts/ConstantsHolder.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:

Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) is declared view but contains assembly code
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) is declared view but contains assembly code

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state

## INFO:Detectors:
Reentrancy in NodesFunctionality.completeWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#179-198):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeft(nodeIndex) (../../share/contracts/NodesFunctionality.sol#186)
	- INodesData(nodesDataAddress).removeNode(nodeIndex) (../../share/contracts/NodesFunctionality.sol#188)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeComplete(nodeIndex,from,IConstants(constantsAddress).NODE_DEPOSIT(),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#191-196)
Reentrancy in NodesFunctionality.createNode(address,uint256,bytes) (../../share/contracts/NodesFunctionality.sol#81-122):
	External calls:
	- nodeIndex = INodesData(nodesDataAddress).addNode(from,name,ip,publicIP,port,publicKey) (../../share/contracts/NodesFunctionality.sol#102-108)
	Event emitted after the call(s):
	- NodeCreated(nodeIndex,from,name,ip,publicIP,port,nonce,uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#112-121)
Reentrancy in NodesFunctionality.initWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#155-170):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeaving(nodeIndex) (../../share/contracts/NodesFunctionality.sol#161)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeInit(nodeIndex,from,uint32(block.timestamp),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#163-168)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#303-310)
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#326-330)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) is declared view but contains assembly code
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) is declared view but contains assembly code

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state

## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#31-34)
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#42-45)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Decryption.sol#20) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ManagerData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IManagerData.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) is declared view but contains assembly code
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) is declared view but contains assembly code

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state

## INFO:Detectors:
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: downtimeArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,0) (../../share/contracts/ValidatorsFunctionality.sol#186)
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: latencyArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,1) (../../share/contracts/ValidatorsFunctionality.sol#187)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setException(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#214)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#215)
ValidatorsFunctionality.generateGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#224-258) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,nodesInGroup[i]) (../../share/contracts/ValidatorsFunctionality.sol#250)
ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301) has external calls inside a loop: IValidatorsData(dataAddress).addValidatedNode(index,bytesParametersOfNodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#292)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop

## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in ValidatorsFunctionality.addValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#114-127):
	External calls:
	- addGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#119)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#120)
	Event emitted after the call(s):
	- ValidatorCreated(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#121-126)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in ValidatorsFunctionality.rotateNode(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#196-200):
	External calls:
	- newNodeIndexEvent = selectNodeToGroup(schainId) (../../share/contracts/ValidatorsFunctionality.sol#198)
	Event emitted after the call(s):
	- ValidatorRotated(schainId,newNodeIndexEvent) (../../share/contracts/ValidatorsFunctionality.sol#199)
Reentrancy in ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177):
	External calls:
	- IValidatorsData(dataAddress).removeValidatedNode(validatorIndex,index) (../../share/contracts/ValidatorsFunctionality.sol#165)
	- IValidatorsData(dataAddress).addVerdict(keccak256(bytes)(abi.encodePacked(toNodeIndex)),downtime,latency) (../../share/contracts/ValidatorsFunctionality.sol#169)
	Event emitted after the call(s):
	- VerdictWasSent(fromValidatorIndex,toNodeIndex,downtime,latency,receiveVerdict,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#171-176)
Reentrancy in ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301):
	External calls:
	- IGroupsData(dataAddress).setException(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#287)
	- indexOfNodesInGroup = generateGroup(groupIndex) (../../share/contracts/ValidatorsFunctionality.sol#288)
	Event emitted after the call(s):
	- ValidatorsArray(nodeIndex,groupIndex,indexOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#294-299)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reentrancy in ValidatorsFunctionality.upgradeValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#129-142):
	External calls:
	- upgradeGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#134)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#135)
	Event emitted after the call(s):
	- ValidatorUpgraded(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#136-141)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3

## INFO:Detectors:
ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177) uses timestamp for comparisons
	Dangerous comparisons:
	- require(bool,string)(time <= block.timestamp,The time has not come to send verdict) (../../share/contracts/ValidatorsFunctionality.sol#163)
	- receiveVerdict = time + IConstants(constantsAddress).deltaPeriod() > uint32(block.timestamp) (../../share/contracts/ValidatorsFunctionality.sol#167)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#344-349)
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#362-368)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IValidatorsFunctionality.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

## INFO:Detectors:
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) is declared view but contains assembly code

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state

## INFO:Detectors:
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFun/share/contracts/SkaleDKG.sol:21:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
pragma experimental ABIEncoderV2;

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Migrations.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Parameter Migrations.upgrade(address).new_address (../../share/contracts/Migrations.sol#20) is not in mixedCase
Variable Migrations.last_completed_migration (../../share/contracts/Migrations.sol#6) is not in mixedCase

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

## INFO:Detectors:
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) is declared view but contains assembly code
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) is declared view but contains assembly code
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) is declared view but contains assembly code
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) is declared view but contains assembly code
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) is declared view but contains assembly code
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) is declared view but contains assembly code

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state

## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#254)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#330)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-1

## INFO:Detectors:
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#322)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-2

## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	Event emitted after the call(s):
	- AllDataReceived(groupIndex,fromNodeIndex) (../../share/contracts/SkaleDKG.sol#245)
	- SuccessfulDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#255)
Reentrancy in SkaleDKG.complaint(bytes32,uint256,uint256) (../../share/contracts/SkaleDKG.sol#178-203):
	External calls:
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#196)
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#201)
	Event emitted after the call(s):
	- ComplaintSent(groupIndex,fromNodeIndex,toNodeIndex) (../../share/contracts/SkaleDKG.sol#190)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleDKG.broadcast(bytes32,uint256,bytes,bytes) (../../share/contracts/SkaleDKG.sol#136-176) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#157-163)
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#433-437)
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#704-707)
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#714-717)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#718-721)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#722-725)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#726-729)
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#772-775)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#800-803)
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#810-815)
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#824-831)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Different versions of Solidity is used in :
	- Version used: ['ABIEncoderV2', '^0.5.0']
	- ^0.5.0 (../../share/contracts/ContractManager.sol#20)
	- ^0.5.0 (../../share/contracts/Ownable.sol#1)
	- ^0.5.0 (../../share/contracts/Permissions.sol#20)
	- ^0.5.0 (../../share/contracts/SkaleDKG.sol#20)
	- ABIEncoderV2 (../../share/contracts/SkaleDKG.sol#21)
	- ^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#different-pragma-directives-are-used

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleDKG.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ECDH.sol#20) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: ! groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i_scope_0]) && nodesData.isNodeActive(nodesWithFreeSpace[i_scope_0]) (../../share/contracts/SchainsFunctionalityInternal.sol#158)
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i]) || ! nodesData.isNodeActive(nodesWithFreeSpace[i]) (../../share/contracts/SchainsFunctionalityInternal.sol#150)
SchainsFunctionalityInternal.findSchainAtSchainsForNode(uint256,bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#172-181) has external calls inside a loop: ISchainsData(dataAddress).schainsForNodes(nodeIndex,i) == schainId (../../share/contracts/SchainsFunctionalityInternal.sol#176)
SchainsFunctionalityInternal.selectNodeToGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#188-209) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodeIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#203)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: groupsData.setException(groupIndex,node) (../../share/contracts/SchainsFunctionalityInternal.sol#239)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: schainsData.addSchainForNode(node,groupIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#240)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop

## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in SchainsFunctionalityInternal.createGroupForSchain(string,bytes32,uint256,uint8) (../../share/contracts/SchainsFunctionalityInternal.sol#61-77):
	External calls:
	- addGroup(schainId,numberOfNodes,bytes32(uint256(partOfNode))) (../../share/contracts/SchainsFunctionalityInternal.sol#68)
	- numberOfNodesInGroup = generateGroup(schainId) (../../share/contracts/SchainsFunctionalityInternal.sol#69)
	- ISchainsData(dataAddress).setSchainPartOfNode(schainId,partOfNode) (../../share/contracts/SchainsFunctionalityInternal.sol#70)
	Event emitted after the call(s):
	- SchainNodes(schainName,schainId,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#71-76)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251):
	External calls:
	- groupsData.setNodesInGroup(groupIndex,nodesInGroup) (../../share/contracts/SchainsFunctionalityInternal.sol#245)
	Event emitted after the call(s):
	- GroupGenerated(groupIndex,nodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#246-250)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionalityInternal.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

## INFO:Detectors:
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external

## INFO:Detectors:
NodesData.isLeavingPeriodExpired(uint256) (../../share/contracts/NodesData.sol#368-370) uses timestamp for comparisons
	Dangerous comparisons:
	- block.timestamp - nodes[nodeIndex].leavingDate >= leavingPeriod (../../share/contracts/NodesData.sol#369)
NodesData.isTimeForReward(uint256) (../../share/contracts/NodesData.sol#377-380) uses timestamp for comparisons
	Dangerous comparisons:
	- nodes[nodeIndex].lastRewardDate + IConstants(constantsAddress).rewardPeriod() <= block.timestamp (../../share/contracts/NodesData.sol#379)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp

## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) is declared view but contains assembly code
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#141-144)
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#253-256)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleVerifier.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
addGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146)
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractReceiver.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsData.isTimeExpired(bytes32) (../../share/contracts/SchainsData.sol#291-293) uses timestamp for comparisons
	Dangerous comparisons:
	- schains[schainId].startDate + schains[schainId].lifetime < block.timestamp (../../share/contracts/SchainsData.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: schain = ISchainsData(schainsDataAddress).schainsAtSystem(i) (../../share/contracts/Pricing.sol#89)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: numberOfNodesInGroup = IGroupsData(schainsDataAddress).getNumberOfNodesInGroup(schain) (../../share/contracts/Pricing.sol#90)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: part = ISchainsData(schainsDataAddress).getSchainsPartOfNode(schain) (../../share/contracts/Pricing.sol#91)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Pricing.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ConstantsHolder.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) is declared view but contains assembly code
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Reentrancy in NodesFunctionality.completeWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#179-198):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeft(nodeIndex) (../../share/contracts/NodesFunctionality.sol#186)
	- INodesData(nodesDataAddress).removeNode(nodeIndex) (../../share/contracts/NodesFunctionality.sol#188)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeComplete(nodeIndex,from,IConstants(constantsAddress).NODE_DEPOSIT(),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#191-196)
Reentrancy in NodesFunctionality.createNode(address,uint256,bytes) (../../share/contracts/NodesFunctionality.sol#81-122):
	External calls:
	- nodeIndex = INodesData(nodesDataAddress).addNode(from,name,ip,publicIP,port,publicKey) (../../share/contracts/NodesFunctionality.sol#102-108)
	Event emitted after the call(s):
	- NodeCreated(nodeIndex,from,name,ip,publicIP,port,nonce,uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#112-121)
Reentrancy in NodesFunctionality.initWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#155-170):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeaving(nodeIndex) (../../share/contracts/NodesFunctionality.sol#161)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeInit(nodeIndex,from,uint32(block.timestamp),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#163-168)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#303-310)
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#326-330)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) is declared view but contains assembly code
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#31-34)
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#42-45)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Decryption.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ManagerData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IManagerData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) is declared view but contains assembly code
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: downtimeArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,0) (../../share/contracts/ValidatorsFunctionality.sol#186)
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: latencyArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,1) (../../share/contracts/ValidatorsFunctionality.sol#187)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setException(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#214)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#215)
ValidatorsFunctionality.generateGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#224-258) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,nodesInGroup[i]) (../../share/contracts/ValidatorsFunctionality.sol#250)
ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301) has external calls inside a loop: IValidatorsData(dataAddress).addValidatedNode(index,bytesParametersOfNodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in ValidatorsFunctionality.addValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#114-127):
	External calls:
	- addGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#119)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#120)
	Event emitted after the call(s):
	- ValidatorCreated(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#121-126)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in ValidatorsFunctionality.rotateNode(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#196-200):
	External calls:
	- newNodeIndexEvent = selectNodeToGroup(schainId) (../../share/contracts/ValidatorsFunctionality.sol#198)
	Event emitted after the call(s):
	- ValidatorRotated(schainId,newNodeIndexEvent) (../../share/contracts/ValidatorsFunctionality.sol#199)
Reentrancy in ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177):
	External calls:
	- IValidatorsData(dataAddress).removeValidatedNode(validatorIndex,index) (../../share/contracts/ValidatorsFunctionality.sol#165)
	- IValidatorsData(dataAddress).addVerdict(keccak256(bytes)(abi.encodePacked(toNodeIndex)),downtime,latency) (../../share/contracts/ValidatorsFunctionality.sol#169)
	Event emitted after the call(s):
	- VerdictWasSent(fromValidatorIndex,toNodeIndex,downtime,latency,receiveVerdict,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#171-176)
Reentrancy in ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301):
	External calls:
	- IGroupsData(dataAddress).setException(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#287)
	- indexOfNodesInGroup = generateGroup(groupIndex) (../../share/contracts/ValidatorsFunctionality.sol#288)
	Event emitted after the call(s):
	- ValidatorsArray(nodeIndex,groupIndex,indexOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#294-299)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reentrancy in ValidatorsFunctionality.upgradeValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#129-142):
	External calls:
	- upgradeGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#134)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#135)
	Event emitted after the call(s):
	- ValidatorUpgraded(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#136-141)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177) uses timestamp for comparisons
	Dangerous comparisons:
	- require(bool,string)(time <= block.timestamp,The time has not come to send verdict) (../../share/contracts/ValidatorsFunctionality.sol#163)
	- receiveVerdict = time + IConstants(constantsAddress).deltaPeriod() > uint32(block.timestamp) (../../share/contracts/ValidatorsFunctionality.sol#167)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#344-349)
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#362-368)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IValidatorsFunctionality.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#153-156)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#157-159)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#160)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#177-180)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#181-183)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#184)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in SchainsFunctionality.addSchain(address,uint256,bytes) (../../share/contracts/SchainsFunctionality.sol#90-119):
	External calls:
	- initializeSchainInSchainsData(schainParameters.name,from,deposit,schainParameters.lifetime) (../../share/contracts/SchainsFunctionality.sol#102-106)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).createGroupForSchain(schainParameters.name,keccak256(bytes)(abi.encodePacked(schainParameters.name)),numberOfNodes,partOfNode) (../../share/contracts/SchainsFunctionality.sol#113-114)
	Event emitted after the call(s):
	- SchainCreated(schainParameters.name,from,partOfNode,schainParameters.lifetime,numberOfNodes,deposit,schainParameters.nonce,keccak256(bytes)(abi.encodePacked(schainParameters.name)),uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionality.sol#116-118)
Reentrancy in SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#163)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#164)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#165)
Reentrancy in SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).delet/share/contracts/SkaleDKG.sol:21:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
pragma experimental ABIEncoderV2;
^-------------------------------^

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Migrations.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Parameter Migrations.upgrade(address).new_address (../../share/contracts/Migrations.sol#20) is not in mixedCase
Variable Migrations.last_completed_migration (../../share/contracts/Migrations.sol#6) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) is declared view but contains assembly code
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) is declared view but contains assembly code
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) is declared view but contains assembly code
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) is declared view but contains assembly code
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) is declared view but contains assembly code
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#254)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#330)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-1
## INFO:Detectors:
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#322)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-2
## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	Event emitted after the call(s):
	- AllDataReceived(groupIndex,fromNodeIndex) (../../share/contracts/SkaleDKG.sol#245)
	- SuccessfulDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#255)
Reentrancy in SkaleDKG.complaint(bytes32,uint256,uint256) (../../share/contracts/SkaleDKG.sol#178-203):
	External calls:
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#196)
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#201)
	Event emitted after the call(s):
	- ComplaintSent(groupIndex,fromNodeIndex,toNodeIndex) (../../share/contracts/SkaleDKG.sol#190)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleDKG.broadcast(bytes32,uint256,bytes,bytes) (../../share/contracts/SkaleDKG.sol#136-176) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#157-163)
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#433-437)
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#704-707)
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#714-717)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#718-721)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#722-725)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#726-729)
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#772-775)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#800-803)
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#810-815)
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#824-831)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Different versions of Solidity is used in :
	- Version used: ['ABIEncoderV2', '^0.5.0']
	- ^0.5.0 (../../share/contracts/ContractManager.sol#20)
	- ^0.5.0 (../../share/contracts/Ownable.sol#1)
	- ^0.5.0 (../../share/contracts/Permissions.sol#20)
	- ^0.5.0 (../../share/contracts/SkaleDKG.sol#20)
	- ABIEncoderV2 (../../share/contracts/SkaleDKG.sol#21)
	- ^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#different-pragma-directives-are-used
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleDKG.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ECDH.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: ! groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i_scope_0]) && nodesData.isNodeActive(nodesWithFreeSpace[i_scope_0]) (../../share/contracts/SchainsFunctionalityInternal.sol#158)
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i]) || ! nodesData.isNodeActive(nodesWithFreeSpace[i]) (../../share/contracts/SchainsFunctionalityInternal.sol#150)
SchainsFunctionalityInternal.findSchainAtSchainsForNode(uint256,bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#172-181) has external calls inside a loop: ISchainsData(dataAddress).schainsForNodes(nodeIndex,i) == schainId (../../share/contracts/SchainsFunctionalityInternal.sol#176)
SchainsFunctionalityInternal.selectNodeToGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#188-209) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodeIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#203)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: groupsData.setException(groupIndex,node) (../../share/contracts/SchainsFunctionalityInternal.sol#239)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: schainsData.addSchainForNode(node,groupIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#240)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in SchainsFunctionalityInternal.createGroupForSchain(string,bytes32,uint256,uint8) (../../share/contracts/SchainsFunctionalityInternal.sol#61-77):
	External calls:
	- addGroup(schainId,numberOfNodes,bytes32(uint256(partOfNode))) (../../share/contracts/SchainsFunctionalityInternal.sol#68)
	- numberOfNodesInGroup = generateGroup(schainId) (../../share/contracts/SchainsFunctionalityInternal.sol#69)
	- ISchainsData(dataAddress).setSchainPartOfNode(schainId,partOfNode) (../../share/contracts/SchainsFunctionalityInternal.sol#70)
	Event emitted after the call(s):
	- SchainNodes(schainName,schainId,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#71-76)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251):
	External calls:
	- groupsData.setNodesInGroup(groupIndex,nodesInGroup) (../../share/contracts/SchainsFunctionalityInternal.sol#245)
	Event emitted after the call(s):
	- GroupGenerated(groupIndex,nodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#246-250)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionalityInternal.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external
## INFO:Detectors:
NodesData.isLeavingPeriodExpired(uint256) (../../share/contracts/NodesData.sol#368-370) uses timestamp for comparisons
	Dangerous comparisons:
	- block.timestamp - nodes[nodeIndex].leavingDate >= leavingPeriod (../../share/contracts/NodesData.sol#369)
NodesData.isTimeForReward(uint256) (../../share/contracts/NodesData.sol#377-380) uses timestamp for comparisons
	Dangerous comparisons:
	- nodes[nodeIndex].lastRewardDate + IConstants(constantsAddress).rewardPeriod() <= block.timestamp (../../share/contracts/NodesData.sol#379)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) is declared view but contains assembly code
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#141-144)
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#253-256)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleVerifier.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
addGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146)
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractReceiver.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsData.isTimeExpired(bytes32) (../../share/contracts/SchainsData.sol#291-293) uses timestamp for comparisons
	Dangerous comparisons:
	- schains[schainId].startDate + schains[schainId].lifetime < block.timestamp (../../share/contracts/SchainsData.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: schain = ISchainsData(schainsDataAddress).schainsAtSystem(i) (../../share/contracts/Pricing.sol#89)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: numberOfNodesInGroup = IGroupsData(schainsDataAddress).getNumberOfNodesInGroup(schain) (../../share/contracts/Pricing.sol#90)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: part = ISchainsData(schainsDataAddress).getSchainsPartOfNode(schain) (../../share/contracts/Pricing.sol#91)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Pricing.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ConstantsHolder.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) is declared view but contains assembly code
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Reentrancy in NodesFunctionality.completeWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#179-198):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeft(nodeIndex) (../../share/contracts/NodesFunctionality.sol#186)
	- INodesData(nodesDataAddress).removeNode(nodeIndex) (../../share/contracts/NodesFunctionality.sol#188)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeComplete(nodeIndex,from,IConstants(constantsAddress).NODE_DEPOSIT(),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#191-196)
Reentrancy in NodesFunctionality.createNode(address,uint256,bytes) (../../share/contracts/NodesFunctionality.sol#81-122):
	External calls:
	- nodeIndex = INodesData(nodesDataAddress).addNode(from,name,ip,publicIP,port,publicKey) (../../share/contracts/NodesFunctionality.sol#102-108)
	Event emitted after the call(s):
	- NodeCreated(nodeIndex,from,name,ip,publicIP,port,nonce,uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#112-121)
Reentrancy in NodesFunctionality.initWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#155-170):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeaving(nodeIndex) (../../share/contracts/NodesFunctionality.sol#161)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeInit(nodeIndex,from,uint32(block.timestamp),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#163-168)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#303-310)
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#326-330)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) is declared view but contains assembly code
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#31-34)
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#42-45)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Decryption.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ManagerData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IManagerData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) is declared view but contains assembly code
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: downtimeArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,0) (../../share/contracts/ValidatorsFunctionality.sol#186)
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: latencyArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,1) (../../share/contracts/ValidatorsFunctionality.sol#187)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setException(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#214)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#215)
ValidatorsFunctionality.generateGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#224-258) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,nodesInGroup[i]) (../../share/contracts/ValidatorsFunctionality.sol#250)
ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301) has external calls inside a loop: IValidatorsData(dataAddress).addValidatedNode(index,bytesParametersOfNodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in ValidatorsFunctionality.addValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#114-127):
	External calls:
	- addGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#119)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#120)
	Event emitted after the call(s):
	- ValidatorCreated(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#121-126)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in ValidatorsFunctionality.rotateNode(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#196-200):
	External calls:
	- newNodeIndexEvent = selectNodeToGroup(schainId) (../../share/contracts/ValidatorsFunctionality.sol#198)
	Event emitted after the call(s):
	- ValidatorRotated(schainId,newNodeIndexEvent) (../../share/contracts/ValidatorsFunctionality.sol#199)
Reentrancy in ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177):
	External calls:
	- IValidatorsData(dataAddress).removeValidatedNode(validatorIndex,index) (../../share/contracts/ValidatorsFunctionality.sol#165)
	- IValidatorsData(dataAddress).addVerdict(keccak256(bytes)(abi.encodePacked(toNodeIndex)),downtime,latency) (../../share/contracts/ValidatorsFunctionality.sol#169)
	Event emitted after the call(s):
	- VerdictWasSent(fromValidatorIndex,toNodeIndex,downtime,latency,receiveVerdict,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#171-176)
Reentrancy in ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301):
	External calls:
	- IGroupsData(dataAddress).setException(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#287)
	- indexOfNodesInGroup = generateGroup(groupIndex) (../../share/contracts/ValidatorsFunctionality.sol#288)
	Event emitted after the call(s):
	- ValidatorsArray(nodeIndex,groupIndex,indexOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#294-299)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reentrancy in ValidatorsFunctionality.upgradeValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#129-142):
	External calls:
	- upgradeGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#134)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#135)
	Event emitted after the call(s):
	- ValidatorUpgraded(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#136-141)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177) uses timestamp for comparisons
	Dangerous comparisons:
	- require(bool,string)(time <= block.timestamp,The time has not come to send verdict) (../../share/contracts/ValidatorsFunctionality.sol#163)
	- receiveVerdict = time + IConstants(constantsAddress).deltaPeriod() > uint32(block.timestamp) (../../share/contracts/ValidatorsFunctionality.sol#167)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#344-349)
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#362-368)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IValidatorsFunctionality.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#153-156)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#157-159)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#160)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#177-180)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#181-183)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#184)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in SchainsFunctionality.addSchain(address,uint256,bytes) (../../share/contracts/SchainsFunctionality.sol#90-119):
	External calls:
	- initializeSchainInSchainsData(schainParameters.name,from,deposit,schainParameters.lifetime) (../../share/contracts/SchainsFunctionality.sol#102-106)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).createGroupForSchain(schainParameters.name,keccak256(bytes)(abi.encodePacked(schainParameters.name)),numberOfNodes,partOfNode) (../../share/contracts/SchainsFunctionality.sol#113-114)
	Event emitted after the call(s):
	- SchainCreated(schainParameters.name,from,partOfNode,schainParameters.lifetime,numberOfNodes,deposit,schainParameters.nonce,keccak256(bytes)(abi.encodePacked(schainParameters.name)),uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionality.sol#116-118)
Reentrancy in SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#163)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#164)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#165)
Reentrancy in SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#187)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#189)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#190)
Reentrancy in SchainsFunctionality.restartSchainCreation(string) (../../share/contracts/SchainsFunctionality.sol#200-211):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInte/share/contracts/SkaleDKG.sol:21:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
pragma experimental ABIEncoderV2;
^-------------------------------^

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Migrations.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Parameter Migrations.upgrade(address).new_address (../../share/contracts/Migrations.sol#20) is not in mixedCase
Variable Migrations.last_completed_migration (../../share/contracts/Migrations.sol#6) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) is declared view but contains assembly code
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) is declared view but contains assembly code
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) is declared view but contains assembly code
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) is declared view but contains assembly code
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) is declared view but contains assembly code
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#254)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#330)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-1
## INFO:Detectors:
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#322)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-2
## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	Event emitted after the call(s):
	- AllDataReceived(groupIndex,fromNodeIndex) (../../share/contracts/SkaleDKG.sol#245)
	- SuccessfulDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#255)
Reentrancy in SkaleDKG.complaint(bytes32,uint256,uint256) (../../share/contracts/SkaleDKG.sol#178-203):
	External calls:
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#196)
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#201)
	Event emitted after the call(s):
	- ComplaintSent(groupIndex,fromNodeIndex,toNodeIndex) (../../share/contracts/SkaleDKG.sol#190)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleDKG.broadcast(bytes32,uint256,bytes,bytes) (../../share/contracts/SkaleDKG.sol#136-176) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#157-163)
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#433-437)
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#704-707)
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#714-717)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#718-721)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#722-725)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#726-729)
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#772-775)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#800-803)
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#810-815)
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#824-831)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Different versions of Solidity is used in :
	- Version used: ['ABIEncoderV2', '^0.5.0']
	- ^0.5.0 (../../share/contracts/ContractManager.sol#20)
	- ^0.5.0 (../../share/contracts/Ownable.sol#1)
	- ^0.5.0 (../../share/contracts/Permissions.sol#20)
	- ^0.5.0 (../../share/contracts/SkaleDKG.sol#20)
	- ABIEncoderV2 (../../share/contracts/SkaleDKG.sol#21)
	- ^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#different-pragma-directives-are-used
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleDKG.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ECDH.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: ! groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i_scope_0]) && nodesData.isNodeActive(nodesWithFreeSpace[i_scope_0]) (../../share/contracts/SchainsFunctionalityInternal.sol#158)
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i]) || ! nodesData.isNodeActive(nodesWithFreeSpace[i]) (../../share/contracts/SchainsFunctionalityInternal.sol#150)
SchainsFunctionalityInternal.findSchainAtSchainsForNode(uint256,bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#172-181) has external calls inside a loop: ISchainsData(dataAddress).schainsForNodes(nodeIndex,i) == schainId (../../share/contracts/SchainsFunctionalityInternal.sol#176)
SchainsFunctionalityInternal.selectNodeToGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#188-209) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodeIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#203)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: groupsData.setException(groupIndex,node) (../../share/contracts/SchainsFunctionalityInternal.sol#239)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: schainsData.addSchainForNode(node,groupIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#240)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in SchainsFunctionalityInternal.createGroupForSchain(string,bytes32,uint256,uint8) (../../share/contracts/SchainsFunctionalityInternal.sol#61-77):
	External calls:
	- addGroup(schainId,numberOfNodes,bytes32(uint256(partOfNode))) (../../share/contracts/SchainsFunctionalityInternal.sol#68)
	- numberOfNodesInGroup = generateGroup(schainId) (../../share/contracts/SchainsFunctionalityInternal.sol#69)
	- ISchainsData(dataAddress).setSchainPartOfNode(schainId,partOfNode) (../../share/contracts/SchainsFunctionalityInternal.sol#70)
	Event emitted after the call(s):
	- SchainNodes(schainName,schainId,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#71-76)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251):
	External calls:
	- groupsData.setNodesInGroup(groupIndex,nodesInGroup) (../../share/contracts/SchainsFunctionalityInternal.sol#245)
	Event emitted after the call(s):
	- GroupGenerated(groupIndex,nodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#246-250)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionalityInternal.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external
## INFO:Detectors:
NodesData.isLeavingPeriodExpired(uint256) (../../share/contracts/NodesData.sol#368-370) uses timestamp for comparisons
	Dangerous comparisons:
	- block.timestamp - nodes[nodeIndex].leavingDate >= leavingPeriod (../../share/contracts/NodesData.sol#369)
NodesData.isTimeForReward(uint256) (../../share/contracts/NodesData.sol#377-380) uses timestamp for comparisons
	Dangerous comparisons:
	- nodes[nodeIndex].lastRewardDate + IConstants(constantsAddress).rewardPeriod() <= block.timestamp (../../share/contracts/NodesData.sol#379)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) is declared view but contains assembly code
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#141-144)
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#253-256)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleVerifier.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
addGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146)
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractReceiver.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsData.isTimeExpired(bytes32) (../../share/contracts/SchainsData.sol#291-293) uses timestamp for comparisons
	Dangerous comparisons:
	- schains[schainId].startDate + schains[schainId].lifetime < block.timestamp (../../share/contracts/SchainsData.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: schain = ISchainsData(schainsDataAddress).schainsAtSystem(i) (../../share/contracts/Pricing.sol#89)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: numberOfNodesInGroup = IGroupsData(schainsDataAddress).getNumberOfNodesInGroup(schain) (../../share/contracts/Pricing.sol#90)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: part = ISchainsData(schainsDataAddress).getSchainsPartOfNode(schain) (../../share/contracts/Pricing.sol#91)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Pricing.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ConstantsHolder.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) is declared view but contains assembly code
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Reentrancy in NodesFunctionality.completeWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#179-198):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeft(nodeIndex) (../../share/contracts/NodesFunctionality.sol#186)
	- INodesData(nodesDataAddress).removeNode(nodeIndex) (../../share/contracts/NodesFunctionality.sol#188)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeComplete(nodeIndex,from,IConstants(constantsAddress).NODE_DEPOSIT(),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#191-196)
Reentrancy in NodesFunctionality.createNode(address,uint256,bytes) (../../share/contracts/NodesFunctionality.sol#81-122):
	External calls:
	- nodeIndex = INodesData(nodesDataAddress).addNode(from,name,ip,publicIP,port,publicKey) (../../share/contracts/NodesFunctionality.sol#102-108)
	Event emitted after the call(s):
	- NodeCreated(nodeIndex,from,name,ip,publicIP,port,nonce,uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#112-121)
Reentrancy in NodesFunctionality.initWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#155-170):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeaving(nodeIndex) (../../share/contracts/NodesFunctionality.sol#161)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeInit(nodeIndex,from,uint32(block.timestamp),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#163-168)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#303-310)
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#326-330)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) is declared view but contains assembly code
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#31-34)
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#42-45)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Decryption.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ManagerData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IManagerData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) is declared view but contains assembly code
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: downtimeArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,0) (../../share/contracts/ValidatorsFunctionality.sol#186)
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: latencyArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,1) (../../share/contracts/ValidatorsFunctionality.sol#187)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setException(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#214)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#215)
ValidatorsFunctionality.generateGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#224-258) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,nodesInGroup[i]) (../../share/contracts/ValidatorsFunctionality.sol#250)
ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301) has external calls inside a loop: IValidatorsData(dataAddress).addValidatedNode(index,bytesParametersOfNodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in ValidatorsFunctionality.addValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#114-127):
	External calls:
	- addGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#119)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#120)
	Event emitted after the call(s):
	- ValidatorCreated(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#121-126)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in ValidatorsFunctionality.rotateNode(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#196-200):
	External calls:
	- newNodeIndexEvent = selectNodeToGroup(schainId) (../../share/contracts/ValidatorsFunctionality.sol#198)
	Event emitted after the call(s):
	- ValidatorRotated(schainId,newNodeIndexEvent) (../../share/contracts/ValidatorsFunctionality.sol#199)
Reentrancy in ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177):
	External calls:
	- IValidatorsData(dataAddress).removeValidatedNode(validatorIndex,index) (../../share/contracts/ValidatorsFunctionality.sol#165)
	- IValidatorsData(dataAddress).addVerdict(keccak256(bytes)(abi.encodePacked(toNodeIndex)),downtime,latency) (../../share/contracts/ValidatorsFunctionality.sol#169)
	Event emitted after the call(s):
	- VerdictWasSent(fromValidatorIndex,toNodeIndex,downtime,latency,receiveVerdict,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#171-176)
Reentrancy in ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301):
	External calls:
	- IGroupsData(dataAddress).setException(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#287)
	- indexOfNodesInGroup = generateGroup(groupIndex) (../../share/contracts/ValidatorsFunctionality.sol#288)
	Event emitted after the call(s):
	- ValidatorsArray(nodeIndex,groupIndex,indexOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#294-299)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reentrancy in ValidatorsFunctionality.upgradeValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#129-142):
	External calls:
	- upgradeGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#134)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#135)
	Event emitted after the call(s):
	- ValidatorUpgraded(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#136-141)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177) uses timestamp for comparisons
	Dangerous comparisons:
	- require(bool,string)(time <= block.timestamp,The time has not come to send verdict) (../../share/contracts/ValidatorsFunctionality.sol#163)
	- receiveVerdict = time + IConstants(constantsAddress).deltaPeriod() > uint32(block.timestamp) (../../share/contracts/ValidatorsFunctionality.sol#167)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#344-349)
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#362-368)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IValidatorsFunctionality.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#153-156)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#157-159)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#160)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#177-180)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#181-183)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#184)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in SchainsFunctionality.addSchain(address,uint256,bytes) (../../share/contracts/SchainsFunctionality.sol#90-119):
	External calls:
	- initializeSchainInSchainsData(schainParameters.name,from,deposit,schainParameters.lifetime) (../../share/contracts/SchainsFunctionality.sol#102-106)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).createGroupForSchain(schainParameters.name,keccak256(bytes)(abi.encodePacked(schainParameters.name)),numberOfNodes,partOfNode) (../../share/contracts/SchainsFunctionality.sol#113-114)
	Event emitted after the call(s):
	- SchainCreated(schainParameters.name,from,partOfNode,schainParameters.lifetime,numberOfNodes,deposit,schainParameters.nonce,keccak256(bytes)(abi.encodePacked(schainParameters.name)),uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionality.sol#116-118)
Reentrancy in SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#163)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#164)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#165)
Reentrancy in SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#187)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#189)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#190)
Reentrancy in SchainsFunctionality.restartSchainCreation(string) (../../share/contracts/SchainsFunctionality.sol#200-211):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInte/share/contracts/SkaleDKG.sol:21:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
pragma experimental ABIEncoderV2;
^-------------------------------^

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Migrations.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Parameter Migrations.upgrade(address).new_address (../../share/contracts/Migrations.sol#20) is not in mixedCase
Variable Migrations.last_completed_migration (../../share/contracts/Migrations.sol#6) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) is declared view but contains assembly code
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) is declared view but contains assembly code
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) is declared view but contains assembly code
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) is declared view but contains assembly code
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) is declared view but contains assembly code
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#254)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#330)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-1
## INFO:Detectors:
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#322)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-2
## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	Event emitted after the call(s):
	- AllDataReceived(groupIndex,fromNodeIndex) (../../share/contracts/SkaleDKG.sol#245)
	- SuccessfulDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#255)
Reentrancy in SkaleDKG.complaint(bytes32,uint256,uint256) (../../share/contracts/SkaleDKG.sol#178-203):
	External calls:
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#196)
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#201)
	Event emitted after the call(s):
	- ComplaintSent(groupIndex,fromNodeIndex,toNodeIndex) (../../share/contracts/SkaleDKG.sol#190)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleDKG.broadcast(bytes32,uint256,bytes,bytes) (../../share/contracts/SkaleDKG.sol#136-176) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#157-163)
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#433-437)
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#704-707)
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#714-717)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#718-721)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#722-725)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#726-729)
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#772-775)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#800-803)
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#810-815)
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#824-831)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Different versions of Solidity is used in :
	- Version used: ['ABIEncoderV2', '^0.5.0']
	- ^0.5.0 (../../share/contracts/ContractManager.sol#20)
	- ^0.5.0 (../../share/contracts/Ownable.sol#1)
	- ^0.5.0 (../../share/contracts/Permissions.sol#20)
	- ^0.5.0 (../../share/contracts/SkaleDKG.sol#20)
	- ABIEncoderV2 (../../share/contracts/SkaleDKG.sol#21)
	- ^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#different-pragma-directives-are-used
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleDKG.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ECDH.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: ! groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i_scope_0]) && nodesData.isNodeActive(nodesWithFreeSpace[i_scope_0]) (../../share/contracts/SchainsFunctionalityInternal.sol#158)
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i]) || ! nodesData.isNodeActive(nodesWithFreeSpace[i]) (../../share/contracts/SchainsFunctionalityInternal.sol#150)
SchainsFunctionalityInternal.findSchainAtSchainsForNode(uint256,bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#172-181) has external calls inside a loop: ISchainsData(dataAddress).schainsForNodes(nodeIndex,i) == schainId (../../share/contracts/SchainsFunctionalityInternal.sol#176)
SchainsFunctionalityInternal.selectNodeToGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#188-209) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodeIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#203)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: groupsData.setException(groupIndex,node) (../../share/contracts/SchainsFunctionalityInternal.sol#239)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: schainsData.addSchainForNode(node,groupIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#240)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in SchainsFunctionalityInternal.createGroupForSchain(string,bytes32,uint256,uint8) (../../share/contracts/SchainsFunctionalityInternal.sol#61-77):
	External calls:
	- addGroup(schainId,numberOfNodes,bytes32(uint256(partOfNode))) (../../share/contracts/SchainsFunctionalityInternal.sol#68)
	- numberOfNodesInGroup = generateGroup(schainId) (../../share/contracts/SchainsFunctionalityInternal.sol#69)
	- ISchainsData(dataAddress).setSchainPartOfNode(schainId,partOfNode) (../../share/contracts/SchainsFunctionalityInternal.sol#70)
	Event emitted after the call(s):
	- SchainNodes(schainName,schainId,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#71-76)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251):
	External calls:
	- groupsData.setNodesInGroup(groupIndex,nodesInGroup) (../../share/contracts/SchainsFunctionalityInternal.sol#245)
	Event emitted after the call(s):
	- GroupGenerated(groupIndex,nodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#246-250)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionalityInternal.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external
## INFO:Detectors:
NodesData.isLeavingPeriodExpired(uint256) (../../share/contracts/NodesData.sol#368-370) uses timestamp for comparisons
	Dangerous comparisons:
	- block.timestamp - nodes[nodeIndex].leavingDate >= leavingPeriod (../../share/contracts/NodesData.sol#369)
NodesData.isTimeForReward(uint256) (../../share/contracts/NodesData.sol#377-380) uses timestamp for comparisons
	Dangerous comparisons:
	- nodes[nodeIndex].lastRewardDate + IConstants(constantsAddress).rewardPeriod() <= block.timestamp (../../share/contracts/NodesData.sol#379)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) is declared view but contains assembly code
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#141-144)
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#253-256)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleVerifier.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
addGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146)
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractReceiver.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsData.isTimeExpired(bytes32) (../../share/contracts/SchainsData.sol#291-293) uses timestamp for comparisons
	Dangerous comparisons:
	- schains[schainId].startDate + schains[schainId].lifetime < block.timestamp (../../share/contracts/SchainsData.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: schain = ISchainsData(schainsDataAddress).schainsAtSystem(i) (../../share/contracts/Pricing.sol#89)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: numberOfNodesInGroup = IGroupsData(schainsDataAddress).getNumberOfNodesInGroup(schain) (../../share/contracts/Pricing.sol#90)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: part = ISchainsData(schainsDataAddress).getSchainsPartOfNode(schain) (../../share/contracts/Pricing.sol#91)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Pricing.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ConstantsHolder.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) is declared view but contains assembly code
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Reentrancy in NodesFunctionality.completeWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#179-198):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeft(nodeIndex) (../../share/contracts/NodesFunctionality.sol#186)
	- INodesData(nodesDataAddress).removeNode(nodeIndex) (../../share/contracts/NodesFunctionality.sol#188)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeComplete(nodeIndex,from,IConstants(constantsAddress).NODE_DEPOSIT(),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#191-196)
Reentrancy in NodesFunctionality.createNode(address,uint256,bytes) (../../share/contracts/NodesFunctionality.sol#81-122):
	External calls:
	- nodeIndex = INodesData(nodesDataAddress).addNode(from,name,ip,publicIP,port,publicKey) (../../share/contracts/NodesFunctionality.sol#102-108)
	Event emitted after the call(s):
	- NodeCreated(nodeIndex,from,name,ip,publicIP,port,nonce,uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#112-121)
Reentrancy in NodesFunctionality.initWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#155-170):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeaving(nodeIndex) (../../share/contracts/NodesFunctionality.sol#161)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeInit(nodeIndex,from,uint32(block.timestamp),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#163-168)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#303-310)
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#326-330)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:/share/contracts/SkaleDKG.sol:21:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
pragma experimental ABIEncoderV2;
^-------------------------------^

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Migrations.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Parameter Migrations.upgrade(address).new_address (../../share/contracts/Migrations.sol#20) is not in mixedCase
Variable Migrations.last_completed_migration (../../share/contracts/Migrations.sol#6) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) is declared view but contains assembly code
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) is declared view but contains assembly code
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) is declared view but contains assembly code
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) is declared view but contains assembly code
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) is declared view but contains assembly code
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#254)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#330)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-1
## INFO:Detectors:
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#322)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-2
## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	Event emitted after the call(s):
	- AllDataReceived(groupIndex,fromNodeIndex) (../../share/contracts/SkaleDKG.sol#245)
	- SuccessfulDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#255)
Reentrancy in SkaleDKG.complaint(bytes32,uint256,uint256) (../../share/contracts/SkaleDKG.sol#178-203):
	External calls:
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#196)
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#201)
	Event emitted after the call(s):
	- ComplaintSent(groupIndex,fromNodeIndex,toNodeIndex) (../../share/contracts/SkaleDKG.sol#190)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleDKG.broadcast(bytes32,uint256,bytes,bytes) (../../share/contracts/SkaleDKG.sol#136-176) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#157-163)
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#433-437)
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#704-707)
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#714-717)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#718-721)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#722-725)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#726-729)
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#772-775)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#800-803)
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#810-815)
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#824-831)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Different versions of Solidity is used in :
	- Version used: ['ABIEncoderV2', '^0.5.0']
	- ^0.5.0 (../../share/contracts/ContractManager.sol#20)
	- ^0.5.0 (../../share/contracts/Ownable.sol#1)
	- ^0.5.0 (../../share/contracts/Permissions.sol#20)
	- ^0.5.0 (../../share/contracts/SkaleDKG.sol#20)
	- ABIEncoderV2 (../../share/contracts/SkaleDKG.sol#21)
	- ^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#different-pragma-directives-are-used
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleDKG.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ECDH.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: ! groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i_scope_0]) && nodesData.isNodeActive(nodesWithFreeSpace[i_scope_0]) (../../share/contracts/SchainsFunctionalityInternal.sol#158)
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i]) || ! nodesData.isNodeActive(nodesWithFreeSpace[i]) (../../share/contracts/SchainsFunctionalityInternal.sol#150)
SchainsFunctionalityInternal.findSchainAtSchainsForNode(uint256,bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#172-181) has external calls inside a loop: ISchainsData(dataAddress).schainsForNodes(nodeIndex,i) == schainId (../../share/contracts/SchainsFunctionalityInternal.sol#176)
SchainsFunctionalityInternal.selectNodeToGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#188-209) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodeIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#203)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: groupsData.setException(groupIndex,node) (../../share/contracts/SchainsFunctionalityInternal.sol#239)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: schainsData.addSchainForNode(node,groupIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#240)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in SchainsFunctionalityInternal.createGroupForSchain(string,bytes32,uint256,uint8) (../../share/contracts/SchainsFunctionalityInternal.sol#61-77):
	External calls:
	- addGroup(schainId,numberOfNodes,bytes32(uint256(partOfNode))) (../../share/contracts/SchainsFunctionalityInternal.sol#68)
	- numberOfNodesInGroup = generateGroup(schainId) (../../share/contracts/SchainsFunctionalityInternal.sol#69)
	- ISchainsData(dataAddress).setSchainPartOfNode(schainId,partOfNode) (../../share/contracts/SchainsFunctionalityInternal.sol#70)
	Event emitted after the call(s):
	- SchainNodes(schainName,schainId,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#71-76)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251):
	External calls:
	- groupsData.setNodesInGroup(groupIndex,nodesInGroup) (../../share/contracts/SchainsFunctionalityInternal.sol#245)
	Event emitted after the call(s):
	- GroupGenerated(groupIndex,nodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#246-250)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionalityInternal.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external
## INFO:Detectors:
NodesData.isLeavingPeriodExpired(uint256) (../../share/contracts/NodesData.sol#368-370) uses timestamp for comparisons
	Dangerous comparisons:
	- block.timestamp - nodes[nodeIndex].leavingDate >= leavingPeriod (../../share/contracts/NodesData.sol#369)
NodesData.isTimeForReward(uint256) (../../share/contracts/NodesData.sol#377-380) uses timestamp for comparisons
	Dangerous comparisons:
	- nodes[nodeIndex].lastRewardDate + IConstants(constantsAddress).rewardPeriod() <= block.timestamp (../../share/contracts/NodesData.sol#379)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) is declared view but contains assembly code
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#141-144)
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#253-256)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleVerifier.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
addGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146)
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractReceiver.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsData.isTimeExpired(bytes32) (../../share/contracts/SchainsData.sol#291-293) uses timestamp for comparisons
	Dangerous comparisons:
	- schains[schainId].startDate + schains[schainId].lifetime < block.timestamp (../../share/contracts/SchainsData.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: schain = ISchainsData(schainsDataAddress).schainsAtSystem(i) (../../share/contracts/Pricing.sol#89)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: numberOfNodesInGroup = IGroupsData(schainsDataAddress).getNumberOfNodesInGroup(schain) (../../share/contracts/Pricing.sol#90)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: part = ISchainsData(schainsDataAddress).getSchainsPartOfNode(schain) (../../share/contracts/Pricing.sol#91)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Pricing.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ConstantsHolder.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) is declared view but contains assembly code
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Reentrancy in NodesFunctionality.completeWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#179-198):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeft(nodeIndex) (../../share/contracts/NodesFunctionality.sol#186)
	- INodesData(nodesDataAddress).removeNode(nodeIndex) (../../share/contracts/NodesFunctionality.sol#188)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeComplete(nodeIndex,from,IConstants(constantsAddress).NODE_DEPOSIT(),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#191-196)
Reentrancy in NodesFunctionality.createNode(address,uint256,bytes) (../../share/contracts/NodesFunctionality.sol#81-122):
	External calls:
	- nodeIndex = INodesData(nodesDataAddress).addNode(from,name,ip,publicIP,port,publicKey) (../../share/contracts/NodesFunctionality.sol#102-108)
	Event emitted after the call(s):
	- NodeCreated(nodeIndex,from,name,ip,publicIP,port,nonce,uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#112-121)
Reentrancy in NodesFunctionality.initWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#155-170):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeaving(nodeIndex) (../../share/contracts/NodesFunctionality.sol#161)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeInit(nodeIndex,from,uint32(block.timestamp),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#163-168)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#303-310)
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#326-330)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) is declared view but contains assembly code
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#31-34)
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#42-45)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Decryption.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ManagerData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IManagerData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) is declared view but contains assembly code
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: downtimeArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,0) (../../share/contracts/ValidatorsFunctionality.sol#186)
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: latencyArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,1) (../../share/contracts/ValidatorsFunctionality.sol#187)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setException(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#214)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#215)
ValidatorsFunctionality.generateGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#224-258) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,nodesInGroup[i]) (../../share/contracts/ValidatorsFunctionality.sol#250)
ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301) has external calls inside a loop: IValidatorsData(dataAddress).addValidatedNode(index,bytesParametersOfNodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in ValidatorsFunctionality.addValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#114-127):
	External calls:
	- addGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#119)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#120)
	Event emitted after the call(s):
	- ValidatorCreated(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#121-126)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in ValidatorsFunctionality.rotateNode(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#196-200):
	External calls:
	- newNodeIndexEvent = selectNodeToGroup(schainId) (../../share/contracts/ValidatorsFunctionality.sol#198)
	Event emitted after the call(s):
	- ValidatorRotated(schainId,newNodeIndexEvent) (../../share/contracts/ValidatorsFunctionality.sol#199)
Reentrancy in ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177):
	External calls:
	- IValidatorsData(dataAddress).removeValidatedNode(validatorIndex,index) (../../share/contracts/ValidatorsFunctionality.sol#165)
	- IValidatorsData(dataAddress).addVerdict(keccak256(bytes)(abi.encodePacked(toNodeIndex)),downtime,latency) (../../share/contracts/ValidatorsFunctionality.sol#169)
	Event emitted after the call(s):
	- VerdictWasSent(fromValidatorIndex,toNodeIndex,downtime,latency,receiveVerdict,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#171-176)
Reentrancy in ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301):
	External calls:
	- IGroupsData(dataAddress).setException(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#287)
	- indexOfNodesInGroup = generateGroup(groupIndex) (../../share/contracts/ValidatorsFunctionality.sol#288)
	Event emitted after the call(s):
	- ValidatorsArray(nodeIndex,groupIndex,indexOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#294-299)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reentrancy in ValidatorsFunctionality.upgradeValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#129-142):
	External calls:
	- upgradeGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#134)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#135)
	Event emitted after the call(s):
	- ValidatorUpgraded(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#136-141)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177) uses timestamp for comparisons
	Dangerous comparisons:
	- require(bool,string)(time <= block.timestamp,The time has not come to send verdict) (../../share/contracts/ValidatorsFunctionality.sol#163)
	- receiveVerdict = time + IConstants(constantsAddress).deltaPeriod() > uint32(block.timestamp) (../../share/contracts/ValidatorsFunctionality.sol#167)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#344-349)
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#362-368)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IValidatorsFunctionality.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#153-156)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#157-159)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#160)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#177-180)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#181-183)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#184)
Reference: https://github.com/crytic/slither/wiki/Detector/share/contracts/SkaleDKG.sol:21:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
pragma experimental ABIEncoderV2;
^-------------------------------^

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Migrations.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Parameter Migrations.upgrade(address).new_address (../../share/contracts/Migrations.sol#20) is not in mixedCase
Variable Migrations.last_completed_migration (../../share/contracts/Migrations.sol#6) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) is declared view but contains assembly code
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) is declared view but contains assembly code
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) is declared view but contains assembly code
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) is declared view but contains assembly code
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) is declared view but contains assembly code
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#254)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#330)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-1
## INFO:Detectors:
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#322)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-2
## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	Event emitted after the call(s):
	- AllDataReceived(groupIndex,fromNodeIndex) (../../share/contracts/SkaleDKG.sol#245)
	- SuccessfulDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#255)
Reentrancy in SkaleDKG.complaint(bytes32,uint256,uint256) (../../share/contracts/SkaleDKG.sol#178-203):
	External calls:
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#196)
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#201)
	Event emitted after the call(s):
	- ComplaintSent(groupIndex,fromNodeIndex,toNodeIndex) (../../share/contracts/SkaleDKG.sol#190)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleDKG.broadcast(bytes32,uint256,bytes,bytes) (../../share/contracts/SkaleDKG.sol#136-176) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#157-163)
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#433-437)
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#704-707)
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#714-717)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#718-721)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#722-725)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#726-729)
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#772-775)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#800-803)
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#810-815)
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#824-831)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Different versions of Solidity is used in :
	- Version used: ['ABIEncoderV2', '^0.5.0']
	- ^0.5.0 (../../share/contracts/ContractManager.sol#20)
	- ^0.5.0 (../../share/contracts/Ownable.sol#1)
	- ^0.5.0 (../../share/contracts/Permissions.sol#20)
	- ^0.5.0 (../../share/contracts/SkaleDKG.sol#20)
	- ABIEncoderV2 (../../share/contracts/SkaleDKG.sol#21)
	- ^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#different-pragma-directives-are-used
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleDKG.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ECDH.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: ! groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i_scope_0]) && nodesData.isNodeActive(nodesWithFreeSpace[i_scope_0]) (../../share/contracts/SchainsFunctionalityInternal.sol#158)
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i]) || ! nodesData.isNodeActive(nodesWithFreeSpace[i]) (../../share/contracts/SchainsFunctionalityInternal.sol#150)
SchainsFunctionalityInternal.findSchainAtSchainsForNode(uint256,bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#172-181) has external calls inside a loop: ISchainsData(dataAddress).schainsForNodes(nodeIndex,i) == schainId (../../share/contracts/SchainsFunctionalityInternal.sol#176)
SchainsFunctionalityInternal.selectNodeToGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#188-209) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodeIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#203)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: groupsData.setException(groupIndex,node) (../../share/contracts/SchainsFunctionalityInternal.sol#239)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: schainsData.addSchainForNode(node,groupIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#240)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in SchainsFunctionalityInternal.createGroupForSchain(string,bytes32,uint256,uint8) (../../share/contracts/SchainsFunctionalityInternal.sol#61-77):
	External calls:
	- addGroup(schainId,numberOfNodes,bytes32(uint256(partOfNode))) (../../share/contracts/SchainsFunctionalityInternal.sol#68)
	- numberOfNodesInGroup = generateGroup(schainId) (../../share/contracts/SchainsFunctionalityInternal.sol#69)
	- ISchainsData(dataAddress).setSchainPartOfNode(schainId,partOfNode) (../../share/contracts/SchainsFunctionalityInternal.sol#70)
	Event emitted after the call(s):
	- SchainNodes(schainName,schainId,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#71-76)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251):
	External calls:
	- groupsData.setNodesInGroup(groupIndex,nodesInGroup) (../../share/contracts/SchainsFunctionalityInternal.sol#245)
	Event emitted after the call(s):
	- GroupGenerated(groupIndex,nodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#246-250)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionalityInternal.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external
## INFO:Detectors:
NodesData.isLeavingPeriodExpired(uint256) (../../share/contracts/NodesData.sol#368-370) uses timestamp for comparisons
	Dangerous comparisons:
	- block.timestamp - nodes[nodeIndex].leavingDate >= leavingPeriod (../../share/contracts/NodesData.sol#369)
NodesData.isTimeForReward(uint256) (../../share/contracts/NodesData.sol#377-380) uses timestamp for comparisons
	Dangerous comparisons:
	- nodes[nodeIndex].lastRewardDate + IConstants(constantsAddress).rewardPeriod() <= block.timestamp (../../share/contracts/NodesData.sol#379)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) is declared view but contains assembly code
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#141-144)
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#253-256)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleVerifier.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
addGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146)
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractReceiver.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsData.isTimeExpired(bytes32) (../../share/contracts/SchainsData.sol#291-293) uses timestamp for comparisons
	Dangerous comparisons:
	- schains[schainId].startDate + schains[schainId].lifetime < block.timestamp (../../share/contracts/SchainsData.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: schain = ISchainsData(schainsDataAddress).schainsAtSystem(i) (../../share/contracts/Pricing.sol#89)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: numberOfNodesInGroup = IGroupsData(schainsDataAddress).getNumberOfNodesInGroup(schain) (../../share/contracts/Pricing.sol#90)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: part = ISchainsData(schainsDataAddress).getSchainsPartOfNode(schain) (../../share/contracts/Pricing.sol#91)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Pricing.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ConstantsHolder.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) is declared view but contains assembly code
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Reentrancy in NodesFunctionality.completeWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#179-198):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeft(nodeIndex) (../../share/contracts/NodesFunctionality.sol#186)
	- INodesData(nodesDataAddress).removeNode(nodeIndex) (../../share/contracts/NodesFunctionality.sol#188)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeComplete(nodeIndex,from,IConstants(constantsAddress).NODE_DEPOSIT(),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#191-196)
Reentrancy in NodesFunctionality.createNode(address,uint256,bytes) (../../share/contracts/NodesFunctionality.sol#81-122):
	External calls:
	- nodeIndex = INodesData(nodesDataAddress).addNode(from,name,ip,publicIP,port,publicKey) (../../share/contracts/NodesFunctionality.sol#102-108)
	Event emitted after the call(s):
	- NodeCreated(nodeIndex,from,name,ip,publicIP,port,nonce,uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#112-121)
Reentrancy in NodesFunctionality.initWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#155-170):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeaving(nodeIndex) (../../share/contracts/NodesFunctionality.sol#161)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeInit(nodeIndex,from,uint32(block.timestamp),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#163-168)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#303-310)
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#326-330)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) is declared view but contains assembly code
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#31-34)
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#42-45)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Decryption.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ManagerData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IManagerData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) is declared view but contains assembly code
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: downtimeArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,0) (../../share/contracts/ValidatorsFunctionality.sol#186)
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: latencyArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,1) (../../share/contracts/ValidatorsFunctionality.sol#187)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setException(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#214)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#215)
ValidatorsFunctionality.generateGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#224-258) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,nodesInGroup[i]) (../../share/contracts/ValidatorsFunctionality.sol#250)
ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301) has external calls inside a loop: IValidatorsData(dataAddress).addValidatedNode(index,bytesParametersOfNodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in ValidatorsFunctionality.addValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#114-127):
	External calls:
	- addGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#119)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#120)
	Event emitted after the call(s):
	- ValidatorCreated(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#121-126)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in ValidatorsFunctionality.rotateNode(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#196-200):
	External calls:
	- newNodeIndexEvent = selectNodeToGroup(schainId) (../../share/contracts/ValidatorsFunctionality.sol#198)
	Event emitted after the call(s):
	- ValidatorRotated(schainId,newNodeIndexEvent) (../../share/contracts/ValidatorsFunctionality.sol#199)
Reentrancy in ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177):
	External calls:
	- IValidatorsData(dataAddress).removeValidatedNode(validatorIndex,index) (../../share/contracts/ValidatorsFunctionality.sol#165)
	- IValidatorsData(dataAddress).addVerdict(keccak256(bytes)(abi.encodePacked(toNodeIndex)),downtime,latency) (../../share/contracts/ValidatorsFunctionality.sol#169)
	Event emitted after the call(s):
	- VerdictWasSent(fromValidatorIndex,toNodeIndex,downtime,latency,receiveVerdict,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#171-176)
Reentrancy in ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301):
	External calls:
	- IGroupsData(dataAddress).setException(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#287)
	- indexOfNodesInGroup = generateGroup(groupIndex) (../../share/contracts/ValidatorsFunctionality.sol#288)
	Event emitted after the call(s):
	- ValidatorsArray(nodeIndex,groupIndex,indexOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#294-299)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reentrancy in ValidatorsFunctionality.upgradeValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#129-142):
	External calls:
	- upgradeGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#134)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#135)
	Event emitted after the call(s):
	- ValidatorUpgraded(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#136-141)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177) uses timestamp for comparisons
	Dangerous comparisons:
	- require(bool,string)(time <= block.timestamp,The time has not come to send verdict) (../../share/contracts/ValidatorsFunctionality.sol#163)
	- receiveVerdict = time + IConstants(constantsAddress).deltaPeriod() > uint32(block.timestamp) (../../share/contracts/ValidatorsFunctionality.sol#167)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#344-349)
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#362-368)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IValidatorsFunctionality.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN(/share/contracts/SkaleDKG.sol:21:1: Warning: Experimental features are turned on. Do not use experimental features on live deployments.
pragma experimental ABIEncoderV2;
^-------------------------------^

## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Migrations.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Parameter Migrations.upgrade(address).new_address (../../share/contracts/Migrations.sol#20) is not in mixedCase
Variable Migrations.last_completed_migration (../../share/contracts/Migrations.sol#6) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) is declared view but contains assembly code
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) is declared view but contains assembly code
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) is declared view but contains assembly code
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) is declared view but contains assembly code
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) is declared view but contains assembly code
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#254)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#330)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-1
## INFO:Detectors:
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	State variables written after the call(s):
	- SkaleDKG.channels (../../share/contracts/SkaleDKG.sol#84) in delete channels[groupIndex] (../../share/contracts/SkaleDKG.sol#322)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-2
## INFO:Detectors:
Reentrancy in SkaleDKG.allright(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#233-257):
	External calls:
	- IGroupsData(channels[groupIndex].dataAddress).setPublicKey(groupIndex,channels[groupIndex].publicKeyx.x,channels[groupIndex].publicKeyx.y,channels[groupIndex].publicKeyy.x,channels[groupIndex].publicKeyy.y) (../../share/contracts/SkaleDKG.sol#247-253)
	Event emitted after the call(s):
	- AllDataReceived(groupIndex,fromNodeIndex) (../../share/contracts/SkaleDKG.sol#245)
	- SuccessfulDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#255)
Reentrancy in SkaleDKG.complaint(bytes32,uint256,uint256) (../../share/contracts/SkaleDKG.sol#178-203):
	External calls:
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#196)
	- finalizeSlashing(groupIndex,channels[groupIndex].nodeToComplaint) (../../share/contracts/SkaleDKG.sol#201)
	Event emitted after the call(s):
	- ComplaintSent(groupIndex,fromNodeIndex,toNodeIndex) (../../share/contracts/SkaleDKG.sol#190)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
Reentrancy in SkaleDKG.finalizeSlashing(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#309-332):
	External calls:
	- newNode = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#317-320)
	- this.openChannel(groupIndex) (../../share/contracts/SkaleDKG.sol#323)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).excludeNodeFromSchain(badNode,groupIndex) (../../share/contracts/SkaleDKG.sol#325-328)
	- IGroupsData(channels[groupIndex].dataAddress).setGroupFailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#329)
	Event emitted after the call(s):
	- BadGuy(badNode) (../../share/contracts/SkaleDKG.sol#314)
	- FailedDKG(groupIndex) (../../share/contracts/SkaleDKG.sol#315)
	- NewGuy(newNode) (../../share/contracts/SkaleDKG.sol#321)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleDKG.broadcast(bytes32,uint256,bytes,bytes) (../../share/contracts/SkaleDKG.sol#136-176) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#157-163)
SkaleDKG.decryptMessage(bytes32,uint256) (../../share/contracts/SkaleDKG.sol#423-439) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#433-437)
SkaleDKG.bigModExp(uint256,uint256) (../../share/contracts/SkaleDKG.sol#694-709) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#704-707)
SkaleDKG.loop(uint256,bytes,uint256) (../../share/contracts/SkaleDKG.sol#711-735) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#714-717)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#718-721)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#722-725)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#726-729)
SkaleDKG.checkCorrectMultipliedShare(bytes,uint256) (../../share/contracts/SkaleDKG.sol#762-805) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#772-775)
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#800-803)
SkaleDKG.bytesToPublicKey(bytes) (../../share/contracts/SkaleDKG.sol#807-817) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#810-815)
SkaleDKG.bytesToG2(bytes) (../../share/contracts/SkaleDKG.sol#819-833) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleDKG.sol#824-831)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Different versions of Solidity is used in :
	- Version used: ['ABIEncoderV2', '^0.5.0']
	- ^0.5.0 (../../share/contracts/ContractManager.sol#20)
	- ^0.5.0 (../../share/contracts/Ownable.sol#1)
	- ^0.5.0 (../../share/contracts/Permissions.sol#20)
	- ^0.5.0 (../../share/contracts/SkaleDKG.sol#20)
	- ABIEncoderV2 (../../share/contracts/SkaleDKG.sol#21)
	- ^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1)
	- ^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#different-pragma-directives-are-used
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleDKG.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ECDH.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: ! groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i_scope_0]) && nodesData.isNodeActive(nodesWithFreeSpace[i_scope_0]) (../../share/contracts/SchainsFunctionalityInternal.sol#158)
SchainsFunctionalityInternal.isEnoughNodes(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#143-164) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodesWithFreeSpace[i]) || ! nodesData.isNodeActive(nodesWithFreeSpace[i]) (../../share/contracts/SchainsFunctionalityInternal.sol#150)
SchainsFunctionalityInternal.findSchainAtSchainsForNode(uint256,bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#172-181) has external calls inside a loop: ISchainsData(dataAddress).schainsForNodes(nodeIndex,i) == schainId (../../share/contracts/SchainsFunctionalityInternal.sol#176)
SchainsFunctionalityInternal.selectNodeToGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#188-209) has external calls inside a loop: groupsData.isExceptionNode(groupIndex,nodeIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#203)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: groupsData.setException(groupIndex,node) (../../share/contracts/SchainsFunctionalityInternal.sol#239)
SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251) has external calls inside a loop: schainsData.addSchainForNode(node,groupIndex) (../../share/contracts/SchainsFunctionalityInternal.sol#240)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in SchainsFunctionalityInternal.createGroupForSchain(string,bytes32,uint256,uint8) (../../share/contracts/SchainsFunctionalityInternal.sol#61-77):
	External calls:
	- addGroup(schainId,numberOfNodes,bytes32(uint256(partOfNode))) (../../share/contracts/SchainsFunctionalityInternal.sol#68)
	- numberOfNodesInGroup = generateGroup(schainId) (../../share/contracts/SchainsFunctionalityInternal.sol#69)
	- ISchainsData(dataAddress).setSchainPartOfNode(schainId,partOfNode) (../../share/contracts/SchainsFunctionalityInternal.sol#70)
	Event emitted after the call(s):
	- SchainNodes(schainName,schainId,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#71-76)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in SchainsFunctionalityInternal.generateGroup(bytes32) (../../share/contracts/SchainsFunctionalityInternal.sol#215-251):
	External calls:
	- groupsData.setNodesInGroup(groupIndex,nodesInGroup) (../../share/contracts/SchainsFunctionalityInternal.sol#245)
	Event emitted after the call(s):
	- GroupGenerated(groupIndex,nodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionalityInternal.sol#246-250)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionalityInternal.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external
## INFO:Detectors:
NodesData.isLeavingPeriodExpired(uint256) (../../share/contracts/NodesData.sol#368-370) uses timestamp for comparisons
	Dangerous comparisons:
	- block.timestamp - nodes[nodeIndex].leavingDate >= leavingPeriod (../../share/contracts/NodesData.sol#369)
NodesData.isTimeForReward(uint256) (../../share/contracts/NodesData.sol#377-380) uses timestamp for comparisons
	Dangerous comparisons:
	- nodes[nodeIndex].lastRewardDate + IConstants(constantsAddress).rewardPeriod() <= block.timestamp (../../share/contracts/NodesData.sol#379)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) is declared view but contains assembly code
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SkaleVerifier.verify(uint256,uint256,bytes32,uint256,uint256,uint256,uint256,uint256,uint256,uint256) (../../share/contracts/SkaleVerifier.sol#90-146) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#141-144)
SkaleVerifier.bigModExp(uint256,uint256) (../../share/contracts/SkaleVerifier.sol#243-258) uses assembly
	- INLINE ASM None (../../share/contracts/SkaleVerifier.sol#253-256)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SkaleVerifier.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
addGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146)
deleteGroup(bytes32) should be declared external:
	- GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159)
upgradeGroup(bytes32,uint256,bytes32) should be declared external:
	- GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractReceiver.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
SchainsData.isTimeExpired(bytes32) (../../share/contracts/SchainsData.sol#291-293) uses timestamp for comparisons
	Dangerous comparisons:
	- schains[schainId].startDate + schains[schainId].lifetime < block.timestamp (../../share/contracts/SchainsData.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: schain = ISchainsData(schainsDataAddress).schainsAtSystem(i) (../../share/contracts/Pricing.sol#89)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: numberOfNodesInGroup = IGroupsData(schainsDataAddress).getNumberOfNodesInGroup(schain) (../../share/contracts/Pricing.sol#90)
Pricing.getTotalLoadPercentage() (../../share/contracts/Pricing.sol#82-95) has external calls inside a loop: part = ISchainsData(schainsDataAddress).getSchainsPartOfNode(schain) (../../share/contracts/Pricing.sol#91)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Pricing.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ConstantsHolder.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) is declared view but contains assembly code
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Reentrancy in NodesFunctionality.completeWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#179-198):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeft(nodeIndex) (../../share/contracts/NodesFunctionality.sol#186)
	- INodesData(nodesDataAddress).removeNode(nodeIndex) (../../share/contracts/NodesFunctionality.sol#188)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeComplete(nodeIndex,from,IConstants(constantsAddress).NODE_DEPOSIT(),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#191-196)
Reentrancy in NodesFunctionality.createNode(address,uint256,bytes) (../../share/contracts/NodesFunctionality.sol#81-122):
	External calls:
	- nodeIndex = INodesData(nodesDataAddress).addNode(from,name,ip,publicIP,port,publicKey) (../../share/contracts/NodesFunctionality.sol#102-108)
	Event emitted after the call(s):
	- NodeCreated(nodeIndex,from,name,ip,publicIP,port,nonce,uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#112-121)
Reentrancy in NodesFunctionality.initWithdrawDeposit(address,uint256) (../../share/contracts/NodesFunctionality.sol#155-170):
	External calls:
	- INodesData(nodesDataAddress).setNodeLeaving(nodeIndex) (../../share/contracts/NodesFunctionality.sol#161)
	Event emitted after the call(s):
	- WithdrawDepositFromNodeInit(nodeIndex,from,uint32(block.timestamp),uint32(block.timestamp),gasleft()()) (../../share/contracts/NodesFunctionality.sol#163-168)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
NodesFunctionality.fallbackDataConverter(bytes) (../../share/contracts/NodesFunctionality.sol#292-311) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#303-310)
NodesFunctionality.fallbackDataConverterPublicKeyAndName(bytes) (../../share/contracts/NodesFunctionality.sol#319-343) uses assembly
	- INLINE ASM None (../../share/contracts/NodesFunctionality.sol#326-330)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/NodesFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) is declared view but contains assembly code
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#31-34)
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#42-45)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Decryption.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ManagerData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IManagerData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) is declared view but contains assembly code
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: downtimeArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,0) (../../share/contracts/ValidatorsFunctionality.sol#186)
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: latencyArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,1) (../../share/contracts/ValidatorsFunctionality.sol#187)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setException(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#214)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#215)
ValidatorsFunctionality.generateGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#224-258) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,nodesInGroup[i]) (../../share/contracts/ValidatorsFunctionality.sol#250)
ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301) has external calls inside a loop: IValidatorsData(dataAddress).addValidatedNode(index,bytesParametersOfNodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in ValidatorsFunctionality.addValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#114-127):
	External calls:
	- addGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#119)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#120)
	Event emitted after the call(s):
	- ValidatorCreated(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#121-126)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in ValidatorsFunctionality.rotateNode(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#196-200):
	External calls:
	- newNodeIndexEvent = selectNodeToGroup(schainId) (../../share/contracts/ValidatorsFunctionality.sol#198)
	Event emitted after the call(s):
	- ValidatorRotated(schainId,newNodeIndexEvent) (../../share/contracts/ValidatorsFunctionality.sol#199)
Reentrancy in ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177):
	External calls:
	- IValidatorsData(dataAddress).removeValidatedNode(validatorIndex,index) (../../share/contracts/ValidatorsFunctionality.sol#165)
	- IValidatorsData(dataAddress).addVerdict(keccak256(bytes)(abi.encodePacked(toNodeIndex)),downtime,latency) (../../share/contracts/ValidatorsFunctionality.sol#169)
	Event emitted after the call(s):
	- VerdictWasSent(fromValidatorIndex,toNodeIndex,downtime,latency,receiveVerdict,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#171-176)
Reentrancy in ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301):
	External calls:
	- IGroupsData(dataAddress).setException(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#287)
	- indexOfNodesInGroup = generateGroup(groupIndex) (../../share/contracts/ValidatorsFunctionality.sol#288)
	Event emitted after the call(s):
	- ValidatorsArray(nodeIndex,groupIndex,indexOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#294-299)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reentrancy in ValidatorsFunctionality.upgradeValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#129-142):
	External calls:
	- upgradeGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#134)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#135)
	Event emitted after the call(s):
	- ValidatorUpgraded(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#136-141)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177) uses timestamp for comparisons
	Dangerous comparisons:
	- require(bool,string)(time <= block.timestamp,The time has not come to send verdict) (../../share/contracts/ValidatorsFunctionality.sol#163)
	- receiveVerdict = time + IConstants(constantsAddress).deltaPeriod() > uint32(block.timestamp) (../../share/contracts/ValidatorsFunctionality.sol#167)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#344-349)
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#362-368)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IValidatorsFunctionality.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#153-156)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#157-159)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#160)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#177-180)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#181-183)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#184)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in SchainsFunctionality.addSchain(address,uint256,bytes) (../../share/contracts/SchainsFunctionality.sol#90-119):
	External calls:
	- initializeSchainInSchainsData(schainParameters.name,from,deposit,schainParameters.lifetime) (../../share/contracts/SchainsFunctionality.sol#102-106)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).createGroupForSchain(schainParameters.name,keccak256(bytes)(abi.encodePacked(schainParameters.name)),numberOfNodes,partOfNode) (../../share/contracts/SchainsFunctionality.sol#113-114)
	Event emitted after the call(s):
	- SchainCreated(schainParameters.name,from,partOfNode,schainParameters.lifetime,numberOfNodes,deposit,schainParameters.nonce,keccak256(bytes)(abi.encodePacked(schainParameters.name)),uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionality.sol#116-118)
Reentrancy in SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#163)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#164)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#165)
Reentrancy in SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#187)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#189)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#190)
Reentrancy in SchainsFunctionality.restartSchainCreation(string) (../../share/contracts/SchainsFunctionality.sol#200-211):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).selectNewNode(schainId) (../../share/contracts/SchainsFunctionality.sol#209)
	Event emitted after the call(s):
	- NodeAdded(schainId,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#210)
Reentrancy in SchainsFunctionality.rotateNode(uint256,bytes32) (../../share/contracts/SchainsFunctionality.sol#193-198):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(nodeIndex,schainId) (../../share/contracts/SchainsFunctionality.sol#196)
	Event emitted after the call(s):
	- NodeRotated(schainId,nodeIndex,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#197)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) uses assembly
	- INLINE ASM None (../../share/contracts/SchainsFunctionality.sol#273-278)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
INFO:Slither:/share/contracts analyzed (114 contracts with 40 detectors), 302 result(s) found
(../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#153-156)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#157-159)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#160)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#177-180)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#181-183)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#184)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in SchainsFunctionality.addSchain(address,uint256,bytes) (../../share/contracts/SchainsFunctionality.sol#90-119):
	External calls:
	- initializeSchainInSchainsData(schainParameters.name,from,deposit,schainParameters.lifetime) (../../share/contracts/SchainsFunctionality.sol#102-106)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).createGroupForSchain(schainParameters.name,keccak256(bytes)(abi.encodePacked(schainParameters.name)),numberOfNodes,partOfNode) (../../share/contracts/SchainsFunctionality.sol#113-114)
	Event emitted after the call(s):
	- SchainCreated(schainParameters.name,from,partOfNode,schainParameters.lifetime,numberOfNodes,deposit,schainParameters.nonce,keccak256(bytes)(abi.encodePacked(schainParameters.name)),uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionality.sol#116-118)
Reentrancy in SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#163)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#164)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#165)
Reentrancy in SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#187)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#189)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#190)
Reentrancy in SchainsFunctionality.restartSchainCreation(string) (../../share/contracts/SchainsFunctionality.sol#200-211):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).selectNewNode(schainId) (../../share/contracts/SchainsFunctionality.sol#209)
	Event emitted after the call(s):
	- NodeAdded(schainId,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#210)
Reentrancy in SchainsFunctionality.rotateNode(uint256,bytes32) (../../share/contracts/SchainsFunctionality.sol#193-198):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(nodeIndex,schainId) (../../share/contracts/SchainsFunctionality.sol#196)
	Event emitted after the call(s):
	- NodeRotated(schainId,nodeIndex,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#197)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) uses assembly
	- INLINE ASM None (../../share/contracts/SchainsFunctionality.sol#273-278)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
INFO:Slither:/share/contracts analyzed (114 contracts with 40 detectors), 302 result(s) found
-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in SchainsFunctionality.addSchain(address,uint256,bytes) (../../share/contracts/SchainsFunctionality.sol#90-119):
	External calls:
	- initializeSchainInSchainsData(schainParameters.name,from,deposit,schainParameters.lifetime) (../../share/contracts/SchainsFunctionality.sol#102-106)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).createGroupForSchain(schainParameters.name,keccak256(bytes)(abi.encodePacked(schainParameters.name)),numberOfNodes,partOfNode) (../../share/contracts/SchainsFunctionality.sol#113-114)
	Event emitted after the call(s):
	- SchainCreated(schainParameters.name,from,partOfNode,schainParameters.lifetime,numberOfNodes,deposit,schainParameters.nonce,keccak256(bytes)(abi.encodePacked(schainParameters.name)),uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionality.sol#116-118)
Reentrancy in SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#163)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#164)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#165)
Reentrancy in SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#187)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#189)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#190)
Reentrancy in SchainsFunctionality.restartSchainCreation(string) (../../share/contracts/SchainsFunctionality.sol#200-211):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).selectNewNode(schainId) (../../share/contracts/SchainsFunctionality.sol#209)
	Event emitted after the call(s):
	- NodeAdded(schainId,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#210)
Reentrancy in SchainsFunctionality.rotateNode(uint256,bytes32) (../../share/contracts/SchainsFunctionality.sol#193-198):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(nodeIndex,schainId) (../../share/contracts/SchainsFunctionality.sol#196)
	Event emitted after the call(s):
	- NodeRotated(schainId,nodeIndex,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#197)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) uses assembly
	- INLINE ASM None (../../share/contracts/SchainsFunctionality.sol#273-278)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
INFO:Slither:/share/contracts analyzed (114 contracts with 40 detectors), 302 result(s) found

Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) is declared view but contains assembly code
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
Decryption.encrypt(uint256,bytes32) (../../share/contracts/Decryption.sol#25-34) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#31-34)
Decryption.decrypt(bytes32,bytes32) (../../share/contracts/Decryption.sol#36-46) uses assembly
	- INLINE ASM None (../../share/contracts/Decryption.sol#42-45)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/Decryption.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ManagerData.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IManagerData.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) is declared view but contains assembly code
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: downtimeArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,0) (../../share/contracts/ValidatorsFunctionality.sol#186)
ValidatorsFunctionality.calculateMetrics(uint256) (../../share/contracts/ValidatorsFunctionality.sol#179-194) has external calls inside a loop: latencyArray[i] = IValidatorsData(dataAddress).verdicts(validatorIndex,i,1) (../../share/contracts/ValidatorsFunctionality.sol#187)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setException(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#214)
ValidatorsFunctionality.selectNodeToGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#202-222) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,indexOfNode) (../../share/contracts/ValidatorsFunctionality.sol#215)
ValidatorsFunctionality.generateGroup(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#224-258) has external calls inside a loop: IGroupsData(dataAddress).setNodeInGroup(groupIndex,nodesInGroup[i]) (../../share/contracts/ValidatorsFunctionality.sol#250)
ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301) has external calls inside a loop: IValidatorsData(dataAddress).addValidatedNode(index,bytesParametersOfNodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#292)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in GroupsFunctionality.addGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#138-146):
	External calls:
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#140)
	Event emitted after the call(s):
	- GroupAdded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#141-145)
Reentrancy in ValidatorsFunctionality.addValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#114-127):
	External calls:
	- addGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#119)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#120)
	Event emitted after the call(s):
	- ValidatorCreated(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#121-126)
Reentrancy in GroupsFunctionality.deleteGroup(bytes32) (../../share/contracts/GroupsFunctionality.sol#153-159):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#156)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#157)
	Event emitted after the call(s):
	- GroupDeleted(groupIndex,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#158)
Reentrancy in ValidatorsFunctionality.rotateNode(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#196-200):
	External calls:
	- newNodeIndexEvent = selectNodeToGroup(schainId) (../../share/contracts/ValidatorsFunctionality.sol#198)
	Event emitted after the call(s):
	- ValidatorRotated(schainId,newNodeIndexEvent) (../../share/contracts/ValidatorsFunctionality.sol#199)
Reentrancy in ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177):
	External calls:
	- IValidatorsData(dataAddress).removeValidatedNode(validatorIndex,index) (../../share/contracts/ValidatorsFunctionality.sol#165)
	- IValidatorsData(dataAddress).addVerdict(keccak256(bytes)(abi.encodePacked(toNodeIndex)),downtime,latency) (../../share/contracts/ValidatorsFunctionality.sol#169)
	Event emitted after the call(s):
	- VerdictWasSent(fromValidatorIndex,toNodeIndex,downtime,latency,receiveVerdict,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#171-176)
Reentrancy in ValidatorsFunctionality.setValidators(bytes32,uint256) (../../share/contracts/ValidatorsFunctionality.sol#285-301):
	External calls:
	- IGroupsData(dataAddress).setException(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#287)
	- indexOfNodesInGroup = generateGroup(groupIndex) (../../share/contracts/ValidatorsFunctionality.sol#288)
	Event emitted after the call(s):
	- ValidatorsArray(nodeIndex,groupIndex,indexOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#294-299)
Reentrancy in GroupsFunctionality.upgradeGroup(bytes32,uint256,bytes32) (../../share/contracts/GroupsFunctionality.sol#168-179):
	External calls:
	- IGroupsData(groupsDataAddress).removeGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#171)
	- IGroupsData(groupsDataAddress).removeAllNodesInGroup(groupIndex) (../../share/contracts/GroupsFunctionality.sol#172)
	- IGroupsData(groupsDataAddress).addGroup(groupIndex,newRecommendedNumberOfNodes,data) (../../share/contracts/GroupsFunctionality.sol#173)
	Event emitted after the call(s):
	- GroupUpgraded(groupIndex,data,uint32(block.timestamp),gasleft()()) (../../share/contracts/GroupsFunctionality.sol#174-178)
Reentrancy in ValidatorsFunctionality.upgradeValidator(uint256) (../../share/contracts/ValidatorsFunctionality.sol#129-142):
	External calls:
	- upgradeGroup(groupIndex,possibleNumberOfNodes,bytes32(nodeIndex)) (../../share/contracts/ValidatorsFunctionality.sol#134)
	- numberOfNodesInGroup = setValidators(groupIndex,nodeIndex) (../../share/contracts/ValidatorsFunctionality.sol#135)
	Event emitted after the call(s):
	- ValidatorUpgraded(nodeIndex,groupIndex,numberOfNodesInGroup,uint32(block.timestamp),gasleft()()) (../../share/contracts/ValidatorsFunctionality.sol#136-141)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ValidatorsFunctionality.sendVerdict(uint256,uint256,uint32,uint32) (../../share/contracts/ValidatorsFunctionality.sol#152-177) uses timestamp for comparisons
	Dangerous comparisons:
	- require(bool,string)(time <= block.timestamp,The time has not come to send verdict) (../../share/contracts/ValidatorsFunctionality.sol#163)
	- receiveVerdict = time + IConstants(constantsAddress).deltaPeriod() > uint32(block.timestamp) (../../share/contracts/ValidatorsFunctionality.sol#167)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#block-timestamp
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
ValidatorsFunctionality.getDataFromBytes(bytes32) (../../share/contracts/ValidatorsFunctionality.sol#340-351) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#344-349)
ValidatorsFunctionality.getDataToBytes(uint256) (../../share/contracts/ValidatorsFunctionality.sol#353-368) uses assembly
	- INLINE ASM None (../../share/contracts/ValidatorsFunctionality.sol#362-368)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/GroupsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/ValidatorsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IValidatorsFunctionality.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) is declared view but contains assembly code
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#constant-functions-changing-the-state
## INFO:Detectors:
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#153-156)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#157-159)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#160)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#177-180)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#181-183)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#184)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in SchainsFunctionality.addSchain(address,uint256,bytes) (../../share/contracts/SchainsFunctionality.sol#90-119):
	External calls:
	- initializeSchainInSchainsData(schainParameters.name,from,deposit,schainParameters.lifetime) (../../share/contracts/SchainsFunctionality.sol#102-106)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).createGroupForSchain(schainParameters.name,keccak256(bytes)(abi.encodePacked(schainParameters.name)),numberOfNodes,partOfNode) (../../share/contracts/SchainsFunctionality.sol#113-114)
	Event emitted after the call(s):
	- SchainCreated(schainParameters.name,from,partOfNode,schainParameters.lifetime,numberOfNodes,deposit,schainParameters.nonce,keccak256(bytes)(abi.encodePacked(schainParameters.name)),uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionality.sol#116-118)
Reentrancy in SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#163)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#164)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#165)
Reentrancy in SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#187)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#189)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#190)
Reentrancy in SchainsFunctionality.restartSchainCreation(string) (../../share/contracts/SchainsFunctionality.sol#200-211):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).selectNewNode(schainId) (../../share/contracts/SchainsFunctionality.sol#209)
	Event emitted after the call(s):
	- NodeAdded(schainId,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#210)
Reentrancy in SchainsFunctionality.rotateNode(uint256,bytes32) (../../share/contracts/SchainsFunctionality.sol#193-198):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(nodeIndex,schainId) (../../share/contracts/SchainsFunctionality.sol#196)
	Event emitted after the call(s):
	- NodeRotated(schainId,nodeIndex,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#197)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) uses assembly
	- INLINE ASM None (../../share/contracts/SchainsFunctionality.sol#273-278)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
INFO:Slither:/share/contracts analyzed (114 contracts with 40 detectors), 302 result(s) found
rnalAddress).selectNewNode(schainId) (../../share/contracts/SchainsFunctionality.sol#209)
	Event emitted after the call(s):
	- NodeAdded(schainId,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#210)
Reentrancy in SchainsFunctionality.rotateNode(uint256,bytes32) (../../share/contracts/SchainsFunctionality.sol#193-198):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(nodeIndex,schainId) (../../share/contracts/SchainsFunctionality.sol#196)
	Event emitted after the call(s):
	- NodeRotated(schainId,nodeIndex,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#197)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) uses assembly
	- INLINE ASM None (../../share/contracts/SchainsFunctionality.sol#273-278)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
INFO:Slither:/share/contracts analyzed (114 contracts with 40 detectors), 302 result(s) found
rnalAddress).selectNewNode(schainId) (../../share/contracts/SchainsFunctionality.sol#209)
	Event emitted after the call(s):
	- NodeAdded(schainId,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#210)
Reentrancy in SchainsFunctionality.rotateNode(uint256,bytes32) (../../share/contracts/SchainsFunctionality.sol#193-198):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(nodeIndex,schainId) (../../share/contracts/SchainsFunctionality.sol#196)
	Event emitted after the call(s):
	- NodeRotated(schainId,nodeIndex,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#197)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) uses assembly
	- INLINE ASM None (../../share/contracts/SchainsFunctionality.sol#273-278)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
INFO:Slither:/share/contracts analyzed (114 contracts with 40 detectors), 302 result(s) found
eGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#187)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#189)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#190)
Reentrancy in SchainsFunctionality.restartSchainCreation(string) (../../share/contracts/SchainsFunctionality.sol#200-211):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).selectNewNode(schainId) (../../share/contracts/SchainsFunctionality.sol#209)
	Event emitted after the call(s):
	- NodeAdded(schainId,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#210)
Reentrancy in SchainsFunctionality.rotateNode(uint256,bytes32) (../../share/contracts/SchainsFunctionality.sol#193-198):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(nodeIndex,schainId) (../../share/contracts/SchainsFunctionality.sol#196)
	Event emitted after the call(s):
	- NodeRotated(schainId,nodeIndex,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#197)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) uses assembly
	- INLINE ASM None (../../share/contracts/SchainsFunctionality.sol#273-278)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
INFO:Slither:/share/contracts analyzed (114 contracts with 40 detectors), 302 result(s) found
ctionality.sol#142-166) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#153-156)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#157-159)
SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#160)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: schainIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).findSchainAtSchainsForNode(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#177-180)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: require(bool,string)(schainIndex < ISchainsData(dataAddress).getLengthOfSchainsForNode(nodesInGroup[i]),Some Node does not contain given Schain) (../../share/contracts/SchainsFunctionality.sol#181-183)
SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191) has external calls inside a loop: ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).removeNodeFromSchain(nodesInGroup[i],schainId) (../../share/contracts/SchainsFunctionality.sol#184)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation/#calls-inside-a-loop
## INFO:Detectors:
Reentrancy in SchainsFunctionality.addSchain(address,uint256,bytes) (../../share/contracts/SchainsFunctionality.sol#90-119):
	External calls:
	- initializeSchainInSchainsData(schainParameters.name,from,deposit,schainParameters.lifetime) (../../share/contracts/SchainsFunctionality.sol#102-106)
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).createGroupForSchain(schainParameters.name,keccak256(bytes)(abi.encodePacked(schainParameters.name)),numberOfNodes,partOfNode) (../../share/contracts/SchainsFunctionality.sol#113-114)
	Event emitted after the call(s):
	- SchainCreated(schainParameters.name,from,partOfNode,schainParameters.lifetime,numberOfNodes,deposit,schainParameters.nonce,keccak256(bytes)(abi.encodePacked(schainParameters.name)),uint32(block.timestamp),gasleft()()) (../../share/contracts/SchainsFunctionality.sol#116-118)
Reentrancy in SchainsFunctionality.deleteSchain(address,string) (../../share/contracts/SchainsFunctionality.sol#142-166):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#163)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#164)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#165)
Reentrancy in SchainsFunctionality.deleteSchainByRoot(string) (../../share/contracts/SchainsFunctionality.sol#168-191):
	External calls:
	- ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).deleteGroup(schainId) (../../share/contracts/SchainsFunctionality.sol#187)
	- ISchainsData(dataAddress).removeSchain(schainId,from) (../../share/contracts/SchainsFunctionality.sol#189)
	Event emitted after the call(s):
	- SchainDeleted(from,name,schainId) (../../share/contracts/SchainsFunctionality.sol#190)
Reentrancy in SchainsFunctionality.restartSchainCreation(string) (../../share/contracts/SchainsFunctionality.sol#200-211):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).selectNewNode(schainId) (../../share/contracts/SchainsFunctionality.sol#209)
	Event emitted after the call(s):
	- NodeAdded(schainId,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#210)
Reentrancy in SchainsFunctionality.rotateNode(uint256,bytes32) (../../share/contracts/SchainsFunctionality.sol#193-198):
	External calls:
	- newNodeIndex = ISchainsFunctionalityInternal(schainsFunctionalityInternalAddress).replaceNode(nodeIndex,schainId) (../../share/contracts/SchainsFunctionality.sol#196)
	Event emitted after the call(s):
	- NodeRotated(schainId,nodeIndex,newNodeIndex) (../../share/contracts/SchainsFunctionality.sol#197)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
## INFO:Detectors:
ContractManager.setContractsAddress(string,address) (../../share/contracts/ContractManager.sol#42-58) uses assembly
	- INLINE ASM None (../../share/contracts/ContractManager.sol#50-54)
SchainsFunctionality.fallbackSchainParametersDataConverter(bytes) (../../share/contracts/SchainsFunctionality.sol#266-285) uses assembly
	- INLINE ASM None (../../share/contracts/SchainsFunctionality.sol#273-278)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage
## INFO:Detectors:
Pragma version^0.5.0 (../../share/contracts/ContractManager.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/Ownable.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/Permissions.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/SchainsFunctionality.sol#20) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IConstants.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/IGroupsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/INodesData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsData.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionality.sol#1) allows old versions
Pragma version^0.5.0 (../../share/contracts/interfaces/ISchainsFunctionalityInternal.sol#1) allows old versions
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Function IConstants.NODE_DEPOSIT() (../../share/contracts/interfaces/IConstants.sol#8) is not in mixedCase
Function IConstants.FRACTIONAL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#9) is not in mixedCase
Function IConstants.FULL_FACTOR() (../../share/contracts/interfaces/IConstants.sol#10) is not in mixedCase
Function IConstants.SECONDS_TO_DAY() (../../share/contracts/interfaces/IConstants.sol#11) is not in mixedCase
Function IConstants.SECONDS_TO_YEAR() (../../share/contracts/interfaces/IConstants.sol#12) is not in mixedCase
Function IConstants.MEDIUM_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#13) is not in mixedCase
Function IConstants.TINY_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#14) is not in mixedCase
Function IConstants.SMALL_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#15) is not in mixedCase
Function IConstants.MEDIUM_TEST_DIVISOR() (../../share/contracts/interfaces/IConstants.sol#16) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#17) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#18) is not in mixedCase
Function IConstants.NUMBER_OF_NODES_FOR_MEDIUM_TEST_SCHAIN() (../../share/contracts/interfaces/IConstants.sol#19) is not in mixedCase
Function IConstants.SIX_YEARS() (../../share/contracts/interfaces/IConstants.sol#27) is not in mixedCase
Function IConstants.NUMBER_OF_VALIDATORS() (../../share/contracts/interfaces/IConstants.sol#28) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
INFO:Slither:/share/contracts analyzed (114 contracts with 40 detectors), 302 result(s) found
