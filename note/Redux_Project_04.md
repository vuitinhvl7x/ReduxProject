# Xử lí validation với **YUP**

-   ```jsx
    const initialValues = {
    title: '',
    categoryId: null,
    photo: '',
    };

    // Xử lí validation 
    const validationSchema = Yup.object().shape({
    title: Yup.string().required('This field is required.'),

    categoryId: Yup.number()
      .required('This field is required.')
      .nullable(),

    photo: Yup.string().when('categoryId', {
      is: 1,
      then: Yup.string().required('This field is required.'),
      otherwise: Yup.string().notRequired(),
    })
    });

    ```

