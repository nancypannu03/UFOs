# UFOs
## Overview of the analysis:
[Index HTML File](index.html)

[App JS File](static/js/app.js)

[Data JS File](static/js/data.js)

[CSS File](static/css/style.css)

In this Analysis, we will be using Javascript as the primary coding language, which has been designed to enhance HTML.It's the backbone of many popular visualization libraries, such as Plotly, and is often used to create custom dashboards. JavaScript also provides a high level of customization: the dashboards built to deliver visual data, such as maps or graphs, can be as simple or complex as needed.

To be successful in this module, we'll apply HTML and Bootstrap skills and have an open mind regarding semicolons.

### The purpose of the analysis:
In this Project:

      We will build a table using data stored in a JavaScript array. 
      
      We will create filters to make this table fully dynamic, meaning that it will react to user input, and then place the table into an HTML file for easy               viewing.
      
      We will customize your webpage using Bootstrap, and equip your table with several fully functional filters that will allow users to interact with our               visualizations.
    
## Results: Code and Images
### Deliverable 1: Filter UFO sightings on multiple criteria

      Using Javascript we will modify index.html file to create more table filters.
      
      The event listener is modified to detect changes to each filter in the app.js file.
      
      The updateFilters() function saves the element, value, and the id of the filter that was changed. 
      
      The filterTable() function loops through all of the filters and keeps any data that matches the filter values.
      
      The webpage filters the table correctly based on user input. 
      
 ![Test Image](/Resources/main.png)
    
 ![Test Image](/Resources/filter_Image.png)
 
 
      // 1. Create a variable to keep track of all the filters as an object.

        var filters={};

     // 3. Use this function to update the filters. 
        function updateFilters() {

    // 4a. Save the element that was changed as a variable.
       let changeElement = d3.select(this);

    // 4b. Save the value that was changed as a variable.
    
        let changeValue = changeElement.property("value");
        console.log(changeValue)

    // 4c. Save the id of the filter that was changed as a variable.

        let  inputID = changeElement.attr("id");
        console.log(inputID);

    // 5. If a filter value was entered then add that filterId and value
    // to the filters list. Otherwise, clear that filter from the filters object.
        if (changeValue) {
          filters[inputID] = changeValue;
        } 
        else {
        filters = {};
        };
  
     // 6. Call function to apply all filters and rebuild the table
       filterTable(filters);
  
       };
  
     // 7. Use this function to filter the table when data is entered.
       function filterTable() {
  
     // 8. Set the filtered data to the tableData.
        let filteredData = tableData;
  
     // 9. Loop through all of the filters and keep any data that
     // matches the filter values
    
        Object.entries(filters).forEach(([key, value]) => {
         filteredData = filteredData.filter(row => row[key] === value);
         });
  
  
     // 10. Finally, rebuild the table using the filtered data
         buildTable(filteredData);
         };
  
    // 2. Attach an event to listen for changes to each filter
  
          d3.selectAll("input").on("change", updateFilters);
  
  
    // Build the table when the page loads
        buildTable(tableData);

 
 ![Test Image](/Resources/light.png)
 
 ![Test Image](/Resources/light_search.png)


## Summary:

### The summary addresses one drawback of this webpage 

### The summary addresses two additional recommendations for further development 
