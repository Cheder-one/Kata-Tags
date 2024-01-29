Это библиотека, предназначенная для маршрутизации страниц в React (`роутинг`).
Позволяет перемещаться по приложению без перезагрузки страницы, тем самым мы реализуем функционал `Single-Page App`

**! Внимание !**
! При выносе роутов, NotFound не сработает в том компоненте где его нет. 
Нужно указывать `<Redirect to="..." />`

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

### _/:slug + Redux_
 
Рабочая `реализация ветвления компонентов` в зависимости от наличия `params`.
Реализация с учетом: 
- `записи в store` => 
- `ререндером  иерархии компонентов которые получают это значение из store` =>
- `получением данных из хранилища Redux` =>
- `отображение компонента с полученными данными` 

```
function App() {
  return (
		<Switch>
			/=/ Независмо, есть slug или нет, отобразить компонент
		  <Route path="/articles/:slug?" component={DynamicArticleRender} />
		  <Route path="/" exact component={ArticlesPage} />
		  <Route component={NotFound} />
		</Switch>
  );
}
```

```
function DynamicArticleRender() {
  const { slug } = useParams();

  return slug ? <FullArticle slug={slug} /> : <ArticlesPage />;
}
```

```
function ArticlesPage({
  articlesChunk,
  pagination,
  errors,
  isLoading,
  setArticlesChunk,
}) {
  const { articles, articlesCount } = articlesChunk;

	useEffect(() => {
    const params = getPaginateParams({ pagination });
    setArticlesChunk(params);
  }, [pagination]);
	/=/ Получение данных => Запись в store => Ререндер

  return !isLoading && !errors.articles ? (
    <Col>
      <ArticleList articles={articles} />
      <Pagination itemsCount={articlesCount} />
    </Col>
  ) : (
    <h1>Loading...</h1>
  );
}
```

```
function FullArticle({ articleOne, isLoadingOne, setArticleOne }) {
  const { slug } = useParams();

  useEffect(() => {
    setArticleOne(slug);
  }, []);
	/=/ Получение данных => Запись в store => Ререндер

  return (
    !isLoadingOne && (
      <div>
        <Article key={articleOne.slug} article={articleOne} isFull />
      </div>
    )
  );
}
```

```
function Article({ article, isFull }) {
  return (
    <article className={_.article_card}>
      <Row className={_.header}>
        <HeaderMeta
          slug={article.slug}
          title={article.title}
          hearts={article.favoritesCount}
          tagList={article.tagList}
        />
        <PostedMeta
          date={article.createdAt}
          image={article.author.image}
          username={article.author.username}
        />
      </Row>
      <Row className={_.description}>
        <div className={_.text}>{article.description}</div>
      </Row>

      {isFull && article.body ? (
        <Markdown className={_.body}>
          {removeInvisibleChar(article.body).trim()}
        </Markdown>
      ) : null}
    </article>
  );
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
				
				<Redirect from="/lk" to="/signin" />
				<Route component={NotFound} />
      </Switch>
    </>
  );
}
```

```

function App() {
  return (
    <>
      <Header />
      <Flex justify="center">
        <Switch>
          <Route path="/articles/:slug?" component={ArticleSwitcher} />
          <Route path="/:loginType" component={LoginSwitcher} />
          <Route path="/" exact component={ArticlesPage} />

          <Redirect to="/not-found" />
          <Route path="/not-found" component={NotFound} />
        </Switch>
      </Flex>
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

**! Внимание !**
! Значение `params` удастся получить только если установлен `Rout` и задан `Компонент для отображения`. При `Redirect => NotFound` `params не получить`.

```
function App() {
  return (
    <Switch>
		  <Route path="/" exact component={ArticlesPage} />
		  <Route path="/articles" component={ArticlesPage} />
		  <Route path="/articles/:slug" component={FullArticle} />
			/=/ Здесь нужно указывать динамический путь ':' в '/articles/:slug'

		  <Route component={NotFound} />
    </Switch>
  );
}
```

-> **! Внимание !**

```
function Article({ slug, title }) {
	return (
		/=/ Пишем /articles, иначе при повторном нажатии будет '/articles/articles/'
		
		<Link to={`/articles/${slug}`} className={_.title}>
			{title}
		</Link>
	)
	/=/ Здесь НЕ нужно указывать ':' в `articles/${slug}`,
	/=/ Тк это будет частью реального URL
}
```

```
function FullArticle() {
  const params = useParams();
  console.log(params); /=/ {slug: 'lorem-ipsum-dolor-ojq1ph'}

  return <h1>FullArticle</h1>;
}
```

____
```
/catalog/category - Фиксированный, статический путь
/catalog/:category - Динамический, необходимый путь
/catalog/:category? - Динамический опциональный путь

