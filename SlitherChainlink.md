# Slither over ChainLink
Results of running slither on chainlink.sol

## Compilation warnings/errors 
/share/chainlink.sol:123:5: Warning: Use of the "var" keyword is deprecated.
    var _allowance = allowed[_from][msg.sender];

/share/chainlink.sol:231:3: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
  function LinkToken()

/share/chainlink.sol:88:5: Warning: Invoking events without "emit" prefix is deprecated.
    Transfer(msg.sender, _to, _value);

/share/chainlink.sol:131:5: Warning: Invoking events without "emit" prefix is deprecated.
    Transfer(_from, _to, _value);

/share/chainlink.sol:142:5: Warning: Invoking events without "emit" prefix is deprecated.
    Approval(msg.sender, _spender, _value);

/share/chainlink.sol:165:5: Warning: Invoking events without "emit" prefix is deprecated.
    Approval(msg.sender, _spender, allowed[msg.sender][_spender]);

/share/chainlink.sol:177:5: Warning: Invoking events without "emit" prefix is deprecated.
    Approval(msg.sender, _spender, allowed[msg.sender][_spender]);

/share/chainlink.sol:196:5: Warning: Invoking events without "emit" prefix is deprecated.
    Transfer(msg.sender, _to, _value, _data);

/share/chainlink.sol:46:3: Warning: No visibility specified. Defaulting to "public". 
  function balanceOf(address who) constant returns (uint256);

/share/chainlink.sol:47:3: Warning: No visibility specified. Defaulting to "public". 
  function transfer(address to, uint256 value) returns (bool);

/share/chainlink.sol:55:3: Warning: No visibility specified. Defaulting to "public". 
  function allowance(address owner, address spender) constant returns (uint256);

/share/chainlink.sol:56:3: Warning: No visibility specified. Defaulting to "public". 
  function transferFrom(address from, address to, uint256 value) returns (bool);

/share/chainlink.sol:57:3: Warning: No visibility specified. Defaulting to "public". 
  function approve(address spender, uint256 value) returns (bool);

/share/chainlink.sol:62:3: Warning: No visibility specified. Defaulting to "public". 
  function transferAndCall(address to, uint value, bytes data) returns (bool success);

/share/chainlink.sol:68:3: Warning: No visibility specified. Defaulting to "public". 
  function onTokenTransfer(address _sender, uint _value, bytes _data);

