<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">

    <!--Bootstrap-->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM" crossorigin="anonymous"></script>
       
    <style>

   .list{
          background-color: white;
          max-width: 100vw;
          margin-top: 1em;
          border-radius: 10px;
          height: 25vh;
      }
      
      
      .fixed_header{
          width: 100%;
          table-layout: fixed;
          border-collapse: collapse;
      }
      
      .fixed_header tbody{
        /* margin-top: 0.5em; */
        display:block;
        width: 100%;
        overflow: auto;
        height: 20vh;
        border-bottom-left-radius: 10px;
        border-bottom-right-radius: 10px;
      }
      
      /* hide scrollbar but allow scrolling */
      .fixed_header tbody{
          -ms-overflow-style: none; /* for Internet Explorer, Edge */
          scrollbar-width: none; /* for Firefox */
          overflow-y: scroll; 
      }
      
      tbody::-webkit-scrollbar {
          display: none; /* for Chrome, Safari, and Opera */
      }
      
      .fixed_header thead{
        border-top-left-radius: 10px;
        border-top-right-radius: 10px;
      }
      
      .fixed_header thead tr {
         display: block;
      }
      
      .fixed_header th, .fixed_header td {
        text-align: left;
        width: 100vw;
      }
      
      </style>

</head>
<body>
<div class="list">
  <table class="fixed_header table table-striped table-hover table-borderless table-primary">
    <thead>
      <tr>
      </tr>
    </thead>
    <tbody>
      <tr>
      </tr>
    </tbody>
  </table>
  
</div>
  <script>
    const waypoints1= [
    {
        "Name": "Alpha",
        "Longitude": 49.2606,
        "Latitude": -123.2460,
        "Altitude": 50.7
    },
    {
        "name": "Beta",
        "longitude": 49.2606,
        "latitude": -123.2560,
        "altitude": 50.7
    },
    {
        "name": "Gamma",
        "longitude": 49.2506,
        "latitude": -123.2360,
        "altitude": 50.7
    },
    {
        "name": "Alpha",
        "longitude": 49.2606,
        "latitude": -123.2460,
        "altitude": 50.7
    },
    {
        "name": "Beta",
        "longitude": 49.2606,
        "latitude": -123.2560,
        "altitude": 50.7
    },
    {
        "name": "Gamma",
        "longitude": 49.2506,
        "latitude": -123.2360,
        "altitude": 50.7
    }
]
  
  function generateTableHead(table, data) {
    let thead = table.createTHead();
    let row = thead.insertRow();
    for (let key of data) {
      let th = document.createElement("th");
      let text = document.createTextNode(key);
      th.appendChild(text);
      row.appendChild(th);
    }
  }
  
  function generateTable(table, data) {
    for (let element of data) {
      let row = table.insertRow();
      for (key in element) {
        let cell = row.insertCell();
        let text = document.createTextNode(element[key]);
        cell.appendChild(text);
      }
    }
  }
  
  let table = document.querySelector("table");
  let data = Object.keys(waypoints1[0]);
  generateTableHead(table, data);
  generateTable(table, waypoints1);

</script>
</body>
</html>