# Aspectos da Arquitetura (API)

O código listado abaixo é conceitual

## Exemplo de projeto React

```
npx create-react-app my-app --template redux
```

## Reducer

```javascript
// reducer: store.getState()
function counterReducer(state = { value: 0 }, action) {
  switch (action.type) {
    case 'counter/incremented':
      return { value: state.value + 1 };
    case 'counter/decremented':
      return { value: state.value - 1 };
    default:
      return state;
  }
}
```

## Store

```javascript
// store: createStore()
const store = createStore(counterReducer);
```

## Actions

```javascript
// actions: store.dipatch()
store.dipatch({ type: 'counter/incremented' }); // {value: 1}
store.dipatch({ type: 'counter/incremented' }); // {value: 2}
store.dipatch({ type: 'counter/decremented' }); // {value: 1}
```

## View

Função que receberá a conexão com o redux

```javascript
// view: connect (react-redux)
function TodoList({todoList, toogleTodo}) {
  return (
    // render
  )
}
```

Função para expor propriedades para o componente relacionados ao store

```javascript
// view: connect (react-redux)
function mapStateToProps(state) {
  return { todoList: state.todos.allIds };
}
export default connect(mapStateToProps)(TodoList);
```

Função para despachar ações com propriedades, em vez de despachar na própria função

```javascript
// view: connect (react-redux)
function mapDispatchToProps(dispatch) {
  return {
    toogleTodo: (id) => dispatch({ type: 'todos/toggle', payload: id }),
  };
}
export default connect(mapStateToProps, mapDispatchToProps)(TodoList);
```

### View - Selectors

Selectors são funções retornam no estado

```javascript
function selectTodoList(state) {
  return state.todos.allIds;
}
//
function mapStateToProps(state) {
  return {
    todoList: selectTodoList(state),
  };
}
```
