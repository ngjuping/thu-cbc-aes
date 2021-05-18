# thu-aes-rijndael
An implementation of AES-128 using CBC mode

## How to use
Put the following code in main function in the cpp file `aes.cpp`
```
uint8_t plain[TEST_DATA_SIZE] = { 0 };
uint8_t original[TEST_DATA_SIZE] = { 0 };
uint8_t key[AES_BLOCK_SIZE] = { 0 };
uint8_t IV[AES_BLOCK_SIZE] = { 0 };

randomFill(plain, TEST_DATA_SIZE);
for (int i = 0; i < TEST_DATA_SIZE; i++) {
  original[i] = plain[i];
}
printHex(plain, TEST_DATA_SIZE);
randomFill(key, AES_BLOCK_SIZE);
randomFill(IV, AES_BLOCK_SIZE);

// encrypt
CBC_AES_encrypt(plain, TEST_DATA_SIZE, key, IV);

// decrypt
CBC_AES_decrypt(plain, TEST_DATA_SIZE, key, IV);
```

Performance: Encrypt and decrypt takes 1.1 x 10^6 bytes/s in total
