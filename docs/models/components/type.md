# Type

The `SCA` method type available for the user

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.TypeSmsOtp

// Open enum: custom values can be created with a direct type cast
custom := components.Type("custom_value")
```


## Values

| Name           | Value          |
| -------------- | -------------- |
| `TypeSmsOtp`   | SMS_OTP        |
| `TypeChipOtp`  | CHIP_OTP       |
| `TypePhotoOtp` | PHOTO_OTP      |
| `TypePushOtp`  | PUSH_OTP       |