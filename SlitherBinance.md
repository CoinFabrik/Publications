# Slither over Binance
Results of running slither on bnb.sol

/share/bnb.sol:37:7: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
      throw;

/share/bnb.sol:66:5: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function BNB(

/share/bnb.sol:82:25: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
        if (_to == 0x0) throw;                               // Prevent transfer to 0x0 address. Use burn() instead

/share/bnb.sol:83:20: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
		if (_value <= 0) throw; 

/share/bnb.sol:84:45: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
        if (balanceOf[msg.sender] < _value) throw;           // Check if the sender has enough

/share/bnb.sol:85:55: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
        if (balanceOf[_to] + _value < balanceOf[_to]) throw; // Check for overflows

/share/bnb.sol:94:20: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
		if (_value <= 0) throw; 

/share/bnb.sol:102:25: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
        if (_to == 0x0) throw;                                // Prevent transfer to 0x0 address. Use burn() instead

/share/bnb.sol:103:20: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
		if (_value <= 0) throw; 

/share/bnb.sol:104:40: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
        if (balanceOf[_from] < _value) throw;                 // Check if the sender has enough

/share/bnb.sol:105:55: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
        if (balanceOf[_to] + _value < balanceOf[_to]) throw;  // Check for overflows

/share/bnb.sol:106:52: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
        if (_value > allowance[_from][msg.sender]) throw;     // Check allowance

/share/bnb.sol:115:45: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
        if (balanceOf[msg.sender] < _value) throw;            // Check if the sender has enough

/share/bnb.sol:116:20: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
		if (_value <= 0) throw; 

/share/bnb.sol:124:45: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
        if (balanceOf[msg.sender] < _value) throw;            // Check if the sender has enough

/share/bnb.sol:125:20: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
		if (_value <= 0) throw; 

/share/bnb.sol:133:44: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
        if (freezeOf[msg.sender] < _value) throw;            // Check if the sender has enough

/share/bnb.sol:134:20: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
		if (_value <= 0) throw; 

/share/bnb.sol:143:26: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
		if(msg.sender != owner)throw;

/share/bnb.sol:35:3: Warning: This declaration shadows a builtin symbol.
  function assert(bool assertion) internal {

/share/bnb.sol:88:9: Warning: Invoking events without "emit" prefix is deprecated.
        Transfer(msg.sender, _to, _value);                   // Notify anyone listening that this transfer took place

/share/bnb.sol:110:9: Warning: Invoking events without "emit" prefix is deprecated.
        Transfer(_from, _to, _value);

/share/bnb.sol:119:9: Warning: Invoking events without "emit" prefix is deprecated.
        Burn(msg.sender, _value);

/share/bnb.sol:128:9: Warning: Invoking events without "emit" prefix is deprecated.
        Freeze(msg.sender, _value);

/share/bnb.sol:137:9: Warning: Invoking events without "emit" prefix is deprecated.
        Unfreeze(msg.sender, _value);

/share/bnb.sol:66:5: Warning: No visibility specified. Defaulting to "public". 
    function BNB(

/share/bnb.sol:81:5: Warning: No visibility specified. Defaulting to "public". 
    function transfer(address _to, uint256 _value) {

/share/bnb.sol:92:5: Warning: No visibility specified. Defaulting to "public". 
    function approve(address _spender, uint256 _value)

/share/bnb.sol:101:5: Warning: No visibility specified. Defaulting to "public". 
    function transferFrom(address _from, address _to, uint256 _value) returns (bool success) {

/share/bnb.sol:114:5: Warning: No visibility specified. Defaulting to "public". 
    function burn(uint256 _value) returns (bool success) {

/share/bnb.sol:123:2: Warning: No visibility specified. Defaulting to "public". 
	function freeze(uint256 _value) returns (bool success) {

/share/bnb.sol:132:2: Warning: No visibility specified. Defaulting to "public". 
	function unfreeze(uint256 _value) returns (bool success) {

/share/bnb.sol:142:2: Warning: No visibility specified. Defaulting to "public". 
	function withdrawEther(uint256 amount) {

/share/bnb.sol:148:2: Warning: No visibility specified. Defaulting to "public". 
	function() payable {

/share/bnb.sol:35:3: Warning: Function state mutability can be restricted to pure
  function assert(bool assertion) internal {
  
## INFO:Detectors:
BNB (../../share/bnb.sol#41-150) has incorrect ERC20 function interface:BNB.transfer(address,uint256) (../../share/bnb.sol#81-89)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-erc20-interface

## INFO:Detectors:
SafeMath.assert(bool) (../../share/bnb.sol#35-39) (function) shadows built-in symbol"

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#builtin-symbol-shadowing

## INFO:Detectors:
Deprecated standard detected THROW None (../../share/bnb.sol#37):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#82):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#83):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#84):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#85):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#94):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#102):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#103):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#104):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#105):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#106):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#115):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#116):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#124):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#125):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#133):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#134):
	- Usage of "throw" should be replaced with "revert()"
	
Deprecated standard detected THROW None (../../share/bnb.sol#143):
	- Usage of "throw" should be replaced with "revert()"	

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#deprecated-standards

## INFO:Detectors:
Pragma version^0.4.8 (../../share/bnb.sol#5) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

## INFO:Detectors:
Parameter BNB.transfer(address,uint256)._to (../../share/bnb.sol#81) is not in mixedCase

Parameter BNB.transfer(address,uint256)._value (../../share/bnb.sol#81) is not in mixedCase

Parameter BNB.approve(address,uint256)._spender (../../share/bnb.sol#92) is not in mixedCase

Parameter BNB.approve(address,uint256)._value (../../share/bnb.sol#92) is not in mixedCase

Parameter BNB.transferFrom(address,address,uint256)._from (../../share/bnb.sol#101) is not in mixedCase

Parameter BNB.transferFrom(address,address,uint256)._to (../../share/bnb.sol#101) is not in mixedCase

Parameter BNB.transferFrom(address,address,uint256)._value (../../share/bnb.sol#101) is not in mixedCase

Parameter BNB.burn(uint256)._value (../../share/bnb.sol#114) is not in mixedCase

Parameter BNB.freeze(uint256)._value (../../share/bnb.sol#123) is not in mixedCase

Parameter BNB.unfreeze(uint256)._value (../../share/bnb.sol#132) is not in mixedCase

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

## INFO:Detectors:
transfer(address,uint256) should be declared external:
	- BNB.transfer(address,uint256) (../../share/bnb.sol#81-89)
	
approve(address,uint256) should be declared external:
	- BNB.approve(address,uint256) (../../share/bnb.sol#92-97)
	
transferFrom(address,address,uint256) should be declared external:
	- BNB.transferFrom(address,address,uint256) (../../share/bnb.sol#101-112)
	
burn(uint256) should be declared external:
	- BNB.burn(uint256) (../../share/bnb.sol#114-121)
	
freeze(uint256) should be declared external:
	- BNB.freeze(uint256) (../../share/bnb.sol#123-130)
	
unfreeze(uint256) should be declared external:
	- BNB.unfreeze(uint256) (../../share/bnb.sol#132-139)
	
withdrawEther(uint256) should be declared external:
	- BNB.withdrawEther(uint256) (../../share/bnb.sol#142-145)
	
fallback() should be declared external:
	- BNB.fallback() (../../share/bnb.sol#148-149)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external

analyzed (2 contracts with 40 detectors), 39 result(s) found
