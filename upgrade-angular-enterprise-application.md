# Upgrading Angular Enterprise Application

## NgUpgrade

* Upgrade individual component using NgUpgrade.
* Can mix and match AngularJS and Angular modules

## Upgrade strategies

* Vertical slice vs horizontal slice

## Upgrade Shell

* Upgrade the top level shell to Angular first and loads up AngularJS later

```ts
ngOnInit() {
	this.upgrade.boostrap(document.body, ["Angular1AppModule"]);
}
```

## Strategy: Vertical Slicing

* Slice route by route (screen by screen or feature by feature)
* Pros
	* Easier to debug
	* Encapsulates migration
	* Application are faster
* Cons
	* Code duplication
	* Coarse-grained

## Strategy: Horizontal Slicing

* Bottom up
* Pros
	* Easy to get started
	* No code duplication
* Cons
	* Harder to debug
	* Harder to coordinate multiple teams
	* Hinders refactoring and tooling
	* Hinders performance

## Managing URLs

* Single ownership
	* Managed by AngularJS router or Angular route

## Strategy: Sibling outlets

```ts
@Componenet({
	// ...
	template: `
		<router-outlet></router-outlet>
		<ui-route></ui-route>
	`
})
// with Custom url handler to skip AngularJS routes
```

