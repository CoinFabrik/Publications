# Slither over Tether
Results of running slither on tether.sol

## Compilation warnings/error
/share/tether.sol:52:5: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function Ownable() public {
    ^ (Relevant source part starts here and spans across multiple lines).
/share/tether.sol:172:9: Warning: Use of the "var" keyword is deprecated.
        var _allowance = allowed[_from][msg.sender];

/share/tether.sol:330:5: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function TetherToken(uint _initialSupply, string _name, string _symbol, uint _decimals) public {
    ^ (Relevant source part starts here and spans across multiple lines).

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

## INFO:Detectors:
UpgradedStandardToken (../../share/tether.sol#307-313) has incorrect ERC20 function interface:ERC20Basic.transfer(address,uint256) (../../share/tether.sol#85)
UpgradedStandardToken (../../share/tether.sol#307-313) has incorrect ERC20 function interface:ERC20.transferFrom(address,address,uint256) (../../share/tether.sol#95)
UpgradedStandardToken (../../share/tether.sol#307-313) has incorrect ERC20 function interface:ERC20.approve(address,uint256) (../../share/tether.sol#96)
UpgradedStandardToken (../../share/tether.sol#307-313) has incorrect ERC20 function interface:BasicToken.transfer(address,uint256) (../../share/tether.sol#126-139)
UpgradedStandardToken (../../share/tether.sol#307-313) has incorrect ERC20 function interface:StandardToken.transferFrom(address,address,uint256) (../../share/tether.sol#171-192)
UpgradedStandardToken (../../share/tether.sol#307-313) has incorrect ERC20 function interface:StandardToken.approve(address,uint256) (../../share/tether.sol#199-209)
TetherToken (../../share/tether.sol#315-451) has incorrect ERC20 function interface:ERC20Basic.transfer(address,uint256) (../../share/tether.sol#85)
TetherToken (../../share/tether.sol#315-451) has incorrect ERC20 function interface:BasicToken.transfer(address,uint256) (../../share/tether.sol#126-139)
TetherToken (../../share/tether.sol#315-451) has incorrect ERC20 function interface:ERC20.transferFrom(address,address,uint256) (../../share/tether.sol#95)
TetherToken (../../share/tether.sol#315-451) has incorrect ERC20 function interface:ERC20.approve(address,uint256) (../../share/tether.sol#96)
TetherToken (../../share/tether.sol#315-451) has incorrect ERC20 function interface:StandardToken.transferFrom(address,address,uint256) (../../share/tether.sol#171-192)
TetherToken (../../share/tether.sol#315-451) has incorrect ERC20 function interface:StandardToken.approve(address,uint256) (../../share/tether.sol#199-209)
TetherToken (../../share/tether.sol#315-451) has incorrect ERC20 function interface:TetherToken.transfer(address,uint256) (../../share/tether.sol#340-347)
TetherToken (../../share/tether.sol#315-451) has incorrect ERC20 function interface:TetherToken.transferFrom(address,address,uint256) (../../share/tether.sol#350-357)
TetherToken (../../share/tether.sol#315-451) has incorrect ERC20 function interface:TetherToken.approve(address,uint256) (../../share/tether.sol#369-375)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-erc20-interface
## INFO:Detectors:
Pragma version^0.4.17 (../../share/tether.sol#5) allows old versions

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity
## INFO:Detectors:
Variable ERC20Basic._totalSupply (../../share/tether.sol#82) is not in mixedCase
Parameter BasicToken.transfer(address,uint256)._to (../../share/tether.sol#126) is not in mixedCase
Parameter BasicToken.transfer(address,uint256)._value (../../share/tether.sol#126) is not in mixedCase
Parameter BasicToken.balanceOf(address)._owner (../../share/tether.sol#146) is not in mixedCase
Parameter StandardToken.transferFrom(address,address,uint256)._from (../../share/tether.sol#171) is not in mixedCase
Parameter StandardToken.transferFrom(address,address,uint256)._to (../../share/tether.sol#171) is not in mixedCase
Parameter StandardToken.transferFrom(address,address,uint256)._value (../../share/tether.sol#171) is not in mixedCase
Parameter StandardToken.approve(address,uint256)._spender (../../share/tether.sol#199) is not in mixedCase
Parameter StandardToken.approve(address,uint256)._value (../../share/tether.sol#199) is not in mixedCase
Parameter StandardToken.allowance(address,address)._owner (../../share/tether.sol#217) is not in mixedCase
Parameter StandardToken.allowance(address,address)._spender (../../share/tether.sol#217) is not in mixedCase
Parameter BlackList.getBlackListStatus(address)._maker (../../share/tether.sol#271) is not in mixedCase
Parameter BlackList.addBlackList(address)._evilUser (../../share/tether.sol#281) is not in mixedCase
Parameter BlackList.removeBlackList(address)._clearedUser (../../share/tether.sol#286) is not in mixedCase
Parameter BlackList.destroyBlackFunds(address)._blackListedUser (../../share/tether.sol#291) is not in mixedCase
Parameter TetherToken.transfer(address,uint256)._to (../../share/tether.sol#340) is not in mixedCase
Parameter TetherToken.transfer(address,uint256)._value (../../share/tether.sol#340) is not in mixedCase
Parameter TetherToken.transferFrom(address,address,uint256)._from (../../share/tether.sol#350) is not in mixedCase
Parameter TetherToken.transferFrom(address,address,uint256)._to (../../share/tether.sol#350) is not in mixedCase
Parameter TetherToken.transferFrom(address,address,uint256)._value (../../share/tether.sol#350) is not in mixedCase
Parameter TetherToken.approve(address,uint256)._spender (../../share/tether.sol#369) is not in mixedCase
Parameter TetherToken.approve(address,uint256)._value (../../share/tether.sol#369) is not in mixedCase
Parameter TetherToken.allowance(address,address)._owner (../../share/tether.sol#378) is not in mixedCase
Parameter TetherToken.allowance(address,address)._spender (../../share/tether.sol#378) is not in mixedCase
Parameter TetherToken.deprecate(address)._upgradedAddress (../../share/tether.sol#387) is not in mixedCase

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions
## INFO:Detectors:
transferOwnership(address) should be declared external:
	- Ownable.transferOwnership(address) (../../share/tether.sol#68-72)
totalSupply() should be declared external:
	- TetherToken.totalSupply() (../../share/tether.sol#394-400)
	- ERC20Basic.totalSupply() (../../share/tether.sol#83)
pause() should be declared external:
	- Pausable.pause() (../../share/tether.sol#254-257)
unpause() should be declared external:
	- Pausable.unpause() (../../share/tether.sol#262-265)
addBlackList(address) should be declared external:
	- BlackList.addBlackList(address) (../../share/tether.sol#281-284)
removeBlackList(address) should be declared external:
	- BlackList.removeBlackList(address) (../../share/tether.sol#286-289)
destroyBlackFunds(address) should be declared external:
	- BlackList.destroyBlackFunds(address) (../../share/tether.sol#291-297)
transferByLegacy(address,address,uint256) should be declared external:
	- UpgradedStandardToken.transferByLegacy(address,address,uint256) (../../share/tether.sol#310)
transferFromByLegacy(address,address,address,uint256) should be declared external:
	- UpgradedStandardToken.transferFromByLegacy(address,address,address,uint256) (../../share/tether.sol#311)
approveByLegacy(address,address,uint256) should be declared external:
	- UpgradedStandardToken.approveByLegacy(address,address,uint256) (../../share/tether.sol#312)
deprecate(address) should be declared external:
	- TetherToken.deprecate(address) (../../share/tether.sol#387-391)
issue(uint256) should be declared external:
	- TetherToken.issue(uint256) (../../share/tether.sol#406-413)
redeem(uint256) should be declared external:
	- TetherToken.redeem(uint256) (../../share/tether.sol#420-427)
setParams(uint256,uint256) should be declared external:
	- TetherToken.setParams(uint256,uint256) (../../share/tether.sol#429-438)

Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-as-external

Analyzed (10 contracts with 40 detectors), 55 result(s) found
