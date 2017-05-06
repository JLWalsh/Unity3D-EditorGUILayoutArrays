# Unity3D - EditorGUILayout Arrays
The EditorGUILayout class provides many features in order to create custom editors, but they sadly lack the simple feature to display arrays. This project aims at preserving the same usage method as the EditorGUILayout functions, so you using it won't be anything too different. In the editor, the array will behave exactly like the original Unity array fields.

### Installation
The class provided doesn't extend the EditorGUILayout class, to prevent confusion. Simply download the **EditorGUILayoutArrays.cs** file and drop it into your assets project.

### Usage
There are two ways to use the array fields. Note that both examples will output the same result.

**Recommended usage**
```csharp
private EditorGUILayoutArrays.ArrayFieldSettings settings = new EditorGUILayoutArrays.ArrayFieldSettings("String array");
private string[] stringArray = new string[] { "Hello", "World!", "Another", "Unoriginal", "Catchphrase" };

// Somewhere else in your code...
void OnInspectorGUI() {
    stringArray = EditorGUILayoutArrays.StringArrayField(settings, stringArray);
}
```

**Not recommended (but still valid) usage**
```csharp
private string arrayFieldTitle = "String array";
private bool arrayFieldOpen = false;
private string[] stringArray = new string[] { "Hello", "World!", "Another", "Unoriginal", "Catchphrase" };

// Somewhere else in your code...
void OnInspectorGUI() {
    stringArray = EditorGUILayoutArrays.StringArrayField(arrayFieldTitle, ref arrayFieldOpen, stringArray);
}
```

#### Result
![image](http://i.imgur.com/jTMB8A3.png)

### Supported Types
Generics could not be used for this project, as Unity has a field function specific for each type. As of now, the supported types are:

- string
- int
- float
- double
- bool
- Vector2
- Vector3
- Vector4
- Color

### Additional note (s)

**EditorGUILayoutArrays.ArrayFieldSettings (string label, bool open)**:

This class aims at simplifying the usage of the fields. Since custom fields can't contain their values (they have to be stored somewhere outside of the *OnInspectorGUI()* function, they have to be stored somewhere. This class contains two values, the **label (string)**, which represents the title of the array in the editor. The second value, **open (bool)** determines the state of the folding. It's set to *false* by default.

**If you have any suggestions for new array types, feel free to contact me.**
