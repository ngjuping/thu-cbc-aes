# thu-aes-rijndael
An implementation of AES-128 using CBC mode, with **NO** padding support, yet!

## How to use
Put the following code in main function in the cpp file `aes.cpp`
```
uint8_t plain[TEST_DATA_SIZE] = { 0 };
uint8_t key[AES_BLOCK_SIZE] = { 0 };
uint8_t IV[AES_BLOCK_SIZE] = { 0 };

randomFill(plain, TEST_DATA_SIZE);
randomFill(key, AES_BLOCK_SIZE);
randomFill(IV, AES_BLOCK_SIZE);

// encrypt
CBC_AES_encrypt(plain, TEST_DATA_SIZE, key, IV);

// decrypt
CBC_AES_decrypt(plain, TEST_DATA_SIZE, key, IV);

// helper functions: checkBytes (check if is correctly decrypted), printHex (print byte array in hexadecimal form)
```

## Interface
### MACROS
```
#define AES_ROUNDS 9
#define AES_BLOCK_SIZE 16
```

### METHODS
```
// generate roundKeys using initial key for 10(default) AES loops, REQUIRED before using AES_encrypt and AS_decrypt
keySchedule(uint8_t* key, uint8_t roundKeys[AES_ROUNDS + 1][AES_BLOCK_SIZE])

// encrypt a single block (16 bytes) of data, does not create round keys
AES_encrypt(uint8_t* state, uint8_t* key, uint8_t roundKeys[AES_ROUNDS + 1][AES_BLOCK_SIZE])

// decrypt a single block (16 bytes) of data, does not create round keys
AES_decrypt(uint8_t* state, uint8_t* key, uint8_t roundKeys[AES_ROUNDS + 1][AES_BLOCK_SIZE])

// encrypt data of which byte count is a multiple of `AES_BLOCK_SIZE`
CBC_AES_encrypt(uint8_t* data, int bytes, uint8_t* key, uint8_t* IV)

// decrypt data of which byte count is a multiple of `AES_BLOCK_SIZE`
CBC_AES_decrypt(uint8_t* data, int bytes, uint8_t* key, uint8_t* IV)
```

Performance: Encrypt and decrypt takes 1.1 x 10^6 bytes/s in total on intel i7-8750H 16GB RAM Windows 10
