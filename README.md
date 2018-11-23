# UnityScriptPolicies
## Intro
The guide is based on my experiences , recommendations from developers and colleges. When doing code reviews always check for these things and if there is an issue then let them know and reference this guide. If you have suggestions or questions then feel free to leave messages.

## Reflection
Reflection is slow and breaks the obfuscator. You can use it in Unity Editor or Debugging but don’t use it in Runtime!
It also doesn’t work on mobile if the “Script Call Optimization” is set to “Fast but no Exception”.

## Public Members
Use as few public members as possible. It’s much easier to refractor one method than to refractor every place that uses that member.

## Globals
Use as few globals as possible. Instead of globals create singletons that hold the data. Singletons are special classes that should be checked to make sure that multiple instances are not created.

## Script Policy
### Class Members
Use the lower camel case for all public, private, and other members.

#### Examples
```
public int exampleInt;
public float exampleFloat;
public bool exampleBool;
```

### private Members
Named the private members with prefix "m_".
#### Examples
```
private int m_exampleInt;
private float m_exampleFloat;
private bool m_exampleBool;
```

### const and readonly
The const and readonly members are spelled with a CAPITAL letter and split the letter with "_";

#### Examples
```
private const int CONST_INT = 1;
public const string DOCUMENT_NAME = "UnityScriptPolicies";
```

### Methods
Named methods with the upper camel case.

#### Examples
```
public void FirstMethod()  
{  
    
}  
```

### Braces
Always seperated the open brace or close brace in a new line.
If you are using if/for or other things where braces are optional for the body always add the braces for it.

#### Examples
```
using UnityEngine;  
    
public class BraceExample : MonoBehaviour    
{    
    private void Start ()    
    {    
        for(int i = 0; i < 10; i++)    
        {    
            Debug.Log(i);    
        }    
    }    
    
    private void Update ()    
    {    
        if(!CanUpdate())    
        {    
            return;    
        }    
    
        //TODO: Update    
    }    
    
    private bool CanUpdate()    
    {    
        return true;    
    }    
}    
```

### interface
Named the interface class with prefix "I".

#### Examples
```
public interface IUpdate  
{  
  
}  
  
public interface IFixedUpdate  
{  
  
}
```

### Action, Delegate, Event, and Func
Named Action, delegate, event, and Func with prefix "On" in methods and "on" in members.

#### Examples
```
public delegate void OnPlayerHealthPointUpdate(float hp);
public Action onAction;
```

### Null Check
Always do the null check.

#### Examples
```
private GameObject m_target;  
  
private void Update()  
{  
    if(m_target == null)  
    {  
        return;  
    }  
  
    //TODO: Update the target  
}  
```

### UI (UGUI)
Named GameObjects and class members with the component's name as the suffix.

#### Examples
```
| Component  | Policy              | Example            |
|------------|---------------------|--------------------|
| Text       | [Feature]Text       | TitleText          |
| Image      | [Feature]Image      | CloseImage         |
| RawImage   | [Feature]RawImage   | BackgroundRawImage |
| Button     | [Feature]Button     | PlayButton         |
| Toggle     | [Feature]Toggle     | BGMToggle          |
| Slider     | [Feature]Slider     | HPSlider           |
| Scrollbar  | [Feature]Scrollbar  | ItemScrollbar      |
| Dropdown   | [Feature]Dropdown   | WeaponDropdown     |
| InputField | [Feature]InputField | PasswordInputField |
| Canvas     | [Feature]Canvas     | MainCanvas         |
```
