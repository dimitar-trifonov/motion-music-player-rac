Here's a step-by-step plan to implement manual mode:

✅ Step 1: Add Control Mode State
Add controlMode to player state
Add isManualControlEnabled flag
Define mode switching logic

✅ Step 2: Create Manual Play/Pause Events
Create manual-play event
Create manual-pause event
Add validation for manual control state

✅ Step 3: Add Mode Switching Events
Create switch-to-manual event
Create switch-to-motion event
Add validation for mode switching

✅ Step 4: Update Existing Events
Modify start-playback to check control mode
Modify stop-playback to check control mode
Keep all other events unchanged

✅ Step 5: Add Mode-Specific Logic
Create validation rules for manual mode
Create validation rules for mode switching
Keep existing motion validation rules

✅ Step 6: Implement Event Priority
Define how manual and motion events interact
Handle potential conflicts
Ensure smooth mode switching

✅ Step 7: Add Error Handling
Add mode-specific error handling
Handle mode switching errors
Maintain existing error handling

✅ Step 8: UI Implementation
Layout Design:
- Single page layout with responsive design
- Component arrangement:
  * Motion Status at the top (prominent position)
    - Large, clear permission request button when needed
    - Clear motion detection status
    - Visual motion state indicator
  * Player Status below motion status
    - Current track information
    - Playback state
    - Simple loading indicator
  * Player Controls at the bottom
    - Play/Pause button
    - Mode switch toggle
    - Other controls

✅ Create Motion Status Component:
- Component Structure:
  * Required fields:
    - id: motion-status
    - version: 1.1
    - type: object
    - description: Motion detection status display
  * Components:
    - Container:
      * type: container
      * fields: [onMount, permissionStatus, availabilityStatus]
      * submitEvent: check-motion-availability
    - Permission Button:
      * type: button
      * fields: [text, onClick]
      * submitEvent: request-motion-permission
    - Status Display:
      * type: text
      * fields: [text]
    - Status Indicator:
      * type: indicator
      * fields: [state, color]

- Component Logic:
  * Permission States:
    - Granted: Motion detection is available
    - Denied: Motion detection is not available
  * Availability States:
    - Available: Device supports motion detection
    - Not Available: Device doesn't support motion detection

✅ Create Player Status Component:
- Component Structure:
  * Required fields:
    - id: player-status
    - version: 1.1
    - type: component
    - description: Player status display
    - bindsTo: player-status
  * Components:
    - Track Info:
      * type: text
      * fields: [title, artist]
    - Playback State:
      * type: indicator
      * fields: [state]
    - Loading:
      * type: indicator
      * fields: [state]

✅ Create Player Controls Component:
- Component Structure:
  * Required fields:
    - id: player-controls
    - version: 1.1
    - type: component
    - description: Player control interface
    - bindsTo: player-controls
  * Components:
    - Play/Pause:
      * type: button
      * fields: [text, onClick]
      * submitEvent: toggle-playback
    - Mode Switch:
      * type: button
      * fields: [text, onClick]
      * submitEvent: switch-mode
    - Volume:
      * type: slider
      * fields: [value, onChange]
    - Progress:
      * type: progress
      * fields: [value, max]
    - Navigation:
      * type: button
      * fields: [text, onClick]
      * submitEvent: [next-track, previous-track]

✅ Create Player Page Component:
- Component Structure:
  * Required fields:
    - id: player-page
    - version: 1.1
    - type: component
    - description: Main player page layout
  * Components:
    - Motion Status:
      * type: component
      * fields: [permissionStatus, availabilityStatus, motionState]
      * submitEvent: check-motion-availability
      * bindsTo: motion-status
    - Player Status:
      * type: component
      * fields: [currentTrack, playbackState, isLoading, error]
      * submitEvent: update-player-status
      * bindsTo: player-status
    - Player Controls:
      * type: component
      * fields: [controlMode, playbackState, volume, currentTime, duration, isLoading, error]
      * submitEvent: update-player-controls
      * bindsTo: player-controls
  * Views:
    - path: /player
    - layout: container with children [motionStatus, playerStatus, playerControls]

State Management:
- In-memory state only (no persistence)
- Shared state between components
- State synchronization
- Component communication
- Event handling across components