/=/ URL:__blog/posts/123
<Route path="/posts/:postId" component={Posts} />

const { postId } = useParams(); /=/ 123
```
____

-> Так выдаст `edit` из `useParams()`:

```
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
```
import { BrowserRouter as Router, Switch, Route, Link } from 'react-router-dom';

function App() {
  return (
    <Router>
      <ul>
        <li>
          <Link to="/">Главная</Link>
        </li>
        <li>
          <Link to="/contacts">Контакты</Link>
        </li>
      </ul>

      <main>
        <Switch>
          <Route path="/contacts" component={Contacts} />
          <Route path="/" exact component={Home} />
          <Route patch="/404" component={NotFound} />
			    <Redirect to="/404" />
          /=/ NotFound сработает при ошибке в роутах 
          /=/ Например если написать '/contactsq1'
          /=/ Но не сработает если написать '/contacts/qwqw'
        </Switch>
      </main>
    </Router>
  );
}

const Home () => <h2>Главная</h2
const NotFound () => <h2>NotFound</h2

const ContactDepartments1 () => <h3>Департамент 1</h3
const ContactDepartments2 () => <h3>Департамент 2</h3

function Contacts() {
  return (
    <>
      <h1>Контакты</h1>
      <ul>
        <li>
          <Link to="/contacts/departments-1">Департамент 1</Link>
        </li>
        <li>
          <Link to="/contacts/departments-2">Департамент 2</Link>
        </li>
      </ul>

      <Switch>
        <Route path="/contacts/departments-1" component={ContactDepartments1} />
        <Route path="/contacts/departments-2" component={ContactDepartments2} />
        /=/ Здесь нет NotFound 
		    /=/ Поэтому необходимо указать <Redirect to="/404" /> 
		    /=/ Или <Route patch="*" component={NotFound} /> (если не работает Redirect)
      </Switch>
    </>
  );
}

export default App;

```

## _Папка Routes_

```
function LoginRoutes() {
  return (
    <Switch>
	    /=/ Указываем exact, чтобы не пропускал /login/sign-in/12313
      <Route path="/login/sign-in" exact component={LoginForm} />
      <Route path="/login/sign-up" exact component={RegisterForm} />
      <Redirect to="/404" />;
    </Switch>
  );
}
```

```
function App() {

  return (
    <Switch>
      <Route path="/" exact component={ArticlesPage} />
      <Route path="/login" component={LoginRoutes} />
      <Route path="/articles/:slug?" component={ArticleSwitcher} />
      <PrivateRoute path="/profile" component={ProfileEditForm} />
      <Route path="/404" component={NotFound} />
      <Redirect to="/404" />;
    </Switch>
  );
}
```

## _PrivateRoute_

```
function PrivateRoute({ component: Component, ...rest }) {
  const isAuthenticated = useSelector(authSelectors.isAuthenticated);

  return (
    <Route
      {...rest}
      render={(props) =>
        isAuthenticated ? <Component {...props} /> : <Redirect to="/sign-in" />
      }
    />
  );
}

|> App.jsx

<PrivateRoute path="/profile" component={ProfileEditForm} />
```

```
import { useSelector } from 'react-redux';
import { Children, cloneElement } from 'react';
import { Route, Redirect } from 'react-router-dom';
 
function PrivateRoute({ children, ...rest }) {
  const isAuthenticated = useSelector(authSelectors.isAuthenticated);

  return (
    <Route
      {...rest}
      render={(props) =>
        isAuthenticated ? (
          Children.map(children, (child) => cloneElement(child, { ...props }))
        ) : (
          <Redirect to="/sign-in" />
        )
      }
    />
  );
}

|> App.jsx

<PrivateRoute>
  <Component1 />
  <Component2 />
</PrivateRoute>
```