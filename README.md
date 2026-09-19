# Global Seismic Event Explorer (USGS Public Dataset)

A web interface that parses and visualizes real-time global seismic data from the United States Geological Survey (USGS) Earthquake Hazards API.

## What This Interface Answers (Beyond Raw JSON)

The raw USGS endpoint provides an unranked array of nested GeoJSON points. This application establishes:
1. **Dynamic Regional Risk Filtering**: Instantly isolates events above critical perception thresholds (e.g., Magnitude 2.5+ or 4.5+).
2. **Aggregated Depth and Peak Intensity**: Automatically computes peak registered magnitude and mean hypocenter depth for the filtered selection.
3. **Location Search**: Fast textual filtering of impacted regions.

## Handling Slow or Failing Remote Sources

- **Timeout AbortController**: Network calls enforce a 7-second cutoff so slow or unresponsive connections don't cause infinite hangs.
- **Visual Failure State**: Clear error messaging (`role="alert"`) specifying whether the problem was a timeout or server refusal, with an in-place **Retry Request** button.
- **Reviewer Simulation**: A one-click **"Simulate Timeout / Fail"** button lets reviewers test error and retry states immediately without code modification.

## What the Data Does and Does Not Support

- **What it supports**: It accurately reflects recent vibrational events detected and verified by USGS seismic stations within the last 24 hours.
- **What it does NOT support**: 
  - It **cannot predict** future seismic events or aftershocks.
  - It does **not establish structural damage** or casualty metrics (which depend on building standards and population density, not magnitude alone).
  - It does **not guarantee exhaustive detection** in remote areas with low seismograph sensor density.

## Running Locally

1. Clone or download this repository:
   ```bash
   git clone [https://github.com/](https://github.com/)<your-username>/earthquake-dataset-viewer.git