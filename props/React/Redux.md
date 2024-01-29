
Использование `Redux` должно соответствовать подходу `функционального программирования`

**! Внимание !**
! При `обновлении значения` из Redux хранилища `в родительском компоненте`, приводит к `перезагрузке всех дочерних компонентов`, что сбрасывает их состояние.

### _Функциональное программирование_

![[func programming]]

## _store/action/dispatch/reducer_

<img src="https://redux.js.org/assets/images/ReduxDataFlowDiagram-49fa8c3968371d9ef6f2a1486bd40a26.gif" >

### _Store (`хранилище`)_

- **Определение:** Хранилище - объект, который `содержит состояние` всего приложения.
- **Функции:**
  - `Хранение` текущего `состояния` приложения.
  - Позволяет `getState`(`получать`) текущее `состояние`.
  - Позволяет `dispatch`(`отправлять/обновлять`) `состояние` с помощью `dispatch(action)`.
  - Позволяет `subscribe`(`добавлять слушателей`) для `отслеживания изменений` состояния.

```
import { createStore } from 'redux';

const store = createStore(counterReducer);
```

`subscribe` используется для `регистрации функции обратного вызова`, которая будет `вызываться` каждый раз, `когда` происходит `изменение состояния`.
Функция `callback` будет получать `текущее состояние` в качестве аргумента.

```
const store = createStore(reducer);

const handleChange = () => {
  const currentState = store.getState();
  console.log('Current state:', currentState);
};

const unsubscribe = store.subscribe(handleChange);

/=/ Вызовите unsubscribe, чтобы отменить подписку
// unsubscribe();

/=/ Когда происходит изменение состояния, handleChange будет вызываться
```

### _Action (`действие`)_

- **Определение:** Действие - это объект, который `описывает изменение состояния` в приложении. Это единственный способ изменения состояния в Redux.
- **Структура:** `{ type: 'НАЗВАНИЕ_ДЕЙСТВИЯ', payload: данные }`
  - `type` - что необходимо сделать
  - `payload` - `вспомогательные данные` которые необходимы для того чтобы `найти`
    и/или `установить` новые данные, и после чего `изменить` `state`.

```
const incrementAction = {
  type: 'INCREMENT',
  payload: 5,
};

store.dispatch(incrementAction);
```

**Нейминг** `actions` происходит `обратным методом`, в виде `совершенного действия`.
Например: Да: `taskCompleted` | Нет: `completeTask`

### _Dispatch (`отправка`)_

- **Определение:** Отправка - это метод `хранилища`(`store`), используемый `для отправки действия`(`action`) в хранилище. Он `инициирует процесс изменения состояния`.

```
store.dispatch(incrementAction);
```

**!** Когда метод `dispatch` вызывается, `хранилище`(`store`) передает `действие`(`action`)
`обработчику`(`reducer`), который `возвращает новое состояние`. Подписчики хранилища, такие как компоненты React, могут быть уведомлены об изменении состояния, чтобы обновить пользовательский интерфейс.

-> Выполнить действие после обновления `state`

```
export const paginateActions = {
  updated: (page, size, callback) => async (dispatch, getState) => {
    await dispatch(updated({ page, size }));
    if (typeof callback === 'function') {
			callback();
		}
  },
};
```

### _Reducer (`обработчик`)_

- **Определение:** Обработчик - это `чистая функция`, которая `принимает предыдущее состояние` и `действие`, и `возвращает новое состояние`.
- **Структура:** `(state, action) => newState`

```
const counterReducer = (state = 0, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return state + action.payload;
    case 'DECREMENT':
      return state - action.payload;
    default:
      return state;
  }
};
```

Функции `Reducer` получили свое название, потому что они похожи на функцию обратного вызова, которую вы передаете методу `Array.reduce()`.

### _Процесс обновления состояния_

1. **Создание действия:** Создается объект действия с определенным типом и данными (при необходимости).
2. **Отправка действия:** Действие отправляется в хранилище с помощью функции `dispatch`.
3. **Вызов редьюсера:** Редьюсер обрабатывает действие и возвращает новое состояние.
4. **Обновление состояния:** Хранилище обновляет свое состояние согласно результатам работы редьюсера.
5. **Уведомление подписчиков:** Зарегистрированные слушатели получают уведомление о изменении состояния.

