Это библиотека, предназначенная для маршрутизации страниц в React (`роутинг`).
Позволяет перемещаться по приложению без перезагрузки страницы, тем самым мы реализуем функционал `Single-Page App`

```
|> main.jsx
createRoot(document.getElementById('root')).render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);

function Navbar() {
  return (
    <ul>
      <li><a href="/">Home</a></li>
      <li><a href="/login">Login</a></li>
      <li><a href="/posts">Posts</a></li>
      <li><a href="/dashboard">Dashboard</a></li>
    </ul>
  );
}

function App() {
  return (
    <>
      <Navbar />
      /=/ Необходимо передавать ссылку на компонент: Home
      <Navbar />
   <Route path="/" exact component={Home} />
   <Route path="/login" component={Login} />
   <Route path="/posts" component={Posts} />
   <Route path="/dashboard" component={Dashboard} />
    </>
  );
}
```

## _Switch_

**Switch** - это коммутатор путей. `Выводит первое совпадение`.
Необходимо `упорядочивать` маршруты от `наиболее конкретизированных` к `наиболее общим`

```
function App() {
  return (
    <>
      <Navbar />
      <Switch>
        <Route path="/" exact component={Home} />
        <Route path="/login" component={Login} />
        <Route path="/posts" component={Posts} />
        <Route path="/dashboard" component={Dashboard} />
      </Switch>
    </>
  );
}
```

Допустим, что мы хотим выводить конкретные записи. Добавим роут “`/posts/some-post`”.

-> Работает
Дочерние страницы нужно определять выше родительских

```
<Switch>
    <Route path="/" exact component={Home} />
    <Route path="/signin" component={SignIn} />
    <Route path="/posts/some-post" component={SomePost} />
    <Route path="/posts" component={Posts} />
    <Route path="/contacts" component={Contacts} />
</Switch>
```

-> Не работает
Если мы будем вызывать роут для SomePost ниже, чем Posts, то мы никогда его не увидим

```
<Switch>
    <Route path="/" exact component={Home} />
    <Route path="/signin" component={SignIn} />
    <Route path="/posts" component={Posts} />
    <Route path="/posts/some-post" component={SomePost} />
    <Route path="/contacts" component={Contacts} />
</Switch>
```

## _Link_

**Link** - это по сути обёртка, которая добавляет обработчик событий на ссылку. `onClick()` блокирует перезагрузку и `передает роутеру новый измененный путь` .

У `Link` нет атрибута `href`, есть только атрибут `to`.
Атрибут `to` говорит `как изменить путь` после нажатия на ссылку.

```
function Navbar() {
  return (
    <ul>
      <li>
        <Link to="/">Home</Link>
      </li>
      <li>
        <Link to="/login">Login</Link>
      </li>
      <li>
        <Link to="/posts">Posts</Link>
      </li>
      <li>
        <Link to="/dashboard">Dashboard</Link>
      </li>
    </ul>
  );
}
```

## _RouteProps_

### _Передача props_

-> `component={}`
Передаются `history, location, match`. Но `не мои props`

```
<Route path="/dashboard" component={Dashboard} />
```

-> `render={(pp) => <Component {...pp}/>}`
Передаем `routerProps` и `мои props`

```
|> App.jsx

<Route
  path="/dashboard"
  render={(routerProps) => <Dashboard isAdmin={true} {...routerProps} />}
/>

 ==/OR/==

<Route path="/dashboard">
 {(routerProps) => <Dashboard {...routerProps} isAdmin />}
</Route>;
```

-> `withRouter()`

```
<Route
 path="/dashboard"
 render={() => <Dashboard isAdmin={true} />}
/>

 ==/OR/==

<Route path="/dashboard">
 <Dashboard isAdmin={false} />
</Route>
```

```
import { withRouter } from 'react-router-dom';

const Dashboard = ({ history, location, match, isAdmin }) => {
  return (
    <>
      <p>Current Path: {location.pathname}</p>
      <button onClick={() => history.push('/other-path')}>Go to Other Path</button>
    </>
  );
};

export default withRouter(Dashboard);
```

