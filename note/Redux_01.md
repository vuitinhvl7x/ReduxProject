#   REDUX Là gì ?
-   Thư viện js quản lí state, mà state đó có thể dự đoán được
-   Sử dụng kiến trúc uni-directional data flow (tức một chiều)
- ![ảnh minh họa cấu trúc của Redux](https://images.viblo.asia/02b5e869-9205-4791-88b1-de11b90d3591.gif)
-  Ví dụ đơn giản khi dùng Redux:
``` js
import { createStore } from 'redux'
// Step 1: Define a reducer
// A pure js function
// that transform the old state to the new one
// based on the action.type
function counter(state = 0, action) {
switch (action.type) {
case 'INCREMENT':
return state + 1
case 'DECREMENT':
return state - 1
default:
return state
}
}
// Step 2: Init your store with the reducer
// Its API is { subscribe, dispatch, getState }.
let store = createStore(counter)
// Step 3: Subscribe to state changes to update UI
store.subscribe(() => console.log(store.getState()))
// Step 4: Dispatch action to update redux state
// The only way to mutate the internal state is to dispatch an action.
store.dispatch({ type: 'INCREMENT' }) // 1
store.dispatch({ type: 'INCREMENT' }) // 2
store.dispatch({ type: 'DECREMENT' }) // 1
```
>   Redux sử dụng kiến trúc 1 chiều: uni-directional data flow  
>   Redux chỉ dùng 1 store duy nhất làm Single Source of Truth  
>   Redux state là READ-ONLY. Muốn update phải dispatch một action (js object)  
>   Những thay đổi của redux state được thực hiện bởi Pure functions (reducer)  
>   Redux có thể dùng cho các javascript apps, không chỉ riêng gì ReactJS.

