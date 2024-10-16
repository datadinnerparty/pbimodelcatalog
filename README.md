# What is the Power BI Model Catalog?

The Model Catalog is a user-facing set of documentation derived from the metadata of a published Power BI model.

The purpose is to drive self-service adoption of Power BI models by allowing end users to understand a semantic model, providing easy access to table and measure descriptions, formulas, relationships, and more.

# Prerequisites

* Your Power BI semantic model must be published in a Premium Power BI/Fabric workspace (P1/F64+ or PPU)
* You must have a current version of Power BI Desktop

# Which files do I need?

To use the catalog with your own semantic model, just download this Power BI template file: [Model Catalog Template.pbit](Model%20Catalog%20Template.pbit)

Open the template in Power BI Desktop, insert your workspace URL and semantic model name, and you will be in business.

# What does the Model Catalog do?

* Queries the metadata of a Power BI model published in a Premium or PPU workspace
* Provides a templated, parameterized report for quick and easy deployment

![image](https://github.com/user-attachments/assets/54042dd9-9fae-41f2-ae5f-bbe995921dd2)

# Extracting Descriptions – Internal Model Documentation

The model catalog extracts descriptions from many Power BI objects: tables, measures, columns, calculation groups, calculation items, hierarchies, security roles, and the model itself.

![image](https://github.com/user-attachments/assets/4e37ac53-b474-45b6-80e3-3814050b71a8)

Note that measure descriptions can now be created with Copilot (preview feature)!

# Model Metadata included in the Model Catalog

* Model name and description
* Tables
* Partitions, including source queries
* Measures, including descriptions and DAX expressions
* Columns
* Hierarchies
* Relationships
* Calculation Groups and Calculation Items
* Security Roles

# Adding hidden descriptions

As of October 2024, the model name, model description, and calculation item descriptions can't be modified directly in Power BI Desktop. They can be updated very easily through Tabular Editor, though. 

![image](https://github.com/user-attachments/assets/314ed005-664a-42bd-ba81-06c6d4bc8881)

# Tagging Table Types

The model catalog introduces the concept of filtering by table type
Table type is assigned using a tag in each table description, using the notation: %%TableType
The tag must come AFTER the table description

![image](https://github.com/user-attachments/assets/0b4bde27-bdb3-4edf-a944-2db948c6e21d)

_Note that the table types of “%%Fact” and “%%Dimension” are required for a diagram visual in the model catalog.
You can also use any additional types that you would like to use for filtering (e.g. %%Utility, %%CalculationGroup, %%Parameter, %%Other, etc.)_

# Connecting the Catalog to Your Published Model

The model catalog uses an Analysis Services connection, and is parameterized to make it easy to connect to any published Power BI model.

![image](https://github.com/user-attachments/assets/50433830-76b1-42c0-b48a-9016b422da49)

# Approve Native Database Queries

The model catalog uses DAX queries to retrieve data from a published semantic model. When connecting to a published model for the first time, hit “Run” several times to approve each query.

![image](https://github.com/user-attachments/assets/f6920153-5bd0-4a6a-999e-aa6ba1ba2717)

Alternatively, you can temporarily disable Power BI Desktop's requirement for approvals of native database queries.

![image](https://github.com/user-attachments/assets/322b5e49-ae84-48bf-9b2b-ea562cfb0900)

# Refreshing a published Model Catalog
Like any other Power BI model, the Model Catalog will only refresh when a schedule has been set up in the service or it is triggered manually or through the API. When setting up a refresh schedule, use oAuth credentials to connect to the data source (the target published model).
