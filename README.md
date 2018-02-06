# Project Overview

In this project you are given a web-based application that reads RSS feeds. The original developer of this application clearly saw the value in testing, they've already included [Jasmine](http://jasmine.github.io/) and even started writing their first test suite! Unfortunately, they decided to move on to start their own company and we're now left with an application with an incomplete test suite. That's where you come in.


## Why this Project?

Testing is an important part of the development process and many organizations practice a standard of development known as "test-driven development". This is when developers write tests first, before they ever start developing their application. All the tests initially fail and then they start writing application code to make these tests pass.

Whether you work in an organization that uses test-driven development or in an organization that uses tests to make sure future feature development doesn't break existing features, it's an important skill to have!


## What will I learn?

You will learn how to use Jasmine to write a number of tests against a pre-existing application. These will test the underlying business logic of the application as well as the event handling and DOM manipulation.


## How will this help my career?

* Writing effective tests requires analyzing multiple aspects of an application including the HTML, CSS and JavaScript - an extremely important skill when changing teams or joining a new company.
* Good tests give you the ability to quickly analyze whether new code breaks an existing feature within your codebase, without having to manually test all of the functionality.

## Change Log
1.  write test code to ensure URL defined and not empty.
```
it('URLs are defined', function () {
            for (var i = 0; i < allFeeds.length; i++) {
                expect(allFeeds[i].url).toBeDefined();
                expect(allFeeds[i].url.length).not.toBe(0)

            }

        });
``` 
2. Write test code to ensure name define and not empty
```
it('names are defined', function () {
            for (var i = 0; i < allFeeds.length; i++) {
                expect(allFeeds[i].name).toBeDefined();
                expect(allFeeds[i].name.length).not.toBe(0)

            }

        })
```
3. Create new test suite named `"The menu"`.
```
 describe('The menu', function () {
 
 });
```
4. Write test code to ensures the menu element is hidden by default.
```
it('hidden by default', function () {
            expect($('body').hasClass('menu-hidden')).toBe(true);
        });
```
5. Write test code to ensures the menu changes visibility when the menu icon is clicked.
```
it("changes visibility when the menu icon is clicked", function () {
            $(".menu-icon-link").trigger("click");
            expect($('body').hasClass('menu-hidden')).toBe(false);//visible
            $(".menu-icon-link").trigger("click");
            expect($('body').hasClass('menu-hidden')).toBe(true);//invisible
        });
``` 
6. Create new test suite named `"Initial Entries"`.
```
describe("Initial Entries", function () {

});
``` 
7. Write test code to ensures when the `loadFeed` function is called and completes its work, there is at least a single `.entry` element within the `.feed` container.
```
beforeEach(function (done) {
            loadFeed(0, done);
        });

        it("has at least a single .entry element within the .feed container when loadFeed function call", function () {
            expect($(".feed .entry").length).toBeGreaterThan(0);
        })
``` 
8. Create test suite named `"New Feed Selection"`.
```
describe("New Feed Selection", function () {

});
```
9.  Write a test code to ensures when a new feed is loaded by the `loadFeed` function that the content actually changes.
```
        var oldLoadFeed;
        var newLoadFeed;
        beforeEach(function (done) {
            loadFeed(0, function () {
                oldLoadFeed = $(".feed").html();
                console.log(oldLoadFeed);
                loadFeed(2, function () {
                    newLoadFeed = $(".feed").html();
                    console.log(newLoadFeed);
                    done();
                });
            });

        });


        it("when a new feed is loaded by the loadFeed function that the content actually changes", function (done) {
            expect(newLoadFeed).not.toEqual(oldLoadFeed);
            console.log("the old is : " + oldLoadFeed);
            console.log("the new is : " + newLoadFeed);
            done();
        });
```
