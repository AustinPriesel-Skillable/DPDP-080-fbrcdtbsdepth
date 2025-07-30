## Use Case 01 – Build SQL database in Microsoft Fabric to query and create reports

**Introduction**

This use case provides a hands-on lab experience for building and
managing a SQL database within **Microsoft Fabric**, a unified data
platform. It is designed for users who want to explore the capabilities
of Microsoft Fabric for data storage, querying, reporting, and sharing.
The lab walks through the complete lifecycle of a SQL database—from
environment setup and data import to advanced analytics and API
creation—using the AdventureWorks sample dataset. It emphasizes
practical application through step-by-step exercises that simulate
real-world data scenarios.

**Objectives**

- Set up a Microsoft Fabric trial environment and create a new
  workspace.

- Enable and configure SQL database capabilities within Fabric.

- Create and manage a SQL database using the Fabric portal.

- Load and explore sample data (AdventureWorksLT) in the SQL database.

- Write and execute T-SQL queries to create and manipulate a database
  objects.

- Query data using the SQL Analytics Endpoint and understand OneLake
  integration.

- Generate and test a GraphQL API from the SQL database.

- Build and publish interactive reports using Power BI connected to the
  Fabric SQL database.

- Share data securely and manage user access and roles within the Fabric
  environment.

- Clean up resources after completing the lab.

## Exercise 1 – Set up your environment

### **Task-1: Sign-In to Microsoft Fabric**

Follow these steps to start your Fabric capacity trial and become the
Capacity administrator of that trial.

1.  Open your browser and browse the **Microsoft Fabric Page**
    +++https://app.fabric.microsoft.com/+++

2.  In the **Microsoft Fabric** window, enter your given credentials,
    and click on the **Submit** button. 
    
    ![A close up of a white and green object AI-generated content may be
    incorrect.](./media/image1.png)

3.  Then, In the **Microsoft** window enter the password and click on
    the **Sign in** button 

    ![A login screen with a red box and blue text AI-generated content may
    be incorrect.](./media/image2.png)

4.  In **Stay signed in?** window, click on the **Yes** button.

    ![A computer screen shot of a computer error AI-generated content may
    be incorrect.](./media/image3.png)

5.  You’ll be navigated to the Microsoft Fabric Home Page.

    ![A screenshot of a computer Description automatically
    generated](./media/image4.png)

### **Task-2: Enable SQL Database (Preview) for a capacity**

1.  Go to the **settings** option on the Fabric Home Page.

    ![A screenshot of a computer Description automatically
    generated](./media/image5.png)

2.  Select Admin portal settings from the drop-down menu.

    ![A screenshot of a computer Description automatically
    generated](./media/image6.png)

3.  In the Admin portal, select the **Fabric Capacity** tab.

    ![A screenshot of a computer Description automatically
    generated](./media/image7.png)

4.  Now, select the **capacity name** associated with your user account.

    ![A screenshot of a computer Description automatically
    generated](./media/image8.png)

5.  Select the **Delegated tenant settings** tab.

    ![A screenshot of a computer Description automatically
    generated](./media/image9.png)

6.  Navigate to the **SQL database (preview)** section and check the
    checkbox for ‘**Override tenant admin selection**’.

    ![A screenshot of a computer Description automatically
    generated](./media/image10.png)

7.  Enable it for **All the users in capacity** and click on **Apply.**

    ![A screenshot of a computer Description automatically
    generated](./media/image11.png)

8.  You will see the following message.

    ![A screenshot of a computer Description automatically
    generated](./media/image12.png)

9.  Now, wait for at least **15 minutes** before creating the SQL
    Database in Fabric.

    **Note**: After 15 minutes, you might need to refresh the page if you
    can’t see the SQL Database (preview) option.

### **Task-3: Create a New Fabric Workspace**

You can use an existing workspace or create a new Fabric workspace. In
workspaces, you create collections of items such as lakehouses,
warehouses, and reports. You must be a member of the Admin or Member
roles for the workspace to create a SQL database.

