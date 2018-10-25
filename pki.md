# PKI Documentation

- Key template
  - Key name
    - ID
    - Expiry date
    - Private key usage
    - Public key usage
    - Private key storage
    - Revocation certificate storage

- Master Bunker key
  - ID is "<First name> <Last name>"
  - No expiry date
  - Private key should only be used once to certify "Master Secured" subkey or for Disaster Recovery (Master Secured has been compromised)
  - Public key should be signed by other users (identity key)
  - Access to this private key is VERY HARD (offline, need to access multiple physical locations, stored as a shared secret)
  - Access to revocation certificate is VERY HARD (offline, need to access multiple physical locations, different from private key location, stored as a shared secret)

- Master Secured subkey
  - ID is "<First name> <Last name>"
  - No expiry date
  - Private key should only once to certify "Master Quick Access" subkey or for Disaster Recovery (Master Quick Access has been compromised)
  - Public key should only be used for cross certification for "Master Quick Access"
  - Access to this private key is HARD (offline, need to access one remote physical location)
  - Access to revocation certificate is HARD (offline, need to access one remote physical location, different from private key location)

- Master Quick Access subkey
  - ID is "<First name> <Last name>"
  - No expiry date
  - Usage

Private Key for signing other users keys: 1 year validity, 10 in advance ?
GitHub keys ?



Public key to verify my identity: Master Bunker
Private key to trust others: ?

Public key to encrypt for me: E0
Private key used by me to sign: S0

S0 is a secured computer I own physically

## Decryption usage

C0: proxy computer for public identity
C1: computer 1
C2: computer 2
CP: public computer (another individual)

E0: C0 key for encryption
E1: C1 key for encryption
E2: C2 key for encryption
EP: CP key for encryption

S0: C0 key for signing
S1: C1 key for signing
S2: C2 key for signing
SP: CP key for signing

C1 sign file for CP
  C1 sign payload with S1 and sends the package to C0
  C0 checks S1 signature, remove it, sign the payload with S0 and send it to CP
  C1 --> |S1|Payload| --> C0 --> |S0|Payload| --> CP

C1 encrypt file for CP
  C1 sign and encrypt payload with S1 and E0 and send it to C0
  C0 decrypts with E0 and checks S1 signature
    C0 sign with S0, encrypt with EP and send it to CP
    C0 sign with S0, encrypt with E2 and send it to C2
  C1 --> |E0|S1|Payload| --> C0 --> |EP|S0|Payload| --> CP
                                --> |E2|S0|Payload| --> C2 # C2 must also be able to decrypt files sent from C1 (if C2 has access to this identity)

CP sign file for C1 / C2
  # Never appends, CP is not aware of C1 and C2

CP sign file for C0
  CP sign payload with SP and send it to C0
    C0 send it to C1
    C0 send it to C2
  CP --> |SP|Payload| --> C0 --> |SP|Payload| --> C1
                             --> |SP|Payload| --> C2

CP encrypt file for C1 / C2
  # Never appends, CP is not aware of C1 and C2

CP encrypt file for C0
  CP --> |E0|SP|Payload| --> C0 --> |E1|S0|Payload| --> C1
                                --> |E2|S0|Payload| --> C2
