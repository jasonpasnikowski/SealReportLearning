# How to Create a Basic Report

This guide will walk you through the steps to create a basic report using the Seal Report Designer. It covers creating reports directly from SQL queries and also by defining reusable Data Sources.

## Prerequisites

* Seal Report Designer installed
* Access to a data source (e.g., a database like Northwind)

## Creating a Report from a SQL Select

This method is quick for one-off reports or when you have a clear SQL query you want to visualize.

#### Build a report from a simple SQL statement (2 minutes)

<div class="row">
    <div class="col-md-12 bs-callout bs-callout-info">
        This guide shows how to create and execute a report from a simple SQL statement and a database connection.
    </div>
</div>
<ol class="sans">
    <li>
        In the Start menu, point to <srmenu>Programs->Seal Report</srmenu> and then click <b>Report Designer</b>.
    </li>
    <li>
        Click on New (top-left in the toolbar)
    </li>
    <li>
        In the left tree view, right-click on the root node named <i>"Sources"</i> and select <strong>[Add a new SQL Data Source]</strong> in the contextual menu.<br />A new source is created and the source connection is displayed.
    </li>
    <li>
        Edit the <code>Connection String</code> property with the OLE DB Wizard and verify the connection is working using the <strong>[Check Connection]</strong> helper or <strong>[F7]</strong>.
    </li>
    <li>
        In the left tree view, right-click on the root node named <i>"Models"</i> and select <strong>[Add a SQL Model]</strong> in the contextual menu.<br />A new SQL Model named "Model2" is created and the SQL Editor is displayed. Click <strong>[Cancel]</strong> to close the dialog.
    </li>
    <li>
        In the model definition, set the <code>Source</code> property to a the Data Source called <i>"Data Source"</i> that you have previously created.
    </li>
    <li>
        In the text box, type your SQL statement (e.g. "select * from products") and click <strong>[OK]</strong>. The Source tree view displays the columns of the Select.
    </li>
    <li>
        In the elements tree view, drag and drop the elements you want to see in the Row panel.
    </li>
    <li>
        If necessary, drag and drop elements in the restrictions panel to filter data.
    </li>
    <li>
        In the left tree view, click on the view node named <i>"Views\View\Model"</i> and set the <code>Current Model</code> property to "Model2".
    </li>
    <li>
        Click <strong>[Execute]</strong> or press <strong>[F5]</strong>.<br />The report is executed.
    </li>
    <li>
        Click <strong>[Close]</strong> then <strong>[Save]</strong> to save the report in the repository.
    </li>
</ol>

### Example: Simple Product List Report Definition

The following is an example of how a report definition (`.srex` file) might look for a simple product listing. This is based on the `01-Simple list (Products).srex` sample report.