## _Параметры и свойства Route_

```
function App() {
  return (
    <>
      <Route path="/posts/:id" render={() => <Post posts={posts} />} />
      <Route path="/posts" render={() => <PostsList posts={posts} />} />
    </>
  );
}
```

### _history, location, match_

1. `history` - Содержит информацию о `текущей` и `предыдущих страницах` в истории браузера.
   Методы для `навигации по истории` браузера: `push()`, `replace()`, `goBack()`.
2. `location` - информация о том, `где` мы сейчас `находимся` и `что искали`.
   Свойства: `patchname`(`путь`), `search`(`строка запроса`), `hash`.
3. `match` - информация о том, `как текущий URL соответствует маршруту в компоненте <Route>` и `по каким параметрам`.
   Свойства: `isExact` - соответствует ли текущий URL точно маршруту Route. Объект `params` - содержит `параметры маршрута`.

```
{
  "history": {
    "length": 50,
    "action": "POP",
    "location": "{hash: "", key: "jwn7l3", pathname: "/", search: ""}",
    "createHref": "ƒ createHref() {}",
    "push": "ƒ push() {}",
    "replace": "ƒ replace() {}",
    "go": "ƒ go() {}",
    "goBack": "ƒ goBack() {}",
    "goForward": "ƒ goForward() {}",
    "block": "ƒ block() {}",
    "listen": "ƒ listen() {}"
  },
  "location": {
    "pathname": "/",
    "search": "",
    "hash": "",
    "key": "jwn7l3"
  },
  "match": {
    "path": "/",
    "url": "/",
    "isExact": true,
    "params": "{}"
  }
}
```

```
Маршрут: /users/:userId
URL:     /users/123

-< match.path - текущий маршрут
-< location.patchname - текущий URL
```

- history используется для управления историей браузера и переходами между страницами.
  - `push`(path, [state]) - перенаправляет на указанный маршрут, добавляет новую запись в историю браузера. Необязательный параметр `state` - предназначен для сохранения необходимой информации при переходе между страницами.
  - `replace`(path, [state]) - заменяет текущую запись в истории браузера на новую и перенаправляет на указанный маршрут.
  - `location` - описывает текущий URL-адрес.
  - `go`(n) - перемещается в истории браузера на указанное количество записей. Если n равно -1, то перемещается на одну запись назад, если n равно 1, то перемещается на одну запись вперед.
  - `goBack`() - перемещается на одну запись назад в истории браузера.
  - `goForward`() - перемещается на одну запись вперед в истории браузера.
  - `action` - указывает на тип действия, которое привело к текущей записи в истории.
  Возможные значения: PUSH (добавление новой записи), POP (перемещение на другую запись в истории), REPLACE (замена текущей записи на другую).
  - `length` - количество записей в истории браузера.

```
  * history используется для управления историей браузера и переходами между страницами.
  -< `push`(path, [state]) - перенаправляет на указанный маршрут, добавляет новую запись в историю браузера. Необязательный параметр `state` - предназначен для сохранения необходимой информации при переходе между страницами.
  -< `replace`(path, [state]) - заменяет текущую запись в истории браузера на новую и перенаправляет на указанный маршрут.
  -< `location` - описывает текущий URL-адрес.
  -< `go`(n) - перемещается в истории браузера на указанное количество записей. Если n равно -1, то перемещается на одну запись назад, если n равно 1, то перемещается на одну запись вперед.
  -< `goBack`() - перемещается на одну запись назад в истории браузера.
  -< `goForward`() - перемещается на одну запись вперед в истории браузера.
  -< `action` - указывает на тип действия, которое привело к текущей записи в истории.
  Возможные значения: PUSH (добавление новой записи), POP (перемещение на другую запись в истории), REPLACE (замена текущей записи на другую).
  -< `length` - количество записей в истории браузера.
```

