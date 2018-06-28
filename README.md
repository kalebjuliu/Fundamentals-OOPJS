# OOP JS
Snippet of OOP JS code

## Sub Classes

``` javascript

class Person {
  constructor(firstName, lastName){
    this.firstName = firstName;
    this.lastName = lastName;
  }
  greeting(){
    return `Hello there ${this.firstName} ${this.lastName}`
  }
}

class Customer extends Person {
  constructor(firstName, lastName, phone, membership){
    super(firstName, lastName)
    this.phone = phone;
    this.membership = membership;
  }
  static getMembershipCost(){
    return 500;
  }
}

const john = new Customer('John', 'Doe', '555-555-555', 'Standard');

console.log(john);
console.log(john.greeting());
console.log(Customer.getMembershipCost());

```

## ES6 Classes

``` javascript

class Person {
  constructor(firstName, lastName, dob){
    this.firstName = firstName;
    this.lastName = lastName;
    this.birthday = new Date(dob);
  }
  greeting(){
    return `Hello there ${this.firstName} ${this.lastName}`
  }
  calculateAge(){
    const diff = new Date(now) - this.birthday.getTime();
    const ageDate = new Date(diff);
    return Math.abs(ageDate.getUTCFullYear() -1970 
   }
}



const john = new Customer('John', 'Doe', '11-13-1980');


```

## Constructor

// Person constructor
 function Person(firstName, lastName, dob) {
   this.firstName = firstName;
   this.lastName = lastName;
   this.birthday = new Date(dob);
   this.calculateAge = function(){
      const diff =  Date.now() - this.birthday.getTime();
      const ageDate = new Date(diff);
      return Math.abs(ageDate.getUTCFullYear() - 1970);
    }
 }

 // Calculate age
 Person.prototype.calculateAge = function(){
   const diff =  Date.now() - this.birthday.getTime();
   const ageDate = new Date(diff);
   return Math.abs(ageDate.getUTCFullYear() - 1970);
 }

 // Get full name
 Person.prototype.getFullName = function(){
   return `${this.firstName} ${this.lastName}`;
 }

 // Gets Married
 Person.prototype.getsMaried = function(newLastName){
   this.lastName = newLastName;
 }




 const john = new Person('John', 'Doe', '8-12-90');
 const mary = new Person('Mary', 'Johnson', 'March 20 1978');



 console.log(mary);



// console.log(john.calculateAge());
// console.log(mary.getFullName());
// mary.getsMaried('Smith');
// console.log(mary.getFullName());
// console.log(mary.hasOwnProperty('firstName'));
// console.log(mary.hasOwnProperty('getFullName'));

## Prototypal Inheritance

function Person(firstName,lastName){
   this.firstName = firstName;   
   this.lastName = lastName;
 }

 Person.prototype.greeting = function(){
   return `Hello there ${this.firstName} ${this.lastName}`;
 }

 const person1 = new Person('Kaleb' , 'Juliu');
 console.log(person1.greeting());

//Customer constructor
 function Customer(firstName, lastName, phone, membership){
   Person.call(this, firstName, lastName);
   this.phone = phone;
   this.membership = membership;
 }

 //Inherit the Person prototype methods
 Customer.prototype = Object.create(Person.prototype);

 //Make customer.prototype return Customer()
 Customer.prototype.constructor = Customer;

 //Create Customer
 const customer1 = new Customer('Tom', 'Jerry', '555-555-555', 'Standard')
 console.log(customer1);

 //Making a custom Customer.greeting
 Customer.prototype.greeting = function(){
   return `Hello there ${this.firstName} ${this.lastName} welcome to our company`;
 }

 console.log(customer1.greeting());
