---
tags:
  - web
  - systemDesign
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses
Status: Refinement
Started: 
EditDate: 2024-03-07
Relates: 
Peer Reviewed: 0
dg-publish:
---
In the realm of RESTful web services, controllers play a pivotal role in enhancing the separation of concerns between servers and clients, fostering network efficiency, and facilitating the atomic implementation of complex operations.

To streamline this process, designate a controller resource for each distinct operation. Clients can then utilize the HTTP method POST to initiate a request and trigger the intended operation. If the outcome involves creating a new resource, respond with a 201 (Created) status code, accompanied by a Location header pointing to the URI of the newly created resource. In case of modifying existing resources, employ a 303 (See Other) status code with a Location URI for clients to fetch the modifications.

Error handling follows the guidelines outlined in "How to Return Errors." A controller, despite not always being evident in the domain model, serves as a resource capable of atomically effecting changes to other resources. This abstraction aids in reducing coupling between clients and servers, fostering flexibility.

Consider the scenario of merging two address books for a user. Instead of the inefficient approach of downloading and merging the entire address book on the client side, a more effective solution involves the creation of a controller resource. This resource enables clients to submit their address books to the server for a merge, avoiding network inefficiencies and promoting a more streamlined separation of concerns.

1. **Controller Resource for Complex Operation:**

```javascript
// Controller resource to handle a complex operation
app.post('/mergeAddressBooks', (req, res) => {
    // Perform the merging logic on the server
    // For simplicity, assuming success
    res.status(200).json({ message: 'Address books merged successfully' });
});
```

2. **Client-Side Operation Trigger using POST:**

```javascript
// Client-side code to trigger the merge operation
fetch('/mergeAddressBooks', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json',
    },
    body: JSON.stringify(/* Data needed for the operation */),
})
    .then(response => {
        if (!response.ok) {
            throw new Error(`HTTP error! Status: ${response.status}`);
        }
        return response.json();
    })
    .then(data => {
        console.log(data); // Handle the successful response from the server
    })
    .catch(error => {
        console.error('Error:', error);
    });
```

3. **Handling Errors on the Server:**

```javascript
// Example of handling errors on the server
app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).send('Something went wrong!');
});
```

4. **Alternative PUT-based Approach for Merging Address Books:**

```javascript
// PUT-based approach for merging address books
app.put('/addressBook', (req, res) => {
    // Perform the merging logic on the server
    // For simplicity, assuming success
    res.status(200).json({ message: 'Address books merged successfully' });
});
```

5. **Client-Side PUT Request for Merging:**

```javascript
// Client-side PUT request for merging address books
fetch('/addressBook', {
    method: 'PUT',
    headers: {
        'Content-Type': 'application/json',
    },
    body: JSON.stringify(/* Merged address book data */),
})
    .then(response => {
        if (!response.ok) {
            throw new Error(`HTTP error! Status: ${response.status}`);
        }
        return response.json();
    })
    .then(data => {
        console.log(data); // Handle the successful response from the server
    })
    .catch(error => {
        console.error('Error:', error);
    });
```

These responses handle both success cases and errors, providing a foundation for more robust client-server interactions.

Following the merging of address books, the server seamlessly redirects the client to the user's freshly updated address book, providing an avenue for the client to retrieve a copy of the merged address book if needed.

In another scenario, let's explore a bookstore example where a store operator aims to decrease the pretax price of a book by 15 percent and concurrently update the posttax price to reflect this discount. The server can present the discount percentage as a resource, enabling clients to submit a PUT request to adjust the current discount. Within the same request, the server efficiently updates the total price of the book, ensuring a streamlined and cohesive modification process.


