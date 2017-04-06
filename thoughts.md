# Personal Thoughts

## Context

This document stores my personal thoughts on Angular while listening to presentations 
in ngConf such as what prevents me from using Angular in production and my 
strategies of implementing Angular in production environment.

## Blocking stones

Before we start, I need to state -- **I love Angular**. But I'm not using Angular in
production yet and not plan to use it before ngConf. Why? There are some blocking
stones for me to consider using it on my work environments.

### Build system

First of all, the biggest blocking point that prevents me from using Angular 
in production is the **build system and configuration**. In my work, I have
to make sure the Angular app works with the existing build system (GulpJS) and 
allows the static server to loads up built assets.

### Existing front-end architecture

After that, we have a team that is jumping between React, AngularJS and even Vue.js.
To make it worse, most recent applications are written in React with a lof of its
own hacks to get custom component working. As this leads on, it becomes harder 
and harder to refactor into a single system or what not. Don't get me wrong, the
way we are doing it now leads to framework agnostic but with a cost

Current workflow is to code lower level reusable components in WebComponent.js 
and have AngularJS & React to handle higher level business logic (such as routing 
& domain-specific logic). This works well for a while, but this requires developers 
to know even more than just single frameowrk. As result, most of time, we cant 
really utilize a framework well and lean toward direct DOM manipulation. Also,
this creates higher chance of bugs like sometimes we forgot to remove event 
listener on custom element deattach.

### Learning curve

Enough of the situation rant, third blocking stone from using Angular on 
prod is the fact having a lot of tools in the framework built in (TypeScript,
RxJS & new build system like SystemJS or Webpack). Although, I'm getting used to 
it more and more as I use Angular more on my free time. This terrifies me to use 
Angular to production as I will need to scale these knowledge to other developers. 
I don't think I have enough time and resouce to do that.

On the other hand, if utilizing these tools correctly, it should reduce the time
to scale knowledge as there should be enough online resouces.

## Future maintainence

Assuming moving with Angular, my next concern is how we maintain application 
structures. In my work, it's very common to reuse components in between 
applications (new and old). This leads to the decision that we need to define common
components that is reusable and sharable between applications while keeping up
the speed of new feature development.

The biggest challenge of the existing workflow is to define common components and
maintain such elements. For most of time, developers cant maintain this element; 
because even reusing same element, UI/UX designers still would like to tweak
the element on one place but not the other (to avoid regression) -- which makes 
developer to just copy and paste the component with new tweak on new feature but 
not modify the old feature ones. Thus, leading to duplication of components and
higher maintainence cost.

Continuing Angular or what not, we need to define this workflow to create and 
maintain the common elements (like custom modal, custom file uploader ... etc.).

Angular seems to have ngModule so that it's easier to split code and reuse. 
However, we'll need to figure out a guidelines for modules.

## Advantage of Angular

So why Angular? From the conference, there a couple things that attracts me as
developer to use Angular over others:

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

Last but not least, TypeScript is a language that back-end developers can find 
themselves familiar and get started with very quickly. Most of features from the
back-end strong typed languages like Java is *optionally* supported in TypeScript.
This means back-end developers should be able to get started very quickly or
even better back-end developers can start to sync up the domain object logic
from the back-end to front-end themselves.

### Why is RxJS good?

A brand new toy for developers to code! No really, it's a nice way to handle 
async actions such as http request, handling browser events ... etc. Aync events
usually leads down to callback hell; however, with ES6, JavaScript developers can
start to use Promise to handle individual http request without going into the
callback hell pattern. Nevertheless, if the developer needs to make multiple
http requests, they start to suffer into the indentation hell (which is similar
to callback hell but ending up high amount of indentations). Observable helps
in this case, Observables are like Promise but handles multiple of them well.

### Why is [Angular-CLI](https://github.com/angular/angular-cli) good?

Allows developer to use CLI to handle common operations like creating new 
componenets. This reduce the chance of going off track and helps to keep high
consistency of the code. Moreover, this allows the framework later to take 
advantage of the application structure to migrate to newer version! Amazing!

In example, one can use `ng new PROJECT_NAME` to create a new project.

With so many features implemented out of box from Angular CLI, my concern on the
CLI is how CLI can integrate with existing build system. We are using GulpJS to
build system and put them into the right folder for Apache httpd module to serve
static assets up. In addition, how does the back-end templating being supported
with Angular index.html. This remains to me as a challenge to resolve in the
front-end build system.

### Why is Dependency Injection good?

This implies testing is done in mind from the beginning of the framework. To do
testing, one usually needs to create their own Dependency Injection to mock data
for testing. And replace such data source on production usage and so on.

Angular supports Dependency Injection from the framework level. This allows 
Angular to do testing without any sort of magic. One who understands Dependency
Injection would know how testing works behind the scene.
