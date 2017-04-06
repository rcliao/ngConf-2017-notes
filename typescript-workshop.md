# Diving into TypeScript

## Slide

http://codewithdan.me/ts-es2015-in60

## TypeScript overview

* TypeScript and ES2015
* Modules and classes
* Type and interfaces
* Arrow functions
* Template strings
* Destructing
* Default and rest parameters

## Why TypeScript?

* Guard rails
* The future, today
	* async, await today!
* Detect errors at dev time
* Intellisense
* Enchanced tooling

## Interface

```ts
inteface ISettings {
	name: string;
	color?: string
}

class Unicron {
	constructor(public settings: ISettings) { }

	getDetail() {
		return `${settings.name} - ${settings.color}`;
	}
}
```

> Can use Inteface for constuctor to reduce the number of parameters passing in