```
/=/ Определение редьюсера
const counterReducer = (state = 0, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return state + action.payload;
    case 'DECREMENT':
      return state - action.payload;
    default:
      return state;
  }
}

/=/ Создание хранилища
const store = createStore(counterReducer);

/=/ Регистрация слушателя для отслеживания изменений состояния
store.subscribe(() => {
  console.log(store.getState()); /=/ Выведет обновленное состояние
});

/=/ Создание действия и отправка в хранилище
const incrementAction = {
  type: 'INCREMENT',
  payload: 5,
};
store.dispatch(incrementAction);
```

## _Воссоздание Redux_

```
import { useState, useEffect } from "react";

const TASK_ADDED = "tasks/added";
const TASK_UPDATED = "tasks/updated";

function taskReducer(state, action) {
  switch (action.type) {
    case TASK_UPDATED:
      return state.map((task) => {
        return task.id === action.payload.id
          ? { ...task, ...action.payload }
          : task;
      });
    case TASK_ADDED:
      return [...state, action.payload];

		default:
      return state;
  }
}

function createStore(reducer, initState) {
  let state = initState;
  let listeners = [];

  function getState() {
    return state;
  }

  function dispatch(action) {
    state = reducer(state, action);
    listeners.forEach((listener) => listener());
    // Notify all listeners that the state has changed.
  }

  function subscribe(listener) {
    listeners.push(listener);
  }

  return { getState, dispatch, subscribe };
}

const initState = [
  { id: 1, title: "Task 1", completed: false },
  { id: 2, title: "Task 2", completed: false },
];
const store = createStore(taskReducer, initState);

const App = () => {
  const [state, setState] = useState(store.getState());

  useEffect(() => {
    store.subscribe(() => {
      setState(store.getState());
      console.log(store.getState());
    });
  }, []);

  const completeTask = (taskId) => {
    const action = {
      type: TASK_UPDATED,
      payload: { id: taskId, completed: true },
    };
    store.dispatch(action);
  };

  const changeTitle = (taskId) => {
    const action = {
      type: TASK_UPDATED,
      payload: { id: taskId, title: `New Title ${taskId}` },
    };
    store.dispatch(action);
  };

  const addTask = () => {
    const action = {
      type: TASK_ADDED,
      payload: {
        id: Date.now(),
        title: "New Task",
        completed: false,
      },
    };
    store.dispatch(action);
  };

  return (
    <>
      <h1>App</h1>
      <p />
      {state.map((task) => (
        <li key={task.id}>
          <span>{task.title}</span>
          <span> {task.completed ? "✅" : "❌"}</span> <p />
          <button onClick={() => completeTask(task.id)}>Complete</button>{" "}
          <button onClick={() => changeTitle(task.id)}>Change Title</button>{" "}
          <hr />
        </li>
      ))}
      <button onClick={addTask}>Add Task</button>
    </>
  );
};

export default App;
```

## _Redux-toolkit_

### _createAction()_

```
/=/ Стало:
const update = createAction("tasks/updated");

export const taskCompleted = (id) => {
  return update({ id: id, completed: true });
};
```

```
/=/ Было:
const TASK_UPDATED = "tasks/added"

export const taskCompleted = (id) => {
  return {
    type: TASK_UPDATED,
    payload: { id: id, completed: true },
  };
};
```
### _createReducer()_

```
import { createAction, createReducer } from 'redux-actions';

/=/ Создание действия с использованием createAction
const addTodo = createAction('ADD_TODO');

/=/ Создание начального состояния
const initialState = {
  todos: [],
};

/=/ Создание обработчика с использованием createReducer
const todoReducer = createReducer(initialState, {
  [addTodo]: (state, action) => ({
    ...state,
    todos: [...state.todos, { text: action.payload, completed: false }],
  }),
});

const todoAdded = () => (dispatch) => {
	dispatch(addTodo('Speak in English'));
}
```

```
const initialState = [
  { id: 1, title: "Task 1", completed: false },
  { id: 2, title: "Task 2", completed: false },
];

const add = createAction("tasks/added");
const update = createAction("tasks/updated");

const taskReducer = createReducer(initState, (builder) => {
  builder
    .addCase(add, (state, action) => {
      state.push(action.payload);
    })
    .addCase(update, (state, action) => {
      return state.map((task) => {
        return task.id === action.payload.id
          ? { ...task, ...action.payload }
          : task;
      });
    });
});
```

