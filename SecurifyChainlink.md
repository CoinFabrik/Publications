# Securifiy over ChainLink
Results of running securfiy on chainlink.sol

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
