# Table of Contents
- [Table of Contents](#table-of-contents)
  - [General](#general)
    - [Name important tab components of Unity 3D.](#name-important-tab-components-of-unity-3d)
    - [What is a GameObject in Unity?](#what-is-a-gameobject-in-unity)
    - [Briefly describe the use of prefab.](#briefly-describe-the-use-of-prefab)
    - [Describe special folders in Unity.](#describe-special-folders-in-unity)
    - [What are the necessary conditions for objects to collide?](#what-are-the-necessary-conditions-for-objects-to-collide)
    - [What are layers in Unity used for?](#what-are-layers-in-unity-used-for)
    - [Name a few Unity packages on the assets store that you know. What is it used for?](#name-a-few-unity-packages-on-the-assets-store-that-you-know-what-is-it-used-for)
  - [Programming](#programming)
    - [What is the order in which `OnEnable`, `Awake`, and `Start` occur during runtime?](#what-is-the-order-in-which-onenable-awake-and-start-occur-during-runtime)
    - [Difference between `Update`, `FixedUpdate` and `LateUpdate`?](#difference-between-update-fixedupdate-and-lateupdate)
    - [How to prevent the existing GameObject from being destroyed when change Scene?](#how-to-prevent-the-existing-gameobject-from-being-destroyed-when-change-scene)
    - [Describe the role of quaternions.](#describe-the-role-of-quaternions)
    - [List some ways to move an object in Unity.](#list-some-ways-to-move-an-object-in-unity)
    - [What is Lerp in Unity?](#what-is-lerp-in-unity)
    - [Explain why `Time.deltaTime` should be used.](#explain-why-timedeltatime-should-be-used)
    - [How to pause the game in Unity?](#how-to-pause-the-game-in-unity)
    - [How do you create and use a `Coroutine`?](#how-do-you-create-and-use-a-coroutine)
    - [What are ScriptableObjects?](#what-are-scriptableobjects)
    - [What is the difference between `GetComponent<T>()` and `FindObjectOfType<T>()`?](#what-is-the-difference-between-getcomponentt-and-findobjectoftypet)
    - [What are the purposes and uses of \[SerializeField\] and \[HideInInspector\] attributes in Unity?](#what-are-the-purposes-and-uses-of-serializefield-and-hideininspector-attributes-in-unity)
    - [What is the purpose and functionality of Raycast in Unity?](#what-is-the-purpose-and-functionality-of-raycast-in-unity)
    - [Why is using object pooling important? How does it work in Unity?](#why-is-using-object-pooling-important-how-does-it-work-in-unity)
    - [How to save local data?](#how-to-save-local-data)
    - [How to quit the game in Unity?](#how-to-quit-the-game-in-unity)
    - [How to lock \& hide the cursor in Unity?](#how-to-lock--hide-the-cursor-in-unity)
    - [How to use random values in Unity?](#how-to-use-random-values-in-unity)
  - [Graphics](#graphics)
    - [What is LOD and what are its advantages and disadvantages?](#what-is-lod-and-what-are-its-advantages-and-disadvantages)
    - [What is the use of Occlusion Culling?](#what-is-the-use-of-occlusion-culling)
    - [Describe how the stencil buffer works and uses in unity?](#describe-how-the-stencil-buffer-works-and-uses-in-unity)
    - [What is the difference between material and shared material in MeshRender?](#what-is-the-difference-between-material-and-shared-material-in-meshrender)
    - [Unity provides several light sources. What are they?](#unity-provides-several-light-sources-what-are-they)
  - [References](#references)


## General

### Name important tab components of Unity 3D.

* **Hierarchy**: The hierarchy displays every GameObject in a list.
* **Inspector** displays detailed information about your currently selected GameObject, including all attached  
Components and their properties. Here, you modify the functionality of GameObjects in your scene.
* **Game view**: The game view option lets developers view the game and make changes to it as they play in real time.
* **Scene view**: The scene view is a 3D preview of the open scene. Here, developers can add and manage GameObjects.
* **Project window**: The project window is ideal for complex games. Game developers can use the project window to find  
game assets in a directory for all models, scripts, and prefabs.
* **Toolbar**: The toolbar contains various tools for the game and scene windows.

---

### What is a GameObject in Unity?

`GameObjects` are the fundamental objects in Unity that represent characters, props and scenery. They do not accomplish  
 much in themselves but they act as containers for Components, which implement the real functionality.

---

### Briefly describe the use of prefab.

Instantiated when the game is running, **prefab** is equivalent to a template, making a default configuration for the  
materials, scripts, and parameters you already have to facilitate future modifications. The content packaged by  
**prefab** simplifies the export operation and facilitates team communication.

---

### Describe special folders in Unity.

* **Assets**:  
  The root folder of your Unity project, containing all assets.
* **Editor**:  
  Scripts placed in this folder are considered Editor scripts and will only be included in the Unity Editor build, not   
  in the final game or application.
* **Resources**:  
  Assets placed in this folder can be loaded at runtime using Resources.Load.
* **Plugins**:  
  Used for native plugins that extend Unity's functionality using native code (e.g., DLLs).
* **Standard Assets**:  
  A folder that Unity recognizes for its Standard Assets packages.
* **StreamingAssets**:
  Assets placed here are included in the build as-is and can be accessed at runtime.
* **Gizmos**:  
  Contains Gizmo icons that can be used in the scene view for custom visualization.
* **Editor Default Resources**:  
  Stores default resources used by the Unity Editor.

---

### What are the necessary conditions for objects to collide?

Both objects must have a **Collider**, and one of the objects must also have a **Rigidbody**.

---

### What are layers in Unity used for?

* **Collision Detection**:  
  Layers are often used to control which objects can collide with each other. By assigning GameObjects to specific  
  layers, you can set up collision matrices to define which layers can interact with each other. This allows for  
  fine-grained control over the physics interactions in your game.
* **Ray-casting**:  
  When performing raycasts, you can specify which layers the ray should interact with. This is useful for targeting   
  specific types of objects or ignoring others based on their layer assignments.
* **Rendering and Camera Culling**:  
  Layers are used to control which objects are visible to specific cameras. This is essential for optimizing rendering   
  performance. For example, you might have a camera that renders only the UI layer or a specific set of layers for   
  certain visual effects.
* **Audio Occlusion**:  
  Layers can be used to control how audio interacts with different objects. For example, you might want certain objects   
  to block or allow the passage of audio based on their layer assignments.
* **Sorting Order**:  
  In 2D games, layers are used to define the sorting order of sprites. Sprites on higher layers are rendered in front   
  of sprites on lower layers, allowing you to control the visual hierarchy of 2D elements.
* **Organizing the Scene**:  
  Layers help organize the GameObjects in the Unity Editor's Scene view. This makes it easier to select, manipulate,   
  and manage objects within the scene.

---

### Name a few Unity packages on the assets store that you know. What is it used for?

* **TextMesh Pro**:
Purpose: It provides advanced text rendering and formatting tools, offering more control and flexibility over Unity's  
built-in Text component.
* **Cinemachine**:
Purpose: Cinemachine is a powerful and customizable camera system for Unity. It simplifies the process of creating   
dynamic and cinematic camera movements in games.
* Post Processing Stack:
Purpose: This package enhances the visual quality of your Unity project by adding post-processing effects like ambient   
occlusion, bloom, color grading, and more.
* **DOTween**:
Purpose: DOTween is a fast, efficient, and easy-to-use animation engine for Unity. It allows developers to create   
smooth and complex animations with a simple syntax.
* **Shader Graph**:
Purpose: Shader Graph is a visual tool for creating shaders in Unity without the need for programming. It enables   
artists and developers to create custom materials and effects through a node-based interface.
* **ProBuilder**:
Purpose: ProBuilder is a 3D modeling tool integrated into the Unity editor. It allows developers to create, edit, and   
prototype 3D models directly within the Unity environment.
* **Rewired**:
Purpose: Rewired is a powerful input management system for Unity. It provides a customizable and unified input solution,   
making it easier to handle various input devices and platforms.
* **Playmaker**:
Purpose: Playmaker is a visual scripting tool that allows game designers and developers to create gameplay mechanics   
and logic without writing code.
* **FinalIK**:
Purpose: FinalIK is an inverse kinematics solution for Unity, helping developers implement realistic character   
animations by simulating the movements of bones in a skeletal hierarchy.
* **EasySave**:
Purpose: EasySave is a serialization and data storage solution for Unity. It simplifies the process of saving and   
loading game data, including player preferences and game progress.

---





## Programming

### What is the order in which `OnEnable`, `Awake`, and `Start` occur during runtime?

`Awake()` –> `OnEnable()` -> `Start()`. `OnEnable()` can occur repeatedly in the same cycle!

---

### Difference between `Update`, `FixedUpdate` and `LateUpdate`?

* `Update()` is called on every Frame, regardless of how much time has passed since the last frame
Good for Movement, InputControl etc. (most of the time you'll use Update)
Usually you will use Time.DeltaTime to take pastime into account (e.g. for GameObject Translations)
* `LateUpdate()` is called after all Update() methods are processed
So e.g. for the camera that follows your character, it's good to Update after it has moved
* `FixedUpdate()` is called by the physics engine at fixed intervals (that can beset in the Options)

---

### How to prevent the existing GameObject from being destroyed when change Scene?
```cs
void Awake()
{
    DontDestroyOnLoad(transform.gameObject);
}
```
---

### Describe the role of quaternions.

**Quaternions** are used to represent rotations. The advantages of relative **Euler angles**: it can perform   
incremental rotation, avoid universal lock, and have two ways of expressing a given orientation that are mutually   
negative (Euler angles have countless ways of expression)

---

### List some ways to move an object in Unity.

There are several ways to move an object. Here are some common methods:
* Transform Translate
* Rigidbody Velocity
* Rigidbody AddForce
* Transform Position
* Lerp Position
---

### What is Lerp in Unity?

Lerp, or Linear Interpolation, is a mathematical function in Unity that returns a value between two others at a point  
on a linear scale.

```cs
lerpValue = Mathf.Lerp(minValue, maxValue, interpolationPoint);
```

The Lerp calculation returns a value from a known range, which is specified using a minimum and maximum value (a & b).  
For example, a range of 0-100.

The value that’s returned is defined by a third value, the interpolation point (t) which returns a point on the scale  
between a and b.

```cs
float a = 0;
float b = 50;
float t = 0.5f;

lerpValue = Mathf.Lerp(a, b, t);

// Returns 25
```
```cs
float a = 10;
float b = 50;
float t = 1;

lerpValue = Mathf.Lerp(a, b, t);

// Returns 50
```

---

### Explain why `Time.deltaTime` should be used.
* Unity games run on different devices with varying hardware capabilities. If you use fixed values for movement or  
animations without considering the frame rate, they might appear too fast on a high-performance device and too slow on  
a low-performance one.
* **Time.deltaTime** represents the time it took to complete the last frame. Multiplying your movement or animation  
values by **Time.deltaTime** ensures that the speed remains consistent across different frame rates.
* When you use **Time.deltaTime**, your game elements move or animate smoothly regardless of the frame rate. This is  
crucial for a consistent and enjoyable user experience.
* Unity's physics engine relies on time to simulate realistic interactions between objects. Using **Time.deltaTime** in  
physics calculations ensures that the behaviour of your game's physics remains consistent across various devices.
* For effects that depend on time, such as fading, flashing, or pulsating, using **Time.deltaTime** allows you to  
control the speed of these effects based on the time elapsed, creating a more dynamic and visually appealing experience.

---

### How to pause the game in Unity?
Setting the time scale affects the time and delta time measuring variables in the Time class.

Put simply, changing the time scale from its default of one will speed up or slow the game down – for example, you can   
run the game at half speed with a time scale of 0.5, or twice as fast with a timescale of 2). Setting it to zero,   
pauses the game entirely.

```cs
void PauseGame ()
{
    Time.timeScale = 0;
}

void ResumeGame ()
{
    Time.timeScale = 1;
}
```

---


### How do you create and use a `Coroutine`?

While the main thread is running, another piece of logic processing is started at the same time to assist the execution   
of the current program. In other words, starting a **coroutine** is to start a logic that can be parallel to the   
program. Can be used to control motion, sequences, and object behaviour.

```cs
IEnumerator MyCoroutine()
{
    yield return new WaitForSeconds(2f);
    Debug.Log("Coroutine executed");
}
StartCoroutine(MyCoroutine());
```
---

### What are ScriptableObjects?

**ScriptableObjects** are data containers that can hold non-MonoBehaviour data and are useful for storing game configurations, data settings, etc.

1. Create the ScriptableObject class:

```cs
using UnityEngine;

[CreateAssetMenu(fileName = "NewItem", menuName = "ScriptableObjects/Item")]
public class Item : ScriptableObject
{
    public string itemName;
    public int itemValue;
}
```
2. Create an instance in the editor:  
   * Right-click in the Project window.
   * Select Create > ScriptableObjects > Item.
   * Configure the itemName and itemValue in the Inspector.

3. Use the ScriptableObject in a script:
```cs
using UnityEngine;

public class ItemUser : MonoBehaviour
{
    public Item item;

    void Start()
    {
        Debug.Log($"Item Name: {item.itemName}, Value: {item.itemValue}");
    }
}
```
---

### What is the difference between `GetComponent<T>()` and `FindObjectOfType<T>()`?

* `GetComponent<T>()` fetches a component attached to the same GameObject.
* `FindObjectOfType<T>()` searches the scene for the first active instance of the specified type.

---

### What are the purposes and uses of [SerializeField] and [HideInInspector] attributes in Unity?

* The [SerializeField] attribute forces a private field to be serialized and visible in the Unity Inspector.
```cs
using UnityEngine;

public class Example : MonoBehaviour
{
    [SerializeField]
    private int myPrivateValue; // Visible in Inspector but remains private in code
}
```
* The [HideInInspector] attribute hides a public field from appearing in the Unity Inspector.
```cs
using UnityEngine;

public class Example : MonoBehaviour
{
    [HideInInspector]
    public int myHiddenValue; // Hidden in Inspector but remains public in code
}
```
---

### What is the purpose and functionality of Raycast in Unity?

In Unity, Raycast is a method used to detect objects along a ray's path, often for collision detection, line-of-sight   
checks, or input handling.

```cs
using UnityEngine;

public class RaycastExample : MonoBehaviour
{
    void Update()
    {
        // Shoot a ray from the camera's position forward
        Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
        RaycastHit hit;

        if (Physics.Raycast(ray, out hit, 100f))
        {
            Debug.Log("Hit: " + hit.collider.name); // Log the object hit by the ray
        }
    }
}
```

---

###  Why is using object pooling important? How does it work in Unity?

Reusing GameObjects after being destroyed such as artillery shells, fx, etc. costs memory each time they are destroyed  
and created. Using Pooling is understood as just hiding the GameObject, then resetting its position, rotation angle,  
etc. and displaying it again when used. This helps increase game performance significantly.

---

### How to save local data?

* PlayerPrefs.
* Serialization to Json.
* Binary Serialization.

---

### How to quit the game in Unity?

```cs
Application.Quit();
```
---

### How to lock & hide the cursor in Unity?

* Lock the cursor: `Cursor.lockState = CursorLockMode.Locked;`
* Hide the cursor: `Cursor.visible = false;`

---


### How to use random values in Unity?
In Unity, you can use the Random class to generate random values.
```cs
float randomValue = Random.Range(0f, 1f); // Random float between 0 and 1
int randomInt = Random.Range(0, 10); // Random integer between 0 and 9
Vector3 randomPoint = Random.insideUnitSphere; // Random point within a sphere of radius 1

string[] colors = { "Red", "Blue", "Green" };
string randomColor = colors[Random.Range(0, colors.Length)];

bool randomBool = Random.value > 0.5f; // 50% chance for true or false
Quaternion randomRotation = Random.rotation;

```
---





## Graphics

### What is LOD and what are its advantages and disadvantages?

* LOD (Level of detail) is the most commonly used game optimization technology. It determines the resource allocation   
  of object rendering according to the position and importance of the model, reducing the number of faces and details   
  of non-important objects, thereby achieving highly efficient rendering operations.
* Disadvantage of LOD is development time and complexity for multiple variation of same model, build size and artifacts.

---

### What is the use of Occlusion Culling?

* Occlusion culling is a process that prevents Unity from performing rendering calculations for GameObjects that are   
  completely hidden from view (occluded) by other GameObjects.
* Every frame, Cameras perform culling operations that examine the Renderers in the Scene and exclude (cull) those that 
  do not need to be drawn. By default, Cameras perform frustum culling, which excludes all Renderers that do not fall within the Camera's view frustum.

---

###  Describe how the stencil buffer works and uses in unity?

* The stencil buffer is a component of the graphics pipeline that is used in computer graphics to achieve various   
  effects like outlining objects, creating reflections, shadows, and more. In Unity, the stencil buffer can be   
  manipulated through shaders to implement custom rendering techniques.
* In game, the stencil buffer is used for creating cutting holes, impossible geometry, magic card, ...

---

### What is the difference between material and shared material in MeshRender?

Modifying sharedMaterial will change the appearance of all objects using this material and will also change the  
material settings stored in the project. Modifying the material returned by sharedMaterial is not recommended. If you  
want to modify the renderer's material, use material instead.

---

### Unity provides several light sources. What are they?

* **Directional Light**:  
  * Simulates distant light sources such as the sun.
  * Illuminates all objects in the scene with parallel light rays.
* **Point Light**:  
  * Emits light in all directions from a specific point in space.
  * Commonly used to simulate light bulbs or other localized light sources.
* **Spotlight**:
  * Emits light in a cone shape from a specific point in space.
  * Can be used to simulate flashlights or focused light sources.
* **Area Light**:
  * Represents a rectangular light source.
  * Useful for simulating large light sources, such as a window or a screen.
* **Light Probe**:
  * Used for dynamic global illumination.
  * Captures and stores lighting information at specific points in the scene.
* **Reflection Probe**:
  * Captures a 360-degree view of the scene's surroundings.
  * Used for calculating reflections and lighting for reflective surfaces.
* **Real-time Global Illumination (GI)**:
  * Unity also provides a real-time global illumination system that allows dynamic lighting changes to affect the scene's lighting in real-time.
---

## References
 - https://gamedevbeginner.com/unity/
 - https://github.com/GuardianOfGods/unity-interview-questions
 - https://github.com/Unity-Technologies/game-programming-patterns-demo/
 - https://docs.unity3d.com/6000.0/Documentation/Manual/execution-order.html
  