- Используйте `return`, когда вы хотите вернуть новое состояние, основанное на предыдущем состоянии и действии.

```
.addCase(update, (state, action) => {
  return { ...state, ...action.payload };
})
```

- Не используйте `return`, когда вы изменяете состояние напрямую, без возвращения нового значения.

```
.addCase(add, (state, action) => {
  state.push(action.payload);
})
```

### _createSlice()_

Внутри он использует `createAction` и `createReducer`.

```
import { createSlice } from '@reduxjs/toolkit';

const initialState = {
  entities: {},
};

const errorsSlice = createSlice({
  name: 'errors',
  initialState,
  reducers: {
    set(state, action) {
      const { key, value } = action.payload;
      state.entities[key] = value;
    },
    clear(state) {
      state.articles = [];
    },
  },
});

const { set, clear } = errorsSlice.actions;

export const setError = (key, value) => (dispatch) => {
  dispatch(set({ key, value }));
};
export const clearErrors = () => (dispatch) => {
  dispatch(clear());
};

export const getErrors = () => (state) => state.errors.entities;

export default errorsSlice.reducer;
```

Желательно не экспортировать сами `actions` за пределы `файла-reducer`.
А использовать для экспорта `внешние функции-обертки` 

```
import { createSlice } from "@reduxjs/toolkit";

import todosService from "../services/todos.service";
import { setErrors } from "./errors";

const initialState = {
  entities: [],
  isLoading: true,
};

const taskSlice = createSlice({
  name: "tasks",
  initialState,
  reducers: {
    received(state, action) {
      state.entities.push(...action.payload);
      state.isLoading = false;
    },
    add(state, action) {
      state.entities.push(action.payload);
      state.isLoading = false;
    },
    update(state, action) {
      const newArr = state.entities.map((task) => {
        return task.id === action.payload.id
          ? { ...task, ...action.payload }
          : task;
      });
      state.entities = newArr;
    },
    remove(state, action) {
      const newArr = state.entities.filter((item) => {
        return item.id !== action.payload.id;
      });
      state.entities = newArr;
    },

    taskRequested(state) {
      state.isLoading = true;
    },
    taskRequestFailed(state) {
      state.isLoading = false;
    },
  },
});

/=/ Actions - нейминг в прошедшем времени PastSimple
const { received, add, update, remove, taskRequested, taskRequestFailed } =
  taskSlice.actions;
 
export const ticketActions = {
	/=/ Обычные функции, обертки actions - обычный нейминг 
  setTasks: () => async (dispatch) => {
    dispatch(taskRequested());
    try {
      const data = await todosService.fetch();
      dispatch(received(data));
    } catch (error) {
      dispatch(taskRequestFailed());
      dispatch(setErrors(error.message));
    }
  },

  createTask: (title) => async (dispatch) => {
    dispatch(taskRequested());
    try {
      const data = await todosService.create(title);
      dispatch(add(data));
    } catch (error) {
      dispatch(taskRequestFailed());
      dispatch(setErrors(error.message));
    }
  },
};

export const = getTasks = () => (state) => state.tasks.entities,
export const = getTasksLoadingStatus = () => (state) => state.tasks.isLoading,

const { reducer: taskReducer } = taskSlice;
export default taskReducer;
```

### _configureStore()_

```
import { configureStore } from '@reduxjs/toolkit';
import rootReducer from './rootReducer';

const createStore = () => {
  return configureStore({
    reducer: rootReducer,
  });
};

export default createStore;
```

### _combineReducers()_

Создание единого хранилища из нескольких сущностей.

```
|> App.jsx

const state = useSelector((state) => state.tasks.entities);
const isLoading = useSelector((state) => state.tasks.isLoading);
```

```
import taskReducer from "./reducers/tasks";
import errorsReducer from "./reducers/errors";

const rootReducer = combineReducers({
  errors: errorsReducer,
  tasks: taskReducer,
});

const createStore = () => {
  return configureStore({
    reducer: rootReducer,
  });
};
```

#### _rootReducer_

