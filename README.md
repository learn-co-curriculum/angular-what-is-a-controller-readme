# What is a Controller?

## Overview

We've talked about controllers before, and now is the time to go into them. Controllers make up a lot of the code we write in Angular so it's important that we learn how to use them correctly and efficiently!

## Objectives

- Describe the role of a Controller
- Create a Controller
- Assign the Controller to the module
- Create an element for Controller scope

## Controllers

You might have noticed that we've mentioned the concept of Controllers quite a lot. These are the backbone for your Angular applications, providing the link between the view and the model.

Controllers differ slightly depending on your architecture. If we're using MVC our controller does a lot more than if we're using MVVM. The nicknames for the controller in these situations are fat and thin controllers.

### Business/Presentational Logic

We'll be using the terms "business" and "presentational" logic quite a lot, so it's important that we understand what these are.

Business logic is all the logic we have to do in order to manipulate our model. For instance, retrieving data from an API endpoint and updating it. If we go back to our coffee shop example, the business logic would be the barista making our coffee.

Presentational logic is when we adapt our model to be displayed correctly in the view. This would be the barista adding our name to the cup as they hand us the drink.

### MVC: Fat Controller  

A fat controller deals with a lot. The controller will fetch all of the model data we need, and do all of the business logic/presentational logic.

### MVVM: Thin Controllers

A thin controller is quite lazy. It hands off all of the business logic to external helpers, such as a service. The controller then handles all of the presentational logic.

## Let's get creative

If you recall our first ever lab, we actually created a controller:

```js
function MainController($scope) {
  $scope.name = 'PUT YOUR NAME HERE!';
}

angular
  .module('app')
  .controller('MainController', MainController);
```
Our controllers are just JavaScript functions. We then use `$scope` (we're covering everything you'll need to know about `$scope` in the next lesson). In short term, `$scope` allows us to put information *into* our views. This is why our first lab has "Hello, PUT YOUR NAME HERE!" when you load the page!

We also assigned the controller to our module named `app`.

We then referenced and initiated that controller in our HTML:

```html
<div ng-app="app">
  <div ng-controller="MainController">
    Hello, {{ name }}!
  </div>
</div>
```

It's important that we initiated our controller inside our initiated module `app` because our controller is assigned to the module `app`. If we tried to use it in a different module, we'd get an error.