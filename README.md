# Dynamic Sliders Stack for ComfyUI

<div align="center">
  <img src="dynamic_slider_stacker_reciever_nodes.png" alt="Slider Stacker and Slider Receiver" />
</div>

[![Version](https://img.shields.io/badge/version-v2.0.0-blue)](https://github.com/FunnyFinger/Dynamic_Sliders_stack/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Issues](https://img.shields.io/github/issues/FunnyFinger/Dynamic_Sliders_stack)](https://github.com/FunnyFinger/Dynamic_Sliders_stack/issues)
[![Pull Requests](https://img.shields.io/github/issues-pr/FunnyFinger/Dynamic_Sliders_stack)](https://github.com/FunnyFinger/Dynamic_Sliders_stack/pulls)
[![Stars](https://img.shields.io/github/stars/FunnyFinger/Dynamic_Sliders_stack?style=social)](https://github.com/FunnyFinger/Dynamic_Sliders_stack/stargazers)

---

A custom node pack for **ComfyUI** providing a stack of named sliders with dynamic behavior.

---

## 🎥 Demo

### Contextual Features
- **Average Contextual Adjustment**  
  Dynamically adjusts all sliders to their average value using the context menu option. This feature is helpful for balancing all sliders evenly without manual adjustments.  
  <div align="center">
    <img src="https://github.com/FunnyFinger/Dynamic_Sliders_stack/blob/main/gif/context_avg.gif" alt="Average Context" width="50%" />
  </div>

- **Maximum Contextual Adjustment**  
  Sets all sliders to the maximum slider value using the context menu option. This ensures that all sliders are at their highest weight for uniform maximum intensity.  
  <div align="center">
    <img src="https://github.com/FunnyFinger/Dynamic_Sliders_stack/blob/main/gif/context_max.gif" alt="Maximum Context" width="50%" />
  </div>

- **Minimum Contextual Adjustment**  
  Adjusts all sliders to the minimum slider value using the context menu option. This is useful for resetting sliders to their lowest intensity.  
  <div align="center">
    <img src="https://github.com/FunnyFinger/Dynamic_Sliders_stack/blob/main/gif/context_min.gif" alt="Minimum Context" width="50%" />
  </div>

- **Context Reset**  
  Resets all sliders to their default values (e.g., 1.0). This feature helps quickly return to baseline settings for all sliders.  
  <div align="center">
    <img src="https://github.com/FunnyFinger/Dynamic_Sliders_stack/blob/main/gif/context_reset.gif" alt="Context Reset" width="50%" />
  </div>

### Sum Lock Toggle and Sliders Sum Widget
- **Sliders with Lock Sum On**  
  Demonstrates how the sum lock feature maintains a constant total sum of sliders while allowing individual adjustments. It ensures that the overall weight does not exceed or drop below a set total.  
  <div align="center">
    <img src="https://github.com/FunnyFinger/Dynamic_Sliders_stack/blob/main/gif/sliders_locksum_on.gif" alt="Sliders Lock Sum On" width="50%" />
  </div>

- **Sliders Max with Lock Sum Off**  
  Allows sliders to be adjusted proportionally to their maximum value without maintaining the sum lock. This is ideal for scenarios where the total weight does not need to be constrained, but you wish to control the highest value while maintaining proportionality between sliders. This has an overall scaling effect that scales the sliders with respect to the minimum (zero).  
  <div align="center">
    <img src="https://github.com/FunnyFinger/Dynamic_Sliders_stack/blob/main/gif/sliders_max_locksum_off.gif" alt="Sliders Max Lock Sum Off" width="50%" />
  </div>

- **Sliders Max with Lock Sum On**  
  Demonstrates how the sum lock can be maintained while adjusting the highest value slider. This ensures all sliders are proportionally scaled with respect to their average without exceeding the allowed total sum.  
  <div align="center">
    <img src="https://github.com/FunnyFinger/Dynamic_Sliders_stack/blob/main/gif/sliders_max_locksum_on.gif" alt="Sliders Max Lock Sum On" width="50%" />
  </div>

- **Sliders Sum with Lock Sum Off**  
  Highlights how sliders can be adjusted freely without sum constraints while dynamically displaying the total sum. This is useful for adjusting the sliders as a whole without changing their offsets.  
  <div align="center">
    <img src="https://github.com/FunnyFinger/Dynamic_Sliders_stack/blob/main/gif/sliders_sum_locksum_off.gif" alt="Sliders Sum Lock Sum Off" width="50%" />
  </div>

---

## 📌 Nodes Overview

### Slider Stacker

- **Inputs**:
  - `slider_max_strength` (FLOAT): The master maximum value. Adjusting this scales all sliders below it.
  - `slider_count` (INT): Controls how many slider rows are visible and processed (1–50).
  - `slider_name_{i}` (STRING): A text field to name or describe the slider (optional).
  - `({i})` (FLOAT Widget): The individual weight for this slider (0.0–2.0). Adjusting this updates the `slider_max_strength` if this slider becomes the new maximum.
  - **Sum Lock Toggle**: A toggle to lock the total sum of all slider values. When enabled, adjusting one slider redistributes the difference proportionally across the other sliders.
  - **Sliders Sum Widget**: Displays the total sum of all slider values in real-time.

- **Output**:
  - `SLIDER_WEIGHTS` (STRING): A comma-separated string of the weight values for sliders 1 through `slider_count`, formatted to two decimal places (e.g., "1.00, 0.50, 0.75").

- **Right-Click Options**:
  - `Average Slider Values`: Sets all visible sliders to their average value.
  - `Reset Slider Values`: Resets all visible sliders to the default value (1.0).
  - `Set All to Max Value`: Finds the highest value among visible sliders and sets all visible sliders to that value.
  - `Set All to Min Value`: Finds the lowest value among visible sliders and sets all visible sliders to that value.

---

### Slider Receiver

- **Inputs**:
  - `weights_string` (STRING): Connect the `SLIDER_WEIGHTS` output from the `Slider Stacker` here.
  - `index` (INT): The 1-based index of the slider whose weight you want to extract (1–50).

- **Output**:
  - `WEIGHT` (FLOAT): The floating-point value of the slider at the specified index (returns 0.0 if the index is out of bounds or input is invalid).

---

## 🛠️ Installation

1. Ensure the folder containing these files is named `Dynamic_sliders_stack`.
2. Place the `Dynamic_sliders_stack` folder inside your ComfyUI `custom_nodes` directory.
3. Restart ComfyUI.

---

## 🎯 Contributing

We welcome contributions! If you have suggestions for improvements or new features, please [open an issue](https://github.com/FunnyFinger/Dynamic_Sliders_stack/issues) or [submit a pull request](https://github.com/FunnyFinger/Dynamic_Sliders_stack/pulls).

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---

Made with ❤️ by [FunnyFinger](https://github.com/FunnyFinger)