```
import { combineReducers } from 'redux';

const rootReducer = combineReducers({
  tickets: ticketsReducer,
  filters: combineReducers({
    transfers: transfersReducer,
    type: typeReducer,
  }),
  errors: errorReducer,
});

export default rootReducer;
```

### _useSelector()_

**useSelector()** используется `для выбора определенных частей состояния из хранилища` Redux и предоставления их компоненту. Он принимает функцию селектора, которая принимает весь стейт и `возвращает только нужные данные`. 

```
const state = useSelector((state) => state.tasks.entities);
const isLoading = useSelector((state) => state.tasks.isLoading);

const dispatch = useDispatch();
```

Когда `состояние, выбранное` с помощью селектора, `изменяется`, компонент автоматически `перерисовывается`. Это позволяет компонентам подписываться на определенные части состояния и получать только необходимые данные.

#### _Передача значений_

Чтобы не искать измененное значение по всему проекту, а изменить лишь в одном месте

```
|> tasks.js

const getTasks = (state) => state.tasks.entities;
const getTasksLoadingStatus = (state) => state.tasks.isLoading;
```

```
|> App.js

import * as selectors from "./store/reducers/tasks";

const { getTasks, getTasksLoadingStatus } = selectors;

const App = () => {
	const state = useSelector(getTasks);
	const isLoading = useSelector(getTasksLoadingStatus);

}
```

-> Внимание `mapStateToProps`

```
/=/ Не сможет обработаться через mapStateToProps!
const getTasks = () => (state) => state.tasks.entities;

/=/ Cможет обработаться через mapStateToProps
const getTasks = (state) => state.tasks.entities;
```
 
### _useDispatch()_

**useDispatch()** возвращает ссылку на функцию `dispatch`, которая используется для отправки действий (`actions`). Для того чтобы `useDispatch()` работал, он должен находится внутри компонента обернутого  `<Provider>` из `react-redux`.

Когда вы используете `useDispatch()`, он ищет ближайший `<Provider>` в иерархии компонентов и получает доступ к объекту `dispatch` из контекста Redux.

### _bindActionCreators_

**bindActionCreators** помогает автоматически связывать действия (`actions`) с функцией отправки (`dispatch`)

-> Воссоздание внутреннего функционала

```
const bindActionCreator = (creator, dispatch) => {
  return (...args) => {
    dispatch(creator(...args));
  };
};

const taskCompletedDispatch = bindActionCreator(taskCompleted, dispatch);

const handleTaskComplete = (id) => {
  taskCompletedDispatch(id);
};
```

-> Полноценный функционал

```
import { bindActionCreators } from "redux";
import { initStore, actions } from "./store";

const { taskCompleted, titleChanged } = bindActionCreators(actions, dispatch);

const handleTaskComplete = (id) => {
  taskCompleted(id);
};

const handleTitleChange = (id) => {
	titleChanged(id);
};
```

### _connect_

```
import { connect } from 'react-redux';
import { bindActionCreators } from 'redux';

function App({
  tickets,
  searchId,
  isLoading,
  searchIdSet,
  ticketsChunkLoaded,
}) {

	return (...)
}

const mapState = (state) => ({
  tickets: getTickets(state),
  searchId: getSearchId(state),
  isLoading: getTicketsLoadingStatus(state),
});

const mapDispatch = (dispatch) => {
  const tickets = bindActions(ticketActions, dispatch);
  const search = bindActions(searchActions, dispatch);

  return { ...tickets, ...search };
};

const ConnectedApp = connect(mapState, mapDispatch)(App);
export default ConnectedApp;
```

-> useDispatch / useSelector

```
import { bindActionCreators as combine } from 'redux';
import { useDispatch, useSelector } from 'react-redux';

function App() {
  const dispatch = useDispatch();
  const tickets = useSelector(getTickets());
  const searchId = useSelector(getSearchId());
  const isLoading = useSelector(getTicketsLoadingStatus());

  const { ticketsChunkLoaded } = combine(ticketActions, dispatch);
  const { searchIdWasSet } = combine(searchActions, dispatch);

	return (...)
}
```
### _Middleware_

**Middleware** - логгер/перехватчик. Позволяет создавать `side-effect`

**Middleware** - `ряд функций` каррирования, которые `обрабатывают действия`(`actions`) `перед тем, как они достигнут reducer-а`.

