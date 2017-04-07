# ngrx with forms

## Github repo

https://github.com/CodeSequence/ngrx-workshop

## Define actions

```ts
import { Action } from '@ngrx/store';
improt { Book } from './book';

export const SEARCH = '[Books] Search';
export const SEARCH_SUCCESS = '[Books] Search Success';

export class Search implements Action  {
	readonly type = SEARCH;
	constructor (public payload: string) {}
}
```

## Define reducers

```ts
interface Reducer<State> {
	(state: State, action: Action): State;
}
```

```ts
import { Book } from './book';
import { ALL, SEARCH } from './SearchActions';

export interface State {
	searchTerms: string;
	results: Book;
}

export function reducer(state = initialState, action: ALL) {
	switch (action.type) {
	case SEARCH: {
		return {
			...state,
			searchTerms: action.payload
		}
	}
	// more cases
	}
}
```

## Inject store service

```ts
class Store<State> extends Observable<State> {
	select<T>(s: (v: State) => T): Observable<T>;
}
```


