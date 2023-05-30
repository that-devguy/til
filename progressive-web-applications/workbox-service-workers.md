# WorkBox Service Worker

Service works are JavaScript files that run run separately from the main browser thread and enable advanced features such as caching, offline support, and background synchronization. **WorkBox** provides an abstraction layer and pre-built strategies to make it easier to handle common service worker tasks.

Step-by-step guide on how to use **WorkBox** for adding service workers to your web app:

1. Install WorkBox CLI globally:
```shell
npm install -g workbox-cli
```

2. Create a new project directory and navigate to it:
```shell
mkdir my-app && cd my-app
```

3. Generate the WorkBox service worker code using the CLI:
```shell
workbox wizard
```
*This command will prompt you with a series of questions to configure the service worker.*

4. After you finish the prompt it will generate the service worker code in a file named `sw.js`.

5. Register the service worker in your web application. Add the following code to your main JS file:
```javascript
if ('serviceWorker' in navigator) {
  window.addEventListener('load', () => {
    navigator.serviceWorker.register('/sw.js')
      .then(registration => {
        console.log('Service Worker registered:', registration);
      })
      .catch(error => {
        console.error('Service Worker registration failed:', error);
      });
  });
}
```
*Make sure to adjust the path to the `sw.js` accordingly*

6. Build and serve your web application using a static file server or dev environment.

The service worker will intercept network requests, cache responses, and provide offline support based on the config specificed during the wizard setup.