```xml
<?xml version="1.0"?>
<Report xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <GUID>a41f0ad3-16f9-4766-b9d3-33f882fad04f</GUID>
  <ViewGUID>53b70185-5682-4d65-abad-089630729ca2</ViewGUID>
  <Sources>
    <ReportSource>
      <GUID>70370890-3da6-4c57-bad7-3729570efef5</GUID>
      <Name>Northwind (Repository)</Name>
      <ConnectionGUID>1</ConnectionGUID>
      <MetaData>
        <Tables>
          <MetaTable>
            <GUID>5c919d36-900b-4c36-9902-9103ef9604e5</GUID>
            <Alias>SealMasterTable</Alias>
            <DynamicColumns>true</DynamicColumns>
          </MetaTable>
        </Tables>
      </MetaData>
      <MetaSourceGUID>52833575-11ae-4b7d-8b5e-0f9b29d1267a</MetaSourceGUID>
    </ReportSource>
  </Sources>
  <Models>
    <ReportModel>
      <GUID>031b29cc-df91-4adc-982a-dbbd8e662393</GUID>
      <Name>model</Name>
      <SourceGUID>70370890-3da6-4c57-bad7-3729570efef5</SourceGUID>
      <Elements>
        <ReportElement>
          <GUID>c07250de-6eed-4c24-bb70-333599f7fa3c</GUID>
          <Name>Products.CategoryID</Name>
          <Category>Master</Category>
          <NumericStandardFormat>Numeric0</NumericStandardFormat>
          <DateTimeStandardFormat>ShortDate</DateTimeStandardFormat>
          <PivotPosition>Page</PivotPosition>
          <AggregateFunction>Count</AggregateFunction>
          <Nvd3Serie>ScatterChart</Nvd3Serie>
          <MetaColumnGUID>f1ca9f05-b6a3-46da-b753-68cb4056cb66</MetaColumnGUID>
          <EnumGUIDEL />
        </ReportElement>
        <ReportElement>
          <GUID>741c7301-94d5-4876-9f73-8e12db3653e5</GUID>
          <Name>Products.ProductName</Name>
          <Category>Master</Category>
          <PivotPosition>Row</PivotPosition>
          <AggregateFunction>Count</AggregateFunction>
          <Nvd3Serie>ScatterChart</Nvd3Serie>
          <MetaColumnGUID>087ed2f1-b58b-4407-9291-8329ee5dbfe1</MetaColumnGUID>
        </ReportElement>
        <ReportElement>
          <GUID>eeaee07b-f5e2-4705-b956-e2dd9b09ad06</GUID>
          <Name>Products.QuantityPerUnit</Name>
          <Category>Master</Category>
          <NumericStandardFormat>Numeric0</NumericStandardFormat>
          <DateTimeStandardFormat>ShortDate</DateTimeStandardFormat>
          <PivotPosition>Row</PivotPosition>
          <AggregateFunction>Count</AggregateFunction>
          <Nvd3Serie>ScatterChart</Nvd3Serie>
          <MetaColumnGUID>fc5b4299-9a72-44b2-b0a5-8bfcc5e15ef9</MetaColumnGUID>
          <EnumGUIDEL />
        </ReportElement>
        <ReportElement>
          <GUID>6d4742f7-4813-4559-a220-6f83a6a309ab</GUID>
          <Name>Products.UnitPrice</Name>
          <Category>Master</Category>
          <NumericStandardFormat>Numeric0</NumericStandardFormat>
          <DateTimeStandardFormat>ShortDate</DateTimeStandardFormat>
          <PivotPosition>Row</PivotPosition>
          <Nvd3Serie>ScatterChart</Nvd3Serie>
          <MetaColumnGUID>b58c7176-d8e6-4edd-9a6c-6444e5a04b3a</MetaColumnGUID>
          <EnumGUIDEL />
        </ReportElement>
        <ReportElement>
          <GUID>22f44cf2-f0c3-4d07-9ee7-72a5712f396e</GUID>
          <Name>Products.UnitsInStock</Name>
          <Category>Master</Category>
          <NumericStandardFormat>Numeric0</NumericStandardFormat>
          <DateTimeStandardFormat>ShortDate</DateTimeStandardFormat>
          <PivotPosition>Row</PivotPosition>
          <Nvd3Serie>ScatterChart</Nvd3Serie>
          <MetaColumnGUID>e603a329-4e4f-48c5-97e0-60c140f5de8a</MetaColumnGUID>
          <EnumGUIDEL />
        </ReportElement>
        <ReportElement>
          <GUID>645cbd50-4920-4b4a-af78-f30aaafc78b8</GUID>
          <Name>Products.UnitsOnOrder</Name>
          <Category>Master</Category>
          <NumericStandardFormat>Numeric0</NumericStandardFormat>
          <DateTimeStandardFormat>ShortDate</DateTimeStandardFormat>
          <PivotPosition>Row</PivotPosition>
          <Nvd3Serie>ScatterChart</Nvd3Serie>
          <MetaColumnGUID>6fa87b3b-048f-4680-9516-35679cba84bf</MetaColumnGUID>
          <EnumGUIDEL />
        </ReportElement>
      </Elements>
    </ReportModel>
  </Models>
  <Views>
    <ReportView>
      <GUID>53b70185-5682-4d65-abad-089630729ca2</GUID>
      <Name>view</Name>
      <Views>
        <ReportView>
          <GUID>2fb686d5-851e-480f-b2aa-3408f092e483</GUID>
          <Name>model</Name>
          <Views>
            <ReportView>
              <GUID>5fe33951-7d28-40e0-8f4a-dd3405aae7dd</GUID>
              <Name>Model Container</Name>
              <Views>
                <ReportView>
                  <GUID>eb23d1f0-836c-46db-b2d3-57f059bc9d87</GUID>
                  <Name>Page Table</Name>
                  <TemplateName>Page Table</TemplateName>
                  <SortOrder>1</SortOrder>
                </ReportView>
                <ReportView>
                  <GUID>e1932b76-0b84-4258-a6ec-b2e7d282d7b4</GUID>
                  <Name>Data Table</Name>
                  <TemplateName>Data Table</TemplateName>
                  <SortOrder>5</SortOrder>
                </ReportView>
              </Views>
              <TemplateName>Container</TemplateName>
              <SortOrder>1</SortOrder>
            </ReportView>
          </Views>
          <TemplateName>Model</TemplateName>
          <ModelGUID>031b29cc-df91-4adc-982a-dbbd8e662393</ModelGUID>
          <CustomTemplate />
          <Parameters>
            <Parameter>
              <Name>model_show_count</Name>
              <Value>True</Value>
            </Parameter>
          </Parameters>
          <SortOrder>1</SortOrder>
        </ReportView>
      </Views>
      <TemplateName>Report</TemplateName>
      <CustomTemplate />
      <Parameters>
        <Parameter>
          <Name>report_description</Name>
          <Value>Simple list with a break per product category.</Value>
        </Parameter>
      </Parameters>
      <SortOrder>0</SortOrder>
    </ReportView>
  </Views>
  <Cancel>false</Cancel>
</Report>
```

