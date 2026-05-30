# Football Tracking Analysis: Possession and Spatial Control

This project is an early prototype for analyzing receiver space using football tracking data. The main goal is to estimate, for a given frame, which areas of the pitch are more favorable for the team in possession to receive the ball, which areas are more strongly controlled by the defending team, and where the space is contested. The current version has **not yet been formally validated**, but based on visual inspection and football understanding, the output appears directionally reasonable in many situations. So far, the prototype has been developed and tested on **one match only**, which means the results should be treated as exploratory rather than generalizable.

The current notebook builds a blended control map by combining:
- ball-carrier identification
- frame-level possession classification
- receiver and defender influence fields
- movement-based player orientation
- pressure context around the ball carrier

The output is an interactive pitch visualization showing:
- receiving-team influence
- defending-team influence
- contested or 50/50 zones
- ball location
- player positions
- optional orientation arrows
- pressure and possession information

## Project Status

This is an **initial design / research prototype**, not a finished model.

The current version is:
- rule-based
- exploratory
- intended for qualitative inspection and iterative improvement

It should be interpreted as an approximate influence map rather than a validated probability model.

## Main Idea

Instead of listing only fixed pass options to specific teammates, this project tries to estimate the broader spatial picture around the ball:

- which areas are easier for the attacking team to receive into
- which areas are more controlled by defenders
- which areas are contested
- how body orientation and local pressure may shift those zones

The current model uses directional influence fields so that player control is not equally distributed in all directions.

## Current Features

- Load and parse SkillCorner-style tracking data
- Convert frames into tidy player position tables
- Identify likely ball possession states:
  - clear possession
  - contested
  - no possession
- Estimate player movement-based orientation from surrounding frames
- Build directional receiver and defender influence maps
- Visualize blended control regions on a 2D pitch
- Show:
  - ball carrier
  - player IDs
  - pressure information
  - 50/50 balance line
  - optional orientation arrows
- Interactively inspect frames using widgets

## Example Visualizations

Below are example outputs from the current prototype across different frames and pressure situations.  
Blue regions indicate areas that are more favorable for the team in possession to receive the ball, red regions indicate stronger defensive control, and the dashed boundary represents an approximate 50/50 balance line between attacking and defending influence.

<p align="center">
  <img src="images/receiver_space1.png" width="48%" />
  <img src="images/receiver_space2.png" width="48%" />
</p>
<p align="center">
  <img src="images/receiver_space3.png" width="48%" />
  <img src="images/receiver_space4.png" width="48%" />
</p>
<p align="center">
  <img src="images/receiver_space5.png" width="60%" />
</p>

## Repository Structure

```text
.
├── receiver-space-analysis.ipynb
├── README.md
└── images/
    ├── receiver_space1.png
    ├── receiver_space2.png
    ├── receiver_space3.png
    ├── receiver_space4.png
    └── receiver_space5.png