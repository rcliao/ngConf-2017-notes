# RxJS - the good parts

## Common operators

### Creating observables

* Observable.of(a, b, c)
* Observable.from([a, b, c]) -- iterable

### Array like operators

* filter
* map
* reduce
* take

### Useful for browser events

* debounce
	* waits X amount of time till last one finishes before continuing
* throttle

### Combining observables

* switchMap
	* cancels all non finished calls and carries on with current one
* mergeMap
	* returns a new observable that will be used henceforth
* zip
	* outputs continuously matching streams
* combineLatest
	* whenever a change happens, take latest from all an cotninue on

### Useful utils

* toArray
	* waits until array is done and combines into 1 array
* share

### In case of error

* retry

## What happened when error happens

* onError
* Halt the sequences
* two levels of erros: class and instances

## Typed

* Generic parameters in Observable like `Observable<T>`

## Performance

* RxJS is actually nice in performance than normal array

