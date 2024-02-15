## In website ( RECOMMENDED )

### How to prepare to use?
You should put this code into `<head>` tag.
 * Change `{version}` to correct version (Example: 1.0.0)
```html
<script src="https://ezajax-js-web.netlify.app/EzAjax-Javascript-web-v{version}.js"></script>
```
Then now, you can use `ajax()` function!

## With library

### How to prepare to use?
First, you should put the file(`EzAjax-Javascript-lib-{version}.js`) to dir.
Second, put this code to top of your code.
```javascript
import { ajax } from "EzAjax.js"
```
and use `ajax()` function!

## Usage
#### Structure
```typescript
enum AjaxMethod {
    'GET', 'HEAD', 'POST', 'PUT', 'DELETE', 'CONNECT', 'OPTIONS', 'TRACE', 'PATCH'
}
interface AjaxOption {
    method?: AjaxMethod | string; // Default to 'GET'
    url: string;
    data?: string | object; // object will be stringified.
    headers?: Record<string, string>; // Example: {"Accepts":"*/*"}
    callback?: function(AjaxResponse) // Example: res => { console.log(res.responseText) }
}
interface AjaxResponse {
    error: boolean; // It NOT means 'is status code is 200?'. It means 'network is not connected'.
    statusCode: integer; // HTTP Status code. (OK: 200)
    statusText: string; // Example: 200 = "OK".
    responseText: string; // Response text.
}
ajax(option: AjaxOption): Promise<AjaxResponse>;
// Params = [ option: AjaxOption ]
// Returns Promise for AjaxResponse
```
#### Example Usage
```javascript
ajax({
    url: "https://google.com",
    method: "GET",
    callback: res => {
        console.log(res.responseText);
    }
});
// Send ajax request to 'https://google.com' with GET method.
// And log responseText to console.
```