## Creating a Report from a Data Source

This approach is more robust for enterprise reporting. You define a Data Source once, describing your database metadata (tables, columns, joins). Then, multiple reports can be built using this Data Source, allowing for dynamic SQL generation and easier maintenance.

#### Build a repository Data Source and Reports based on your database schema (5 minutes)

<div class="row">
    <div class="col-md-12 bs-callout bs-callout-info">
        This guide shows how to create a first Data Source describing your database metadata. Based on this Data Source, reports can be easily built and executed using dynamic SQL generation.
    </div>
</div>

<h3><strong>Step 1:</strong> Create your first Data Source.</h3>
<ol class="sans">
    <li>
        In the Start menu, point to <srmenu>Programs->Seal Report</srmenu> and then click <b>Server Manager</b>.
    </li>
    <li>
        On the File menu, click <srmenu>New->Data Source</srmenu>.<br />A new Data Source is created and the connection is selected.
    </li>
    <li>
        Edit the <code>Connection String</code> property with the OLE DB Wizard and check the connection configured using the <strong>[Check Connection]</strong> helper or <strong>[F7]</strong>.
    </li>
    <li>
        In the left tree view, right-click on the root node called <i>"Tables"</i> and select <strong>[Add Tables from Catalog...]</strong> in the contextual menu.<br />A dialog box appears.
    </li>
    <li>
        Select the tables in your Data Source and click <strong>[OK]</strong>.<br />Tables, columns and joins have been automatically added.
    </li>
    <li>
        Click <strong>[Save]</strong> to save the Data Source in the repository.
    </li>
</ol>
<h3><strong>Step 2:</strong> Create, execute and store your first reports.</h3>
<ol class="sans">
    <li>
        On the Start menu, point to <srmenu>Programs->Seal Report</srmenu> and then click <b>Report Designer</b>.
    </li>
    <li>
        Click on <strong>[New]</strong> (top-left in the toolbar).
    </li>
    <li>
        In the left tree view, click on the Model node called <i>"Model"</i>.<br />The model is displayed.
    </li>
    <li>
        In the model definition, select the Data Source you have previously created.
    </li>
    <li>
        In the elements tree view, expand the nodes with the table names, then drag and drop the elements you want to see in the Row panel.
    </li>
    <li>
        If necessary, drag and drop elements in the restrictions panel to filter data.
    </li>
    <li>
        Click <strong>[Execute]</strong> or press <strong>[F5]</strong>.<br />The report is executed.
    </li>
    <li>
        Click <strong>[Close]</strong> then <strong>[Save]</strong> to save the report in the repository.
    </li>
</ol>

### Example: Simple Product List Report Definition (using a Data Source)

The report definition below is similar to the previous example but assumes you have already set up a Data Source named "Northwind (Repository)" that contains the "Products" table and its columns.

