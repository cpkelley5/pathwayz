# Pathwayz - Complete Game Rules Specification

## Core Game Mechanics ✅ VALIDATED IN PHASE 0

### **Sequential Number Visiting**
- Start at number 1, visit numbers in order: 1→2→3→4→5→6
- Must visit ALL numbers to progress toward win condition
- Cannot skip numbers or visit out of order
- Game stops accepting new numbered targets after reaching final number

### **Path Drawing Rules**
- **Hold-to-Draw**: Must maintain finger/mouse contact throughout drawing
- **Lifting finger/mouse**: Immediately clears entire path and resets to start
- **Adjacent Movement Only**: Can only move to cells directly adjacent (no diagonal)
- **No Revisiting**: Cannot visit the same cell twice in one path
- **Continuous Path**: Path must be unbroken from start to current position

### **Backtracking Mechanics**
- **Sequential Only**: Can only backtrack along existing path
- **Leading Edge**: Must backtrack from the current "leading edge" of path
- **Number Decrement**: Backtracking past a numbered cell decrements current target
- **Visual Reset**: Backtracked cells lose their path highlighting
- **Full Reset Allowed**: Can backtrack all the way to beginning (number 1)

### **Win Condition (STRICT)**
- **ALL Numbers**: Must visit all 6 numbers in sequence (6/6)
- **ALL Cells**: Must visit every non-wall cell exactly once
- **Simultaneous**: Both conditions must be met simultaneously
- **No Partial Wins**: 35/36 cells is NOT a win, even with all numbers

### **Post-Win Behavior**
- **Game Freeze**: Once won, game state is preserved and frozen
- **No Reset on Lift**: Lifting finger/mouse after win does NOT reset the game
- **Drawing Disabled**: Cannot start new paths or modify existing path
- **Manual Reset Only**: Only Reset or New Game buttons can restart
- **UI State Change**: Hint button disappears, New Game button appears
- **Victory Preservation**: Win message and celebration remain visible

### **Movement After Final Number**
- **Continue Drawing**: After reaching number 6, can continue drawing path
- **No New Numbers**: Cannot target any more numbered cells
- **Fill Remaining**: Must cover all remaining empty cells to win
- **Status Change**: UI shows "Cover all cells:" instead of "Find number:"

## Mobile UX Requirements ✅ VALIDATED

### **Touch Sensitivity**
- **Enhanced Detection**: If direct touch misses, check nearest cell
- **Consistent Sensitivity**: Forward and backward movement equally responsive  
- **44px+ Touch Targets**: Minimum touch target size for accessibility
- **No Page Scroll**: Prevent page scrolling during touch interaction

### **Visual Feedback**
- **Current Number**: Highlight currently targeted number
- **Path Visualization**: Show visited cells vs. current target vs. empty
- **Progress Display**: Show "Cells: X/36 | Numbers: Y/6" counter
- **Win Celebration**: Animation and message when puzzle complete

## Puzzle Requirements ✅ TESTED

### **Solvability**
- **Algorithm Verification**: Every puzzle must pass solvability check
- **Complete Coverage**: Must be possible to visit all non-wall cells
- **Sequential Access**: Must be possible to reach all numbers in order
- **No Dead Ends**: Path must not get trapped before completion

### **Phase 0 Simple Pattern**
- **Straight Line Numbers**: Numbers 1-6 in adjacent horizontal line
- **No Walls**: Ensures trivial solvability for testing
- **36 Total Cells**: 6x6 grid with no obstacles

## Technical Implementation Notes

### **Game State Management**
```javascript
gameState = {
    currentNumber: 1,           // Next number to find (1-6)
    path: [],                   // Array of {x, y} coordinates
    visited: new Set(),         // Set of "x,y" coordinate strings
    isDrawing: false,           // Currently drawing path
    gameWon: false             // Puzzle completed
}
```

### **Critical Functions**
- `isPuzzleSolveable()`: Verify puzzle has valid solution
- `isValidMove(x, y)`: Check if move is allowed
- `canBacktrack(x, y)`: Check if backtracking is allowed
- `backtrackToCell(x, y)`: Remove path back to specified cell
- `checkWinCondition()`: Verify both numbers and cells complete
- `resetGame()`: Reset all game state and UI elements
- `newGame()`: Generate new puzzle (Phase A+) or reset current (Phase 0)

### **Event Handling**
- **mousedown/touchstart**: Begin drawing if valid start cell (unless game won)
- **mousemove/touchmove**: Continue path or backtrack (unless game won)
- **mouseup/touchend**: Clear path and reset (unless game won - then preserve state)
- **Enhanced touch detection**: Calculate nearest cell on miss
- **Reset button**: Always resets game regardless of state
- **New Game button**: Appears after win, generates new puzzle (future)

## Phase 0 Validation Results ✅

### **Confirmed Working**
- Sequential number visiting (1→2→3→4→5→6)
- Hold-to-draw behavior (path clears on lift)
- Backtracking along existing path
- Strict win condition (all numbers + all cells)
- Post-win game freeze and state preservation
- Mobile touch sensitivity with enhancements
- Puzzle solvability verification

### **Performance Metrics**
- 60fps animations on mobile devices
- Smooth path drawing without lag
- No page scrolling interference
- Touch targets feel appropriate size

---

## Next Phase Implementation

**Phase A+**: These rules form the foundation for React component architecture
**Phase B**: Puzzle generation must follow solvability requirements  
**Phase C**: UI components must implement exact touch behavior
**Phase D**: Game logic integration must preserve all validated mechanics

**Status**: All core mechanics validated and documented
**Ready for**: Full React implementation with confidence 