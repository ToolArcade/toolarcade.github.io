# ToolArcade Turntable
## What is it?
<video controls width="600">
  <source src="https://github.com/user-attachments/assets/cd926339-0ddb-4d62-b608-c297c6469518" type="video/mp4">
  Your browser does not support the video tag.
</video>

The Turntable component rotates actors in the Editor viewport, as if on a turntable, even while you work with it.

This can be useful for visualizing how an object looks from all angles without moving the viewport camera, e.g. when setting up asset galleries or zoos, or content that's hostile to depth perception such as wireframes, PCG debug geometry, or special render buffers.

The turntable is an editor-only tool, and has no effect in Play-in-Editor or in shipping games.

## How do I use it?
Add the Turntable component to an actor.  The turntable will start automatically and can be paused, resumed, and stopped using buttons in the Details view.

<video controls width="600">
  <source src="https://github.com/user-attachments/assets/81bb2459-4f66-4a13-8ac3-622e6c41fc74" type="video/mp4">
  Your browser does not support the video tag.
</video>

You can configure the rotation using the component's options:
* **Period**: using the default revolution curve, this is the duration of a single revolution, or the time over which the revolution curve is evaluated.  If negative, the turntable will rotate in the opposite direction.
* **Revolution Curve**: controls the revolution's extremes and speed.
  * The time axis is the duration through the configured period: 0.0 = start of period, 1.0 = end of period.
  * The value axis is the amount and direction of rotation at a moment in time.  For example,
    * Value 0.0 = original rotation (0 degrees)
    * Value 1.0 = one revolution (360 degrees)
    * Value -0.5 = one half revolution in reverse (-180 degrees)
  * Adjust the curve's shape to achieve different turntable behaviors, or use the provided presets.

## Configuration tips
| To achieve this effect...                          | ...use this curve                                                                                       |
|----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Single constant-speed revolution                   | Linear ramp from 0.0 to 1.0                                                                             |
| Single constant-speed anti-revolution              | Linear ramp from 0.0 to -1.0, _or_ use a negative period.                                               |
| Slow turn around the front, faster around the back | Ease-in/out curve                                                                                       |
| Wibble-wobble                                      | Wave curve from 1.0 to -1.0 and back to 1.0                                                             |
| Revolution with a pause at the end                 | Linear ramp from 0.0 to 1.0 for the first 3/4 of the curve, remain at 1.0 for the last 1/4 of the curve |
