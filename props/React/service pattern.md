`API Wrapper Pattern` или же `Service Pattern` - подразумевает создание отдельного слоя или модуля для взаимодействия с внешним API. Затем в этом модуле `создаются методы`, `предоставляющие` удобный `интерфейс для выполнения` различных `CRUD операций`. 

-> Вариант 0

```
import axios from 'axios';

const BASE_URL = 'https://blog.kata.academy/api/';

const api = axios.create({
  baseURL: BASE_URL,
  headers: {
    'Content-Type': 'application/json',
    Accept: 'application/json',
    // Authorization: `Bearer 'token'`
  },
});

const apiService = {
  get(url, params) {
    return api.get(url, params);
  },
  post(url, data) {
    return api.post(url, data);
  },
};

export default apiService;
```

-> Чтобы сократить код в `articleService`

```
articleService.createArticle()
             .setTitle("Заголовок")
             .setContent("Содержание")
             .setAuthor("Автор")
             .save();
```

-> Вариант 1

```
import axios from 'axios';

const API_BASE_URL = 'https://example.com/api';

const api = axios.create({
  baseURL: API_BASE_URL,
  headers: {
    'Content-Type': 'application/json',
    'Authorization': `Bearer ${yourToken}`
  },
});

export const articlesAPI = {
  getAllArticles: () => api.get('/articles'),
  getArticle: (articleId) => api.get(`/articles/${articleId}`),
  createArticle: (data) => api.post('/articles', data),
  updateArticle: (articleId, data) => api.put(`/articles/${articleId}`, data),
  deleteArticle: (articleId) => api.delete(`/articles/${articleId}`),
};
```

```
const ArticlesComponent = () => {
  const dispatch = useDispatch();
  const articles = useSelector((state) => state.articles);

  useEffect(() => {
    dispatch(articlesAPI.getAllArticles())
      .then((response) => console.log('Articles:', response.data)})
      .catch((error) => console.error('Error fetching articles:', error.message)});
  }, [dispatch]);
};
```

-> Вариант 2

```
import axios from 'axios';

const API_BASE_URL = 'https://api.example.com';   

const api = axios.create({
  baseURL: API_BASE_URL
});

// Обработка ошибок
const handleErrors = (error) => {
  console.error('API Error:', error);
  throw error;
};

// Методы для работы с Articles
const ArticlesAPI = {
  getAll: () => {
    return api.get('/articles')
      .then(response => response.data)
      .catch(handleErrors);
  },
  getOne: (articleId) => {
    return api.get(`/articles/${articleId}`)
      .then(response => response.data)
      .catch(handleErrors);
  },
  create: (articleData) => {
    return api.post('/articles', articleData)
      .then(response => response.data)
      .catch(handleErrors);
  },
  update: (articleId, articleData) => {
    return api.put(`/articles/${articleId}`, articleData)
      .then(response => response.data)
      .catch(handleErrors);
  },
  delete: (articleId) => {
    return api.delete(`/articles/${articleId}`)
      .then(response => response.data)
      .catch(handleErrors);
  }
};
```

```
 const ArticleList = () => {
	const dispatch = useDispatch();
	const articles = useSelector((state) => state.articles);

  useEffect(() => {
		/=/ Инкапсулировать это в Redux
    ArticlesAPI.getAll().then((data) => {
      dispatch({ type: 'SET_ARTICLES', payload: data.articles });
    });
  }, [dispatch]);
};
```

-> Вариант 3

```
// apiService.js

import axios from 'axios';
import { useDispatch } from 'react-redux';
import { startLoading, setError, setArticles } from './articlesSlice'; // Импортируйте ваши actions

const BASE_URL = 'https://example.com/api';

const useApiService = () => {
  const dispatch = useDispatch();

  const apiClient = axios.create({
    baseURL: BASE_URL,
    headers: {
      // Добавьте необходимые заголовки, например, авторизацию, сюда
      // Authorization: `Bearer ${yourToken}`
    },
  });

  const handleRequest = async (requestFn, successAction, errorCallback) => {
    try {
      dispatch(startLoading());
      const response = await requestFn();
      dispatch(successAction(response.data));
    } catch (error) {
      dispatch(setError(error.message || 'Something went wrong'));
      if (errorCallback) errorCallback(error);
    }
  };

  const getArticles = async () => {
    await handleRequest(
      () => apiClient.get('/articles'),
      setArticles,
      (error) => {
        // Дополнительная логика обработки ошибок при загрузке статей
        console.error('Error loading articles:', error);
      }
    );
  };

  return {
    getArticles,
  };
};

export default useApiService;
```

```
import React, { useEffect } from 'react';
import { useDispatch, useSelector } from 'react-redux';
import useApiService from './apiService';

const ExampleComponent = () => {
  const dispatch = useDispatch();
  const articles = useSelector((state) => state.articles);
  const apiService = useApiService();

  useEffect(() => {
    apiService.getArticles();
  }, [apiService]);
};

export default ExampleComponent;
```