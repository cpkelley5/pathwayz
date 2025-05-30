# Game Rules Documentation Template

## When Adding New Game Mechanics

### 1. Core Game Mechanics Section
```markdown
### **[New Mechanic Name]**
- **[Behavior]**: Description of what happens
- **[Trigger]**: When this mechanic activates
- **[Rules]**: Constraints and limitations
- **[Visual Feedback]**: How user sees this mechanic
```

### 2. Technical Implementation Section
```markdown
### **Critical Functions**
- `[functionName()]`: Description of what it does

### **Event Handling**  
- **[event type]**: What this event now does
```

### 3. Validation Results Section
```markdown
### **Confirmed Working**
- [New mechanic name and brief description]
```

## When Modifying Existing Mechanics

### Find the existing section and update:
- Change behavior descriptions
- Update technical function list
- Modify validation results
- Add notes about changes

## Quick Documentation Checklist

For ANY game logic change, ask:
- [ ] What mechanic changed/was added?
- [ ] How does user interact with it?
- [ ] What functions implement it?
- [ ] Has it been tested/validated?
- [ ] Does it affect other mechanics?

## Commit Message Format

```
[Type]: Brief description

- Code changes: [what changed in code]
- Documentation: [what changed in GAME_RULES_SPECIFICATION.md]
- Validation: [any testing done]
```

---
**Remember**: Documentation should be updated IMMEDIATELY after code changes, not as an afterthought. 