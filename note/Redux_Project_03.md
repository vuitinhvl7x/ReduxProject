# Tạo Custom Field cho Formik
-   Trước đó dùng **Form** của thư viện **reactstrap** để tạo UI tĩnh. Mà có rất nhiều việc cần xử lí với Form: tạo dữ liệu, quản lí sự kiện thay đổi, submit Form, quản lí Error => Đễ dễ dàng hơn trong việc xử lí Form thì có thể dùng Formik 
-   ``` jsx
    import { FastField, Form, Formik } from 'formik';
    function PhotoForm(props) {
    
    // Khi tạo Formik cần một initialValue để khởi tạo
    const initialValues = {
    // lưu ý: Do ban đầu input mình là UNCONTROLLED sau khi dùng Fomirk thành CONTROLLED nên nếu đặt giá trị title là undefined => cho controll: uncontrolled
    // Vì vậy nên cập nhật giá trị để controll có thể empty string hoặc null 
    title: '', 
    categoryId: null, 
    };
    <Formik
      initialValues={initialValues}
    >
      // bên trong là 1 callback
      {formikProps => {
    
        const { values, errors, touched } = formikProps; 
        console.log({ values, errors, touched });

        return (
            // Form này là của Formik không phải của reacstrap => giúp hanlde sẵn như reset submit,... 
          <Form>
            // Trong này gồm controlls - là 1 FormGroup bao gồm như: label, input, errorMess, ...
            // Người ta thường dùng FastField(độc lập - chỉ re-render khi tác động vào Field của nó thôi) hoặc Field (phụ thuộc lẫn nhau- thay đổi của là Field nào cũng là re-render)
            <FastField
              // prop của FastField
              name="title"
              component={InputField}

              // các props truyền vào InputField 
              label="Title"
              placeholder="Eg: Wow nature ..."
            />

            <FastField
              name="categoryId"
              component={SelectField}

              label="Category"
              placeholder="What's your photo category?"
              options={PHOTO_CATEGORY_OPTIONS}
            />

            <FormGroup>
              <Label for="categoryId">Photo</Label>

              <div><Button type="button" outline color="primary">Random a photo</Button></div>
              <div>
                <img width="200px" height="200px" src={Images.COLORFUL_BG} alt="colorful background" />
              </div>
            </FormGroup>

            <FormGroup>
              <Button color="primary">Add to album</Button>
            </FormGroup>
          </Form>
        );
      }}
    </Formik>
    }
    ```
- Dưới đây là ví dụ 1 component **InputField** được truyền trong **FastField**
``` jsx
import PropTypes from 'prop-types';
import React from 'react';
import { FormGroup, Input, Label } from 'reactstrap';

InputField.propTypes = {
    // Props được truyền thêm từ Formik
  field: PropTypes.object.isRequired,
  form: PropTypes.object.isRequired,

    // Props được định nghĩa thêm bởi dev
  type: PropTypes.string,
  label: PropTypes.string,
  placeholder: PropTypes.string,
  disabled: PropTypes.bool,
};

InputField.defaultProps = {
  type: 'text',
  label: '',
  placeholder: '',
  disabled: false,
}

function InputField(props) {
  const {
    field,
    type, label, placeholder, disabled,
  } = props;

  // trong field có 4 thứ là name, value, onChange, onBlur
  const { name } = field;

  return (
    <FormGroup>
    //  ô có label hoặc không có
      {label && <Label for={name}>{label}</Label>}

      <Input
        id={name}
        {...field}

        type={type}
        disabled={disabled}
        placeholder={placeholder}
      />
    </FormGroup>
  );
}

export default InputField;        
 ```


 - Chốt lại:
    -   Câu nối giữa UI control và Formik.
 
    -   UI control là một controlled component với props:
        -   name: tên xác định control
        -   value: giá trị của control
        -   onChange: trigger hàm này với giá trị mới khi có thay đổi
        -   onBlur: xác định khi nào thi control này bị touched
    