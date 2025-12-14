# Standard Operating Procedure (SOP)
## Robot Control System - LOREAL Project

**Document Version:** 1.0  
**Date:** December 2025  
**Purpose:** This document provides step-by-step instructions for operating the Robot Control System for recording and replaying robot movements.

---

## Table of Contents

1. [System Overview](#system-overview)
2. [Initial Setup and Connection](#initial-setup-and-connection)
3. [Recording Robot Movements](#recording-robot-movements)
4. [Replaying Recordings](#replaying-recordings)
5. [File Management](#file-management)
6. [Safety Procedures](#safety-procedures)
7. [Troubleshooting](#troubleshooting)

---

## 1. System Overview

The Robot Control System is a software application designed to:
- **Record** robot movements and actions
- **Replay** recorded movements with various modes and speed controls
- **Manage** recording files (browse, load, rename, delete)

**Main Interface Sections:**
- **New Record**: For creating new recordings
- **Replay**: For managing and playing back recordings
- **Emergency Stop**: Safety button for immediate shutdown

---

## 2. Initial Setup and Connection

### 2.1 Port Check and Connection Setup

**Step 1: Check Available Ports**
1. Open a terminal window
2. Navigate to the project directory: `cd ~/lerobot`
3. Run the port detection command:
   ```bash
   lerobot-find-port
   ```
4. The system will display all available ports

**Step 2: Identify MotorsBus Port**
1. Note all ports listed under "Ports before disconnecting"
2. **Disconnect the USB cable** from the MotorsBus device
3. Press **Enter** in the terminal
4. The system will identify which port was removed (this is your MotorsBus port)
5. **Reconnect the USB cable** to the MotorsBus

**Step 3: Verify Connection**
1. Launch the Robot Control application
2. Check the connection status at the top of the interface
3. **Green "Connected"** text indicates successful connection
4. If not connected, verify USB cable and port settings

---

## 3. Recording Robot Movements

### 3.1 Starting a New Recording

**Step 1: Prepare the System**
1. Ensure the robot is in the desired starting position
2. Verify connection status shows "Connected" (green text)
3. Check that no other recording or replay is in progress

**Step 2: Initiate Recording**
1. Locate the **"New Record"** section in the interface
2. Click the red **"New Record"** button
3. The interface will show:
   - **"Starting in X..."** countdown (yellow text)
   - Button changes to **"Stop Recording"** (red button)

**Step 3: Perform Robot Movements**
1. During the countdown, prepare to move the robot
2. After countdown completes, the system is recording
3. Move the robot through the desired sequence
4. All movements are being captured automatically

**Step 4: Stop Recording**
1. Click the red **"Stop Recording"** button
2. The recording is automatically saved
3. The system will generate a filename (e.g., `LOREAL_RECORD_XX.pk1`)
4. The interface returns to the normal state

**Important Notes:**
- Recordings are saved automatically
- Default save location: `/home/orin_nano/lerobot/backend/projects/LOREAL/`
- Files are named sequentially (LOREAL_RECORD_01.pk1, LOREAL_RECORD_02.pk1, etc.)

---

## 4. Replaying Recordings

### 4.1 Selecting and Loading a Recording

**Step 1: Access Recorded Files**
1. Locate the **"Replay"** section in the interface
2. Find the **"Select Recorded File"** dropdown menu
3. Click the dropdown to see available recordings

**Step 2: Load a Recording**
- **Option A: Use Dropdown**
  1. Select a file from the dropdown (e.g., `LOREAL_RECORD_02.pk1`)
  2. Click **"Load Recording"** button
  3. Verify "Loaded File: [filename]" appears in green text

- **Option B: Browse Files**
  1. Click the **"Browse"** button
  2. A file browser window will open
  3. Navigate to: `/home/orin_nano/lerobot/backend/projects/LOREAL/`
  4. Select the desired `.pk1` file
  5. Click **"Open"**
  6. The file is automatically loaded

**Step 3: Refresh File List (if needed)**
- If new recordings don't appear, click **"Refresh List"** button
- This updates the dropdown with the latest files

### 4.2 Configuring Replay Settings

**Step 1: Select Replay Mode**
Choose one of three replay modes using the radio buttons:

- **Range Mode:**
  - Replays the recording a specific number of times
  - Requires setting the "Replay Limit" (1-200 times)
  - Best for: Testing specific number of repetitions

- **Infinity Mode:**
  - Replays continuously until manually stopped
  - No limit on repetitions
  - Best for: Continuous operation or testing

- **Sensor Mode:**
  - Replays based on sensor input/triggers
  - Two sensor options available (Sensor 0, Sensor 1)
  - Best for: Automated, sensor-triggered operations

**Step 2: Set Replay Limit (Range Mode Only)**
1. If "Range" mode is selected, locate the "Replay Limit" field
2. Enter the number of times to replay (1-200)
3. Example: Enter "5" to replay 5 times

**Step 3: Adjust Replay Speed**
1. Locate the **"Replay Speed"** slider
2. Current speed is displayed (e.g., "1.0x" = normal speed)
3. Drag the slider to adjust:
   - **Left**: Slower playback
   - **Right**: Faster playback
4. Speed value updates in real-time (e.g., "0.5x", "1.5x", "2.0x")

### 4.3 Starting and Stopping Replay

**Step 1: Start Replay**
1. Verify all settings are configured correctly
2. Ensure the robot is in a safe starting position
3. Click the large green **"Replay"** button
4. The interface will show "Replay playing..." or similar status
5. The robot will begin executing the recorded movements

**Step 2: Monitor Replay**
- Watch the robot movements carefully
- Check for any unexpected behavior
- Monitor the replay status indicator

**Step 3: Stop Replay**
- **Normal Stop:** Click the **"Stop"** button (appears during replay)
- **Emergency Stop:** Use the **"EMERGENCY STOP"** button (see Safety section)
- The system will halt immediately

---

## 5. File Management

### 5.1 Renaming Recordings

**Step 1: Load the Recording**
1. Select and load the recording you want to rename (see Section 4.1)

**Step 2: Rename the File**
1. Click the green **"Rename"** button
2. A rename dialog will appear
3. Enter the new filename (without extension)
4. Click **"OK"** or **"Save"**
5. The file is renamed and the list updates

**Important:**
- Do not include the `.pk1` extension in the new name
- The system will add the extension automatically
- Ensure the new name is unique to avoid conflicts

### 5.2 Deleting Recordings

**Step 1: Load the Recording**
1. Select and load the recording you want to delete (see Section 4.1)

**Step 2: Delete the File**
1. Click the red **"Delete"** button
2. A confirmation dialog may appear
3. Confirm the deletion
4. The file is permanently removed from the system
5. Refresh the list if needed

**Warning:**
- Deletion is permanent and cannot be undone
- Ensure you have backups if the recording is important
- Do not delete recordings that are currently in use

### 5.3 Browsing and Organizing Files

**Accessing File Browser:**
1. Click the **"Browse"** button in the Replay section
2. Navigate through directories to find recordings
3. Files are stored in: `/home/orin_nano/lerobot/backend/projects/LOREAL/`
4. All recordings use the `.pk1` file extension

---

## 6. Safety Procedures

### 6.1 Emergency Stop

**When to Use:**
- Robot is moving unexpectedly
- Robot is in an unsafe position
- Any emergency situation occurs
- Equipment malfunction detected

**How to Use:**
1. **Immediately** locate the large red **"EMERGENCY STOP"** button at the bottom of the interface
2. Click the button without hesitation
3. All robot operations will halt immediately
4. The system will enter a safe state

**After Emergency Stop:**
1. Assess the situation
2. Verify the robot has stopped completely
3. Check for any damage or issues
4. Do not resume operations until the issue is resolved
5. Document the incident if required

### 6.2 Safety Checklist

**Before Starting Any Operation:**
- [ ] Verify robot is in a safe starting position
- [ ] Ensure workspace is clear of obstacles
- [ ] Check that connection status shows "Connected"
- [ ] Confirm no other operations are in progress
- [ ] Know the location of the Emergency Stop button
- [ ] Ensure proper lighting and visibility

**During Operations:**
- [ ] Monitor robot movements continuously
- [ ] Keep hands and objects away from robot during operation
- [ ] Be ready to use Emergency Stop if needed
- [ ] Do not leave the robot unattended during replay

---

## 7. Troubleshooting

### 7.1 Connection Issues

**Problem: Connection status shows "Not Connected" or is missing**

**Solutions:**
1. Check USB cable connection to MotorsBus
2. Verify the correct port is configured
3. Run `lerobot-find-port` again to verify port
4. Restart the Robot Control application
5. Check if MotorsBus device is powered on

### 7.2 Recording Issues

**Problem: Recording doesn't start**

**Solutions:**
1. Verify connection status is "Connected"
2. Check if a previous recording is still active
3. Ensure robot is powered and responsive
4. Try stopping any active operations first
5. Restart the application if needed

**Problem: Recording stops unexpectedly**

**Solutions:**
1. Check for loose USB connections
2. Verify MotorsBus is receiving power
3. Check system logs for error messages
4. Ensure sufficient disk space for saving recordings

### 7.3 Replay Issues

**Problem: Replay doesn't start**

**Solutions:**
1. Verify a file is loaded (check "Loaded File" status)
2. Ensure replay mode is selected
3. Check that robot is in a safe starting position
4. Verify connection is active

**Problem: Replay stops unexpectedly**

**Solutions:**
1. Check connection status
2. Verify robot motors are functioning
3. Check for sensor issues (if using Sensor mode)
4. Review the recording file for corruption

**Problem: Replay speed doesn't change**

**Solutions:**
1. Verify the slider is moving (check value display)
2. Some recordings may have speed limitations
3. Try reloading the recording file
4. Restart the application

### 7.4 File Management Issues

**Problem: Files don't appear in dropdown**

**Solutions:**
1. Click **"Refresh List"** button
2. Verify files exist in the project directory
3. Check file permissions
4. Ensure files have `.pk1` extension

**Problem: Cannot rename or delete file**

**Solutions:**
1. Ensure the file is not currently loaded for replay
2. Check file permissions
3. Verify the file is not in use by another process
4. Try refreshing the list first

---

## 8. Quick Reference Guide

### Recording Workflow
```
1. Check Connection → 2. Click "New Record" → 3. Perform Movements → 4. Click "Stop Recording"
```

### Replay Workflow
```
1. Select File → 2. Load Recording → 3. Choose Mode → 4. Set Speed → 5. Click "Replay" → 6. Monitor → 7. Stop
```

### File Management
```
Rename: Load File → Click "Rename" → Enter New Name → Save
Delete: Load File → Click "Delete" → Confirm
Browse: Click "Browse" → Navigate → Select File → Open
```

### Emergency Procedures
```
Emergency: Click "EMERGENCY STOP" → Assess Situation → Resolve Issue → Resume Safely
```

---

## 9. Best Practices

1. **Always verify connection** before starting operations
2. **Test recordings** with a short sequence first
3. **Use appropriate replay mode** for your application:
   - Range: For specific number of tests
   - Infinity: For continuous operation
   - Sensor: For automated triggering
4. **Start with slower speeds** (0.5x - 1.0x) when testing new recordings
5. **Keep recordings organized** with descriptive names
6. **Backup important recordings** regularly
7. **Document any issues** or unexpected behaviors
8. **Never leave robot unattended** during replay operations

---

## 10. Contact and Support

For technical support or questions:
- Check system logs in the project directory
- Review troubleshooting section above
- Contact system administrator or technical support team

---

**Document End**

*Last Updated: December 2025*  
*For: Robot Control System - LOREAL Project*

