# Securifiy over Binance
Results of running securfiy on bnb.sol

## Compilation warnings/errors 
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

