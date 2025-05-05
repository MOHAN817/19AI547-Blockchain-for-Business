# Experiment 6: Blockchain-Based Passwordless Authentication (Using Public-Private Key Cryptography)
# Aim:
To implement a secure passwordless authentication system using public-private key cryptography on Ethereum. This prevents phishing and password leaks.

# Algorithm:
Step 1: User Registration
A user registers with their Ethereum public key (instead of a password).


Step 2: Login Process
When logging in, the user signs a random challenge message using their private key.


The smart contract verifies the signature using the user’s public key.



# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract PasswordlessAuth {
    mapping(address => bool) public registeredUsers;

    event UserRegistered(address user);
    event UserAuthenticated(address user);

    function registerUser() public {
        require(!registeredUsers[msg.sender], "Already registered");
        registeredUsers[msg.sender] = true;
        emit UserRegistered(msg.sender);
    }

    function authenticate(bytes32 hash, uint8 v, bytes32 r, bytes32 s) public view returns (bool) {
        require(registeredUsers[msg.sender], "User not registered");
        address signer = ecrecover(hash, v, r, s);
        return signer == msg.sender;
    }
}
```

# Expected Output:
Users can register without a password.


Users sign a challenge with their private key for authentication.


The smart contract verifies signatures to confirm identity.



# High-Level Overview:
Eliminates password hacks & phishing attacks.


Uses Ethereum's built-in cryptographic functions.


Inspired by Web3 login solutions like MetaMask authentication.

# RESULT:
![block chain1](https://github.com/user-attachments/assets/1d8fa341-ba8e-462b-83e9-c8deb276078c)

![block chain2](https://github.com/user-attachments/assets/65bf313b-ce90-42a1-ac5b-77ae1891e015)

![block chain3](https://github.com/user-attachments/assets/18f63053-11d2-4e17-941c-99c7f3f9e063)

![block chain4](https://github.com/user-attachments/assets/a202aaa8-c493-41ab-9106-0e77b9e16e94)






