# Angular

### Module
* contains the different components of an AngularJS app

### Directive
* can bind behavior to HTML elements
* can define the scope of something inside an HTML element
    - **ng-app**
        + for modules
    - **ng-controller**
        + for controllers
    - **ng-repeat**
        + loops through an array and displays each element
    - **ng-src**
        + sets the `src` attribute of an element (like img) to a property in the controller
    - **ng-click**
        + sets the `onClick` attribute of an element to a function property in the controller
        `
        <p class="likes" ng-click="plusOne($index)">+ {{ product.likes }}</p>
        `

### Controller
* Manages the app's data
* add _properties_ to the **$scope** variable and pass them into the HTML
* can be literal values, objects, arrays, and so on

### Expression
* Use double curly braces to display the value of a \{\{ variable \}\} on the page
    - use with the | 'pipe' symbol to apply _filters_ to a value, formatting the output
        + avaiable filters include: currency, date, uppercase

###### AngularJS Flow
![AngularJS Flow](http://i.imgur.com/1r6Bb15.png)

### Model

### View
* .html files
* presents the app's data through the use of expressions, filters, and directives
* The view automatically changes and displays updated data without reloading

### Controller
* .js files
* The function in the controller updates the state of the data



## Example Code from first excersize

##### Example Controller MainController.js file

```
app.controller('MainController', ['$scope', function($scope) {
  $scope.title = 'Books from the Cosmos';
  $scope.promo = 'See what cool shit we have to offer!';
  $scope.products = [
    {
      name: 'The Book of Trees',
      price: 19,
      pubdate: new Date('2014', '03', '08'),
      cover: 'img/the-book-of-trees.jpg',
      likes: 0,
      dislikes: 0
    },
    {
      name: 'Program or be Programmed',
      price: 8,
      pubdate: new Date('2013', '08', '01'),
      cover: 'img/program-or-be-programmed.jpg',
      likes: 0,
      dislikes: 0
    },
    {
      name: 'Code Complete',
      price: 43,
      pubdate: new Date('2012', '01', '11'),
      cover: 'img/the-book-of-trees.jpg',
      likes: 0,
      dislikes: 0
    },
    {
      name: 'The Fireman',
      price: 11.99,
      pubdate: new Date('2016', '02', '01'),
      cover: 'img/program-or-be-programmed.jpg',
      likes: 0,
      dislikes: 0
    }
  ];
  $scope.plusOne = function(index) {
    $scope.products[index].likes += 1;
  };
  $scope.minusOne = function(index) {
    $scope.products[index].dislikes += 1;
  };  
}]);
```

##### Example index.html view
```
<!doctype html>
<html>
  <head>
      <link href="https://s3.amazonaws.com/codecademy-content/projects/bootstrap.min.css" rel="stylesheet" />
    <link href='https://fonts.googleapis.com/css?family=Roboto:500,300,700,400' rel='stylesheet' type='text/css'>
    <link href="css/main.css" rel="stylesheet" />

    <script src="//ajax.googleapis.com/ajax/libs/angularjs/1.3.5/angular.min.js"></script>
  </head>
  <body ng-app="myApp">
    <div class="header">
      <div class="container">
        <h1>Book End</h1>
      </div>
    </div>

    <div class="main" ng-controller="MainController">
      <div class="container">

        <h1>{{ title }}</h1>
        <h2>{{ promo }}</h2>
        
        <div ng-repeat="product in products" class="col-md-6">
         <div class="thumbnail">
           <img ng-src="{{ product.cover }}">
           <p class="title">{{ product.name }}</p>
           <p class="price">{{ product.price | currency }}</p>
           <p class="date">{{ product.pubdate | date }}</p>
           <div class="rating">
             <p class="likes" ng-click="plusOne($index)">+ {{ product.likes }}</p>
             <p class="dislikes" ng-click="minusOne($index)">- {{ product.dislikes }}</p>
           </div>
          </div>
        </div>

      </div>
    </div>

    <div class="footer">
      <div class="container">
        <h2>Available for iPhone and Android.</h2>
        <img src="https://s3.amazonaws.com/codecademy-content/projects/shutterbugg/app-store.png" width="120px" />
        <img src="https://s3.amazonaws.com/codecademy-content/projects/shutterbugg/google-play.png" width="110px" />
      </div>
    </div>


    <!-- Modules -->
    <script src="js/app.js"></script>

    <!-- Controllers -->
    <script src="js/controllers/MainController.js"></script>
  </body>
</html>


```


##### Example app.js module
```
var app = angular.module("myApp", []);
```