```
 * location - Все про URL. Содержит информацию о текущем URL, включая pathname, search, hash и state.
  -< `search` - содержит параметры Запроса.
  Параметры Запроса: запрос добавляется к URL-адресу после символа (?) и разделяются знаком (&).
  Например, если текущий URL /users/123?name=John, то `search` будет равен '?name=John'.
  -< `pathname` - указывает на текущий маршрут.
  Например, если текущий URL /users/123, то `pathname` будет равен /users/123.
  -< `hash` - это часть URL-адреса, которая содержит хэш. Хэш используется для прокрутки к определенному элементу на странице. Хэш добавляется после знака (#).
  Например, если текущий URL /users/123#profile, то hash будет равен #profile.
  -< `state` - это объект, который может быть использован для передачи данных между маршрутами.
  Например, вы можете установить `state` в объект, содержащий данные о пользователе, при переходе на страницу пользователя.
```

```
 * match - соответствие текущего URL и маршрута. Он содержит параметры, переданные в URL, данные о самом маршруте и т.д.
  -< `params` - определить параметры переданные в URL.
  Например, если маршрут определен как /users/:userId, а
  текущий URL /users/123, то params будет содержать { userId: '123' }.
  -< `path` - это строка, которая определяет шаблон маршрута. Шаблон маршрута  сопоставляется с текущим URL-адресом и позволяет определить, какой Компонент должен быть отображен на странице.
  Например, если маршрут определен как /users/:userId, то
  `path` будет равен /users/:userId.
  -< `url` - это строка, которая содержит фактический URL-адрес, соответствующий маршруту.
  Например, если маршрут определен как /users/:userId, и текущий URL /users/123, то url будет равен /users/123.
  -< `isExact` - это булевое значение, которое указывает, соответствует ли текущий URL полностью маршруту. Если isExact равен true, то URL точно соответствует маршруту. Если isExact равен false, то URL соответствует маршруту только частично.
```

### _Опциональные параметры_

Путь `path="/posts/:postId?"` - говорит маршрутизатору о том что, `независимо есть ли postId` или `postId нет` - он `должен отобразить` компонент `<Posts {...props}/>`

```
<Route path="/posts/:id?" component={Posts} />
```

-> С помощью `опционального параметра`, реализуем `HOC`

```
const posts = [
  { id: 1, title: 'Post 1' },
  { id: 2, title: 'Post 2' },
  { id: 3, title: 'Post 3' },
];

function Posts({ match }) {
  const { id } = match.params;

  return id
    ? <Post id={id} posts={posts} />
    : <PostsList posts={posts} />;
}
```

```
function Post({ id, posts }) {
  const post = posts.find((item) => {
    return item.id === Number(id);
  });
  return <h3>{post ? post.title : 'Post not found'}</h3>;
}

function PostsList({ posts }) {
  return posts.map((post) => {
    return <h3 key={post.id}>{post.title}</h3>;
  });
}
```

### _Query-параметры_

`Query-параметры` - `параметры запроса` в `URL`, перечисленные после знака “`?`”

-> `query-string.parse()` - преобразует `строку` запроса `в объект`

```
http://localhost:5173/posts/?count=1
```

```
import qs from "query-string";

function Posts({ match, location }) {
  const { id } = match.params;
  const { count } = qs.parse(location.search); /=/ { count: '2' }

  const cropPosts = count ? posts.slice(0, count) : posts;

  return id
    ? <Post id={id} posts={posts} />
    : <PostsList posts={cropPosts} />;
}

export default withRouter(Posts);
```

## _Redirect_

```
function App() {
  return (
   <>
      <Switch>
    <Route path="/" exact component={Home} />
    <Route path="/signin" component={SignIn} />
    <Route path="/posts/:postId?" component={Posts} />
    <Route path="/contacts" component={Contacts} />
    <Redirect from="/lk" to="/signin" />
    <Route component={NotFound} />
      </Switch>
    </>
  );
}
```

## _History_

```
function PostsList({ posts }) {
  return posts.map(({ id, title }) => (
    <Link key={id} to={`posts/${id}`}>
      <h3>{title}</h3>
    </Link>
  ));
}
```

