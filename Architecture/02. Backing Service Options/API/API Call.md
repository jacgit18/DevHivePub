---
tags:
  - API
  - servers
  - performance
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the decision making process around API call on the frontend versus the backend which depends on various factors, and there isn't a one-size-fits-all answer.
Status: Done
Started: 
EditDate: 2024-02-27
Relates: 
Peer Reviewed: 0
dg-publish: true
---
### API Call on the Frontend:  
  
1. **Real-Time Updates:**  
- If you need real-time updates in your application and want to reflect changes immediately without waiting for a round trip to the server, making API calls directly from the frontend can be beneficial.  
  
2. **User Experience:**  
- For responsive and interactive user interfaces, making certain API calls on the frontend can enhance the user experience by reducing latency.  
  
3. **Reduced Server Load:**  
- Offloading some API calls to the frontend can reduce the load on the backend server, distributing the processing between client and server.  
  
4. **Offline Functionality:**  
- If your application needs to function offline or in low-connectivity scenarios, making API calls on the frontend can enable caching and local data storage for better offline support.  
  
### API Call on the Backend:  
  
1. **Security:**  
- Sensitive operations and data manipulations are generally better suited for the backend to ensure proper authentication, authorization, and protection of sensitive information.  
  
2. **Data Validation and Sanitization:**  
- Backend API calls allow for centralized data validation and sanitization, ensuring that data conforms to business rules and security standards.  
  
3. **Third-Party API Secrets:**  
- If your application interacts with third-party APIs that require secrets (API keys, tokens), it's more secure to make those calls from the backend to avoid exposing sensitive information on the client side.  
  
4. **Business Logic:**  
- Complex business logic, especially if it involves multiple data sources or computations, is often better handled on the backend to maintain consistency and reduce duplication.  
  
5. **Scalability:**  
- Backend API calls provide better scalability as server-side infrastructure can be more easily scaled to handle increased load.  
  
### Hybrid Approach:  
  
1. **Authentication and Authorization:**  
- Initial authentication and authorization can be performed on the backend, and subsequent API calls (based on user actions) can be made from the frontend.  
  
2. **Performance Optimization:**  
- Consider optimizing performance by caching data on the frontend where appropriate, but still rely on the backend for critical operations and data integrity.  
  
3. **Cross-Origin Resource Sharing (CORS):**  
- Be mindful of CORS restrictions when making API calls directly from the frontend. If your frontend and backend are served from different domains, ensure proper CORS configuration on the server.  
> 💡 A bad designed API were you're getting data from and using in your app can mess with your apps performance.
  
In many cases, a combination of frontend and backend API calls is used to strike a balance between real-time updates and security. The specific requirements of your application and the characteristics of your data and operations will guide the decision-making process.


