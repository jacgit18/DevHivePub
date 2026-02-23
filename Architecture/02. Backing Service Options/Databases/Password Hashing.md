---
tags:
  - databases
  - data
  - security
  - schema
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses password hashing.
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
Password hashing on the database side is a crucial security practice to protect user passwords from unauthorized access, even if the database is compromised. Here's an explanation of the key concepts involved:

1. **Hashing Algorithm:**
   - A hashing algorithm is used to convert the user's plain-text password into a fixed-length string of characters, which is typically a hash value.
   - Common hashing algorithms include SHA-256, SHA-3, and bcrypt.

2. **Salt:**
   - A salt is a random value unique to each password. It is concatenated with the password before hashing.
   - Salting prevents attackers from using precomputed tables (rainbow tables) for common passwords because the same password will have different hashes due to unique salts.

3. **Cryptographic Hash Function:**
   - A good cryptographic hash function should be fast to compute but computationally infeasible to reverse (find the original input from the hash).
   - The one-way nature of cryptographic hash functions ensures that even a small change in the input results in a significantly different hash.

4. **Database Storage:**
   - Instead of storing plain-text passwords, databases store the hashed passwords along with their corresponding salts.
   - The hashed password and salt together create a secure representation of the user's credentials.

5. **Verification Process:**
   - During the login process, the entered password is combined with the stored salt, hashed using the same algorithm, and then compared with the stored hashed password.
   - If the computed hash matches the stored hash, the entered password is considered valid.

Here's a simple example using the `crypt` function in PostgreSQL:

```sql
-- Storing a hashed password with a salt
INSERT INTO users (username, password_hash)
VALUES ('user123', crypt('user_password', gen_salt('bf')));

-- Verifying a password during login
SELECT * FROM users
WHERE username = 'user123'
  AND password_hash = crypt('entered_password', password_hash);
```

App side :


```typescript
export interface LoginCreds {
  email: string;
  password: string;
}

async function validateUserCredentials(userCreds: LoginCreds): Promise<any> {
  return db("testuser")
    .select()
    .where(db.raw(`password=crypt(?, password)`, [userCreds.password]))
    .where("email", userCreds.email);
}
```


By using strong, adaptive hashing algorithms with salts, the database ensures that even if the hashed passwords are exposed, it is computationally infeasible for attackers to reverse the process and obtain the original passwords.