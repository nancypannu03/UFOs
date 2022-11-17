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
 #### HTML Code
 
    </head>
<body class ="bg-dark">
    
        <div class="wrapper">
            <nav class="navbar navbar-dark bg-dark navbar-expand-lg">
                <a class="navbar-brand" href="index.html">UFO Sightings</a>
              </nav>
        </div>

        <div class="jumbotron">
            <h1 class="display-4">The Truth is Out There</h1>
        </div>
           

        <div class="container-fluid">
            <div class="row">
              <div class="col-md-4">
                <h3>UFO Sightings: Fact of Fancy? <small>Ufologists Weigh In</small></h3>
              </div>

              <div class="col-md-8">
                <p>
                  Are we alone in the universe? For millennia, humans have turned to the sky to answer this question. Now, thanks to research generously funded by W. Avy, a UFO-enthusiast and amateur ufologist, we can supplement our sky-searching with data analysis.<br><br>"The release of this analysis is well-timed: It coincides with the celebration of World UFO Day, which is a moment for ufologists around the world to connect, relax, and sample a range of UFO-themed snacks," said Dr. Ursula F. Olivier, the world's preeminent expert on circular sightings. "Citizen-scientists can be especially helpful in both cataloguing sightings—which is hugely helpful for us in our search for aliens—and in helping us celebrate the work that has already been done, such as this data visualization project, which will help us raise awareness of the ubiquity of sightings!"<br><br>Not everyone is ready to celebrate, however. Local CEO and vocal anti-alien activist V. Isualize reached out to our reporters to go on record as firmly opposed to any attempts to provide access to this data. "If there are aliens, they certainly would like to be left alone," she stated, before directing us to the Leave Aliens Alone (LAA) community engagement initiative she founded and funds.<br><br>So what do YOU think? Are we alone in the universe? Are aliens trying to contact us, or do they want to be left alone? Dig through the data yourself, and let us know what you see.
    
    
                </p>
              </div>
            </div>
          </div>
        
          <div class="container-fluid">
            <div class="row">
              <div class="col-md-3">
                <form class ="bg-dark">
                    <p>Filter Search</p>
                  
                  <ul class="list-group bg-dark">
                    <li class="list-group-item bg-dark">

                      <!-- Adding filter date and input box-->
                        <label for="date">Enter Date</label>
                        <input type="text" placeholder="1/10/2010" id="datetime" />
                    </li>
                    <li class="list-group-item bg-dark">
                        <label for="city">Enter City</label>
                        <input type="text" placeholder="roswell" id="city">
                    </li>

                    <li class="list-group-item bg-dark" >
                        <label for="state">Enter State</label>
                        <input type="text" placeholder="ca" id="state">
                    </li>

                    <li class="list-group-item bg-dark" >
                        <label for="country">Enter Country</label>
                        <input type="text" placeholder="us" id="country">
                    </li>

                    <li class="list-group-item bg-dark" >
                        <label for="shape">Enter Shape</label>
                        <input type="text" placeholder=" circle " id="shape">
                    </li>

                    <li class="list-group-item bg-dark" >
                    
                    <button id="filter-btn" type="button" class="btn btn-dark">Filter Table</button>
                    <button id="clear-btn" type="button" class="btn-dark">
                        Clear Table
                        </button>    
                    </li>

                </ul>
                </form>
              </div>

              <div class="col-md-9">
                <table class="table table-striped">
              <thead>
                <tr>
                  
                  <th>Date</th>
                  <th>City</th>
                  <th>State</th>
                  <th>Country</th>
                  <th>Shape</th>
                  <th>Duration</th>
                  <th>Comments</th>
                </tr>
              </thead>
              <tbody></tbody>
            </table>

              </div>
            </div>
          </div>
          <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/4.12.0/d3.js"></script>
          <script src="static/js/data.js"></script>
          <script src="static/js/app.js"></script>
    
</body>
</html>
 ![Test Image](/Resources/main.png)
    
 ![Test Image](/Resources/filter_Image.png)
 
  
#### JS Code 
 
 
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
