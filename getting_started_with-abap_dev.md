# Get started with ABAP development

https://www.sap.com/developer/groups/abap-basic-app.html

## Table of Content
1. [Create an ABAP project in Eclipse](#create-an-abap-project-in-eclipse)
2. [Display database content and run SQL queries](#display-database-content-and-run-sql-queries)
3. [Create and run an ABAP application](#create-and-run-an-abap-application)
4. [Create a new Data Dictionary structure](#create-an-abap-data-dictionary-structure)
5. [Create a Global ABAP Class](#create-a-global-abap-class)
6. [Create a data element](#create-a-data-element)
7. [Create ABAPDoc comments in your class](#create-abapdoc-comments-in-your-class)
8. [Create a CDS view (ABAP)](#create-a-cds-view-abap)
9. [Display a CDS view using ALV with IDA](#display-a-cds-view-using-alv-with-ida)

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