To create a workspace:

1.  Navigate to the **Workspaces** from the left pane.

    ![A screenshot of a computer Description automatically
    generated](./media/image13.png)

2.  In the **Fabric** home page, select **+New workspace**.

    ![A screenshot of a computer Description automatically
    generated](./media/image14.png)

3.  In the **Create a workspace tab**, enter the following details and
    click on the **Apply** button.

    |   |    |
    |-----|-----|
    |Name|	+++SQLDatabaseXX+++ (XX can be a unique number)|
    |Advanced	|Under License mode, select **fabric capacity**|

    ![](./media/image15.png)

    ![](./media/image16.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image17.png)

## Exercise 2 – Create a SQL Database in the Fabric Portal

1.  In the Fabric Portal, click on **+ New Item**, search for **SQL
    databases**, and select **SQL database (preview) tile. (If in case,
    this tile is not showing, you might need to refresh the page after
    15-20 minutes of enabling SQL Database from the Admin portal
    settings-Task-2)**

    ![](./media/image18.png)

2.  Provide a name for the **New Database** as **+++sqldb+++**.
    Select **Create**.

    ![](./media/image19.png)

3.  When the new database is provisioned, on the **Home** page for the
    database, notice the **Explorer** pane showing database objects.

    ![](./media/image20.png)

4.  Under **Build your database**, three useful tiles can help you get
    your newly created database up and running.

    - **Sample data** option lets you import a sample data into
    your **Empty** database.

    - **T-SQL** option gives you a web-editor that can be used to write
    T-SQL to create database object like schema, tables, views, and more.
    For users who are looking for code snippets to create objects, they
    can look for available samples in **Templates** drop down list at the
    top of the menu.

    - **Connection strings** option shows the SQL database connection string
    that is required when you want to connect using SQL Server Management
    Studio, the mssql extension with Visual Studio Code, or other external
    tools.

    ![](./media/image21.png)

## Exercise 3 - Load AdventureWorks sample data in your SQL database in Microsoft Fabric

1.  Once the new database is created, open the database's home page.
    Select **Sample Data**.

    ![](./media/image22.png)

2.  You'll see a **Loading Sample Data** notification.

- Don't modify the database while the import is in process.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image23.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image24.png)

3.  Once complete, there's a notification. The object explorer also
    refreshes to show the new **SalesLT** schema. You're now ready to
    get started with the AdventureWorksLT sample database.

    ![](./media/image25.png)

4.  Expand the SalesLT schema in the **Object Explorer** to see the
    objects that were created. Select on any of the tables to quickly
    view the data.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image26.png)

5.  For more options, like select top 1000 rows or to script an object
    out, right-click or select the context menu (...) of the object
    name.

    ![](./media/image27.png)

    ![](./media/image28.png)

## Exercise 4 – Create a table in SQL Database in Fabric

### **Task-1: Create a table with T-SQL Queries**

1.  Select the **New Query** button in the main ribbon.

    ![](./media/image29.png)

2.  Create the definition of your table in T-SQL with the help of this
    sample, in the query editor, copy and paste the following code.
    Select the entire text and click on *the **Run*** button to execute
    the query. After the query is executed, you will see the results.

    ```
    CREATE TABLE dbo.products ( 
    product_id INT IDENTITY(1000,1) PRIMARY KEY, 
    product_name VARCHAR(256), 
    create_date DATETIME2 
    )
    ```

    ![](./media/image30.png)

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image31.png)

3.  If the **Object Explorer** is already expanded to show tables, it
    will automatically refresh to show the new table upon create. If
    not, expand the tree to see the new table.

    ![](./media/image32.png)

### **Task-2: Creating a table with Copilot**

1.  Again, Select the **New Query** button in the main ribbon.

    ![A screenshot of a computer Description automatically
    generated](./media/image29.png)

2.  Type in the following text as a T-SQL comment into the query window
    and press Tab on your keyboard:

    ```
    --create a new table that to store information about products with some typical columns and a monotonistically increasing primary key called ProductID
    ```

    ![A screenshot of a computer Description automatically
    generated](./media/image33.png)

