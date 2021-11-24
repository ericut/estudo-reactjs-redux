# Gerenciando a Store do Redux

## Dev Experience

Aplicações e extensões para verificar comportamento do Redux nas aplicações.

### Redux Devtools Ext

Extensão do Chrome

```javascript
  // na chamada do createStore
  preloadedState: {},
  window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE(),
```

### redux-devtools-extension

Lib do próprio Redux/React

`yarn --save redux-devtools-extension`

```javascript
import { createStore, applyMiddleware } from 'redux';
import { composeWithDevTools } from 'redux-devtools-extension';
const store = createStore(reducer, composeWithDevTools(applyMiddleware(...middleware)));
```

## Melhores práticas

### Redux Style Guide

Como deve desenhar os pedaços de códigos relacionados ao Redux

- Não mutaciona estado
- Reducers não devem ter efeitos colaterais
- Não adicione valores não serializáveis nos estados e nas ações
- Use somente um Store por Aplicação
