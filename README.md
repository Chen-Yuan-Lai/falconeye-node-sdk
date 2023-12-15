# FalconEye SDK for JavaScript

## Content

- ### Supported Platforms
- ### Installation and Usage

## Supported Platforms

- ### Express
- ### Javascript

## Installation and Usage

### Just simply install by npm

```
npm install --save @falcon-tech/node
```

### Setup and usage of the SDK follows by the principle.

**Initialization**

```javascript
import fe from '@falconeye-tech/sdk';

const er = new fe();

await er.init({
  apiHost: 'https://handsomelai.shop',
  userKey: '',
  clientToken: '',
});
```

If you initialize successfully, you will see the text on the terminal:

```bash
initialize SDK successfully
Listening on port 3001

```

**Custom error logger in the try/catch**

```javascript
app.get('/programError', async (req, res, next) => {
  try {
    console.log('Hi');
    throw new Error('This is the error!');
  } catch (e) {
    er.captureError(e);
  }
});
```

**Usage in express framework**

```javascript
app.use(er.requestHandler());

app.get('/typeError', async (req, res, next) => {
  try {
    console.logg('Hi');
  } catch (e) {
    next(e);
  }
});

// ... routes

app.use(er.errorHandler());

// Global error handler
app.use((err, req, res, next) => {
  res.status(error.statusCode).json({
    error: error.message,
  });
});
```
