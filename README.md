# SafeType

## Features
- Uses XOR and Rol64 for encryption
- Runtime value verification to detect memory tampering
- Serializable in Unity Inspector
- Supports various data types with operator overloading

## Usage (Unity)

### Declaration
```csharp
private SafeInt _score = new SafeInt(0);
```

### Usage
Use it like a normal int:
```csharp
_score = 100;
_score++;
```

### Display in UI
```csharp
textComponent.SetText($"{_score}");
```

### Serialize in Unity Inspector
```csharp
[SerializeField] private SafeInt _health = new SafeInt(100);
```

## Supported Types
- `SafeInt`
- `SafeFloat`
- `SafeDouble`
- `SafeVector2`
- `SafeVector3`
- `SafeQuaternion`
- `SafeBool`

## SafeInt Example
```csharp
SafeInt a = new SafeInt(5);
SafeInt b = new SafeInt(10);
SafeInt c = a + b; // c is 15
```

## SafeVector3 Example
```csharp
SafeVector3 pos1 = new SafeVector3(new Vector3(1, 2, 3));
SafeVector3 pos2 = new SafeVector3(new Vector3(4, 5, 6));
SafeVector3 result = pos1 + pos2; // result is (5, 7, 9)
```

## SafeQuaternion Example
```csharp
SafeQuaternion rot1 = new SafeQuaternion(Quaternion.Euler(0, 45, 0));
SafeQuaternion rot2 = new SafeQuaternion(Quaternion.Euler(0, 45, 0));
SafeQuaternion result = rot1 * rot2; // result is a combined rotation
```

## Notes
- Values are encrypted in memory using XOR and Rol64 operations.
- Runtime verification ensures that memory tampering is detected.
- Designed for client-side use only.

## TODO
- Add more supported types (optional)
- Implement OnValueChanged event
- Port to C++ / Unreal Engine
- Change encryption method (optional)

## Technical Details

### Encryption
The encryption uses a combination of XOR and Rol64 (rotate left) operations to secure the values in memory. The `CryptoUtils` class provides methods for encryption, decryption, and key generation.

### SafeType Class
The `SafeType<T>` class is a generic class that provides encryption and runtime verification for various data types. It supports operator overloading for arithmetic and comparison operations.

### BaseSafeValue Class
The `BaseSafeValue<T>` class is an abstract class that provides the base implementation for safe value types. It includes methods for getting and setting values, as well as serialization support for Unity.

### SafeValueDrawer Class
The `SafeValueDrawer` class is a custom property drawer for Unity that allows safe values to be displayed and edited in the Unity Inspector.

### Operations Interface
The `INumeric<T>` interface defines the operations that can be performed on numeric types. Various implementations of this interface provide support for different data types such as `int`, `float`, `double`, `Vector2`, `Vector3`, and `Quaternion`.

### Example Implementations
The `SafeInt`, `SafeFloat`, `SafeDouble`, `SafeVector2`, `SafeVector3`, `SafeQuaternion`, and `SafeBool` classes are concrete implementations of the `BaseSafeValue<T>` class, providing safe value types for different data types.


## License
This project is licensed under the MIT License.

## 📞 Contact

Paro - [@Pamenarti](https://twitter.com/pamenarti)

Email - [pamenarti@gmail.com](pamenarti@gmail.com)

Project Link: [https://github.com/Pamenarti/dex-contract-bypass](https://github.com/Pamenarti/dex-contract-bypass)