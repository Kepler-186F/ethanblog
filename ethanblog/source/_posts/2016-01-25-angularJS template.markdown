---
layout: post
title: "AngularJS template "
date: 2016-01-25 11:06:00 -0700
comments: true
categories:
---
This post wrap up a hello-world demo for ngularJS web app, and should serve well as a template.


AngularJS is also MVC. However, different from true MVC, it's everything running at client side within javascript runtime. Which means less performance and less security.


So what is Microservice Architecture:
{% img /images/img/angularjs.jpg %}




index.html
```
<html lang="en" ng-app="mvcApp">
<head>
	<script src="bower_components/angular/angular.js"></script>
	<script src="bower_components/angular-route/angular-route.js"></script>
	<script src="main/main.js"></script>
	<script src="about/about.js"></script>
</head>
<body>

	<p>Hello world index page</p>
	<div ng-view>this used for routing</div>

</body>
</html>
```


main.js
```
'use strict';


/* App Module */
var mvcApp = angular.module('mvcApp', [
		'ngRoute',
		'module_about'
		]);


mvcApp.config(['$routeProvider',
	function($routeProvider) {
		//console.log($routeProvider)
		$routeProvider.when('/about', {
				templateUrl: 'about/about.html',
				controller: 'aboutCrtl'
			}).otherwise({
				redirectTo: '/about'
			});
	}]);
```


about/about.html
```
<h2>About page</h2>
Author is: {{about_author}}
<helloworld/>
```

about/about.js
```

//Declaration of this module
var module_about = angular.module('module_about',[]);

/* Controllers */
module_about.controller('aboutCrtl',['$scope','aboutFac',aboutCrtl]);
function aboutCrtl($scope,aboutFac){
	$scope.about_author='ethan wang';
	//Now I'm going to use this factory
	aboutFac.doGreet();
}

/* Model */
module_about.factory('aboutFac',aboutFac);
function aboutFac(){
	var factory={};
	factory.doGreet = function(){
		alert('doGreet method called!');
	}
	return factory;
}


//TO show case about directive
mvcApp.directive('helloworld',helloworldDirective);
function helloworldDirective(){
	return {
		restrict: 'AEC',
		replace: 'true',
		template: '<h3>Helloworld! Welcome to About page!!</h3>',
		link: function(scope, element, attrs){
			element.bind('click',function(){
				alert('you clicked!');
				//scope.$apply(function(){scope.color = "black";});
			});
		}
	}
}

```


To access code and see hello world in 5 sec, just go to this link:
```
https://github.com/Template-EthanFavoriate/TEMPLATE_ANGULARJS.git
```
