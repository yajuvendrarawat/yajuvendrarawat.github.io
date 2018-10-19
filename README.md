
### Welcome to Yajuvendra's Page

## The work is in progress you should see the site running very soon

<script src='https://cdnjs.cloudflare.com/ajax/libs/tabletop.js/1.5.1/tabletop.min.js'></script>
<script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
<div id="myPlot"></div>
<script type='text/javascript'>
  var publicSpreadsheetUrl = 'https://docs.google.com/spreadsheets/d/1biDY9jaOJvXGdSD_sqdE8DugCfVZ8_EL5hPNEU9utSc/edit?usp=sharing';

  function init() {
    Tabletop.init( { key: publicSpreadsheetUrl,
                     callback: showInfo,
                     simpleSheet: true } )
  }

  function showInfo(data, tabletop) 
  {
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
    y: yValues2
  }];
  
  //finally draw the plot
  Plotly.plot('myPlot', xValues, yValues1);
  //Plotly.plot('myPlot', xValues, yValues2);
  }

  window.addEventListener('DOMContentLoaded', init)
</script>
