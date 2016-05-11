```javascript
// CREATE a doughnut
$.ajax({
      url: 'https://api.doughnuts.ga/doughnuts/',
      type: 'POST',
      dataType: 'json',
      data: {"style": "Cake",
      "flavor": "Schmitty"},
      success: function(data){
      	console.log(data);
      }
    });

// UPDATE a doughnut
$.ajax({
      url: 'https://api.doughnuts.ga/doughnuts/1',
      type: 'PUT',
      dataType: 'json',
      data: {
      	"style": "Cake"
      },
      success: function(data){
      	console.log(data);
      }
    });

// GET an individual doughnut
$.ajax({
      url: 'https://api.doughnuts.ga/doughnuts/1',
      type: 'GET',
      dataType: 'json',
      data: {
      	"style": "Cake"
      },
      success: function(data){
      	console.log(data);
      }
    });