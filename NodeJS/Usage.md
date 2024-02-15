### How to prepare to use?
First, you should put the file(`EzAjax-Javascript-lib-{version}.js`) to dir.
Second, put this code to top of your code.
```javascript
import { ajax } from "EzAjax-Javascript-lib-{version}.js"
```
or
```javascript
const ajax = require("EzAjax-Javascript-lib-{version}.js").ajax;
```
and use `ajax()` function!

##### npm?
###### We will publish to npm soon. Please wait for it!

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