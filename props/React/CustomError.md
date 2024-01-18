```
 class ServiceError extends Error {
  constructor(error, info = '') {
    super();
    this.status = error?.response?.status;
    this.name = this.constructor.name;
    this.info = info;
    this.pureMessage = error.message;
    this.message = `${error.message} | ${info}`;
    Error.captureStackTrace(this, this.constructor);
  }
}

export default ServiceError;
```

```
const REDUCER = 'articles';

export const articleActions = {
  chunkLoaded: () => async (dispatch) => {
    dispatch(requested());
    try {
      const data = await articlesApi.getChunk();
      dispatch(received(data));
    } catch (error) {
      console.error(error);
      dispatch(requestFailed());
      dispatch(setErrors(REDUCER, error.message));
    }
  },
};
```