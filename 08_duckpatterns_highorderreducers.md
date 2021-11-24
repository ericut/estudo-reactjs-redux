# Ducks Patterns & High Order Reducers

## Ducks Patterns

- Exportar como padrão uma função chamada reducer()
- Exportar action creators como funções
- Action types tem que ter a forma de UPPERCASE
  -- `const EXEMPLO = "my_app/pasta/UPPERCASE_ACTION_TYPE"`

## Higher Order Reducers

```javascript
// exemplo de alta ordem dos reducers
const withPagination = (section, reducer) => (state, action) => {
  switch (action.type) {
    case `${section}_GO_NEXT_PAGE`: {
      return { ...state, page: state.page + 1 };
    }
  }
  // outras ações
  default: {
    return reducer(state, action)
  }
};
```

```javascript
export default createStore(
  combineReducers({
    users: withPagination('USERS', users),
    articles: withPagination('ARTICLES', articles),
    login,
  })
);
```
