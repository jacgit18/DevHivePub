#### **1. Data Lambda: Understanding and Access**

- Goal: Walk through how to access data from the data lambda.
- Scope: Includes codebase navigation and using the dev console.
- Objective: Understand how to pull contract data.


#### **2. Data Flow Logic**

- Pull **contract** from data lambda.
- **Check:** `contract.status === "enrolled"`
- If enrolled:

This process can be a lambda or something else ask bobby what he is doing around his data after getting it from data lambda from contracts into his step function
    
- Extract `draftScheduledPayments` from the contract:
	
	- This will be a list of scheduled contract payments.
		
	- Key fields: `paymentDate`, `paymentAmount`
            
- Use this list to build input for the **RT Payment Scheduler Lambda**.
    


#### **3. Integration with RT Payment Scheduler**
Create new list with this data that has to include the stuff below and what ever else stuff 
- **Input Needed:**  
    this a list of ptp this is not the exact full input:
    
    ```json
    { 
      paymentDate: string, 
      paymentAmount: number 
    }
    ```

ending output could maybe include these two fields since things aren't finalized


- **Step Function Responsibilities:**
    
    - Send the input to the RT Payment Scheduler lambda.
    - Handle errors per payment request.
    - Await response with status fields.



#### **4. Response Handling**

there will be a list of multiple scheduled payments meaning more then one ptp

- Expected fields in response from payment RT for every PTP in the list sent an API call is made in RT Payment that can fail or pass those results are routed to created and failed promise:
- top 4 will be included in step function output    
    ```json
    {
      result: "SUCCESS" | "ERROR" | "PARTIAL_SUCCESS",
      hasPromiseToPayError: boolean,
      createdPromiseToPays: [{ date, amount }],
      failedPromiseToPays: [{ date, amount }],

	// other stuff in the body not required
      autoPayConfirmationCode: string, // autoPaySeriesId
      oneTimePaymentConfirmationCode: string, // NOT paymentId
      hasOneTimePaymentError: boolean,
      hasAutoPayError: boolean
    }
    ```
    



#### **5. Design Questions / Unknowns**

- **Clarify with RT Team:**
    
    - Is the **RT Payment Scheduler** fully developed or still in progress?
    - What should the **input format** look like?




