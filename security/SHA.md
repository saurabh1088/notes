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
is known as avalanche effect.

### Use Cases

Hashing is used to store passwords. Passwords are never stored as is for users.
When a user signs in then a hashing function is used to convert password into a
hash value and stored, next time when user logs in then the hash value of entered
password is compared with stored hash.

### Collisions

A collision is said to happen when two values have same hash digest. SHA-1 can easily
create collisions.
