```

.checkbox_wrapper {
  :global {
    .ant-checkbox {
      border-color: $daybreak-blue-blue-6;
    }

    .ant-checkbox-inner {
      border-color: $daybreak-blue-blue-6;

      &::after {
        border-color: $grey-grey-1;
      }
    }

    .ant-checkbox-checked .ant-checkbox-inner {
      background-color: $daybreak-blue-blue-6;
      border-color: $daybreak-blue-blue-6;
    }

    .ant-checkbox-wrapper:not(.ant-checkbox-wrapper-disabled):hover
      .ant-checkbox-checked:not(.ant-checkbox-disabled)
      .ant-checkbox-inner {
      background-color: $daybreak-blue-blue-6;
      border-color: $daybreak-blue-blue-6;
      background-clip: border-box;
    }
  }

  &--error {
    :global {
      .ant-checkbox {
        border-color: $error-color;
      }

      .ant-checkbox-inner {
        border-color: $error-color;

        &::after {
          border-color: $error-color;
        }
      }

      .ant-checkbox-checked .ant-checkbox-inner {
        border-color: $error-color;
      }

      .ant-checkbox-wrapper:not(.ant-checkbox-wrapper-disabled):hover
        .ant-checkbox-checked:not(.ant-checkbox-disabled)
        .ant-checkbox-inner {
        border-color: $error-color;
      }
    }
  }
}
```