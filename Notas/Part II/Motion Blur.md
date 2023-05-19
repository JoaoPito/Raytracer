It can be achieved by **sending multiple rays at random times** and then averaging them. With that, moving objects will sometimes be intersecting the rays and sometimes they won't.
Generally, the rays only exist for a specific point in time, independently of the moving objects/camera.

If Depth of Field is ray sampling in the camera lens area, Motion Blur is ray sampling according to time.

## Implementation
- Here, the rays are emitted between to specific points in time, **the camera keeps track of the time**, but it could also be handled by the user too

## Changes
- The camera now has to keep track of the shutter times. It attaches a random time, between shutter open/close, that that ray was emitted.
- The rays are attached to a specific point in time.
- Objects need to move. Created a new type of object: **Moving Spheres**
- The materials' scattered rays had to be updated to include time