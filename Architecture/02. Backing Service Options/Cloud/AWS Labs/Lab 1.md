
# Lab Environment

The lab environment provides you with the following resources to get started:

- An Amazon Virtual Private Cloud (Amazon VPC)
- The necessary underlying network structure
- A security group allowing the HTTP protocol over port 80
- An Amazon Elastic Compute Cloud (Amazon EC2) instance with the Amazon CLI installed
- An associated Amazon EC2 instance profile

The instance profile contains the permissions necessary to allow Session Manager, a capability of AWS Systems Manager, to access the Amazon EC2 instance.

The following diagram shows the interactive flow of the AWS API for creating AWS services and resources used in the lab through the AWS Management Console and AWS CLI.

## AWS Services Not Used in This Lab

AWS services not used in this lab are deactivated in the lab environment. In addition, the capabilities of the services used in this lab are limited to only what the lab requires. Expect errors when accessing other services or performing actions beyond those provided in this lab guide.

---

# Task 1: Explore and Configure the AWS Management Console

## Task 1.1: Choose an AWS Region

1. On the navigation bar, choose the **Region selector** at the top-right corner of the console.
2. Choose the **Region** to which you want to switch.

    > **Caution:** If the chosen Region opens a different webpage instead of the console home page, choose **Cancel** and try a different Region.

3. To open the **General Settings** page, click the **gear icon** from the menu bar.
4. Click on **More user settings**.
5. In the **Localization and default Region** section, choose **Edit**.
6. Select a **Default Region** from the dropdown menu.
7. Choose **Save settings**.
8. If the current Region shown on the Region selector matches the default Region you chose, try selecting a different Region to see the success message.
9. Choose **Go to new default Region**.
10. Choose the **AWS logo** to return to the console home page.
11. Ensure that the Region matches the **LabRegion** value.

---

## Task 1.2: Search with the AWS Management Console

1. In the **Search box** on the navigation bar, enter `cloud`.
2. Choose a **category** on the left navigation pane to refine results.
3. In the **Services** section, hover over **AWS Cloud Map** and choose the link.
4. Choose the **AWS logo** to return to the home page.

---

## Task 1.3: Add and Remove Favorites

### Add a Service to Favorites

1. Choose **Services** from the navigation bar.
2. Select **All services** or **Recently visited**.
3. Choose a service and select the **star** next to its name.
4. View favorites under **Favorites** in the left navigation menu.

### Remove a Service from Favorites

1. Choose **Services** from the navigation bar.
2. In the **Favorites list**, deselect the **star** next to a service.

---

## Task 1.4: Open a Console for a Service

1. Choose **Services** from the navigation bar.
2. Select a service under **Favorites**, **Recently visited**, or **All services**.
3. The chosen service console page is displayed.
4. Choose the **AWS logo** to return to the home page.

---

## Task 1.5: Create and Use Dashboard Widgets

### Add a Widget

1. Choose **+ Add widgets**.
2. Drag the widget to the console page.

### Rearrange a Widget

- Drag the **title bar** of the widget to a new location.

### Resize a Widget

- Drag the **bottom-right corner** of the widget.

### Remove a Widget

1. Choose the **ellipsis icon** on the widget.
2. Select **Remove widget**.

---

# Task 2: Create an Amazon S3 Bucket Using the AWS Management Console

> **Caution:** Ensure that the Region matches the **LabRegion** value.

1. Choose **All Services** from the **Services menu**.
2. Scroll down and choose **Storage**.
3. Select **S3**.
4. In the **navigation pane**, choose **Buckets**.
5. Choose **Create bucket**.
6. Enter a **Bucket name**: `labbucket-NUMBER` (replace `NUMBER` with a random number).
7. The **AWS Region** should match the **LabRegion**.
8. Keep default settings and choose **Create bucket**.

> **Success Message:** `"Successfully created bucket 'labbucket-xxxxx'"`.

---

# Task 3: Upload an Object into the Amazon S3 Bucket Using the S3 Console

1. **Download an image** and save it as `HappyFace.jpg`.
2. Open the **Amazon S3 console** and select **labbucket-xxxxx**.
3. Choose **Upload**.
4. Choose **Add files** and select `HappyFace.jpg`.
5. Choose **Upload**.
6. Choose **Close**.

> **Success Message:** `"Upload succeeded"`.

---

# Task 4: Create an Amazon S3 Bucket and Upload an Object Using the AWS CLI

## Task 4.1: Create a Connection to the Command Host Using Session Manager

1. Search for **EC2** in the AWS Management Console.
2. Choose **Instances** from the navigation pane.
3. Select **Command Host**.
4. Choose **Connect**.
5. Select the **Session Manager** tab.
6. Choose **Connect**.

---

## Task 4.2: Use High-Level S3 Commands with the AWS CLI

1. List all S3 buckets:

   ```sh
   aws s3 ls
```

2. Create a new S3 bucket:
    
    ```sh
    aws s3 mb s3://labbucket-NUMBER
    ```
    
    > Replace `NUMBER` with a unique identifier.
    
3. Upload a file:
    
    ```sh
    aws s3 cp HappyFace.jpg s3://labbucket-NUMBER/
    ```
    
4. Verify the upload:
    
    ```sh
    aws s3 ls s3://labbucket-NUMBER/
    ```
    
