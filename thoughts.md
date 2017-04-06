# Personal Thoughts

## Context

This document stores a couple of my personal thoughts while listening to 
presentations in ngConf such as what prevents me from using Angular in production.

## Blocking stones

### Build system

First of all, the biggest blocking point that prevents me from using Angular 
in production is build system and configuration. In my work environment, I have
to make sure the Angular app works with the existing build system and allows the
server side application to loads up such assets (Angular).

This implies the first blocking stone to use Angular on production is actually
build system.

### Learning curve

After that, in my work, we have a team that is jumping between React and AngularJS.
To make it worse, most recent applications are written in React with a lof of its
own hack to get component working. As this leads on, it becomes harder and harder
to refactor into a single system or what not.

Current workflow is to code reusable components in WebComponent.js and have AngularJS
& React to handle higher level logic (such as routing & business logic). This works
for a while, but this requires developers to know even more than just single frameowrk.
As result, most of time, we cant really utilize a framework well and leaning toward
direct DOM manipulation. This also leads to higher chance of bugs.

### Tols

Enough of the situation rant, third point that blocks me from using Angular on 
prod is the fact having a lot of tools in the framework built in (TypeScript,
RxJS & new build system). On my end, I'm getting used to it more and more as I
use Angular more on my free time. This makes me scared to push it to production
as I will need to teach/mentor other developers to pick up knowledge. I don't
think I have enough time and resouce to do that.

## Future maintainence

Assuming moving with Angular, my next concern is how we maintain application 
modules. In my work, it's very common to reuse components in between 
applications. This leads to the direction that we need a way to define common
components that is reusable and sharable between applications while keeping up
the speed of feature development.

The biggest challenge of the existing workflow is to define common elements and
maintain such elements. For most of time, developers cant maintain this element.
Due to that even reusing same element, UI/UX designer still would like to tweak
this element on one place but not the other, which makes developer to just copy
and paste the element with new tweak. Thus, leading to duplication of elements and
higher maintainence cost.

Continuing Angular or what not, I need to define this workflow to create and 
maintain the common elements (like custom modal, custom file uploader ... etc.).

Angular seems to have ngModule so that it's easier to split code and reuse. 
However, I'll need to figure out a guidelines for modules.

## Advantage of Angular

Angular has a couple unique supports out of box or some refers to high learning
curve:

* TypeScript
* RxJS
* Angular CLI
* Dependency Injection (Testing made easy)

### Why is TypeScript good?

TypeScript gives IDE like feature in text editor like VS Code. For example, you 
can easily do intellisense, navigate by command click method name and so on.
Moreover, TypeScript is a strong typed language. This implies the type testing
is implicitly done and it will reduce the chance of runtime error in application.

Overall, TypeScript is a nice language. One can argue they have to learn new 
language coming from the JavaScript background. However, with the newest version
of TypeScript, you can simply replace the `.js` file to `.ts` file to begin with.
And slowly, you can replace the arguments to strong type one by one. This is, I
think the path transitioning into TypeScript.

In addition to strong type, developers may start to use 
[Domain Driven Design (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design) 
on front end application. In my opinion, DDD leads to easier to understand code.
I'm gonig to use Page object as example since I work for CMS system for past 3 
years. Page can have some special methods in it like page layout factory. 
Usually, front end application scatters these code to handle layout construction
everywhere (or at least in my experience). Worst of all, the code is duplicated
on many different components. Some better developers may create a utilities class
to hold such methods. However, other developers to came into this system without
any previous knowledge or documentation may find it confusing to follow code.


### Why is RxJS good?

A brand new toy for developers to code! No really, it's a nice way to handle 
async actions such as http request, handling browser events ... etc. Aync events
usually leads down to callback hell; however, with ES6, JavaScript developers can
start to use Promise to handle individual http request without going into the
callback hell pattern. Nevertheless, if the developer needs to make multiple
http requests, they start to suffer into the indentation hell (which is similar
to callback hell but ending up high amount of indentations). Observable helps
in this case, Observables are like Promise but handles multiple of them well.

### Why is Angular-CLI good?

Allows developer to use CLI to handle common operations like creating new 
componenets. This reduce the chance of going off track and helps to keep high
consistency of the code. Moreover, this allows the framework later to take 
advantage of the application structure to migrate to newer version! Amazing!
