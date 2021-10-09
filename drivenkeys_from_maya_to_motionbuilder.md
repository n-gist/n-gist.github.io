---
title: "Driven Keys from Maya to MotionBuilder"
---

# Driven Keys from Maya to MotionBuilder

[![Driven Keys from Maya to MotionBuilder](/images/DrivenKeys_MAYA.gif)](/images/DrivenKeys_MAYA.gif){:target="_blank" rel="noopener"}

Driven Keys is a nice thing that does not work when we transfer scene from MAYA to MotionBuilder. There are solutions on the Internet, but most of them just explain how to build Relation Constraint in MotionBuilder between driver and driven objects manually. That is impossible with a large number of objects, or when changing/tuning connections, in terms of time costs.

Solution is two python scripts. One is for export data from MAYA, second is for import to MotionBuilder.

## Export

[![Driven Keys - Export](/images/DrivenKeys_Export.gif)](/images/DrivenKeys_Export.gif){:target="_blank" rel="noopener"}

On pressing 'Construct' button, Driven Keys data is collected, serialized and saved in ExtraAttributes fields of the created objects acting as data containers. After this, the scene can be sent to MotionBuilder. Data is collected for selected driven objects or for entire scene, if nothing selected. MAYA can stuck hard if you select these objects while AttributeEditor is opened, especially if ExtraAttributes category exposed, thats why data splits to smaller chunks, but it is recommended to keep AttributeEditor closed. 'Delete' button deletes these objects, and other four is just shortcuts for SDK window, selecting all objects in scene and sending them to MotionBuilder.

* *If not all channels was constructed, there is option to run construction with 'Work Log' checkbox ticked. This will output information that can be used to fix channels inputs. 'BAD' channels can be found by searching for the 'SKIP CONSTRUCT' string in the Script Editor console log. Information before this lines will tell what exactly is 'BAD' in the chain of inputs of the channel. Most often these are nodes without inputs, which sometimes remain when editing Driven Keys. Such nodes can be removed from connections network using Node Editor.*

## Import

[![Driven Keys - Import](/images/DrivenKeys_Import.gif)](/images/DrivenKeys_Import.gif){:target="_blank" rel="noopener"}

Once all objects are transferred to MotionBuilder, connections network can be constructed using 'Update' button, which will create Relation Constraints for each driven object attribute. It is possible to activate, deactivate and delete these constraints with the corresponding buttons.

### Supports:
* *blended influences from multiple driver objects*
* *pre' and post' extrapolations: Constant, Linear (Keep Slope), Cycle (Repetition), Cycle with offset (Relative Repetition), Oscillate (Mirror Repetition)*
* *key tangents: Auto, Spline, Linear, Step, StepNext*

### Does not supports:
* *driving any other things except translation, rotation and scale*
* *Custom tangents. They will be treated as Auto*
* *mixing various key tangents types in one curve. There is inconsistencies between MAYA and MotionBuilder when keys of different tangent types are neighbors (Auto and Linear tangents on one curve comparison):*
[![Driven Keys - Tangents](/images/DrivenKeys_DifferentTangents.png)](/images/DrivenKeys_DifferentTangents.png){:target="_blank" rel="noopener"}
* *so it's best to use the same tangent types on one curve*

Worth to note. There is no way to drive attribute on one axis, leaving it free on other axes. In order to be able to control attributes on other axes, they need to be constrained too, otherwise attributes on not constrained axes will be frozen at current values.

[DrivenKeys_MAYAtoMOBU.zip](/files/DrivenKeys_MAYAtoMOBU.zip){:target="_blank" rel="noopener"}