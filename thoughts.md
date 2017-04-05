# Personal Thoughts

## Context

This document stores a couple of my personal thoughts while listening to 
presentations in ngConf such as what prevents me from using Angular in production.

## Blocking stones

First of all, the biggest blocking point that prevents me from using Angular 
in production is build system and configuration. In my work environment, I have
to make sure the Angular app works with the existing build system and allows the
server side application to loads up such assets (Angular).

This implies the first blocking stone to use Angular on production is actually
build system.

After that, in my work, we have a team that is jumping between React and AngularJS.
To make it worse, most recent applications are written in React with a lof of its
own hack to get component working. As this leads on, it becomes harder and hader
to refactor into a single system or what not.

Current workflow is to code reusable components in WebComponent.js and have AngularJS
& React to handle higher level logic (such as routing & business logic). This works
for a while, but this requires developers to know even more than just single frameowrk.
As result, most of time, we cant really utilize a framework well and leaning toward
direct DOM manipulation. This also leads to higher chance of bugs.

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
