# Superstore Data Analysis_ AWS Quicksight
### Introduction to Project
This project focuses on analyzing superstore data using a comprehensive process involving various AWS services. Starting with filtering and saving CSV files, it moves through creating an AWS account, setting up an S3 bucket, configuring AWS Glue for data crawling, querying with Amazon Athena, and visualizing data in Amazon QuickSight. This step-by-step approach ensures efficient data management and insightful analytics.
### Architecture Diagram of Superstore analysis

<img width="700" alt="Architecture" src="https://github.com/gudimetlarohini/Superstore-Analysis_AWS-Quicksight/assets/164952263/22723043-65e3-4095-bd76-19a8f11685d8">

### Agenda for Superstore data analysis
- Excel/CSV file
- AWS root account
- IAM user account
- Amazon S3
- AWS Glue
- Amazon Athena
- Amazon Quicksight

### Step-by-step process of the project:
#### Excel:
- Download the Superstore dataset (CSV file) from Kaggle.
- Apply a filter to the order_date column to select orders dated 2017-01-01.
- Save this filtered data in a new worksheet and name it Order_Jan_2017.csv.
- Apply the same conditions every January of each year and save each file using the same format and naming convention as the respective year.

#### AWS account:
- Create an AWS account.
- The root account is the owner of the AWS account. In an organization, it is generally managed by AWS administrators.
- IAM User account: This type of account has specific permissions for a single user or application (It is used by developers working on projects).
- When creating an IAM account, assign the "admin access" policy to grant access to all AWS services for the IAM user.
- After creating an IAM user account, sign out from the root account and log in as an IAM user.

#### Amazon S3:
- Go to the S3 services and create a bucket with a globally unique name using only lowercase alphanumeric characters. Within that bucket, I created a folder called "aws-project-1-superstore."
- Following that, I created a subfolder named "Orders_Superstore" and then created four more subfolders named "Order_day=2017-01-01"(with each year) to store the saved dataset(s).

#### AWS Glue:
- Go to the Glue service and create a database named "db_superstore," which will appear in the left panel.
  
  <img width="700" alt="AWS Glue" src="https://github.com/gudimetlarohini/Superstore-Analysis_AWS-Quicksight/assets/164952263/ea36243d-9f3c-41b0-b396-c6aad6e9de4b">
   
- Next, create a crawler named "Superstore_Crawler." 
  - When creating the crawler, select the data source from which the crawler will read the data. 
  - In this case, the data source is "Order_Superstore," which is in S3. Opt for "Crawl new subfolders only," which means the crawler will read only the newly added files. 
  - Then create an IAM role to access and perform the job on AWS services. 
  - The name of the role should be "AWSGlueServiceRole-Role_Superstore." Once the data is crawled, store the metadata (tables) in the "db_superstore" database.

  
  <img width="700" alt="Glue2" src="https://github.com/gudimetlarohini/Superstore-Analysis_AWS-Quicksight/assets/164952263/c2b2eff7-fa36-4cdb-9d04-b3738cde0312">
  
- Finally, create a crawler and run it.
#### Note: 
- The main function of the crawler is to access the S3, locate the file, and transform raw data into metadata in the form of tables. 
- In S3, we name folders like "Order_day=2017-01-01," where "Order_day" represents the partition key. By specifying a folder in this format, the crawler will directly navigate to that partition key and read the data.

#### Amazon Athena:
- Go to the Athena Query Editor. It provides a workspace to write or modify queries and run them.
  
<img width="700" alt="Athena" src="https://github.com/gudimetlarohini/Superstore-Analysis_AWS-Quicksight/assets/164952263/87cb2443-373f-4e74-9d82-69fc69eb46c7">


#### Amazon QuickSight:
- Sign up for QuickSight standard edition (one month free).
- Go to the datasets, click on "new dataset," and select Athena.
- Make sure you are in the same region(It is there in the top right corner)where you created the S3, Glue, and Athena services.
- Provide a name for the data source, validate the connection, and create the data source.

  <img width="700" alt="Quicksight_2" src="https://github.com/gudimetlarohini/Superstore-Analysis_AWS-Quicksight/assets/164952263/1a2546fe-6b92-408f-abbf-3286a9087c4a">

- After creation, select the database and table names, and click on "select."
- Choose "Import to SPICE" for faster analytics and visualization.
- Here is the work sapce to create charts.

  <img width="700" alt="Quicksight_5" src="https://github.com/gudimetlarohini/Superstore-Analysis_AWS-Quicksight/assets/164952263/f63ee355-4107-46b1-bc8e-0c0ef60983fb">

- Then, create various charts to meet the business requirements.
  - I have conducted an analysis of sales and profits categorized by different product categories. The results are illustrated using two types of visualizations: Pie Chart And Bar Graph.
  - In addition to the category-wise breakdown, I have also analyzed sales and profits segmented by customer groups.

  <img width="700" alt="Sales Analysis" src="https://github.com/gudimetlarohini/Superstore-Analysis_AWS-Quicksight/assets/164952263/c415109c-9e4a-4f4b-83e9-001e12bcfd0a">

  - To gain a comprehensive understanding of our business performance across different states, I have conducted a detailed analysis encompassing several key metrics. The results are illustrated using Bar and Line graphs for clarity and ease of comparison.

    <img width="700" alt="Statewide Analysis" src="https://github.com/gudimetlarohini/Superstore-Analysis_AWS-Quicksight/assets/164952263/fc1e56e4-0cd6-4248-bde4-2df2f1320ad0">

These visualizations provide a detailed and actionable view of business performance metrics across different states, enabling better strategic planning and decision-making at the regional level.



