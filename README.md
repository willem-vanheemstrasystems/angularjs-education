# angularjs-education
AngularJS - Education

#AngularJS Education by Brian Petro

Content:

01 Why You Should Be Using Angular 2

02 Learn the core concepts behind ES6/TypeScript 

03 How to Transpile/compile TypeScript to JavaScript

04 Get started with the Angular CLI

05 The Role of Components in Angular 2

06 Decorators in Components (aka metadata)

07 Bind data to views to create a masterpiece

08 When dependency injection and providers make sense

09 Input and output properties

10 Managing remote data calls using Angular 2 services

11 Where to use Http and RxJS Observables

12 Angular 2 routing and page navigation

##01 Why You Should Be Using Angular 2

Written by Joe Eames, Founder, ng-conf (the AngularJS conference)

Angular 2 is just about to release, and many developers are asking themselves, “should I learn Angular 2?” The short answer is yes, but we’ll look at some of the reasons why.

First, it’s a good idea to understand where front end web development is at currently. A few short years ago, there were very few choices, but today, we have quite a few very good frameworks to choose from. This is a better situation than when there were no choices, but it can also lead to analysis paralysis, where we can’t make a decision because there’s just too many good choices. In addition, we have seen a recent rash of tool fatigue - developers complaining that there is just too many moving pieces in even a simple app, and for new developers especially, this can be a particularly challenging environment in which to try to get work done.
 
***Angular 1***

Although Angular 1 is a great framework, it’s beginning to show its age. Even though it is still gaining popularity, there are some fundamental problems with it. First and foremost is its performance. Angular 1 is fine for many sites, but it doesn’t take long before a developer can encounter a situation where Angular 1 experiences some speed problems. Second, Angular 1 was not built with modern tools and standards in mind. If you want to use it with a module system, you will be quickly disappointed with how much friction you experience. Finally it suffers from a bit of ambiguity in some of the different pieces. With the most recent version of Angular, you can accomplish the same thing with either a controller, a directive, or a component. So which one is the right one to use in a given situation can be problematic.

***Other Frameworks***

Although there are some great frameworks available now, they each have a few problems that a developer can experience. First off, many of these other frameworks have a much smaller adoption than Angular, so for both your career, and when trying to hire experienced talent, that can be a challenge. With Angular 2, it will become a natural choice for Angular 1 shops to write new projects in Angular 2, which will likely mean that the adoption for it will be very widespread.

Second, many other frameworks are partial solutions, unlike Angular, meaning that you may have to put together a lot of different pieces before you have everything you need to write your application.

Finally, some of the other frameworks were developed with an eye towards solving a specific kind of problem, and therefore they have a hard time existing in a typical enterprise environment with the usual trappings that come along, such as unit testing, localization, and accessibility.

***Angular 2***

Now that we’ve identified some issues with both Angular 1 and other frameworks, let’s look at how Angular 2 addresses these issues.

The first item of discussion will be performance. Angular 2 is fast. Blazing fast. No framework is faster. Some are right there with it neck and neck, but nothing is faster than Angular 2.

Next, Angular 2 was built with modern tools and standards in mind. It supports ES6 modules, tools like webpack and SystemJS, and has even helped push the standards by helping to pioneer decorators in ECMAScript.

The mental model of Angular 2 is much simplified from Angular 1. No longer do you have to choose between three similar concepts. Components handle everything.

Angular 2 is the natural successor to Angular 1, so it’s poised to become just as popular, if not even more so than Angular 1 was. That means that learning it will likely be good for your career, and down the road, you will have an easier time finding experienced Angular 2 developers.

Angular 2 is also a complete solution. It includes rendering, compilation, binding, server communication, and unit testing all together. No worry about trying to choose from twenty different libraries when you need to actually make a HTTP call.

Finally, Angular 2 was built from the ground up to solve the same problems Angular 1 solves: everything from simple demo apps to large enterprise-scale applications. It is highly testable, supports accessibility and localization. 

***Conclusion***

So, should you learn Angular 2? The answer is pretty obvious. It will definitely be a major player in the JavaScript framework scene for the foreseeable future. There’s no better time than today to learn Angular 2.

##02 Learn the core concepts behind ES6/TypeScript

