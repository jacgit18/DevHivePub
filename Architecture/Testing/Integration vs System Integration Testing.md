---
tags:
  - testing
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the difference between integration and system integration testing.
Status: Done
Started: 2023-11-30
EditDate: 
Relates: "[[Testing in Jest]]"
Peer Reviewed: 0
dg-publish: true
---
Integration tests and system integration tests are two different levels of testing in software development that focus on ensuring that various components of a software system work together seamlessly. Let's break down each of these terms:

### Integration Tests:
When creating an integration test, the process closely mirrors that of a unit test, especially when assessing a function. While unit tests focus on individual units, integration tests examine the interactions between different units or modules within an application testing different flows of business logic. The primary distinction emerges when breaking down a function into modular helper functions. In such cases, integration tests center on the main function, concentrating on verifying edge cases addressed by the helper functions. These tests are crucial for identifying issues like data inconsistencies, communication problems, or unexpected behavior resulting from the combined interactions of various units. Integration tests are typically performed after thorough unit testing, serving as a crucial step in ensuring the robustness of the overall system.

#### Examples 

Let's say you have a simple function that calculates the total price of items in a shopping cart, and you want to create an integration test for it. Here's the code:

```typescript
// cart.ts

// Helper function 1
function calculateSubtotal(price: number, quantity: number): number {
  return price * quantity;
}

// Helper function 2
function applyDiscount(subtotal: number, discountPercentage: number): number {
  const discount = (subtotal * discountPercentage) / 100;
  return subtotal - discount;
}

// Main function
export function calculateTotalPrice(items: { price: number; quantity: number }[], discountPercentage: number): number {
  const subtotal = items.reduce((acc, item) => acc + calculateSubtotal(item.price, item.quantity), 0);
  const totalPrice = applyDiscount(subtotal, discountPercentage);
  return totalPrice;
}
```

Now, let's create an integration test for this code using Jest.

```typescript
// cart.test.ts

import { calculateTotalPrice } from './cart';

describe('calculateTotalPrice', () => {
  it('calculates the total price with a discount', () => {
    const items = [
      { price: 10, quantity: 2 },
      { price: 5, quantity: 3 },
    ];
    const discountPercentage = 10; // 10% discount

    const totalPrice = calculateTotalPrice(items, discountPercentage);

    // The expected total price after a 10% discount would be 4.5 + 13.5 = 18
    expect(totalPrice).toBe(18);
  });

  it('calculates the total price without a discount', () => {
    const items = [
      { price: 10, quantity: 2 },
      { price: 5, quantity: 3 },
    ];
    const discountPercentage = 0; // No discount

    const totalPrice = calculateTotalPrice(items, discountPercentage);

    // The expected total price without a discount would be 20
    expect(totalPrice).toBe(20);
  });
});
```

#### Advanced Example 

```typescript
import * as bcrypt from 'bcrypt';

// Main authentication function using helper functions
function authenticateUser(username: string, password: string): boolean {
    const storedPasswordHash = retrieveStoredPasswordHash(username);
    if (storedPasswordHash) {
        const passwordMatch = verifyPassword(password, storedPasswordHash);
        return passwordMatch;
    }
    return false;
}

function retrieveStoredPasswordHash(username: string): string | null {
    // Simulated database retrieval, in a real-world scenario, this would interact with a database
    const storedHash = userDatabase[username];
    return storedHash || null;
}

function verifyPassword(password: string, storedHash: string): boolean {
    // Use bcrypt to compare the provided password with the stored hash
    return bcrypt.compareSync(password, storedHash);
}

// Simulated user database
const userDatabase: Record<string, string> = {
    'exampleUser': bcrypt.hashSync('secretPassword', 10),
};

// Integration test for authentication
function authenticationIntegrationTest() {
    // Test with correct credentials
    const successfulAuthentication = authenticateUser('exampleUser', 'secretPassword');
    if (successfulAuthentication) {
        console.log("Authentication test passed for correct credentials!");
    } else {
        console.error("Authentication test failed for correct credentials!");
    }

    // Test with incorrect password
    const failedAuthentication = authenticateUser('exampleUser', 'wrongPassword');
    if (!failedAuthentication) {
        console.log("Authentication test passed for incorrect password!");
    } else {
        console.error("Authentication test failed for incorrect password!");
    }

    // Test with non-existent user
    const nonExistentUser = authenticateUser('nonExistentUser', 'somePassword');
    if (!nonExistentUser) {
        console.log("Authentication test passed for non-existent user!");
    } else {
        console.error("Authentication test failed for non-existent user!");
    }
}

// Run the authentication integration test
authenticationIntegrationTest();
```


### System Integration Tests:
   System integration tests, on the other hand, focus on testing the interactions and integration between different systems or subsystems within a larger software application or ecosystem. This level of testing is broader in scope than integration tests and verifies that different parts of the software application work harmoniously as a complete system.

   System integration tests often involve testing interactions between multiple components, services, databases, and other external dependencies. The goal is to ensure that the entire software system functions correctly and that data flows smoothly between different parts of the system.

In summary, the key difference between integration tests and system integration tests lies in the scope of testing:

- **Integration tests** focus on the interactions between smaller units or modules within an application.
- **System integration tests** focus on the interactions between larger components, subsystems, or systems within the entire software ecosystem.

Both levels of testing are crucial for identifying and resolving issues that can arise when integrating different parts of a software application, ultimately contributing to a more reliable and functional product.