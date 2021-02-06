# Project: APM-RXJS-START

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 10.0.1.

## Janban Task #1: Flash Card and Code Examples in "https://stackblitz.com/"

### Task: Handling Errors

1. Module #5 Going Reactive - Handling Errors Demo
2. "Catch and Replace" code

### Example use: Replace original Observable stream with

1. An Observable created from hard-coded or local data.
2. An Observable that emits emty value OR empty array
3. Return RxJS constant EMPTY

### Catch and Replace

```TypeScript
/**
 * Product Service
 */
return this.http.get<Product[]>(this.productsUrl)
   .pipe(
      catchError(err => {
        // stream is stopped, err emited
        console.error(err); 
        // new stream emited default array of products
        return of ([
          {id:1 productName: 'cart'},
          {id:2, poductName: 'hammer'}
        ]);
      });
   )
```

```TypeScript
/**
 * Product List Component
 */
ngOnInit() {
  this.productService.getProducts()
    .subscribe(
      // the observers next method is fired with the new default array
      products => this.products = products,
      // the err is not raised because the err has been caught and replaced
      err => this.errorMessage = err
    );
}
```
