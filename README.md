# DependencyProperty
[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://lbesson.mit-license.org/)
[![GPLv3 license](https://img.shields.io/badge/License-GPLv3-blue.svg)](http://perso.crans.org/besson/LICENSE.html)

## Ncoresoft Repository
> Ncoresoft Git. [here.](https://github.com/ncoresoftsource/ncoresoftgit)

## 2. DependencyProperty
1. Class
2. Naming Rules
3. DependencyProperty.Register
4. PropertyMetadata

### 2.1. Class Structure
namespace: `System.Windows`   
assembly: `WindowsBase.dll`   
class access: `sealed`   
first version: `.net 3.0`
```csharp
namespace System.Windows
{
    public sealed class DependencyProperty
    {

    }   
}
```

### 2.2. Naming Rules



### 2.3. DependencyProperty.Register

### 2.4. PropertyMetadata

## 3. Example

### 3.1. Standard Type

```csharp
public class Profile : Control
{
    public int Age
    {
        get { return (int)this.GetValue(AgeProperty); }
        set { this.SetValue(AgeProperty, value); }
    }

    public static readonly DependencyProperty AgeProperty = DependencyProperty.Register(
        "Age", typeof(int), typeof(Profile), new PropertyMetadata(0));
}
```
### 3.2. Extander Property
```csharp
class PasswordExtender
{
    public static readonly DependencyProperty PasswordProperty =
        DependencyProperty.RegisterAttached("Password",
        typeof(string), typeof(PasswordExtender),
        new FrameworkPropertyMetadata(string.Empty, OnPasswordPropertyChanged));
}
```
```csharp
public static string GetPassword(DependencyObject dp)
{
    return (string)dp.GetValue(PasswordProperty);
}

public static void SetPassword(DependencyObject dp, string value)
{
    dp.SetValue(PasswordProperty, value);
}
```
```csharp
private static void OnPasswordPropertyChanged(DependencyObject sender,
    DependencyPropertyChangedEventArgs e)
{
}
```

### 3.3. Value Callback Changed
```csharp
public string Password
{
    get { return (string)this.GetValue(PasswordProperty); }
    set { this.SetValue(PasswordProperty, value); }
}
public static readonly DependencyProperty PasswordProperty =
    DependencyProperty.Register("Password", typeof(string), typeof(VisualPassword),
        new PropertyMetadata(string.Empty, PasswordPropertyChanged));

private static void PasswordPropertyChanged(DependencyObject d, DependencyPropertyChangedEventArgs e)
{
    
}
```
## 4. Opensource

## 99. References
> Article Tutorial 2 [here.](https://www.wpftutorial.net/DependencyProperties.html)
> Article Tutorial 2 [here.](https://sodocumentation.net/wpf/topic/2914/dependency-properties)
