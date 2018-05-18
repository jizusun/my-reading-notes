# SAP Developer Tutorial

## Get started with ABAP development
https://www.sap.com/developer/groups/abap-basic-app.html
> Create your first ABAP project and application in Eclipse to run queries and display data.

1. [Create an ABAP project in Eclipse](#create-an-abap-project-in-eclipse)
2. [Display database content and run SQL queries](#display-database-content-and-run-sql-queries)
3. [Create and run an ABAP application](#create-and-run-an-abap-application)
4. [Create a new Data Dictionary structure](#create-an-abap-data-dictionary-structure)
5. [Create a Global ABAP Class](#create-a-global-abap-class)
6. [Create a data element](#create-a-data-element)
7. [Create ABAPDoc comments in your class](#create-abapdoc-comments-in-your-class)

## ABAP development: Work with Core Data Services (CDS)
https://www.sap.com/developer/groups/abap-cds.html
> These tutorials show you how to retrieve data from the database and display it in a SAP List Viewer (ALV grid), and in Integrated Data Access (IDA).
1. [Create an ABAP project in Eclipse](#create-an-abap-project-in-eclipse)
2. [Create and run an ABAP application](#create-and-run-an-abap-application)
3. [Create a CDS view (ABAP)](#create-a-cds-view-abap)
4. [Display a CDS view using ALV with IDA](#display-a-cds-view-using-alv-with-ida)

## Create custom UI extension for Business Suite app on Cloud Platform

https://www.sap.com/developer/groups/cp-s4-ext-ui.html
> Build a new user interface application on top of SAP Cloud Platform, based on an OData API from your SAP Business Suite or SAP S/4HANA on-premises system.

1. Sign up for a free trial account on SAP Cloud Platform
2. Install openSUSE in VirtualBox Virtual Machine
3. Install SAP NetWeaver in openSUSE
4. Enable OData APIs in SAP NetWeaver
5. Expose OData services to SAP Cloud Platform
6. Create SAP Fiori launchpad on SAP Cloud Platform
7. Extend an SAPUI5 application

## Create SAP S/4HANA data mart on SAP Cloud Platform
https://www.sap.com/developer/groups/cp-s4-ext-datamart.html

> Build a data mart on SAP Cloud Platform for decoupling access and analyzing data coming from your SAP NetWeaver or SAP S/4HANA on-premises system.

1. Sign up for a free trial account on SAP Cloud Platform
2. Install openSUSE in VirtualBox Virtual Machine
3. Install SAP NetWeaver in openSUSE
4. Set up SAP HANA database on SAP Cloud Platform
5. Replicate data using SLT
6. Create OData service based on HANA custom view


## Create a web front end with React JS in SAP Web IDE
https://www.sap.com/developer/groups/cp-frontend-react-1.html
> React JS is a very popular web application toolkit. It is one of many choices for web application designs supported by SAP. Learn how to use React JS inside SAP Cloud Platform, using SAP Web IDE.

1. Getting started with React on SAP Cloud Platform
2. React JS - Define the Bootstrap Template
3. React JS - Add the React JavaScript
4. RSeparate the CSS and JavaScript Files
5. Convert to dynamic components
6. React JS - Add REST OData retrieval
7. React JS - Add header and modal dialog
8. React JS - Create children components in React

## Introducing SAP Front-End Technologies
https://www.sap.com/developer/groups/introducing-front-end-development.html

> Explore SAPUI5, SAP Build and SAP Web IDE available through the SAP Cloud Platform. Learn about design and prototyping, cloud based development, and application deployment with SAP.
> 
1. Sign up for a free trial account on SAP Cloud Platform
2. Create your own Fiori Launchpad
3. Get started with SAP Build
4. Create an SAP Build prototype
5. Import your TechEd BUILD project into SAP Web IDE
6. Commit your project to Git
7. Code with SAPUI5
8. Create a destination for your live OData service for TechEd
9. Change from a mock server to live OData service for TechEd
10. Deploy your app to Fiori Launchpad

## Model OData with SAP Web IDE
https://www.sap.com/developer/groups/webide-odata-modeling.html
> Create an OData model in the Common Schema Definition Language (CSDL) using SAP Web IDE, build and run an SAPUI5 app from your custom model with mock data, then convert your app to run against a live OData service.

1. Manually creating a data model to use in SAP Web IDE's Mock Data server
2. Build an SAPUI5 mobile app based on your data model and run it with mock data
3. Switch your app from mock data to a live OData service


## Build an SAPUI5 app with Grunt
https://www.sap.com/developer/groups/webide-grunt.html
> Learn to use the basic SAPUI5 Grunt plugin, which comes with SAP Web IDE, and then how to add your own Grunt plugins to the build.

1. Getting Started with the SAP Web IDE Multi-Cloud Version (Trial)
2. Grunt Build in SAP Web IDE
3. Adding Grunt Plugins (TypeScript) in SAP Web IDE

## Tutorials

### [Create an ABAP project in Eclipse](https://www.sap.com/developer/tutorials/abap-create-project.html)

### [Create and run an ABAP application](https://www.sap.com/developer/tutorials/abap-create-basic-app.html)

### [Display database content and run SQL queries](https://www.sap.com/developer/tutorials/abap-display-data-queries.html)

### [Create an ABAP Data Dictionary structure](https://www.sap.com/developer/tutorials/abap-dev-adt-create-new-structure.html)

### [Create a data element](https://www.sap.com/developer/tutorials/abap-dev-adt-create-data-element.html)

### [Create a Global ABAP Class](https://www.sap.com/developer/tutorials/abap-dev-create-new-class.html)

## [Create ABAPDoc comments in your class](https://www.sap.com/developer/tutorials/abap-dev-create-abapdoc.html)

### [Create a CDS view (ABAP)](https://www.sap.com/developer/tutorials/abap-dev-adt-create-cds-view.html)
Core Data Services (CDS): is an extension of the ABAP Dictionary
1. Create a CDS View: 
    1. Name: `Z_INVOICE_ITEMS`
    2. Template: Choose `Define View`
2. Enter the data source
    1. SQL view name: `ZINVOICEITEMS`
    2. data source: `sepm_sddl_so_invoice_items`
3. Edit the SELECT statement
    1. Press `Ctrl + Space` to get `Insert all elements - template`
4. Use an existing CDS association
    1. Press `F2` on the data source name
5. Add fields from existing associations
6. Add a CASE statement
    ```
    case header.payment_status
        when 'P' then 'X'
        else ' '
    end as payment_status
    ```
7. Add a WHERE clause
8. Check your code and view you changes
    ```
    @AbapCatalog.sqlViewName: 'ZINVOICEITEMS'
    @AbapCatalog.compiler.compareFilter: true
    @AccessControl.authorizationCheck: #CHECK
    @EndUserText.label: 'Invoice Items'
    define view Z_INVOICE_ITEMS as select from sepm_sddl_so_invoice_item{
        header.buyer.company_name,
        currency_code, 
        gross_amount,
        case header.payment_status
            when 'P' then 'X'
            else ' '
        end as payment_status
    }
    where currency_code = 'EUR'
    ```
    1. Choose `F8` to open the CDS view in the Data Preview


### [Display a CDS view using ALV with IDA](https://www.sap.com/developer/tutorials/abap-dev-adt-use-cds-view.html)
Learn how to consume the CDS view in the SAP List Viewer with Integrated Data Access (ALV with IDA)
1. Open the ABAP Program
    1. Choose `Open ABAP Development Object(Ctrl+Shift+A)` to open the program `Z_INVOICES_ITEMS_EURO`
2. Add ALV Grid to method implementation
    ```
    method run.
        cl_salv_gui_table_ida=>create_for_cds_view( 'Z_INVOICE_ITEMS' )->fullscreen( )->display( ).
    endmethod.
    ```

    1. `Save(Ctrl+S)` and `Activate(Ctrl+F3)`
    2. `Execute(F8)`
3. Set the tooltip information with an annotation
4. optional: Create a data element
5. optional: Add a CAST statement
6. Check the code and the execute the program
    ```cds
    // CDS View: Z_INVOICE_ITEMS

    @AbapCatalog.sqlViewName: 'ZINVOICEITEMS'
    @AbapCatalog.compiler.compareFilter: true
    @AccessControl.authorizationCheck: #CHECK
    @EndUserText.label: 'Invoice Items'

    define view Z_INVOICE_ITEMS as select from sepm_sddl_so_invoice_item{
        header.buyer.company_name,
        currency_code, 
        gross_amount,
        @EndUserText.quickInfo: 'Paid'
        cast(
          case header.payment_status
              when 'P' then 'X'
              else ' '
          end
        as zso_invoice_payment_status ) 
       as payment_status
    }
    where currency_code = 'EUR'
    ```
    ```abap
    * Program:  Z_INVOICE_ITEMS_EURO_CDS

    *&---------------------------------------------------------------------*
    *& Report z_invoice_items_euro
    *&---------------------------------------------------------------------*
    *&
    *&---------------------------------------------------------------------*
    report z_invoice_items_euro_cds.


    class lcl_main definition create private.

      public section.
        CLASS-METHODS create
          RETURNING
            value(r_result) TYPE REF TO lcl_main.
          methods run.
      protected section.
      private section.

    endclass.

    class lcl_main implementation.

      method create.
        create object r_result. 
      endmethod.

      method run.
        cl_salv_gui_table_ida=>create_for_cds_view( 'Z_INVOICE_ITEMS' )->fullscreen( )->display( ).
      endmethod.

    endclass.

    start-of-selection.
        lcl_main=>create( )->run( ) .

    ```

### References
* Github Markdown Heading Anchors: https://gist.github.com/asabaylus/3071099