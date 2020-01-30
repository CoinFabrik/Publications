# Securifiy over Tether
Results of running securfiy on tether.sol

## Compilation warnings/errors 
/share/tether.sol:52:5: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function Ownable() public {

/share/tether.sol:172:9: Warning: Use of the "var" keyword is deprecated.
        var _allowance = allowed[_from][msg.sender];

/share/tether.sol:330:5: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function TetherToken(uint _initialSupply, string _name, string _symbol, uint _decimals) public {

/share/tether.sol:136:13: Warning: Invoking events without "emit" prefix is deprecated.
            Transfer(msg.sender, owner, fee);

/share/tether.sol:138:9: Warning: Invoking events without "emit" prefix is deprecated.
        Transfer(msg.sender, _to, sendAmount);

/share/tether.sol:189:13: Warning: Invoking events without "emit" prefix is deprecated.
            Transfer(_from, owner, fee);

/share/tether.sol:191:9: Warning: Invoking events without "emit" prefix is deprecated.
        Transfer(_from, _to, sendAmount);

/share/tether.sol:208:9: Warning: Invoking events without "emit" prefix is deprecated.
        Approval(msg.sender, _spender, _value);

/share/tether.sol:256:5: Warning: Invoking events without "emit" prefix is deprecated.
    Pause();

/share/tether.sol:264:5: Warning: Invoking events without "emit" prefix is deprecated.
    Unpause();

/share/tether.sol:283:9: Warning: Invoking events without "emit" prefix is deprecated.
        AddedBlackList(_evilUser);

/share/tether.sol:288:9: Warning: Invoking events without "emit" prefix is deprecated.
        RemovedBlackList(_clearedUser);

/share/tether.sol:296:9: Warning: Invoking events without "emit" prefix is deprecated.
        DestroyedBlackFunds(_blackListedUser, dirtyFunds);

/share/tether.sol:390:9: Warning: Invoking events without "emit" prefix is deprecated.
        Deprecate(_upgradedAddress);

/share/tether.sol:412:9: Warning: Invoking events without "emit" prefix is deprecated.
        Issue(amount);

/share/tether.sol:426:9: Warning: Invoking events without "emit" prefix is deprecated.
        Redeem(amount);

/share/tether.sol:437:9: Warning: Invoking events without "emit" prefix is deprecated.
        Params(basisPointsRate, maximumFee);
