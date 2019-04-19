[![NPM](https://img.shields.io/npm/v/axios-react.svg)](https://www.npmjs.com/package/axios-react)
[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

# Axios React

HTTP client component for React with child function callback to creating async requests in render based on [Axios](https://github.com/axios/axios).


**[Online Playground](https://codesandbox.io/s/888j39z688)**


## Usage:

```
import React, { Fragment } from 'react';
import Request from "axios-react";

const Demo = () => (
  <Request
    config={{
      method: 'get',
      url: 'https://jsonplaceholder.typicode.com/todos/1',
    }}
    skip={false} // optional
  >
    {({ loading, response, error, refetch, networkStatus }) => (
      <Fragment>
          {networkStatus && <span>{networkStatus}</span>}
          {loading && <span>Loading...</span>}
          {error && <span>{error.response.data}</span>}
          {response && <h3>{response.data.title}</h3>}
          <button onClick={refetch}>Refetch!</button>
      </Fragment>
    )}
  </Request>
)
```

**Note:**

You can pass `skip` prop to `Request` component for stop sending request on mounting.


## Request Config:

These are the available config options for making requests. Only the URL is required. Requests will default to get if the method is not specified. You can use all of the [Axios request config options](https://github.com/axios/axios#request-config)


## Response Schema:

The response for a request contains the [Axios response schema](https://github.com/axios/axios#response-schema).