```
function Post({ id, posts, history }) {
  const post = posts.find((item) => {
    return item.id === Number(id);
  });

  const handleSave = () => {
    // history.push('/posts');
    history.replace('/posts'); /=/ Запрещаем возврат(например в редактирование)
  };

  return (
    <>
      <h3>{post ? JSON.stringify(post) : 'Post not found'}</h3>
      <button type="button" onClick={handleSave}>
        Сохранить
      </button>
    </>
  );
}
```

## _Hooks RRD_

### _useHistory()_

Позволяет получить `доступ к объекту истории браузера`, который можно использовать `для перехода на другой Route` или для получения `информации о предыдущих` маршрутах.

```
const history = useHistory();

<button
   type="submit"
   onClick={() => history.push(`/users/${userId}`)}
>
   Сохранить
</button>
```

### _useLocation()_

Позволяет получить доступ к информации о `текущем URL-адресе` и `поисковом параметре запроса`.

```
const location = useLocation();
const isEdit = location.pathname.endsWith("/edit");
```

### _useRouteMatch()_

Позволяет получить `информацию о совпадении маршрута`.

```
import { useRouteMatch } from 'react-router-dom';

function MyComponent() {
  const match = useRouteMatch('/users/:id');

  if (match) {
    /=/ Код, который будет выполнен,
    /=/ если текущий URL совпадает с маршрутом '/users/:id'

    console.log(match.path); /=/ '/users/:id'
    console.log(match.url); /=/ Текущий URL
    console.log(match.params); /=/ Параметры маршрута, например { id: '123' }
  }
}
```

### _useParams()_

Позволяет получить доступ к `параметрам маршрута`, определенным с помощью `Route`.
Выведет `динамические параметры` указанные `после` "`:`", но `не статические параметры`.

```
/catalog/category - Фиксированный, статический путь
/catalog/:category - Динамический, необходимый путь
/catalog/:category? - Динамический опциональный путь

/=/ URL:__blog/posts/123
<Route path="/posts/:postId" component={Posts} />

const { postId } = useParams(); /=/ 123
```

-> Так выдаст `edit` из `useParams()`:

```
|> App.jsx

<Route path="/users/:userId?/:edit?" component={Users} />
```

```
const Users = () => {
    const params = useParams();
    const { userId, edit } = params;
    /=/ { userId: '67rdca3eeb7f6fgeed471817', edit: undefined }

    return <>{userId ? <UserPage {...params} /> : <UsersListPage />}</>;
};
```

-> Не выдаст `edit`:

```
|> App.jsx

/=/ Убрали ':' из `edit`
<Route path="/users/:userId?/edit?" component={Users} />
```

```
const Users = () => {
    const params = useParams();
    const { userId, edit } = params;
    /=/ { userId: '67rdca3eeb7f6fgeed471817', edit: undefined }

    return <>{userId ? <UserPage {...params} /> : <UsersListPage />}</>;
};
```

## _Вложенные маршруты_

Разгружаем основной узел роутов в `App`

```
function App() {
  return (
   <>
      <Switch>
    <Route path="/contacts/departaments-1" component={...} /> <- Выносим
    <Route path="/contacts/departaments-2" component={...} /> <- Выносим
    <Route path="/contacts" component={Contacts} />
        /=/ Основной путь к HOC-узлу роутов
        
        <Route component={NotFound} />
      </Switch>
    </>
  );
}
```

```
function Contacts() {
  return (
    <>
      <h1>Контакты</h1>
      <ul>
        <li><Link to="/contacts/departaments-1">Департамент 1</Link></li>
        <li><Link to="/contacts/departaments-2">Департамент 2</Link></li>
      </ul>
      
      <Switch>
        <Route
          path="/contacts/departaments-1"
          component={ContactDepartaments1}
        />
        <Route
          path="/contacts/departaments-2"
          component={ContactDepartaments2}
        />
      </Switch>
    </>
  );
}
```
