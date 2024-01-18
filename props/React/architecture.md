```
```plaintext
src/
|-- components/
|   |-- ui/
|   |   |-- Button.js
|   |   |-- Loader.js
|   |   |-- Modal.js
|   |
|   |-- common/
|   |   |-- Header.js
|   |   |-- Footer.js
|   |   |-- Pagination.js
|   |
|   |-- feature/
|       |-- UserList.js
|       |-- SomeOtherFeature.js
|
|-- pages/
|   |-- Home.js
|   |-- SomeFeaturePage.js
|
|-- hooks/
|-- routes/
|-- stores/
|-- utils/
|
|-- App.js
|-- index.js
```

- `common` - это место для `общих компонентов`.
- `feature` - это место для компонентов, `связанных с конкретными функциональными возможностями` вашего приложения.
- `pages` - это место где `отдельные страницы` вашего приложения `собранные вместе`.

-> Пример компонента связанного с конкретным функционалом

```
const UserList = () => {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    const fetchData = async () => {
      const response = await fetch('https://jsonplaceholder.typicode.com/users');
      const data = await response.json();
      setUsers(data);
    };

    fetchData();
  }, []);

  return (
    <div>
      <h2>Список пользователей</h2>
      <ul>
        {users.map(user => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
};
```

-> Page

```
const SomeFeaturePage = () => {
  return (
    <div>
      <Header />
      <UserList />
      <Footer />
    </div>
  );
};
```