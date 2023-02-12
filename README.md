# JointSavings Contract

This is a Solidity smart contract that implements a joint savings mechanism, where two Ethereum addresses are set as the account owners and can withdraw funds from the contract balance. The contract is designed to enforce rules such as ensuring that only the account owners can withdraw funds, and that each withdrawal operation updates the last account owner to have made a withdrawal.

## Variables
- `accountOne` and `accountTwo`: `address payable` variables to store the address of the two account owners
- `lastToWithdraw`: `address public` variable to store the address of the last person who made a withdrawal
- `lastWithdrawAmount` and `contractBalance`: `uint public` variables to store the last withdrawal amount and the current balance of the contract

## Functions

### withdraw(amount, recipient)
This function allows either `accountOne` or `accountTwo` to withdraw a specified `amount` of funds and send it to the `recipient` address.
- The function checks if the `recipient` address matches either `accountOne` or `accountTwo`
- If the recipient does not match either account, the function returns an error message: "You don't own this account!"
- The function also checks if there are sufficient funds in the contract to make the withdrawal. If there are insufficient funds, the function returns an error message: "Insufficient funds!"
- The function updates the `lastToWithdraw` variable with the `recipient` address and `lastWithdrawAmount` with the `amount` if `recipient` is different from the previous `lastToWithdraw`.

### deposit()
This function allows users to deposit funds into the contract. The `contractBalance` is updated to reflect the current balance of the contract.

### setAccounts(account1, account2)
This function sets the values of `accountOne` and `accountTwo` to `account1` and `account2` respectively.

### default fallback function
The contract also has a default fallback function that stores any incoming Ether into the contract and updates the `contractBalance` accordingly.


## Interacting with Smart Contract
Once the contract was deployed, I tested its functionality and captured the results which are saved in the `Execution_Results` folder. First, I used account addresses from Ganache to set `account1` and `account2` values. Next, I performed a series of deposits to the smart contract and verified they worked by using the `contractBalance` function. Finally, I tested the `withdraw` function to verify that funds were able to be withdrawn from the contract. 