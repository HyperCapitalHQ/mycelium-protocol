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