```javascript
const express = require('express');
const bodyParser = require('body-parser');

const app = express();
const port = 3000;

// Middleware to parse JSON in the request body
app.use(bodyParser.json());

// Initial book data with pretax and posttax prices
let book = {
    title: 'Sample Book',
    pretaxPrice: 50,
    posttaxPrice: 0,
    discountPercentage: 0,
};

// Endpoint to get the current book information
app.get('/book', (req, res) => {
    res.json(book);
});

// Endpoint to update the discount and recalculate prices
app.put('/discount', (req, res) => {
    const newDiscount = req.body.discountPercentage;

    // Update discount percentage
    book.discountPercentage = newDiscount;

    // Recalculate posttax price based on the updated discount
    book.posttaxPrice = book.pretaxPrice * (1 - book.discountPercentage / 100);

    res.json({ message: 'Discount updated successfully', updatedBook: book });
});

// Start the server
app.listen(port, () => {
    console.log(`Server is listening on port ${port}`);
});
```

To test this example:

1. Start the server.
2. Make a `GET` request to `/book` to retrieve the initial book information.
3. Make a `PUT` request to `/discount` with a JSON payload like `{ "discountPercentage": 15 }` to update the discount.
4. Make another `GET` request to `/book` to see the updated book information with recalculated prices.

This example demonstrates how a server can offer a discount percentage as a resource, allowing clients to efficiently submit a `PUT` request to modify both the discount and the associated prices in a single operation.

In the server's response, a link is thoughtfully included to guide clients in discovering the 30-day offer. For clients presenting a user interface, embedding this link enables users to seamlessly navigate to the offer, enhancing the overall user experience.

Notably, these examples shed light on the challenges of mapping application operations to methods in the uniform interface. In the discount scenario, the server treats the current discount value as a resource, allowing clients to utilize the `PUT` method for updates. Similarly, for 30-day free electronic book offers, the server identifies them as a collection, permitting clients to use `POST` for adding new books. However, when amalgamating these tasks into a single request, a direct mapping to any HTTP method becomes less apparent, making controllers particularly relevant in such multifaceted scenarios.

For instances like the one described, it's advised to avoid using the `POST` method directly on the book resource to avert tunneling. Tunneling occurs when a client uses the same method on a single URI for different actions. Here's an illustration of tunneling:


Certainly! Let's extend the previous example to include a 30-day free electronic book offer as a collection and demonstrate how a client can discover the offer by following a link in the server's response.

```javascript
const express = require('express');
const bodyParser = require('body-parser');

const app = express();
const port = 3000;

app.use(bodyParser.json());

let book = {
    title: 'Sample Book',
    pretaxPrice: 50,
    posttaxPrice: 0,
    discountPercentage: 0,
};

let freeBookOffers = [];

app.get('/book', (req, res) => {
    // Include a link to the 30-day offer in the response
    const bookWithLink = { ...book, offerLink: '/offers/30-day' };
    res.json(bookWithLink);
});

app.get('/offers/30-day', (req, res) => {
    res.json(freeBookOffers);
});

app.post('/offers/30-day', (req, res) => {
    const newBook = req.body;

    // Add the new book to the 30-day offer collection
    freeBookOffers.push(newBook);

    res.json({ message: 'Book added to 30-day offer', updatedOffers: freeBookOffers });
});

app.put('/discount', (req, res) => {
    const newDiscount = req.body.discountPercentage;

    book.discountPercentage = newDiscount;
    book.posttaxPrice = book.pretaxPrice * (1 - book.discountPercentage / 100);

    res.json({ message: 'Discount updated successfully', updatedBook: book });
});

app.listen(port, () => {
    console.log(`Server is listening on port ${port}`);
});
```

To test this example:

1. Start the server.
2. Make a `GET` request to `/book` to retrieve the initial book information, which now includes a link to the 30-day offer.
3. Make a `GET` request to `/offers/30-day` to discover the existing offers.
4. Make a `POST` request to `/offers/30-day` with a JSON payload to add a new book to the 30-day offer collection.
5. Make another `GET` request to `/offers/30-day` to see the updated offers.

This example demonstrates how links in the server's response can guide clients to discover additional resources, in this case, the 30-day free electronic book offers.

In the requests, the parameters op=updateDiscount and op=30dayOffer signify the operation. This leads to tunneling. 

Tunneling reduces protocol-level visibility (see How to Keep Interactions Visible) because the visible parts of requests such as the request URI, the HTTP method used, headers, and media types do not unambiguously describe the operation.