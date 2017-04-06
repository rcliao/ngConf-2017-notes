# formControl frekas: Redux edition

## Slides

https://github.com/renvrant/formcontrol-freaks

## Why?

* Lower maintainance cost.
* Centralizes form data
* Declarative and template-driven forms (with validations)
* Pure JS functions

## In this talk

* Form + Redux
* Add form data to state
* Support multi-entry fields

## Libraries

* Redux & angular-redux
* Rambda

## One reducer to rule them all

## Form can be defined with Type

## Trick

Subscribe to `ngForm.valueChanges.debounceTime(0).subscribe;` to send action
to Redux

## Validation

Use validation as selectors from Redux. We can use selector to compute if the 
data is valid in the store or what not.
