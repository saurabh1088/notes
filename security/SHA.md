# SHA

SHA : Secure Hashing Algorithm

SHA is an algorithm to convert a data into hash value/digest.

- Modified version of MD5
- Used to hash data and certificates

## hashing

Hashing is a process where a piece of data is scrambled beyond recognition. A hash
funtion is used to convert data into hash value or digest. Now this may appear similar
to encryption but there is a key difference. In encryption one can decrypt and get
the original data back, but in hashing there isn't any way to get back original data
from a hash value.

Goal of any hash function is to ensure that is generates a hash value/digest which
appears to be consisting of a random sequece of characters.

Even a slight change in data should produce a drastically different hash value. This
is known as *avalanche effect*.

### Use Cases

Passwords :

Hashing is used to store passwords. Passwords are never stored as is for users.
When a user signs in then a hashing function is used to convert password into a
hash value and stored, next time when user logs in then the hash value of entered
password is compared with stored hash.

File's Integrity :
Hashing can be used to indicate a file's integrity. If a file's content is tampered
with then it's hash value will change than what it would have been originally and
this can be used to determine file's integrity. Git uses hashing with SHA algorith
to maintain file integrity.

Data Deduplication :
For a storage system hash value can be used to compare two data sets and remove
duplicates which helps in saving storage space.

### Collisions

A collision is said to happen when two values have same hash digest. SHA-1 can easily
create collisions.


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

Broadly there are only two types SHA-1 and SHA-2. One often come across various others
like SHA-256m but those are mostly versions of SHA-2 only

### SHA-1

### SHA-2
