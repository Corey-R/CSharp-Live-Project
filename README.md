# CSharp-Live-Project

For this live project, I joined a development team who were tasked with redesigning, modifying, and refining a theatre website for a company named Vertigo located in Portland, Oregon. During my 2 weeks in attendance, I was responsible for scaffolding the Rental Histories section, styling the Edit and Index Pages, creating and styling the Contact Page, and if time persists scaffold the Rental Requests section and style the Index Page as an Accordion for the website. In this code summary, I will include the full code base and app images for the rental histories section, code snippets and images for the edit page, and code snippets for the accordion which was created for the rental requests section,

## Languages Used
* Javascript/AJAX
* HTML/CSS
* C#

## Other Tools & Frameworks Used
* ASP.NET MVC
* Entity Framework
* Bootstrap
* Font Awesome
* Visual Studio 2019 (IDE)

Code Snippets
* [Rental History](./Code-Snippets/historyIndex.txt)
* [Edit Page](./Code-Snippets/edit.txt)
* [Accordion](./Code-Snippets/requestsIndex.txt)

## App Images 
* [Rental History](./App-Images/csharp-index.png)
* [Edit Page](./App-Images/csharp-edit1.png)
* [Accordion](./App-Images/csharp-accordion.png)

### Rental History

The [rental history](./App-Images/csharp-index.png) index page contains a table of all the current rental histories created. Starting on the far left are icons that respond to rental damages (shows a red x is rental was damaged, shows a green checkmark if not damaged), next is the name of the rental, then a description of the rental's condition (or notes about the rental if not damaged denoted by the faded text), on the far right of the table is a dropdown that appears when hovering over a row. The dropdown contains lcons and links to edit, show details, or delete the current record hovered. The [code base](./Code-Snippets/historyIndex.txt) begins with the models section which lists all the properties (or table columns) created for the database. 

The controller section contains logic that allows for the table to be sorted upon selecting one of the options from the "sort by" dropdown menu located at the top right of the table. The Viewbag.NameSortParm is a custom named container that holds the value of the option selected from the dropdown. This value is first processed through a ternary operator that will assign a default value if found null or empty, otherwise it will pass the value through a switch statement which will perform the sorting action that matches the option selected. This assortment is then returned to the cshtml file where (through AJAX) the table is then replaced and updated with the new sorted organization of the collected records. 

### Edit Page
It's important to note that the .NET and Entity Framework has the capability to scaffold (or auto-generate) CRUD functionality to their websites so long as you create the model properties and set the database. The [Edit Page](./App-Images/csharp-edit1.png), as well as the Create Page, uses javascript to change the label of "Damages Incurred" to "Notes" if rental damage was left unchecked. You can find the code referencing this statement [here](./Code-Snippets/edit.txt). The cshtml code snippet shows where the onChange attribute was added on the checkbox which is the event handler that allows the label to be changed.

### Accordion
One of my biggest issues with the [acordion](./App-Images/csharp-accordion.png) feature was finding a way to open and collapse only ONE record at a time instead of opening and closing ALL of them simultaneously with one click. This was only an issue because in order to access all records in the database, I needed to use a for loop, but this causes every record to have the exact same ID and data-target for the accordion collapse. One work around I found was to set the ID and data-target instead of "collapseOne" to "@item.ContactPerson" (NOTE: the [code snippet](./Code-Snippets/requestsIndex.txt) shows "for 'item' in Model"). By doing this, I was able to get the records to individually respond when clicked, however, in the case two contact persons have the same name multiple records could still potentially be opened together. Since I couldn't use @item.RentalHistoyID as the data-target and ID, contact person was the next best thing. I would recommend also adding the company name with the contact person to improve selection accuracy and reduce the chance of more than one record opening.