3.  After a few seconds, Copilot will generate a suggested T-SQL script
    based on the prompt.

    ![A screenshot of a computer Description automatically
    generated](./media/image34.png)

4.  Press the Tab key again to accept Copilot's suggestion. It should
    look something like this:

    ```
    CREATE TABLE [dbo].[NewProducts] (
    ProductID INT PRIMARY KEY IDENTITY(1,1),
    ProductName NVARCHAR(100) NOT NULL,
    StandardCost DECIMAL(18, 2),
    ListPrice DECIMAL(18, 2),
    CreateDate DATETIME DEFAULT GETDATE()
    );
    ```

    ![](./media/image35.png)

5.  If the **Object Explorer** is already expanded to show tables, it
    will automatically refresh to show the new table upon create. If
    not, expand the tree to see the new table.

    ![A screenshot of a computer Description automatically
    generated](./media/image36.png)

## Exercise 5 – Query the SQL Analytics Endpoint of your SQL Database in Fabric

### **Task-1: Query the SQL Analytics Endpoint**

1.  Expand the **Object Explorer** and make note of the tables in the
    database.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image37.png)

2.  Select the replication menu at the top of the editor,
    select **Monitor Replication**.

    ![](./media/image38.png)

3.  A list containing the tables in the database will appear. If this is
    a new database, you'll want to wait until all of the tables have
    been replicated. There is a refresh button in the toolbar. If there
    are any problems replicating your data, it is displayed on this
    page.

    ![A screenshot of a computer Description automatically
    generated](./media/image39.png)

4.  Once your tables are replicated, close the **Monitor
    Replication** page.

5.  Select the SQL analytics endpoint from the dropdown in the SQL query
    editor. (**Note**: Refresh the page once if the SQL analytics
    endpoint is disabled.)

    ![](./media/image40.png)

    You now see that the **Object Explorer** changed over to the warehouse
    experience.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image41.png)

6.  Select **Address** table under the **SalesLT** database to see the
    data appear, reading directly from OneLake.

    ![](./media/image42.png)

7.  Select the context menu (...) for any table, and
    select **Properties** from the menu. Here you can see the OneLake
    information and ABFS file path.

    ![](./media/image43.png)

    ![](./media/image44.png)

8.  Close the **Properties** page and select the context menu (...) for
    one the tables again. Select **New Query** and **SELECT TOP 100**.

    ![](./media/image45.png)

9.  **The query will automatically run**. You’ll see the top 100 rows of
    data, queried from the SQL analytics endpoint, a copy of the
    database in OneLake.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image46.png)

    ![](./media/image47.png)

## Exercise 6 – Create GraphQL API from your SQL Database

To create an API for GraphQL:

1.  In the  **Fabric** page menu bar on the left side, select **sqldb**
    database .

    ![](./media/image48.png)

2.  Open the database where you want to create a GraphQL API and select
    **New API for GraphQL** from the toolbar 
    
    ![](./media/image49.png)

3.  Enter the **Name API for GraphQL** as **+++sqldb_api+++** and
    select **Create**.

    ![](./media/image50.png)

    At this point, the API is ready but it's not exposing any data. APIs for
    GraphQL are defined in a schema organized in terms of types and fields,
    in a strongly typed system. Fabric automatically generates the necessary
    GraphQL schema based on the data you choose to expose to GraphQL
    clients.

    ![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image51.png)

4.   The **Choose data** screen allows you to search and choose the
    objects you want exposed in your GraphQL schema. Select the
    checkboxes next to the individual tables or stored procedures you
    want to expose in the API. To select all the objects in a folder,
    select the checkbox with the data source name at the top.

5. Select **Load** to start the GraphQL schema generation process.

    ![](./media/image52.png)

6. To add data to the API for GraphQL, click on **'Select data
    source'**.

    ![](./media/image53.png)

