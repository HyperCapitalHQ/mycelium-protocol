# Social Recovery
The ideal AirAccount for everyone, is a layer security like an onion.
If you launch a 10$ transaction, it just verify your fingerprint.
But if you launch a 100$ or 1000$ transaction, it will verify your fingerprint 
and ask for 2-3 people to verify you(depend on your settings).
It is a setting trigger for different security level by amounts or other rules.

## Theory
From [https://github.com/eth-infinitism/account-abstraction](https://github.com/eth-infinitism/account-abstraction)
Social Recovery Implementation Approach
For social recovery, you would need to:

1. Extend the owner storage model - Instead of a single owner address, implement a guardian system with multiple authorized addresses
2. Override the _validateSignature method - Implement custom logic that can validate signatures from guardians during recovery
3. Add recovery functions - Create functions that allow guardians to collectively change the owner address

社交恢复的工作原理
社交恢复实现时：

对外钱包地址保持不变 - 智能合约地址本身不会改变
内部owner地址可以被替换 - 通过守护者机制更新内部的owner状态变量
用户体验无缝 - 用户继续使用同一个钱包地址，但用新的私钥进行签名

社交恢复的实现扩展
基于SimpleAccount，社交恢复需要这样扩展：

```
contract SocialRecoveryAccount is SimpleAccount {
    address[] public guardians;
    uint256 public threshold;
    
    // 守护者投票更换owner
    function recoverOwner(address newOwner, bytes[] calldata guardianSignatures) external {
        // 验证足够数量的守护者签名
        require(verifyGuardianSignatures(newOwner, guardianSignatures), "Invalid signatures");
        
        // 更新owner（这里改变的是内部验证地址）
        owner = newOwner;
        
        // 智能合约地址本身不变，对外钱包地址保持一致
    }
}
```

实际使用场景

初始化：
```
// 部署时的典型场景
SimpleAccount wallet = new SimpleAccount(entryPoint, eoaAddress);
//                                                   ↑
//                                            这是EOA地址，设为owner

// 结果：
// wallet.address = 0x1234...（智能合约地址）
// wallet.owner = 0x5678...（EOA地址）
// 这两个地址完全不同
```

验证流程
```
function _validateSignature(PackedUserOperation calldata userOp, bytes32 userOpHash)
    internal override virtual returns (uint256 validationData) {
    
    // ECDSA.recover 从签名中恢复出签名者的EOA地址
    address signer = ECDSA.recover(userOpHash, userOp.signature);
    
    // 检查签名者是否是授权的owner（通常是EOA地址）
    if (owner != signer)
        return SIG_VALIDATION_FAILED;
    return SIG_VALIDATION_SUCCESS;
}
```

用户操作流程：

用户用私钥对交易进行签名
签名被发送到智能合约钱包
合约使用ECDSA.recover从签名中恢复出EOA地址
检查这个EOA地址是否等于存储的owner
如果匹配，验证通过

总结

❌ owner ≠ 钱包地址 - owner是EOA地址，钱包地址是合约地址
✅ owner = EOA地址 - 通常owner存储的是控制该钱包的EOA地址
✅ 签名验证逻辑 - 验证签名来自于授权的EOA（owner），而不是合约本身

所以正确的理解是：SimpleAccount的owner通常是一个EOA地址，用于验证交易签名，但它绝不等同于智能合约钱包的地址。