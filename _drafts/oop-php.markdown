---
title: OOP PHP
layout: post
date: 
categories: php course
---


## What is OOP?

- OOP is a coding methodology and style
- it makes it easy to extend and reuse our code
- easier to maintain and debug when things go wrong


## Blocks of OOP

- Classes, properties & methods
- Access modifiers(private, public, static), getters & setters
- Inheritance, static properties & magic methods


## Classes

they are blueprints for objects. So this contains properties(variables) and methods(functions) of an object.



### Creating a class

There are a few conventions to follow when creating a class

- First letter Capital
- Singular Name


```php

// creating a user clas
class User {

}

// Instantiating a new user and creating a use object
$userOne = new User();
$userTwo = new User();
```


## Properties and Methods
<br>

### Properties

They are like variables for classes

```php
class User {

	// public makes it for these properties to be accessed by the object later
	public $username = 'ramos';
	public $email = 'karsoft92@gmail.com'; 

}

$userOne = new User();

//accessing the properties above

echo $userOne->username

```


### Methods

These are functions 

<br>

```php
class User {

	// public makes it for these properties to be accessed by the object later
	public $username = 'ramos';
	public $email = 'karsoft92@gmail.com'; 


	public function addFriend(){
		// this refers to the instance on which the method is being called on
		// $this->username;
		return "$this->username added a new friend";
	}

}


// calling a method of the User class
echo $userOne->addFriend();

// shows different properties in class
print_r(get_class_vars('User'));

// shows different methods available in that class
print_r(get_class_methods());
```

### Setting

we can set the properties to another value we desire

```php

// 
$userOne->username="kofi";
$userOne->email="karsoft93@gmail.com"
```


## Constructors

Use a constructor function to run the moment we instantiate a class

<br>

```php
class User {

	// public makes it for these properties to be accessed by the object later
	public $username;
	public $email;
	//constructor function to make class able to access parameters

	public function __construct($username, $email){
		$this->username= $usename;
		$this->email= $email;
	}


	public function addFriend(){
		// this refers to the instance on which the method is being called on
		// $this->username;
		return "$this->username added a new friend";
	}

}


// instatiating and filling object with parameters
echo $userOne = new User('kofiramos','kofiramos87@fmail.com');
```

## Access Modifiers

Access Modifiers defines the access scopes of methods and properties of a class.


- `public`  makes properties and methods accessible inside and outside the class
- `private` makes properties and methods accessible only inside the class but not outside the class


## Getters and Setters


### Getters

creating getters to be able to access private properties

```php
class User {

 	public $username;
	private $email; // private property
	//constructor function to make class able to access parameters

	public function __construct($username, $email){
		$this->username= $usename;
		$this->email= $email;
	}

	//getter for email

	public function getEmail(){
		return $this->email;
	}


	public function addFriend(){
		// this refers to the instance on which the method is being called on
		// $this->username;
		return "$this->username added a new friend";
	}

}


// echoing the the email through the method
echo $userOne->getEmail();
```

### Setters

Updating private property with setters



```php
class User {

 	public $username;
	private $email; // private property
	//constructor function to make class able to access parameters

	public function __construct($username, $email){
		$this->username= $usename;
		$this->email= $email;
	}

	//getter for email

	public function getEmail(){
		return $this->email;
	}

	//setter 

	public function setEmail($email){
		//checking if @ exists in the string to confirm it's an email
		if(strpos($mail,'@') > -1):
			$this->email = $email;
		endif;
	}


	public function addFriend(){
		// this refers to the instance on which the method is being called on
		// $this->username;
		return "$this->username added a new friend";
	}

	public function message(){
		return "$this->email person sent a message";
	}

}


// echoing the the email through the method
echo $userOne->getEmail();

//setting email
$userOne->setEmail('kar@zmail.com');
```


## Inherintance

It's when one calss inherits properties & methods from another class

```php

class AdminUser extends User{

	public $level;
	public function __construct($username,$email,$level){
		$this->level = $level;

		// this is to get access and inherit User class properties
		parent::__contstruct($username,$eimail);
	}
	
}

// instantiating a AdminUser object

$userThree = new AdminUser('Ramos','Kofiramos9238@zmail.com',5);
```

### Overriding properties and methods

```php
class AdminUser extends User{

	public $level;
	public $role="admin"; // overriding parent properties


	public function __construct($username,$email,$level){
		$this->level = $level;

		// this is to get access and inherit User class properties
		parent::__contstruct($username,$eimail);
	}

	// can't be accessed because it's a private property
	public function message(){
		return "$this->email, an admin, sent a message;"
	}
	
}


```

### Dealing with protected properties

Protected properties behave as private but they can be used between classes but not outside the classes.


```php
class User{
	protected $email;
}

class AdminUser extends User{

	public $level;
	public $role="admin"; // overriding parent properties


	public function __construct($username,$email,$level){
		$this->level = $level;

		// this is to get access and inherit User class properties
		parent::__contstruct($username,$eimail);
	}

	public function message(){
		return "$this->email, an admin, sent a message;"
	}
	
}


```


## Magic methods

`__contstruct`, `__distruct` and `__clone`



### Distruct method

This removes any instance references after all methods have been  executed
<br>

```php

class AdminUser extends User{

	public $level;
	public $role="admin"; // overriding parent properties


	public function __construct($username,$email,$level){
		$this->level = $level;

		// this is to get access and inherit User class properties
		parent::__contstruct($username,$eimail);
	}

	public function __destruct(){
		echo "the user $this->username was removed"
	}

	public function message(){
		return "$this->email, an admin, sent a message;"
	}
	
}
```


<br>

### Clone method


this is used to clone methods and properties

```php

class AdminUser extends User{

	public $level;
	public $role="admin"; // overriding parent properties


	public function __construct($username,$email,$level){
		$this->level = $level;

		// this is to get access and inherit User class properties
		parent::__contstruct($username,$eimail);
	}

	public function __destruct(){
		echo "the user $this->username was removed"
	}

	public function __clone(){
		$this->email = $his->email. '(cloned)';
	}

	public function message(){
		return "$this->email, an admin, sent a message;"
	}
	
}
$userFour = clone $userOne;

```

## Static Properties and Methods

They are accessed directly from the class and not an instance.


```php
 
 class Weather {

 	public static $conditions = ['cold','mild','warm'];

 	// converts from celsius to farenheit
 	public static function celsiusToFarenheit($c){

 		return $c * 9 / 5 + 32;
 	}

 	public static function determineTempCondition($f){
 		if($f < 40){
 			return self::$condition[0]; // self is the equivalent of $this in static properties and methods
 		}else if ($f < 70){
 			return self::$condition[1];
 		}else{
 			return self::$condition[2];
 		}
 	}

 }

//accessing static properties
 print_r(weather::$conditions);

// accessing static method
echo Weather::celsiusToFarenheit(20);
```




