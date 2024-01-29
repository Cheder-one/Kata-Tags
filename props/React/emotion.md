## _Переиспользуемый UI-компонент_

Лучше использовать `scss.module + :global` и `@mixin` для переиспользуемых стилей, тк emotion плохо перезаписывает стили.

```
.article_actions {
  .delete_btn {
    color: $error-color;
    border-color: $error-color;
    @include default-bth-padding-center;

    &:hover {
      border-color: $error-color;
      @include default-bth-hover-style($error-color);
    }
  }

  .edit_btn {
    color: $success-color;
    border-color: $success-color;
    @include default-bth-padding-center;

    &:hover {
      border-color: $success-color;
      @include default-bth-hover-style($success-color);
    }
  }
}
```

-> Не использовать для перезаписи стилей:

```
import { Button } from 'antd';
/** @jsxImportSource @emotion/react */
import { css } from '@emotion/react';
import styled from '@emotion/styled';

const ButtonMod = styled(Button)`
  ${(props) => css`
    color: ${props.color}; /=/ !important если необходимо
    background-color: ${props['bg-color']}; /=/ props не пропускает bgColor
  `}
`;

ButtonMod.defaultProps = {
  'bg-color': 'black',
};
```

`==/OR/==`

```
const dynamicStyle = (props) => css`
  color: ${props.color};
`;

const ButtonMod = styled(Button)`
  ${dynamicStyle};
`;
```


