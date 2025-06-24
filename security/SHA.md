# SHA

SHA : Secure Hashing Algorithm

SHA is an algorithm to convert a data into hash value/digest.

- Modified version of MD5
- Used to hash data and certificates


## hashing
Hashing is a process where a piece of data is scrambled beyond recognition. A hash funtion is used to convert data into
hash value or digest. Now this may appear similar to encryption but there is a key difference. In encryption one can
decrypt and get the original data back, but in hashing there isn't any way to get back original data from a hash value.

Goal of any hash function is to ensure that is generates a hash value/digest which appears to be consisting of a random
sequece of characters.

Even a slight change in data should produce a drastically different hash value. This is known as *avalanche effect*.

### Use Cases

1. Passwords :
Hashing is used to store passwords. Passwords are never stored as is for users. When a user signs in then a hashing
function is used to convert password into a hash value and stored, next time when user logs in then the hash value of
entered password is compared with stored hash.

2. File's Integrity :
Hashing can be used to indicate a file's integrity. If a file's content is tampered with then it's hash value will change
than what it would have been originally and this can be used to determine file's integrity. Git uses hashing with SHA
algorith to maintain file integrity.

3. Data Deduplication :
For a storage system hash value can be used to compare two data sets and remove duplicates which helps in saving storage space.

### Collisions
A collision is said to happen when two values have same hash digest. SHA-1 can easily create collisions.

### Dictionary Attack or Rainbow Table Attack

A **dictionary attack** is a type of cyberattack that aims to gain unauthorized access to a password-protected system or decrypt encrypted data by systematically trying words and common phrases from a pre-defined list (a "dictionary") as potential passwords.

#### How it works

- **The "Dictionary":**
    - Attackers compile lists of common words, phrases, names, popular password variations (e.g., `password123`, `qwerty`), frequently leaked passwords from past data breaches, and even context-specific terms (like sports teams if targeting a specific organization).
    - These lists can contain millions of entries.
- **Automated Software:**
    - Specialized software automatically inputs each word from the dictionary as a password attempt into the target system's login page or tests against a compromised password hash file (in an offline attack).
- **Trial and Error:**
    - The software tries one word after another until it finds a match.
    - If a user's password is a word or a common variation found in the dictionary, the attack will succeed.

#### Why are dictionary attacks effective?

They exploit the common human tendency to choose simple, memorable, and predictable passwords. Many users still use:

- Common words (e.g., `admin`, `welcome`)
- Personal information (e.g., pet names, birthdates)
- Keyboard patterns (e.g., `qwerty`, `123456`)
- Passwords exposed in previous data breaches

#### Dictionary Attack vs. Brute-Force Attack

- **Brute-Force Attack:**  
    Tries every possible combination of characters (letters, numbers, symbols) until the correct password is found. This is exhaustive but can take an extremely long time for complex passwords.
- **Dictionary Attack:**  
    Focuses only on a pre-compiled list of likely passwords, making it much faster and more efficient if the target's password is on that list. However, it won't find highly unique or randomly generated passwords not in the dictionary.

#### How to protect against dictionary attacks

- **Strong, Unique Passwords:**  
    Use long, complex passwords that combine uppercase and lowercase letters, numbers, and special characters. Avoid common words or personal information.
- **Passphrases:**  
    Use a sequence of several unrelated words, which is easier to remember but much harder to guess.
- **Multi-Factor Authentication (MFA):**  
    Adds an extra layer of security, requiring a second form of verification (like a code from your phone) even if the password is compromised.
- **Account Lockouts:**  
    Lock out an account after a certain number of failed login attempts to deter continuous attacks.
- **Rate Limiting:**  
    Slow down repeated login attempts from the same IP address.
- **Password Managers:**  
    Generate and store strong, unique passwords for all your accounts.
- **Hashing and Salting:**  
    Store password hashes (not plain text) and use "salting" (adding a random string to the password before hashing) to make dictionary and rainbow table attacks much less effective.


## MD5 vs SHA
Both MD5 and SHA are cryptographic hash functions differing in following ways:

|MD5|SHA|
|---|---|
|Message Digest|Secure Hash Algorithm|
|Fast|Slower than MD5|
|Simpler than SHA|Complex than MD5|
|128 bit hash value|160 bit hash value for SHA-1, 256/512 bit for SHA-2|
|Less secure as is more susceptible to collision attacks|SHA-2 is very secure|
|No longer considered for cryptographic purposes|SHA-2 is widely used in cryptography|


## SHA Family
Broadly there are only two types SHA-1 and SHA-2. One often come across various others like SHA-256m but those are mostly
versions of SHA-2 only. There is one latest SHA-3 as well released in Aug, 2015

### SHA-1
- 160 bits
- Due to short length, it can be easily brute forced.
- Can easily create collisions.

### SHA-2
- 256 to 512 bits
- Brute force attacks can take years to crack.
- SHA-224, SHA-256, SHA-384, SHA-512

### SHA-3
- More secure than SHA-2
- Employs sponge construction