7. On **Choose connectivity option** dialog box, select **Connect to
    Fabric data sources with single-on (SSo) authentication** and click
    on **Ok** button.

    ![](./media/image54.png)

8. In the OneLake catalog tab, select the **sqldb of the SQL Analytics
    endpoint** and click on the '**Connect'** button.

    ![A screenshot of a computer Description automatically
    generated](./media/image55.png)

9. In the Choose data tab select **Address**, **SalesOrder**,
    **Customer** and **Product** tables and click on **Load** button.

    ![](./media/image56.png)

10. The schema is generated, and you can start prototyping GraphQL
    queries (read, list) or mutations (create, update, delete) to
    interact with your data. The following image shows the **Schema
    explorer** with an API call template.

    ![](./media/image57.png)

    Your API for GraphQL is now ready to accept connections and requests.
    You can use the API editor to test and prototype GraphQL queries and the
    Schema explorer to verify the data types and fields exposed in the API.

## Exercise 7: Create simple reports on your SQL database in Power BI

1.  Select the **SQL Analytics endpoint** view of the database from the
    left pane.

    ![A screenshot of a computer Description automatically
    generated](./media/image58.png)

2.  Select the **Reporting** menu from the ribbon, and then select **New
    Report** option.

    ![A screenshot of a computer Description automatically
    generated](./media/image59.png)

3.  Choose** Continue** to create a new report with all available data. 

    ![A screenshot of a computer Description automatically
    generated](./media/image60.png)

4.  Expand the **Customers** table, check the checkbox of the column
    **CompanyName** for the report. 

    ![A screenshot of a computer Description automatically
    generated](./media/image61.png)

5.  Notice that as soon as you select the column, the data is displaying
    on the report area. Now, select the **EmailAddress** column. You’ll
    see EmailAddress data is also displayed in the report area.

    ![A screenshot of a computer Description automatically
    generated](./media/image62.png)

6.  Now, select **FirstName** as well and see the column in the report.

    ![A screenshot of a computer Description automatically
    generated](./media/image63.png)

7.  Click on the **blank area** on the report canvas.
    Under **Visualizations**, click on the **Clustered** **Column
    chart** icon to add a **Column chart** to your report.

    ![A screenshot of a computer Description automatically
    generated](./media/image64.png)

8.  On the Data pane, expand **SalesOrderDetail and** check the box next
    to **OrderQty**. This creates a column chart and adds the field to
    the X-axis. 

    ![A screenshot of a computer Description automatically
    generated](./media/image65.png)

9.  Check the box next to **UnitPrice.**

    ![A screenshot of a computer Description automatically
    generated](./media/image66.png)

10. Check the box next to **UnitPriceDiscount**.

    ![A screenshot of a computer Description automatically
    generated](./media/image67.png)

11. Click on the **Save** button to save the report.

    ![A screenshot of a computer Description automatically
    generated](./media/image68.png)

12. Enter a name for your report as +++**sqldb_report**+++ and make sure
    you’re in the correct workspace ‘**SQLDatabase56’**. Click on
    **Save**.

    ![A screenshot of a computer Description automatically
    generated](./media/image69.png)

13. Your report has been saved.

    ![A screenshot of a computer Description automatically
    generated](./media/image70.png)

### **Clean up resources**

1.  In the left navigation bar, select the icon for your workspace to
    view all of the items it contains.

    ![](./media/image71.png)

2.  In the menu on the top toolbar, select **Workspace settings**.

    ![](./media/image72.png)

3.  In the **General** section, select **Remove this workspace**.

    ![](./media/image73.png)

    ![](./media/image74.png)

    ![](./media/image75.png)

## Summary

This lab offers a comprehensive walkthrough of building a SQL database
in Microsoft Fabric, showcasing its capabilities for modern data
warehousing and analytics. Participants learn to set up their
environment, create and query databases, load sample data, and build
reports using Power BI. The lab also introduces advanced features like
GraphQL API generation and secure data sharing. By completing the
exercises, users gain practical experience in leveraging Microsoft
Fabric for end-to-end data management and reporting workflows.