/share/chainlink.sol:85:3: Warning: No visibility specified. Defaulting to "public". 
  function transfer(address _to, uint256 _value) returns (bool) {

/share/chainlink.sol:97:3: Warning: No visibility specified. Defaulting to "public". 
  function balanceOf(address _owner) constant returns (uint256 balance) {

/share/chainlink.sol:122:3: Warning: No visibility specified. Defaulting to "public". 
  function transferFrom(address _from, address _to, uint256 _value) returns (bool) {

/share/chainlink.sol:140:3: Warning: No visibility specified. Defaulting to "public". 
  function approve(address _spender, uint256 _value) returns (bool) {

/share/chainlink.sol:152:3: Warning: No visibility specified. Defaulting to "public". 
  function allowance(address _owner, address _spender) constant returns (uint256 remaining) {

/share/chainlink.sol:162:3: Warning: No visibility specified. Defaulting to "public". 
  function increaseApproval (address _spender, uint _addedValue) 

/share/chainlink.sol:169:3: Warning: No visibility specified. Defaulting to "public". 
  function decreaseApproval (address _spender, uint _subtractedValue) 

/share/chainlink.sol:13:3: Warning: Function state mutability can be restricted to pure
  function mul(uint256 a, uint256 b) internal constant returns (uint256) {

/share/chainlink.sol:19:3: Warning: Function state mutability can be restricted to pure
  function div(uint256 a, uint256 b) internal constant returns (uint256) {

/share/chainlink.sol:26:3: Warning: Function state mutability can be restricted to pure
  function sub(uint256 a, uint256 b) internal constant returns (uint256) {

/share/chainlink.sol:31:3: Warning: Function state mutability can be restricted to pure
  function add(uint256 a, uint256 b) internal constant returns (uint256) {

/share/chainlink.sol:213:3: Warning: Function state mutability can be restricted to view
  function isContract(address _addr)


## INFO:Detectors:
LinkToken.totalSupply (../../share/chainlink.sol#226) shadows:
	- ERC20Basic.totalSupply (../../share/chainlink.sol#45)
	
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#state-variable-shadowing-from-abstract-contracts

## INFO:Detectors:
Reentrancy in ERC677Token.transferAndCall(address,uint256,bytes) (../../share/chainlink.sol#191-201):
	External calls:
	- contractFallback(_to,_value,_data) (../../share/chainlink.sol#198)
	Event emitted after the call(s):
	- Transfer(msg.sender,_to,_value,_data) (../../share/chainlink.sol#196)
	
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3

## INFO:Detectors:
ERC677Token.isContract(address) (../../share/chainlink.sol#213-220) uses assembly
	- INLINE ASM None (../../share/chainlink.sol#218-219)
	
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#assembly-usage

## INFO:Detectors:
Pragma version^0.4.16 (../../share/chainlink.sol#5) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Parameter BasicToken.transfer(address,uint256)._to (../../share/chainlink.sol#85) is not in mixedCase

Parameter BasicToken.transfer(address,uint256)._value (../../share/chainlink.sol#85) is not in mixedCase

Parameter BasicToken.balanceOf(address)._owner (../../share/chainlink.sol#97) is not in mixedCase

Parameter StandardToken.transferFrom(address,address,uint256)._from (../../share/chainlink.sol#122) is not in mixedCase

Parameter StandardToken.transferFrom(address,address,uint256)._to (../../share/chainlink.sol#122) is not in mixedCase

Parameter StandardToken.transferFrom(address,address,uint256)._value (../../share/chainlink.sol#122) is not in mixedCase

Parameter StandardToken.approve(address,uint256)._spender (../../share/chainlink.sol#140) is not in mixedCase

Parameter StandardToken.approve(address,uint256)._value (../../share/chainlink.sol#140) is not in mixedCase

Parameter StandardToken.allowance(address,address)._owner (../../share/chainlink.sol#152) is not in mixedCase

Parameter StandardToken.allowance(address,address)._spender (../../share/chainlink.sol#152) is not in mixedCase

Parameter StandardToken.increaseApproval(address,uint256)._spender (../../share/chainlink.sol#162) is not in mixedCase

Parameter StandardToken.increaseApproval(address,uint256)._addedValue (../../share/chainlink.sol#162) is not in mixedCase

Parameter StandardToken.decreaseApproval(address,uint256)._spender (../../share/chainlink.sol#169) is not in mixedCase

Parameter StandardToken.decreaseApproval(address,uint256)._subtractedValue (../../share/chainlink.sol#169) is not in 
mixedCase

Parameter ERC677Token.transferAndCall(address,uint256,bytes)._to (../../share/chainlink.sol#191) is not in mixedCase

Parameter ERC677Token.transferAndCall(address,uint256,bytes)._value (../../share/chainlink.sol#191) is not in mixedCase

Parameter ERC677Token.transferAndCall(address,uint256,bytes)._data (../../share/chainlink.sol#191) is not in mixedCase

Parameter ERC677Token.contractFallback(address,uint256,bytes)._to (../../share/chainlink.sol#206) is not in mixedCase

Parameter ERC677Token.contractFallback(address,uint256,bytes)._value (../../share/chainlink.sol#206) is not in mixedCase

Parameter ERC677Token.contractFallback(address,uint256,bytes)._data (../../share/chainlink.sol#206) is not in mixedCase

Parameter LinkToken.transferAndCall(address,uint256,bytes)._to (../../share/chainlink.sol#243) is not in mixedCase

Parameter LinkToken.transferAndCall(address,uint256,bytes)._value (../../share/chainlink.sol#243) is not in mixedCase

Parameter LinkToken.transferAndCall(address,uint256,bytes)._data (../../share/chainlink.sol#243) is not in mixedCase

Parameter LinkToken.transfer(address,uint256)._to (../../share/chainlink.sol#256) is not in mixedCase

Parameter LinkToken.transfer(address,uint256)._value (../../share/chainlink.sol#256) is not in mixedCase

Parameter LinkToken.approve(address,uint256)._spender (../../share/chainlink.sol#269) is not in mixedCase

Parameter LinkToken.approve(address,uint256)._value (../../share/chainlink.sol#269) is not in mixedCase

Parameter LinkToken.transferFrom(address,address,uint256)._from (../../share/chainlink.sol#283) is not in mixedCase

Parameter LinkToken.transferFrom(address,address,uint256)._to (../../share/chainlink.sol#283) is not in mixedCase

Parameter LinkToken.transferFrom(address,address,uint256)._value (../../share/chainlink.sol#283) is not in mixedCase

Constant LinkToken.totalSupply (../../share/chainlink.sol#226) is not in UPPER_CASE_WITH_UNDERSCORES

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

## INFO:Detectors:
ERC20Basic.totalSupply (../../share/chainlink.sol#45) should be constant

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#state-variables-that-could-be-declared-constant

## INFO:Detectors:
balanceOf(address) should be declared external:
	- BasicToken.balanceOf(address) (../../share/chainlink.sol#97-99)
	- ERC20Basic.balanceOf(address) (../../share/chainlink.sol#46)

allowance(address,address) should be declared external:
	- StandardToken.allowance(address,address) (../../share/chainlink.sol#152-154)
	- ERC20.allowance(address,address) (../../share/chainlink.sol#55)

onTokenTransfer(address,uint256,bytes) should be declared external:
	- ERC677Receiver.onTokenTransfer(address,uint256,bytes) (../../share/chainlink.sol#68)

increaseApproval(address,uint256) should be declared external:
	- StandardToken.increaseApproval(address,uint256) (../../share/chainlink.sol#162-167)

decreaseApproval(address,uint256) should be declared external:
	- StandardToken.decreaseApproval(address,uint256) (../../share/chainlink.sol#169-179)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external

analyzed (9 contracts with 40 detectors), 41 result(s) found