```xml
<?xml version="1.0"?>
<Report xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <GUID>a41f0ad3-16f9-4766-b9d3-33f882fad04f</GUID>
  <ViewGUID>53b70185-5682-4d65-abad-089630729ca2</ViewGUID>
  <Sources>
    <ReportSource>
      <GUID>70370890-3da6-4c57-bad7-3729570efef5</GUID>
      <Name>Northwind (Repository)</Name> <!-- This name should match your existing Data Source -->
      <ConnectionGUID>1</ConnectionGUID> <!-- This might vary based on your Data Source setup -->
      <MetaData>
        <Tables>
          <MetaTable>
            <GUID>5c919d36-900b-4c36-9902-9103ef9604e5</GUID>
            <Alias>SealMasterTable</Alias>
            <DynamicColumns>true</DynamicColumns>
          </MetaTable>
        </Tables>
      </MetaData>
      <MetaSourceGUID>52833575-11ae-4b7d-8b5e-0f9b29d1267a</MetaSourceGUID> <!-- This GUID points to your repository Data Source -->
    </ReportSource>
  </Sources>
  <Models>
    <ReportModel>
      <GUID>031b29cc-df91-4adc-982a-dbbd8e662393</GUID>
      <Name>model</Name>
      <SourceGUID>70370890-3da6-4c57-bad7-3729570efef5</SourceGUID> <!-- This links to the ReportSource above -->
      <Elements>
        <ReportElement>
          <GUID>c07250de-6eed-4c24-bb70-333599f7fa3c</GUID>
          <Name>Products.CategoryID</Name>
          <Category>Master</Category>
          <NumericStandardFormat>Numeric0</NumericStandardFormat>
          <DateTimeStandardFormat>ShortDate</DateTimeStandardFormat>
          <PivotPosition>Page</PivotPosition>
          <AggregateFunction>Count</AggregateFunction>
          <MetaColumnGUID>f1ca9f05-b6a3-46da-b753-68cb4056cb66</MetaColumnGUID>
        </ReportElement>
        <ReportElement>
          <GUID>741c7301-94d5-4876-9f73-8e12db3653e5</GUID>
          <Name>Products.ProductName</Name>
          <Category>Master</Category>
          <PivotPosition>Row</PivotPosition>
          <AggregateFunction>Count</AggregateFunction>
          <MetaColumnGUID>087ed2f1-b58b-4407-9291-8329ee5dbfe1</MetaColumnGUID>
        </ReportElement>
        <ReportElement>
          <GUID>eeaee07b-f5e2-4705-b956-e2dd9b09ad06</GUID>
          <Name>Products.QuantityPerUnit</Name>
          <Category>Master</Category>
          <PivotPosition>Row</PivotPosition>
          <AggregateFunction>Count</AggregateFunction>
          <MetaColumnGUID>fc5b4299-9a72-44b2-b0a5-8bfcc5e15ef9</MetaColumnGUID>
        </ReportElement>
        <ReportElement>
          <GUID>6d4742f7-4813-4559-a220-6f83a6a309ab</GUID>
          <Name>Products.UnitPrice</Name>
          <Category>Master</Category>
          <NumericStandardFormat>Currency</NumericStandardFormat> <!-- Changed for better display -->
          <PivotPosition>Data</PivotPosition> <!-- Changed for typical table layout -->
          <AggregateFunction>Sum</AggregateFunction> <!-- Changed for numeric data -->
          <MetaColumnGUID>b58c7176-d8e6-4edd-9a6c-6444e5a04b3a</MetaColumnGUID>
        </ReportElement>
        <ReportElement>
          <GUID>22f44cf2-f0c3-4d07-9ee7-72a5712f396e</GUID>
          <Name>Products.UnitsInStock</Name>
          <Category>Master</Category>
          <NumericStandardFormat>Numeric0</NumericStandardFormat>
          <PivotPosition>Data</PivotPosition> <!-- Changed for typical table layout -->
          <AggregateFunction>Sum</AggregateFunction> <!-- Changed for numeric data -->
          <MetaColumnGUID>e603a329-4e4f-48c5-97e0-60c140f5de8a</MetaColumnGUID>
        </ReportElement>
      </Elements>
    </ReportModel>
  </Models>
  <Views>
    <ReportView>
      <GUID>53b70185-5682-4d65-abad-089630729ca2</GUID>
      <Name>view</Name>
      <Views>
        <ReportView>
          <GUID>2fb686d5-851e-480f-b2aa-3408f092e483</GUID>
          <Name>model</Name>
          <Views>
            <ReportView>
              <GUID>5fe33951-7d28-40e0-8f4a-dd3405aae7dd</GUID>
              <Name>Model Container</Name>
              <Views>
                <ReportView>
                  <GUID>eb23d1f0-836c-46db-b2d3-57f059bc9d87</GUID>
                  <Name>Page Table</Name>
                  <TemplateName>Page Table</TemplateName>
                  <SortOrder>1</SortOrder>
                </ReportView>
              </Views>
              <TemplateName>Container</TemplateName>
              <SortOrder>1</SortOrder>
            </ReportView>
          </Views>
          <TemplateName>Model</TemplateName>
          <ModelGUID>031b29cc-df91-4adc-982a-dbbd8e662393</ModelGUID>
          <Parameters>
            <Parameter>
              <Name>model_show_count</Name>
              <Value>True</Value>
            </Parameter>
          </Parameters>
          <SortOrder>1</SortOrder>
        </ReportView>
      </Views>
      <TemplateName>Report</TemplateName>
      <Parameters>
        <Parameter>
          <Name>report_description</Name>
          <Value>Simple list of products, demonstrating reporting from a defined Data Source.</Value>
        </Parameter>
      </Parameters>
      <SortOrder>0</SortOrder>
    </ReportView>
  </Views>
  <Cancel>false</Cancel>
</Report>
```

## Next Steps

*   Explore advanced features like parameters, calculated fields, and sub-reports.
*   Learn about different output formats (PDF, Excel, HTML).
*   Refer to the official Seal Report documentation for more in-depth information.

This concludes the basic guide to creating a report.
