#   Tổ chức Routing 
- từ thư viện react-router-dom:
    -   ```jsx
        import { BrowserRouter, Route, Switch, Redirect, Link } from 'react-router-dom';
        ```
    -   BrowserRouter: là một component cha cho các Route, giúp quản lý đường dẫn URL hiện tại của ứng dụng.
    -   Route: là một component để khai báo một đường dẫn URL cho ứng dụng. Nó có các thuộc tính như path, component, exact, render,... để xác định URL và component tương ứng khi đường dẫn URL được truy cập.
    -   Switch: là một component để quản lý các Route. Nó bao bọc các Route và chỉ hiển thị component của Route đầu tiên mà khớp với đường dẫn URL hiện tại. Điều này giúp tránh trường hợp hiển thị nhiều component cùng lúc.
    -   Redirect: là một component để chuyển hướng người dùng đến một đường dẫn URL khác.
    -   Link: là một component để tạo ra các liên kết URL trong ứng dụng. Nó thay thế cho thẻ a truyền thống và sử dụng history.push để chuyển hướng người dùng đến đường dẫn URL tương ứng.
``` jsx
function App() {
  return (
    <BrowserRouter>
      <Switch>
        <Route path="/photos" component={Photo} />
        <Route path="/user" component={User} />
        <Route component={NotFound} />
      </Switch>
    </BrowserRouter>
  )
}
```
-   Sử dụng lazy load components: Không load ngay component khi dùng khi điều hướng bằng **Route**
    -   ``` jsx
        const Photo = React.lazy(() => import(url))
        ```
    -   Khi xài react lazy thì phải dùng 
    -   ``` jsx
        <Suspense fallback={<div>Loading ...</div>}>
        <Suspense/>
        ```
        bọc ngoài **BrowserRouter** để chờ trang loading 
    - Ngoài ra dùng **useRouteMatch()** để lấy path từ cha với 
-   Load theo features