# face_estimation_detection-
Real-time face distance estimation using computer vision and facial landmark detection.
# Monocular Face Distance Estimation

A real-time computer vision system that estimates the **distance of a human face from a single monocular 2D camera** and calculates the **horizontal deviation angle of the face relative to the camera center**.

This project uses the **pinhole camera model** and the approximately known real-world width of a human face to estimate depth from a single image. The system detects the face, measures its pixel width and center position, and uses these parameters to calculate the approximate distance and viewing angle.

## 🎯 Objective

The goal of this project is to develop a lightweight and real-time monocular vision system capable of estimating:

* **Face depth (Z)** — approximate distance between the face and camera
* **Horizontal deviation angle (θ)** — angle between the camera's optical axis and the face center

The system is designed to work using only a **single 2D camera**, without requiring stereo cameras, LiDAR, or depth sensors.

## 🚀 Key Features

* Real-time face detection
* Monocular depth estimation
* Horizontal deviation angle estimation
* Uses a single 2D camera
* Pinhole camera model-based calculation
* Approximate real-world face width calibration
* Lightweight and suitable for real-time applications
* Designed for stable performance under varied environments

## 🧠 Working Principle

The system follows these main steps:

1. Capture a frame from the monocular camera.
2. Detect the face in the image.
3. Identify the face center pixel `(x, y)`.
4. Measure the detected face width in pixels `(w_px)`.
5. Use the known average real-world face width `W`.
6. Estimate the focal length `f` through camera calibration.
7. Calculate the approximate face depth `Z`.
8. Calculate the horizontal deviation angle `θ` based on the face center's displacement from the camera center.
9. Display the estimated distance and angle in real time.

## 📐 Mathematical Model

### Face Distance Estimation

Using the pinhole camera model:

**Z = (f × W) / w_px**

Where:

* `Z` = Estimated distance from camera
* `f` = Camera focal length in pixels
* `W` = Approximate real-world face width in meters
* `w_px` = Detected face width in pixels

The assumed average real-world face width is approximately:

**W ≈ 0.14–0.16 meters**

### Horizontal Deviation Angle

The horizontal deviation angle is estimated using:

**θ = arctan((x - c_x) / f)**

Where:

* `θ` = Horizontal deviation angle
* `x` = Face center x-coordinate in pixels
* `c_x` = Camera image center x-coordinate
* `f` = Focal length in pixels

## 📊 Input Parameters

| Parameter    | Description                   | Unit   |
| ------------ | ----------------------------- | ------ |
| `(x, y)`     | Face center pixel coordinates | Pixels |
| `w_px`       | Detected face width           | Pixels |
| `f`          | Camera focal length           | Pixels |
| `(c_x, c_y)` | Image center                  | Pixels |
| `W`          | Average real-world face width | Meters |

## 📤 Expected Output

The system produces:

```text
(depth, θ) = (Z, θ)
```

Example:

```text
Face Detected
Estimated Distance: 2.35 m
Horizontal Deviation: 8.42°
```

The estimated distance is intended to provide **approximate real-world accuracy**, with an acceptable error range of approximately **±50–150 cm**, depending on camera quality, face detection accuracy, calibration, and environmental conditions.

## 🏗️ System Architecture

```text
Monocular 2D Camera
        │
        ▼
   Video Frame
        │
        ▼
   Face Detection
        │
        ├───────────────┐
        ▼               ▼
Face Center (x,y)   Face Width (w_px)
        │               │
        └───────┬───────┘
                ▼
      Pinhole Camera Model
                │
                ▼
       Distance Estimation (Z)
                │
                ▼
      Horizontal Angle (θ)
                │
                ▼
       Real-Time Output
```

## 🛠️ Technologies Used

* Python
* OpenCV
* Computer Vision
* Face Detection
* Pinhole Camera Model
* Monocular Depth Estimation
* Real-Time Video Processing

## 🎯 Applications

This technology can be applied to:

* Human-computer interaction
* Smart camera systems
* Robotics
* Autonomous systems
* Surveillance and monitoring
* Gesture and interaction systems
* Proximity-aware applications
* Computer vision research

## ⚡ Performance Considerations

The system is designed to achieve a balance between:

* Face detection accuracy
* Distance estimation accuracy
* Angle estimation accuracy
* Real-time FPS
* Computational efficiency

Performance can be improved through optimized face detection models, image resizing, hardware acceleration, and efficient video processing.

## ⚠️ Limitations

Distance estimation accuracy may be affected by:

* Variations in actual face size
* Incorrect camera calibration
* Face detection errors
* Camera lens distortion
* Extreme viewing angles
* Poor lighting conditions
* Partial face occlusion

Since the system uses a single 2D camera, the estimated depth is **approximate rather than directly measured**.

## 🔮 Future Enhancements

* Improve camera calibration
* Add automatic focal length estimation
* Support multiple faces simultaneously
* Improve accuracy using facial landmarks
* Add temporal smoothing for stable predictions
* Optimize for edge devices
* Add 3D visualization of face position
* Integrate with robotic or autonomous systems

## 👩‍💻 Project

Developed as part of **HackTronix 2.0 – Final Round**.

**Problem Statement:** Monocular Face Distance Estimation

**End Goal:** Estimate face depth and horizontal deviation angle from a single monocular 2D camera image with real-time performance and acceptable approximate real-world accuracy.
