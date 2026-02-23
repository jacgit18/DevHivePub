---
tags: 
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
In programming, **stubbing** is a technique used primarily in testing, where you replace a real piece of code with a "stub"—a simplified version that mimics the behavior of the actual code. Stubs allow you to isolate parts of the code being tested by controlling the behavior of dependencies, making it easier to test specific components or functions without relying on the full implementation.

### How Stubbing Works

A stub is typically a mock version of a function, module, or object that returns predefined responses when called. This way, you can test how your code behaves without depending on external systems or complex components.

### Key Benefits of Stubbing

1. **Isolation**: Stubs help isolate the code under test, so you can focus on specific functionality without interference from other parts of the system.
2. **Reliability**: Stubs provide consistent, controlled outputs, which is useful if the real components could produce unpredictable or time-consuming results (e.g., API calls).
3. **Speed**: By using a stub instead of calling real external systems (like databases or APIs), you can speed up testing.

Here is a JavaScript example illustrating the use of stubbing in the context of unit testing with a popular testing framework like Mocha and a stubbing library like Sinon.  

Let’s say you have a function that depends on data from an API. Instead of calling the API in every test (which might be slow, unreliable, or cost money), you can use a stub to mimic the API’s response.
### Example Scenario  
Suppose we have a `UserService` that fetches user data from an external API.  
  
### Actual Code  
```javascript  
// userService.js  
class UserService {  
async fetchUserData(userId) {  
const response = await fetch(`[https://api.example.com/users/$](https://api.example.com/users/$){userId}`);  
const data = await response.json();  
return data;  
}  
}  
  
module.exports = UserService;  
```  
  
### Test Code with Stubbing  
```javascript  
// userService.test.js  
const sinon = require('sinon');  
const { expect } = require('chai');  
const UserService = require('./userService');  
  
describe('UserService', function() {  
let userService;  
let fetchStub;  
  
beforeEach(function() {  
userService = new UserService();  
fetchStub = sinon.stub(global, 'fetch');  
});  
  
afterEach(function() {  
fetchStub.restore();  
});  
  
it('should fetch user data', async function() {  
// Arrange: Set up the stub to return a predefined response  
const fakeResponse = {  
json: () => Promise.resolve({ id: 1, name: 'John Doe' })  
};  
fetchStub.resolves(fakeResponse);  
  
// Act: Call the method under test  
const userData = await userService.fetchUserData(1);  
  
// Assert: Verify the results  
expect(userData).to.deep.equal({ id: 1, name: 'John Doe' });  
expect(fetchStub.calledOnce).to.be.true;  
expect(fetchStub.calledWith('https://api.example.com/users/1')).to.be.true;  
});  
});  
```  
In programming, **stubbing** is a technique used primarily in testing, where you replace a real piece of code with a "stub"—a simplified version that mimics the behavior of the actual code. Stubs allow you to isolate parts of the code being tested by controlling the behavior of dependencies, making it easier to test specific components or functions without relying on the full implementation.

### How Stubbing Works
A stub is typically a mock version of a function, module, or object that returns predefined responses when called. This way, you can test how your code behaves without depending on external systems or complex components.

### Key Benefits of Stubbing
1. **Isolation**: Stubs help isolate the code under test, so you can focus on specific functionality without interference from other parts of the system.
2. **Reliability**: Stubs provide consistent, controlled outputs, which is useful if the real components could produce unpredictable or time-consuming results (e.g., API calls).
3. **Speed**: By using a stub instead of calling real external systems (like databases or APIs), you can speed up testing.

### Stubbing Simplified
Let’s say you have a function that depends on data from an API. Instead of calling the API in every test (which might be slow, unreliable, or cost money), you can use a stub to mimic the API’s response.

#### Without Stubbing:
```javascript
function getDataFromAPI() {
    return fetch('https://example.com/data').then(response => response.json());
}
```

#### With Stubbing (using a testing library):
```javascript
function getDataFromAPI() {
    return { data: 'stubbed data' }; // A predefined response
}
```

In this case, the stub replaces the `fetch` call, allowing you to test how `getDataFromAPI()` works without an actual API request. You can further customize stubs to return various responses to test different scenarios, such as errors or edge cases.

Stubbing is widely used in unit testing and works alongside **mocking** and **spying**, which are also techniques for controlling and observing code behavior during tests.
### Explanation  
  
1. **Setting Up the Test**:  
- `sinon.stub(global, 'fetch')` creates a stub for the global `fetch` function, which is used by the `UserService` to fetch data from an API.  
  
2. **Configuring the Stub**:  
- `fetchStub.resolves(fakeResponse)` configures the stub to return a predefined response (`fakeResponse`) when it is called. This response mimics the structure of a real fetch response.  
  
3. **Calling the Method Under Test**:  
- `userService.fetchUserData(1)` calls the method under test, which internally uses the stubbed `fetch` function.  
  
4. **Assertions**:  
- The test checks that the returned user data matches the expected data.  
- The test verifies that the stubbed `fetch` function was called once and with the correct URL.  
  
By using stubs, we can test the `UserService` in isolation without making actual network requests, making our tests faster and more reliable.