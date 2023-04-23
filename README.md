# randomBuster
**randomBuster** is a generative adversarial network (**GAN**) model trained to imitate token sequences and predict pseudo-random IDs, sequence predictions, purchase orders, electronic receipts, and identification numbers. The model learns to generate new tokens that are similar to the training data, making it a valuable tool for pentesting applications. RandomBuster can be fine-tuned on specific datasets and used to generate new, realistic token sequences, allowing for the identification and exploitation of weak number or sequence generators.


RandomBuster is a generative adversarial network (GAN) model designed to imitate token sequences generated by weak number generators. This makes it a valuable tool in the context of penetration testing, where it can be used to test the security of systems that rely on weak random number generators.

###Example

Consider a company that uses a default code for employee access to their HR interface. This code is generated using a linear congruential generator (LCG), which is a type of weak random number generator. The LCG generates the code by following a simple formula:

```python
def lcg_str(seed, length):
    a = 1664525
    c = 1013904223
    m = 2**32
    x = seed
    while True:
        x = (a * x + c) % m
        yield hex(x)[2:].zfill(length)

rand = lcg_str(12345, 8)
for i in range(10):
    print(str(next(rand)))
```

This code generates a set of 10 pseudo-random strings of length 8 and stores them in a file. 

```
05391c44
043c7ad3
8b0c4216
a289127d
e8f7b1b8
1cca49b7
7ef29baa
8c609701
989a046c
c89034db
```

An attacker could use RandomBuster to generate similar codes that are likely to be accepted by the system..

```
..
1/1 [==============================] - 0s 156ms/step
1/1 [==============================] - 0s 138ms/step
6250/6250 [==============================] - 27s 4ms/step
Valid token found! : df7eda32
Valid token found! : 64a34e25
Valid token found! : a7beef41
Valid token found! : dadeea45
..
```

RandomBuster works by learning the statistical patterns of the token sequences generated by the LCG and then generating new token sequences that are statistically similar. The model does not need to know the seed or any of the other parameters of the LCG to generate valid tokens.

To use RandomBuster in this scenario, the attacker would need to obtain a sample of valid codes generated by the LCG. The attacker would then train RandomBuster on this sample to learn the statistical patterns of the valid codes. Once trained, the attacker could use RandomBuster to generate new codes that are likely to be accepted by the system.

RandomBuster is a flexible tool that can be fine-tuned on specific datasets and used to generate realistic token sequences in various contexts. Its potential applications are vast, including predicting pseudo-random IDs, sequence predictions, purchase orders, electronic receipts, and identification numbers.


Potential applications of randomBuster:

1. Predicting weak passwords or PIN codes used for authentication.
2. Generating synthetic credit card numbers for testing payment systems.
3. Imitating device MAC addresses to bypass network access controls.
4. Creating spoofed GPS location data for location-based services.
5. Generating synthetic traffic data to test traffic prediction systems.
6. Mimicking user behavior to evade intrusion detection systems.
7. Generating synthetic system logs to test security information and event management (SIEM) systems.
8. Creating fake online profiles for social engineering attacks.
9. Generating synthetic website traffic to test load-balancing and caching systems.
10. Mimicking fingerprint or facial recognition data to bypass biometric authentication systems.
