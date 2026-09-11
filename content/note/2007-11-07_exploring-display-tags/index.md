---
title: 'Exploring Display Tags'
author: "Jasdeep Singh"
date: Wed, 07 Nov 2007 11:35:09 +0000
slug: 'exploring-display-tags'
draft: false
excerpt: "Details adding sorting and CSV/Excel/PDF export functionality to JSP tables using the Display Tag open-source library."
categories: ['display tags', 'export', 'jsp', 'Open Source', 'Programming', 'sorting', 'sourceforge.']
---

Being a J2EE developer you have an edge over others , as you can explore thousands of prebuilt open source components over internet . [Display Tag](http://displaytag.sourceforge.net/11/) is one cool component which i explored recently .

It provides pagination to the JSP page , one just have to set the arraylist of bean object int the request scope of the page and display tags iterate that arraylist and provides a cool tabular view of the data. One just have to mention property names of beans in the dispaly column tag. It uses [commons beanutils](http://commons.apache.org/beanutils/) for iterating the beans.

Now my point in exploring is that i had to provide much more functionalty for my project .

1\. Sorting by table headers 2. Exporting to CSV , Excel file .

Both had a simple solution i just had to mention "export=true" in the table header for exporting the table data.

I had to write "sortable=true" in the table column.

Sorting worked out fine with String values but , there was error for date column as it took date as string also. So i had explore more .

What i did, I changed the type of my date field in bean to java.util.Date . The sorting problem was resolved , But the date format caused problem as i had to show it in GMT . For that I downloaded the source code of display tag from sourceforge. There is org.displaytag.sample package in the source . I placed the source of this package in my code and added decorator to the column :

Now it displayed the proper output.

Now with export set to true in table header . It display links to export in CSV,EXCEl,PDF,RTF formats etc. for exporting to be prper ihad to add 'displaytag.properties' to the classpath of my application .

`export.types=csv excel xml pdf rtf export.excel=true export.csv=true export.xml=true export.pdf=true export.rtf=true export.excel.class=org.displaytag.export.excel.DefaultHssfExportView export.pdf.class=org.displaytag.export.DefaultPdfExportView export.rtf.class=org.displaytag.export.DefaultRtfExportView export.excel.filename=data.xls export.pdf.filename=data.pdf export.xml.filename=data.xml export.csv.filename=data.csv export.rtf.filename=data.rtf`

But it still didn't work it displayed all the records on the next page.

So what i had to do to sort out the problem was to add a filter fior exporting in the web.xml.

Configure the Filter in your web.xml:

ResponseOverrideFilter org.displaytag.filter.ResponseOverrideFilter

And add mappings for urls the filter will intercept, for example:

ResponseOverrideFilter \*.do ResponseOverrideFilter \*.jsp

Thats it . I made my report table specfic to the client needs. Thanks Display Tags.

Long Live The open Source Revolution.

_Crossposted from [https://jasdeepsingh.wordpress.com/2007/11/07/exploring-display-tags/](https://jasdeepsingh.wordpress.com/2007/11/07/exploring-display-tags/)_