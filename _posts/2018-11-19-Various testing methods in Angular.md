---
layout: post
title: Various testing methods in Angular
subtitle: How do we test program in Angular?
tags: [testing, Angular]
---


## Why do we need testing?

Testing methods are approaches to ensure that our programs can run safely and correctly.

This often involves testing the product in certain specifications and won't create any effects when using the products outside.

Also, as the programs and softwares are built with more complex structure and various platforms, it would be a tons of work to do those checking. Therefore, we can use software testing methodologies to check the software (for example, does the product meets the specific requirements) in the easiest way.

![Various testing methods](https://www.inflectra.com/GraphicsViewer.aspx?url=~/Ideas/Topics/testing-methodologies.doc&name=wordml://03000001.png)

## Unit tesing

In this testing methods, each individual modules or components that made up program will be checked for specific requirements.

**Benefits of unit testing**

 1. Improve the design of implementations
 	In unit testings, it forces you to re-think the whole design of the program, as this the a commmon mistake happens in developers
 2. Allows you to add more featues without breaking the program
 	As you have the tests, you can easily change the code and implement new features without interrupt or break other parts.

## How to do unit test in Angular

For unit test, we would use Jasmine and Karma.

**What is Jasmine**

Jasmine is a javascript testing framework that supports a software development practice called ``Behaviour Driven Development`` (BDD).

Jasimine and BDD are written in human readable format, therefore non-technical people can understand them too.

For example:

``
function helloWorld() {
	return 'Hello world!';
}
``

In ``jasmine test spec``:

``
describe('Hello world', () => {
	it('says hello', () => {
	expect(helloWorld()) 
		.toEqual('Hello world!');
	});
});
``

For a deeper level of Jasmine, please go [here](https://codecraft.tv/courses/angular/unit-testing/jasmine-and-karma/).

**What is Karma?**

Karma allows us to test the code in the command line, in order to save time. It can also watch your development files for changes and re-run the tests automatically.

**Angular CLI - An easier way to set up the Jasmine and Karma**

As we created an Angular project in Angular CLI, it automatically generates unit tests using Jasmine and Karma.

If we create a Pipe using the CLI like so:

``
ng generate pipe My
``

This would create two files:
	- ``my-pipe.ts`` — This is the main code file where we put the code for the pipe.
	- ``my-pipe.spec.ts`` — This is the jasmine test suite for the pipe.

The spec file will have some code already bootstrapped, like so:

``
import { TestBed, async } from '@angular/core/testing';
import { MyPipe } from './my.pipe';

describe('Pipe: My', () => {
  it('create an instance', () => {
    let pipe = new MyPipe();
    expect(pipe).toBeTruthy();
  });
});
``

**Run the test**

	1. In the project root.
	2. Type ``ng serve``
	3. Watch how it goes ;) (It will automatically change when you change some codes in the project)
	
	
	
## Integration Testing

A tesing method that run the code as a group of many units combined together.

The purpose:
	- To find the bugs and faults between each intergrated units.
	
**Example of integration test:**
``

  beforeEach(
    async(() => {
      TestBed.configureTestingModule({
        providers: [SomeProvider],
        declarations: [DropzoneComponent, DocumentsComponent, FoldersComponent],
        schemas: [CUSTOM_ELEMENTS_SCHEMA]
      }).compileComponents();
    })
  );
  ``
  In integration tests the points of integration are tested:
  	- correct output events chain
	- correct input values chain
	

**Here's an example of unit test for you to compare with integration, you will be able to spot the differences:**

``
  beforeEach(
    async(() => {
      TestBed.configureTestingModule({
        providers: [SomeProvider],
        declarations: [DropzoneComponent],
        schemas: [CUSTOM_ELEMENTS_SCHEMA]
      }).compileComponents();
    })
  );
``