One of the very common surprises that people have when learning about Angular 2 is its close ties with TypeScript. This relationship seemingly came out of nowhere, and many people have been asking questions about this. Additionally, developers may feel a little trepidation when faced with learning yet again something new. So let’s get a quick look at not only the rationale, but the absolute basics and how much of an additional learning curve TypeScript might add when learning Angular 2.
 
***History***

It’s easier to understand the present by understanding the past. When the Angular team started on Angular 2, they realized that with such a large undertaking, that having types would eliminate a large segment of possible bugs as they wrote the code for the framework. So internally they were interested in adding types to JavaScript. Furthermore, the dependency injection system of Angular 2 works better with types. So there was a good reason to use types not only within the source code of Angular 2, but also for developers using Angular 2. Additionally, one of the design goals for Angular 2 has always been for it to be forward looking. Using the latest version of JavaScript, ECMAScript 6, was a big part of that goal. So for now, some kind of transpiler is necessary.

When analyzing the existing tools, nothing quite matched the requirements they had. That gave birth to an internal language called AtScript. The team used this language for quite a while, but eventually ended up in a meeting with the TypeScript team where they looked at the few things they needed that were missing from TypeScript. This resulted in an agreement to have those items added to TypeScript. AtScript was dropped and the project was converted to TypeScript.

***What’s the Difference?***

Now TypeScript is by no means required to work with Angular 2. It just simplifies the code. Let’s take a quick look at what the same code looks like using TypeScript vs just regular old JavaScript.

Here’s a simple component written in JavaScript:
 
```javascript
(function(app) {
  app.HeroFormComponent = ng.core
    .Component({
      selector: 'hero-form',
      templateUrl: 'app/hero-form.component.html'
    })
    .Class({
      constructor: [function() {
        this.powers = ['Really Smart', 'Super Flexible', 'Super Hot', 'Weather Changer'];
        this.model = new app.Hero(18, 'Dr IQ', this.powers[0], 'Chuck Overstreet');
        this.submitted = false;
      }],
      setSubmitted: function(newValue) {
        this.submitted = newValue;
      },
    });
});
```

And here’s the same thing in TypeScript:
 
```javascript
import { Component } from '@angular/core';
import { Hero } from './hero';

@Component({
  selector: 'hero-form',
  templateUrl: 'app/hero-form.component.html'
})

export class HeroFormComponent {
  powers = ['Really Smart', 'Super Flexible', 'Super Hot', 'Weather Changer'];
  model = new Hero(18, 'Dr IQ', this.powers[0], 'Chuck Overstreet');
  submitted = false;
  setSubmitted(newValue: boolean) { this.submitted = newValue; }
}
```

Right off the bat, you can see that the TypeScript code is more succinct. Only 13 lines instead of 20. Additionally, once you understand the various ES6 and TypeScript constructs used, TypeScript is just more expressive. It takes less ceremony to express the same thing.
 

What About ES6?
There’s actually another piece involved in this whole thing that we haven’t really discussed. And that is ES6 (and ES7 and maybe even ES8). Much of the syntax that we’re seeing in the above TypeScript example is actually current and future versions of ECMAScript (JavaScript). So learning these features is important for working with Angular 2. Although there’s a clear difference between ECMAScript and TypeScript, we’re going to make it simple and just bundle it all up together, and look at the absolute minimum you need to know to work with Angular 2.


So What DO I Need to Know?
Understanding enough TypeScript to work with Angular 2 is actually a lot easier than you may first think. There’s four major features you need to know. We’ll get a very abbreviated explanation of each of these features. This won’t eliminate the need to do further learning, but this will be enough to let you tread water when looking at Angular 2 code and dealing with tutorials, and also give you a jump start if you happen to be attending our Ultimate Angular 2 Workshop in Florida this October (LINK HERE).


1. Import & Export
The import and export keywords you see in the above example is part of ECMAScript modules, introduced in ECMAScript 6. There’s a lot you CAN learn about them, but the absolutely necessary knowledge is pretty straightforward when dealing with Angular 2.

