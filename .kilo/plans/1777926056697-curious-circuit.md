# Fix: Delete Button, Add Bones, Move Origin Functionality

## Issues Identified

### 1. Delete Button (Critical - Missing Function Reference)
- **Location**: Line 363-366 in index.html
- **Problem**: `deleteFrame` function is defined (line 274) but NOT exposed on `window` object
- **Fix**: Add `window.deleteFrame = deleteFrame;` to expose the function

### 2. Adding Bones
- **Problem**: No UI button or functionality to add new bones to the chain
- **Current State**: Only one root bone exists, Bone class supports parent-child chains
- **Fix**: 
  - Add "Add Bone" button in Rig Controls section
  - Implement `addBone()` function that creates a child bone
  - Track selected bone for editing

### 3. Moving Point of Origin
- **Problem**: Root bone position is hardcoded at (0,0,0)
- **Fix**: 
  - Add X/Y position sliders or input fields
  - Update root bone world position based on controls

## Implementation Plan

1. **Fix deleteFrame exposure** (line ~366)
   - Add `window.deleteFrame = deleteFrame;`

2. **Add bone chain functionality**
   - Create `bones` array and `selectedBone` tracking
   - Add "Add Bone" button UI
   - Implement `addBone()` to append bone to chain
   - Update frame data structure to store full bone hierarchy

3. **Add origin position controls**
   - Add X/Y position sliders in Rig Controls panel
   - Update root bone position in animation loop
   - Store position in frame data

## Files to Modify
- `pivot3d_v1.0.html` - New file (copy of index.html with fixes)