#   Tích hợp Redux vào ReactJS App
-   Các bước setup trong pure js app:
```js
        const initialState = {
        list: ['Listening to music'],
        selectedId: null,
        }
        const hobbyReducer = (state = initialState, action) => {
        switch (action.type) {
        case 'ADD_HOBBY': {
        const newList = [...state.list];
        newList.push(action.payload);
        return {
        ...state,
        list: newList,
        }
        }
        default:
        return state;
        }
        };
        const { createStore } = window.Redux;
        const store = createStore(hobbyReducer);
```

-   Các bước setup trong ReactJS:
1. Cài đặt package react-redux và redux:
        - npm install --save redux react-redux
2.  Setup reducers và root reducer:  
``` js
                // reducers/hobby.js
                const initialState = {
                list: ['Listening to music'],
                selectedId: null,
                }
                const hobbyReducer = (state = initialState, action) => {
                switch (action.type) {
                case 'ADD_HOBBY': {
                const newList = [...state.list];
                newList.push(action.payload);
                return {
                ...state,
                list: newList,
                }
                }
                default:
                return state;
                }
                };
                export default hobbyReducer;
                // reducers/index.js (ROOT)
                const rootReducer = combineReducers({
                hobby: hobbyReducer,
                })
                export default rootReducer;

```  
3. Setup redux store
        
``` js
        // src/store.js
        const store = createStore(rootReducer);
        export default store;
```

4. Setup Store Provider cho toàn app src/index.js
``` js
    const Main = () => (
    <Provider store={store}>
    <App />
    </Provider>
)
``` 
5.  Connect vào redux từ reactjs component