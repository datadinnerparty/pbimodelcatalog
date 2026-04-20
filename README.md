# What is the Power BI Model Catalog?
The Model Catalog is a user-facing set of documentation derived from the metadata of a published Power BI model.

The purpose is to drive self-service adoption of Power BI models by allowing end users to understand a semantic model, providing easy access to table and measure descriptions, formulas, relationships, and more.

# Prerequisites
* Your Power BI semantic model must be published in a Premium Power BI/Fabric workspace (P1/F64+ or PPU)
* The XMLA endpoint must be enabled (Read only)
* You must have a current version of Power BI Desktop
Note: If you use the MultiModel_SingleWorkspace or MultiModel_MultiWorkspace versions, you MUST set the option to ignore sensitivity labels.  (Only for this particular documentation model, you do NOT need to disable this across your tenant.)

# Which Files do I Need?
The easiest way to use the catalog with your own semantic model(s) is to download the files in the FabricNotebook folder.
You'll need the notebook, and the PowerBI template that matches your preferred method, either DirectLake or Import. 

If you want to contribute to this project, create a branch and pull request here in GitHub (approval required for PR).

# Release Notes
Note: earlier release notes were not captured.  Starting with this release, we'll be adding them in for each release
3/26/2026 - Removed 2 typos, and one remaining call of the logActivity function, which was removed earlier.

# What does the Model Catalog Do?
* Queries the metadata of a Power BI model published in a Premium or PPU workspace
* Provides a templated, parameterized report for quick and easy deployment

![Collage of 10 pages from Model Catalog](/images/modelcatalogreport.jpg)

# Extracting Descriptions – Internal Model Documentation
The model catalog extracts descriptions from many Power BI objects: tables, measures, columns, calculation groups, calculation items, hierarchies, security roles, and the model itself.

![Measure description](/images/measuredescription.jpg)

Note that measure descriptions can now be created with Copilot (preview feature)!

# Model Metadata Included in the Model Catalog
* Model name and description
* Tables
* Partitions, including source queries
* Measures, including descriptions and DAX expressions
* Columns
* Hierarchies
* Relationships
* Calculation Groups and Calculation Items
* Security Roles

# Adding Hidden Descriptions
As of October 2024, the model name, model description, and calculation item descriptions can't be modified directly in Power BI Desktop. They can be updated very easily through Tabular Editor, though. 

![Updating model name and description in Tabular Editor](/images/modelname.jpg)

# Tagging Table Types
The model catalog introduces the concept of filtering by table type
Table type is assigned using a tag in each table description, using the notation: %%TableType
The tag must come AFTER the table description

![Table type tag](/images/tabletag.jpg)

_Note that the table types of “%%Fact” and “%%Dimension” are required for a diagram visual in the model catalog.
You can also use any additional types that you would like to use for filtering (e.g. %%Utility, %%CalculationGroup, %%Parameter, %%Other, etc.)_

# Connecting the Catalog to Your Published Model
The model catalog uses an Analysis Services connection, and is parameterized to make it easy to connect to any published Power BI model.
Note: The Semantic Model parameter can be a comma-separated list of models within the same workspace.

![Parameters dialog](/images/pbitparameters.jpg)

![Parameters dialog](/images/parameters.jpg)

To find your workspace connection, look under Workspace Settings --> License info in the Power BI service.

![Workspace settings](/images/workspacesettings.jpg)

You are connecting to a published Power BI model, so be sure to log in using your Microsoft account.

![Microsoft account login option](/images/microsoftaccount.png)

# Approve Native Database Queries
The model catalog uses DAX queries to retrieve data from a published semantic model. When connecting to a published model for the first time, hit “Run” several times to approve each query.

![Native query dialog](/images/nativequery.jpg)

Alternatively, you can temporarily disable Power BI Desktop's requirement for approvals of native database queries.

![Security option](/images/securityoption.jpg)

# Refreshing a published Model Catalog
If you've opted to use DirectLake methodology, then refreshing the model isn't necessary.
If you've elected to use Import mode, then you can schedule the refresh like any other powerbi report, or add a refresh step in a pipeline.


# Release Notes
I've started adding release notes, to keep track of what's being modified.  Older release notes were not captured, so we are starting now.
4/20/2026 - Removed older versions of the files, this repo only supports the FabricNotebook option now.  Added in Calculation Group Precedence to the Calculation Items table, to help understand ordering of calculations.