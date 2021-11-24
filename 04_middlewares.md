# Middlewares

Providencia ponto entre um dispatch e uma action, até o momento que isso encontre o reducer

## Definição

```javascript
type MiddlewareAPI = { dispatch: Dispatch, getState: () => State };
type Middleware = (api: MiddlewareAPI) => (next: Dispatch) => Dispatch;
```

```javascript
// função recebe o middleware
function logger({ getState }) {
  // retorna uma função que retorna outra função
  return (next) => (action) => {
    // a ação recebe um retorno
    console.log('will dispatch', action);
    const returnValue = next(action);

    // retorna a próxima função
    console.log('state after dispatch', getState());
    return returnValue;
  };
}
```

```javascript
const store = createStore(reducer, {}, applyMiddleware(logger));
```

## Heranças de Store

```javascript
type StoreEnhancer = (next: StoreCreator) => StoreCreator;
```