```
const loggerMiddleware = store => next => action => {
  console.log('Dispatching:', action);
  const result = next(action);
  console.log('Next state:', store.getState());
  return result;
};
```

```
|> logger.js

const logger = (store) => {
  return function wrapDispatch(next) {
    return function handleAction(action) {
			/=/ Перехватываем и переназначаем action
      if (action.type === "tasks/remove") {
        store.dispatch({
          type: "tasks/add",
          payload: {
            id: Date.now(),
            title: "Task Middleware",
            completed: false,
          },
        });
        console.log("Added a new task");
        return; 
        /=/ Останавливаем локальное распространение ранее назначенного actions
      }
      return next(action); 
      /=/ Позволяет распространятся следующим actions
      /=/ Если не возвращать, то actions не работают
    };
  };
};
```

```
|> store.js

import { configureStore } from "@reduxjs/toolkit";

import taskReducer from "./task";
import logger from "./middleware/logger";

const initStore = () => {
  return configureStore({
    reducer: taskReducer,
    middleware: (getDefaultMiddleware) => [...getDefaultMiddleware(), logger],
  });
};

export default initStore;
```

### _Thunk_

**Thunk** это такой же `middleware` перехватчик, который можно создать самостоятельно. 
При использовании `configureStore` из `@reduxjs/toolkit`, **Thunk** вшит туда по-умолчанию.

**Redux Thunk** позволяет `dispatch-ить функции-создатели действий`, которые `возвращают функции вместо обычных объектов действий`.

```
dispatch(setErrors(error.message)); 
/=/ Отправляем в хранилище функцию под видом actions
/=/ Передаем message в первый callback у setErrors
```

```
|> ThunkMiddleware

const thunkMiddleware = ({ dispatch, getState }) => {
  return function wrapDispatch(next) {
    return function handleAction(action) {
      if (typeof action === "function") {
        action(dispatch, getState);
        /=/ Перехватываем action который является функцией 
        /=/ Вызываем действие передав dispatch в параметры вызова
        /=/ Тем самым вызываем второй callback у setErrors
      }
      return next(action);
    };
  };
};

export default thunkMiddleware;
```

```
const { set } = actions;

export const setErrors = (message) => (dispatch) => {
  dispatch(set(message));
  /=/ Получаем переданный dispatch из thunkMiddleware
  /=/ Второй коллбэк вызывается
  /=/ Внутри него вызывается полученный dispatch(set(message))
	/=/ И отправляет в хранилище полноценное действие 
};
```

### _Отладка запросов_

```
|> task.js 

const taskRequested = createAction("tasks/requested");
const taskRequestFailed = createAction("tasks/requestFailed");

export const fetchTasks = () => async (dispatch) => {
  dispatch(taskRequested());
  try {
    const data = await todosService.fetch();
    dispatch(received(data));
  } catch (error) {
    dispatch(taskRequestFailed(error.message));
  }
};
```

-> Полная версия

```

const initialState = {
  entities: [],
  isLoading: true,
  error: null,
};

const taskSlice = createSlice({
  name: "tasks",
  initialState,
  reducers: {
    received(state, action) {
      state.entities.push(...action.payload);
      state.isLoading = false;
    },
    add(state, action) {
      state.entities.push(action.payload);
    },
    update(state, action) {
      const newArr = state.entities.map((task) => {
        return task.id === action.payload.id
          ? { ...task, ...action.payload }
          : task;
      });
      state.entities = newArr;
    },
    remove(state, action) {
      const newArr = state.entities.filter((item) => {
        return item.id !== action.payload.id;
      });
      state.entities = newArr;
    },

    taskRequested(state) {
      state.isLoading = true;
    },
    taskRequestFailed(state, action) {
      state.isLoading = false;
      state.error = action.payload;
    },
  },
});

const { reducer: taskReducer } = taskSlice;
const { received, add, update, remove, taskRequested, taskRequestFailed } =
  taskSlice.actions;

export const fetchTasks = () => async (dispatch) => {
  dispatch(taskRequested());
  try {
    const data = await todosService.fetch();
    dispatch(received(data));
  } catch (error) {
    dispatch(taskRequestFailed(error.message));
  }
};
```

