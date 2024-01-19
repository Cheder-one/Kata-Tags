``` 
|> FormComponent.js

import { Form, Input, Button } from 'antd';
import { useForm, Controller } from 'react-hook-form';
import { emailCheck, passwordCheck } from './validation';  

const FormComponent = () => {
  const { handleSubmit, control, formState: { errors } } = useForm();

  const onSubmit = (data) => {
    // Обработка данных формы
    console.log(data);
  };

  return (
    <Form onFinish={handleSubmit(onSubmit)}>
      <Form.Item 
	      label="Email" 
	      help={errors.email?.message} 
	      validateStatus={errors.email ? 'error' : ''}
	    >
        <Controller
          name="email"
          control={control}
          rules={emailCheck} 
          render={({ field }) => <Input {...field} />}
        />
      </Form.Item>

      <Form.Item
	      label="Password" 
	      help={errors.password?.message} 
	      validateStatus={errors.password ? 'error' : ''}
	    >
        <Controller
          name="password"
          control={control}
          rules={{ 
	          required: 'Password is required', 
	          minLength: { value: 6, message: 'Password is too short' } 
	        }}
          render={({ field }) => <Input.Password {...field} />}
        />
      </Form.Item>

      <Form.Item>
        <Button type="primary" htmlType="submit">Submit</Button>
      </Form.Item>
    </Form>
  );
};
```

``` 
|> validation.js

export const emailCheck = {
  required: true,
  pattern: { value: /\S+@\S+\.\S+/, message: 'Invalid email' },
};

export const passwordCheck = {
  required: 'Your password needs to be at least 6 characters.',
  minLength: {
    value: 6,
    message: 'Your password needs to be at least 6 characters.',
  },
};

export const confirmPassCheck = (prevPass) => ({
  required: 'Passwords must match',
  validate: (pass) => prevPass === pass || 'Passwords must match',
});
```

## _Вынос в функционала_

```
function FormController({
  name,
  label,
  control,
  rules,
  errors,
  children,
  className,
  hasFeedback,
}) {
  return (
    <Form.Item
      name={name}
      label={label}
      className={className}
      help={errors[name]?.message}
      validateStatus={errors[name] ? 'error' : 'success'}
      hasFeedback={hasFeedback}
    >
      <Controller
        name={name}
        control={control}
        rules={rules}
        render={({ field }) => cloneElement(children, { ...field })}
      />
    </Form.Item>
  );
}
```
#cloneElement 

```
import { Flex, Form, Input, Divider, Checkbox, Button } from 'antd';
import { useForm } from 'react-hook-form';
import { Link } from 'react-router-dom';

function RegisterForm() {
  const {
    watch,
    control,
    handleSubmit,
    formState: { errors },
  } = useForm();

  const onSubmit = (data) => {
    console.log(data);
  };

  return (
    <Flex className={_.login_box} id="login-form" justify="center">
      <Form
        className={_.login_form}
        layout="vertical"
        onFinish={handleSubmit(onSubmit)}
      >
        <h3 className={_.title}>Create new account</h3>
        <FormController
          name="name"
          label="Username"
          control={control}
          rules={{ required: true }}
          errors={errors}
        >
          <Input id="name" placeholder="Username" />
        </FormController>
        <FormController
          name="email"
          label="Email address"
          control={control}
          rules={emailCheck}
          errors={errors}
        >
          <Input id="email" placeholder="Email address" />
        </FormController>

        <FormController
          name="password"
          label="Password"
          control={control}
          rules={passwordCheck}
          errors={errors}
        >
          <Input.Password
            id="password"
            type="password"
            placeholder="Password"
          />
        </FormController>
        <FormController
          name="password-repeat"
          label="Repeat Password"
          control={control}
          rules={confirmPassCheck(watch('password'))}
          errors={errors}
        >
          <Input.Password
            id="password-repeat"
            type="password"
            placeholder="Password"
          />
        </FormController>

        <Divider />
        <FormController
          name="checkbox"
          control={control}
          className={_[`checkbox_wrapper${errors.checkbox ? '--error' : ''}`]}
          rules={{ required: true }}
          errors={errors}
          hasFeedback
        >
          <Checkbox>
            I agree to the processing of my personal information
          </Checkbox>
        </FormController>

        <Button htmlType="submit" type="primary" block>
          Create
        </Button>

        <div className={_.have_account}>
          Already have an account?
          <Link className={_.toggle_login} to="/sign-in/">
            Sign In
          </Link>
        </div>
      </Form>
    </Flex>
  );
}
```