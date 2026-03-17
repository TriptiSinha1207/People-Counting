This project presents an automated people counting system that
detects and tracks individuals entering and exiting a store using
computer vision techniques. By leveraging the YOLOv8 deep learning
model for object detection and a custom tracking algorithm, the
system identifies human movement in real-time from a surveillance
video feed. Two polygonal regions are defined to represent the entry
and exit zones, enabling directional counting based on spatial
transitions. The solution offers accurate, real-time occupancy
monitoring and supports applications in crowd management,
business analytics, and regulatory compliance. It helps store
managers analyze customer flow, enhance safety protocols, and
make data-driven operational decisions. The system is implemented
using Python, OpenCV, and Ultralytics’ YOLO framework, and
provides visual feedback, count overlays, and a scalable foundation
for smart surveillance and retail automation.


System Structure
The people counting system is built around a modular architecture
that combines deep learning-based detection, object tracking, and
region-based logic for accurate entry and exit monitoring. The
system is composed of the following key components:

1. Input Module

• Function: Captures real-time video from a camera or loads pre-
recorded footage.

• Tools Used: cv2.VideoCapture() from OpenCV.
• Input: Surveillance video (e.g., peoplecount1.mp4).

2. Object Detection Module
• Function: Detects all persons in the video frame using the
YOLOv8 deep learning model.
• Model: YOLOv8s.pt (Ultralytics).
• Output: Bounding boxes for each detected person.

3. Object Tracking Module
• Function: Assigns unique IDs to each detected person and
tracks them across frames.
• Tracker Used: Custom tracker (likely based on IoU or a variant
of SORT).
• Purpose: Maintains consistent identity for each person to avoid
duplicate counting.

4. Zone Definition & Spatial Logic
• Function: Defines polygonal zones (entry and exit) in the frame
using coordinates.
• Zones:
o area2: Outside/Entry zone.
o area1: Inside/Exit zone.
• Library Used: cv2.pointPolygonTest() to check if a person
enters/leaves a zone.

5. Entry/Exit Logic Module
• Function: Tracks direction of movement:
o Entry: From area2 to area1.
o Exit: From area1 to area2.
• Data Structure Used: Sets (entering, exiting) to store unique
IDs.

6. Visualization & Display
• Function: Displays live video feed with:
o Bounding boxes and ID tags.
o Entry/exit counters.
o Marked zones and movement paths.
• Library Used: OpenCV drawing functions (cv2.rectangle,
cv2.putText, etc.)

7. Output Module
• Function: Displays live entry/exit counts on screen.
• Optional Enhancements: Can be extended to save counts to
CSV, send alerts, or feed a dashboard.

System Workflow Diagram (Text-Based)
[Video Input]
↓
[YOLOv8 Detection]
↓
[Tracker → Assign IDs]
↓
[Check Positions in Zones]
↓
[Direction Logic]
↓
[Update Entry/Exit Counts]
↓
[Display Output Frame + Counts]

OUTPUT ANALYSIS
Here's an output analysis of your people counting project that
detects and counts individuals entering and exiting a store using a
YOLOv8 model and a tracking algorithm:

OUTPUT ANALYSIS
Project Overview
The script performs real-time people detection and direction-based
tracking in a surveillance video to determine how many individuals
enter or exit a defined store area.

Objectives Achieved
• People Detection: Accurately detects humans using YOLOv8
and filters out non-human objects.
• Entry & Exit Region Mapping: Defines two polygonal regions
(area1 and area2) representing entrance and exit zones.
• Tracking with Unique IDs: Maintains consistent identities for
detected individuals using a custom tracker.
• Direction-Based Counting: Counts people entering or exiting by
observing transitions between defined areas.
• Visual Feedback: Displays bounding boxes and ID labels on
detected individuals with live counter updates.
