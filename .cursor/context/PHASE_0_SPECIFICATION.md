# Phase 0: Pathwayz Proof of Concept

## Goal
Create a minimal working prototype in a single HTML file to validate core game mechanics and mobile touch interactions.

## Success Criteria
- [ ] Path drawing works smoothly with touch and mouse
- [ ] 60fps animations on mobile device
- [ ] Win condition detection works
- [ ] Game feels responsive and fun to play
- [ ] Deployed and testable on mobile phone

## Game Setup (Hardcoded 6x6 Puzzle)
```javascript
const PUZZLE = {
  size: 6,
  numbers: [
    {num: 1, x: 0, y: 0},
    {num: 2, x: 2, y: 1}, 
    {num: 3, x: 4, y: 2},
    {num: 4, x: 1, y: 3},
    {num: 5, x: 3, y: 4},
    {num: 6, x: 5, y: 5}
  ],
  walls: [
    {x: 1, y: 1},
    {x: 3, y: 2}
  ]
};