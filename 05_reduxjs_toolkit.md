# @reduxjs/toolkit

Ferramenta que tornaram o Redux no React mais acessível proporcionando maior facilidade no desenvolvimento

## Algumas funcionalidades

### configureStore (redux-thunk + Redux DevTools Ext)

```javascript
import { configureStore } from '@reduxjs/toolkit';
import rootReducer from './reducers';

const store = configureStore({ reducer: rootReducer });
```

### createReducer (immer.js)

Criar um reducer com Builder, podendo acessar todas as funções no Reducer

```javascript
import { createAction, createReducer } from '@reduxjs/toolkit';
const increment = createAction('counter/increment');
const decrement = createAction('counter/decrement');
const incrementByAmount = createAction < number > 'counter/incrementByAmount';

const initialState = { value: 0 };

const counterReducer = createReducer(initialState, (builder) => {
  builder
    .addCase(increment, (state, action) => {
      state.value++;
    })
    .addCase(decrement, (state, action) => {
      state.value--;
    })
    .addCase(incrementByAmount, (state, action) => {
      state.value += action.payload;
    });
});
```

### createAction

```javascript
import { createAction } from '@reduxjs/toolkit';

const increment = createAction('counter/increment');

let action = increment();

action = increment(3);

console.log(increment.toString());
```

### createSlice (reducers + actions)

```javascript
import { createSlice, PayloadAction } from '@reduxjs/toolkit';

const initialState = { value: 0 }

const counterSlice = createSlice({
  name: 'counter',
  initialState,
  reducers: {
    increment(state) {
      state.value++
    },
    decrement(state) {
      state.value--
    }
    incrementByAmount(state, action: PayloadAction<number> {
      state.value += action.payload
    })
  }
})

export const { increment, decrement, incrementByAmount } = counterSlice.actions
export default counterSlice.reducer
```