✅ Step 9: Testing Scenarios

✅ Motion Status Component Testing:
- Availability Check:
  * Device supports motion detection
    - Shows permission request button
    - Shows "Motion detection: Ready" when granted
    - Shows "Motion detection: Permission required" when denied
  * Device doesn't support motion detection
    - Shows "Motion detection: Not available"
    - No permission button shown
    - Indicator shows not-available state

- Permission Flow:
  * Initial State
    - Shows permission request button
    - Shows "Motion detection: Permission required"
  * Permission Granted
    - Hides permission request button
    - Shows "Motion detection: Ready"
    - Indicator shows available state
  * Permission Denied
    - Shows permission request button
    - Shows "Motion detection: Permission required"
    - Indicator shows not-available state

- Component Mount:
  * Triggers availability check
  * Sets correct initial state
  * Shows appropriate UI elements

- Error Handling:
  * Graceful handling of permission errors
  * Clear error messages
  * Proper state recovery

✅ Player Status Component Testing:
- Component Structure:
  * Required fields:
    - id: player-status
    - version: 1.1
    - type: component
    - description: Player status display
    - bindsTo: player-status
  * Components:
    - Track Info:
      * type: text
      * fields: [title, artist]
    - Playback State:
      * type: indicator
      * fields: [state]
    - Loading:
      * type: indicator
      * fields: [state]

- Test Cases:
  * Initial State:
    - Empty track info
    - Paused playback state
    - Loaded state
  * Track Loaded:
    - Correct track info display
    - Paused playback state
    - Loaded state
  * Playback Started:
    - Correct track info display
    - Playing state
    - Loaded state
  * Playback Paused:
    - Correct track info display
    - Paused state
    - Loaded state
  * Track Loading:
    - Correct track info display
    - Paused state
    - Loading state
  * Track Load Error:
    - Empty track info
    - Paused state
    - Error state
  * Track Ended:
    - Empty track info
    - Paused state
    - Loaded state

✅ Player Controls Component Testing:
- Test Cases:
  * Initial State:
    - Play button disabled
    - Mode switch enabled
    - Volume slider enabled
    - Progress bar disabled
    - Navigation buttons disabled
  * Track Loaded:
    - Play button enabled
    - Mode switch enabled
    - Volume slider enabled
    - Progress bar enabled
    - Navigation buttons in correct state
  * Playback Started:
    - Play button shows "Pause"
    - All controls enabled
    - Progress bar active
  * Playback Paused:
    - Play button shows "Play"
    - All controls enabled
    - Progress bar paused
  * Mode Switching:
    - Manual to Motion:
      * Play button disabled
      * Mode switch shows "Switch to Manual"
      * Other controls enabled
    - Motion to Manual:
      * Play button enabled
      * Mode switch shows "Switch to Motion"
      * All controls enabled
  * Volume Control:
    - Slider updates volume
    - State properly updated
  * Progress Control:
    - Bar updates position
    - State properly updated
  * Loading State:
    - All controls disabled
    - Progress bar shows loading
  * Error State:
    - Play button disabled
    - Mode switch enabled
    - Volume slider enabled
    - Progress bar disabled
    - Navigation buttons disabled

✅ Manual Mode Testing:
- Play/pause button functionality
- Volume control operation
- Track navigation
- Progress bar interaction
- Mode switch to motion
- Error state display
- Loading state handling

✅ Motion Mode Testing:
- Motion detection triggering playback
- Motion stop triggering pause
- Volume control operation
- Track navigation
- Progress bar interaction
- Mode switch to manual
- Error state display
- Loading state handling
- Motion permission scenarios:
  * Initial permission request flow
  * Permission granted state
  * Permission denied state
  * Permission revoked state
  * Permission button visibility
  * Permission status indicator accuracy
  * Error handling for permission states

✅ Mode Switching Testing:
- Switch from manual to motion
- Switch from motion to manual
- State preservation during switch
- Error handling during switch
- UI feedback during switch
- Control state validation

✅ Integration Testing:
- Component interaction
- State synchronization
- Event propagation
- Error handling across components
- Performance testing
- Edge case handling