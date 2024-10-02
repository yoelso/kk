# kk
Contrato Vulnerable: VulnerableContract.sol

solidity
pragma solidity ^0.8.0;

contract VulnerableContract {
    address public owner;
    uint public balance;

    constructor() public {
        owner = msg.sender;
        balance = 100;
    }

    // Vulnerabilidad: función pública sin restricciones
    function withdraw() public {
        msg.sender.transfer(balance);
    }

    // Vulnerabilidad: función interna sin validación
    function internalTransfer(address _to) internal {
        balance -= 10;
        _to.transfer(10);
    }

    // Vulnerabilidad: función externa sin validación
    function externalTransfer(address _to) external {
        balance -= 20;
        _to.transfer(20);
    }
}