The import statements we see at the top lets us bring in pieces of the Angular 2 framework for us to use, and also lets us bring in other pieces of our own code for us to use. The syntax is very simple. The import keyword, followed by curly braces that contain whatever pieces we want to use, then the from keyword, and finally a string that indicates what file we’re pulling them from. In the above example code, line 1 imports the Component from the core of Angular. Line 2 refers to a file that was written by the developer named hero.ts (the extension is implied) and that file exists in the same directory. The way we know this is that it starts with a period. That means it’s a local file, not some library we’re accessing.

Finally, we will need to export what we’re creating in this file. In the case above, it’s the HeroFormComponent, which is represented by a class. So that class is exported. That lets another file use this component with its own import statement which might look something like this:
 



That’s it. If you can put together your imports and exports following the above pattern, you’re set.
 

2. Decorators
Probably the strangest looking syntax from our TypeScript example is the @Component on line 3. This is simply metadata that describes the HeroFormComponent class that is created on line 7. This is an ECMAScript feature called a decorator. Decorators are put before the code construct that they are decorating. In this case, it’s right before the class. So when the compiler sees this decorator, it will look for the very next thing, our HeroFormComponent class, and apply this decorator to that class.

Under the hood there’s a lot of interesting stuff going on, but for our purposes we only need to understand that each of the properties we specify in that decorator, the selector and the template URL will end up getting attached to the HeroFormComponent for the Angular 2 framework to use as it runs your application. Simple right?
 

3. Classes
Classes are the next feature we need to understand. Thankfully most languages support classes, so this will feel familiar to anyone who programs in just about any other language. If they look strange to you, no worries. They will soon feel very familiar. There’s only a couple things about classes you need to learn. First is how to specify properties of a class. We see this on lines 8, 10, and 11 of the above code. A property is created by specifying an identifier, and equals sign, and then a value. If you don’t have an initial value, you can just specify the identifier and skip the equals sign and the initial value.

The other feature that is important is the constructor, which is just a method named “constructor”. We don’t see an example of that in the above code, but here’s a quick example.
 



Here we have a constructor that takes in a name, and sets that name to an internal property which is also called “name”.

Here’s a tip: this pattern of taking in values in the constructor and setting them to internal properties is so common, there’s a shorthand syntax for that shown here:
 



This does the same thing as the above code but removes 2 lines of code just by adding the public keyword in front of the property name of the constructor. This creates a property “name” on the class that is visible to other objects. We can also use the “private” keyword instead if we don’t want external code to be able to see the property.

Taking advantage of this is easy. If this was the constructor for a class named Hero, then we can create a new hero like this:
 



This would create a hero with a name property set to “Mr. Imposter”.

Again, once we learn the pattern, then the code becomes very readable and easy to deal with.
 

4. Types
The final feature we need to understand is Types. Types are the only one of the four features we’re discussing that are specific to TypeScript. The rest are technically ECMAScript constructs.

Types are really rather simple. Just look for the colon. That separates an object from its type. There are three basic types: number, string, and boolean. Creating a variable of a specific type just involves creating the identifier, then a colon, then the type as shown here:
 



This creates a variable “name” that is of type string. Naturally if we try to assign 3 to it, then our TypeScript compiler will complain. It’s far more common to use this when creating properties of classes, in which case we simply omit the “var” from the above code, which would create a name property of type string.

We can use types in functions (even constructors) as we see here:
 



Here we have changed our constructor to note that the name must be a string. So if someone tries to send in a number or a boolean as the name when constructing a Hero, TypeScript will prevent it at compile time.

There’s a fourth type that is very important to know: the any type.
 



This type indicates that the variable can be assigned any value, which is the situation we’re used to in JavaScript. So the something variable can be assigned the value of 3, or true, or the string “Mr. Impostor”. It can even be assigned all three values at given points of time during the execution of your application.

The final commonly encountered type is the array type. Often we need an array, but we want to constrain the values of the array to be of a specific type. For example in line 8 of our sample code, we create an array of powers which are all of type string. We can create an empty array that can only contain strings with the following code:
 



This will mean that we can only add strings to the powers array. If we try to add a number or boolean, TypeScript will stop us.

There’s obviously more to TypeScript’s types than what little I’ve shown here, but really, this is the 20% that’ll get you 80% of the result. For further reading I recommend you check out the TypeScript documentation at http://www.typescriptlang.org/docs/tutorial.html.
