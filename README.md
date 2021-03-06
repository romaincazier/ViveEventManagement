# ViveEventManager v0.1
A small utility class to easily add listeners to hmd/controllers events


## How to use it ?
+ Download and place the `ViveEventManager.cs` file in your "Assets" folder
+ Create a new script in the GameObject you want to react on an event and add a listener function:

   * `void FunctionName(ControllerEventObject evt)` for a controller event or
   
   * `void FunctionName(HMDEventObject evt)` for a HMD event

+ In the same GameObject, execute on `Awake()` (or `Start()`) the following code:

   * `ViveEventManager.Instance.[Event] += [Listener];`
   
+ You can use a "debug" mode that will print you the events as they occur and display the raycast from both controllers:

   * create an empty GameObject, add the script and select the "Debug Mode" or
   
   * at runtime, select "Debug Mode" on the "Event Manager" GameObject


## Supported events
#### Trigger
+ `OnTriggerPressStart`
+ `OnTriggerPress`
+ `OnTriggerPressEnd`
+ `OnTriggerClick`

#### Grip
+ `OnGripPressStart`
+ `OnGripPress`
+ `OnGripPressEnd`
+ `OnGripClick`, triggered if the delta time between `OnGripPressStart` and `OnGripPressEnd` is less than 300 milliseconds

#### Touchpad
+ `OnTouchStart`
+ `OnTouchMove`
+ `OnTouchEnd`
+ `OnTouchTap`, triggered if the delta time between `OnTouchStart` and `OnTouchEnd` is less than 300 milliseconds
+ `OnSwipe`
+ `OnTouchpadPressStart`
+ `OnTouchpadPress`
+ `OnTouchpadPressEnd`
+ `OnTouchpadClick`, triggered if the delta time between `OnTouchStart` and `OnTouchEnd` is less than 300 milliseconds

#### HMD
+ [to be added]


## Event object
#### Controller
+ `.side` returns "left" or "right"
+ `.position` returns the position of the controller
+ `.rotation` returns the rotation of the controller
+ `.pressure` returns the pressure on the trigger (from 0.0f to 1.0f)
+ `.isTriggerClicked` returns `true` if the trigger has been clicked while it's still pressed
+ `.touchPoint` returns the finger's position on the touchpad, from -1.0f to 1.0f on both x- (left to right) and y-axis (bottom to top). Returns a Vector2.zero by default
+ `.swipeDirection` returns "+X" (left-to-right), "-X" (right-to-left), "+Y" (top-to-bottom), "-Y" (bottom-to-top). Returns "none" by default
+ `.controller` returns the controller object

#### HMD
+ [to be added]


## To-do
+ add `OnPointerEnter`, `OnPointerOver`, `OnPointerLeave` events on the controllers using a raycast
+ add `OnLookEnter`, `OnLookOver`, `OnLookLeave` events on the HMD
+ add a Unity scene with an example
+ switch to `UnityEvent` ? To allow to add custom events in a centralized object ?
