<script src='https://cdnjs.cloudflare.com/ajax/libs/tabletop.js/1.5.1/tabletop.min.js'></script>
<script type='text/javascript'>
  var publicSpreadsheetUrl = 'https://docs.google.com/spreadsheets/d/1biDY9jaOJvXGdSD_sqdE8DugCfVZ8_EL5hPNEU9utSc/edit?usp=sharing';

  function init() {
    Tabletop.init( { key: publicSpreadsheetUrl,
                     callback: showInfo,
                     simpleSheet: true } )
  }

  function showInfo(data, tabletop) {
    alert('Successfully processed!')
    googleSheet = JSON.parse(JSON.stringify(data));
    console.log(googleSheet);
  }

  window.addEventListener('DOMContentLoaded', init)
</script>


### Welcome to Yajuvendra's Page

## The work is in progress you should see the site running very soon
