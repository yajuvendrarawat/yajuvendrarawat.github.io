
### Welcome to Yajuvendra's Page

## The work is in progress you should see the site running very soon

<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.1.0/papaparse.min.js"></script>
<script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
<div id="myPlot"></div>
<script type='text/javascript'>
 
var publicSpreadsheetUrl='https://docs.google.com/spreadsheets/d/e/2PACX-1vTBjjumI_CAILUHpsOa6sGGrq2O9caxS_rDzXXpiUW2MO4_nYOn0beRvDj1YjLcuHDoYQuLyC4A3ikM/pub?output=csv';
  
  function init() {
    Papa.parse( publicSpreadsheetUrl, {
          download: true,
          header: true,
          complete: showInfo
  } )
  }
  window.addEventListener('DOMContentLoaded', init)
  function showInfo(results) 
  {
    var data = results.data;
    var xValues = []; //all the values which are shown on the x-axis
    var yValues1 = []; //all the values which are shown on the y-axis
    var yValues2 = []; //all the values which are shown on the y-axis
    alert('Successfully processed!')
    console.log(data);
    
      //get all possible x and y-values
   for (var i = 0; i < data.length; i++) 
    {
     // if (xValues.indexOf(data[i].Date) === -1) 
      {
        xValues.push(data[i].Date);
      }
      //if(i === 1 )
      {
      //  if (yValues1.indexOf(data[i].TempC) === -1) 
        {
          yValues1.push(data[i].TempC);
        }
      }
      //if(i === 2 )
      {
      //  if (yValues2.indexOf(data[i].Humid) === -1) 
        {
          yValues2.push(data[i].Humid);
        }
      }
    }
    
  //create an empty array for all possible z-values based on the dimensions of x and y
  var zValues = new Array(yValues1.length).fill(0).map(row => new Array(xValues.length).fill(0));

  var x = 0;
  var y = 0;

  for (i = 0; i < 1; i++) {
    x = xValues.indexOf(data[i].x);
    y = yValues1.indexOf(data[i].y);
    if (x !== -1 && y !== -1) {
      zValues[y][x] = parseFloat(data[i].z);
    }
  }

  //the data which is passed to Plotly
  var plotlyData = [{
    x: xValues,
    y: yValues1
  }];
  
  var plotlyData1 = [{
    x: xValues,
    y: yValues2,
    xaxis: "x2",
    yaxis: "y2"
  }];
  
  var data = [plotlyData, plotlyData1];
  
  var layout = {
  xaxis: {domain: [0, 0.45]},
  yaxis2: {anchor: "x2"},
  xaxis2: {domain: [0.55, 1]}
  };
  
  //var graphOptions = {layout: layout, filename: "simple-subplot", fileopt: "overwrite"};
  //finally draw the plot
  Plotly.plot('myPlot', plotlyData, { margin: { t: 0 } });
 // Plotly.plot(data, graphOptions, function (err, msg) {console.log(msg);});
     
  }

  window.addEventListener('DOMContentLoaded', init)
</script>
