// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract Module3 is ERC20{

    address public OwnerWalletAddress;

    constructor() ERC20("GeloToken", "GTN"){
        OwnerWalletAddress = msg.sender;
    }

    mapping (address Wallet => uint GTN) public CheckBalance;

    function GTNMinting(address WalletAddress, uint256 GTN) public {
        require(WalletAddress == OwnerWalletAddress, "Only Owner can access");
        _mint(WalletAddress, GTN);
        CheckBalance[WalletAddress] += GTN;
    }

    function GTNBurning(address WalletAddress, uint256 GTN) public{
        if(CheckBalance[WalletAddress] >= GTN){
            _burn(WalletAddress, GTN);
            CheckBalance[WalletAddress] -= GTN;
        }else{
            revert("Account doesnt have enough GTN Token to burn");
        }
    }

    function GTNTransferring(address spender, address receiver, uint256 GTN)public{
        if(CheckBalance[spender] >= GTN){
            _approve(spender, receiver, GTN);
            _transfer(spender, receiver, GTN);

            CheckBalance[spender] -= GTN;
            CheckBalance[receiver] += GTN;
        }else{
            revert("Account doesnt have enough GTN Token to transfer");
        }
    }
}
