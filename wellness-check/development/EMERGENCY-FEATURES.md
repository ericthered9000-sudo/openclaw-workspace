# Emergency Features Implementation Plan

**Created:** 2026-03-05
**Priority:** High (requested by store manager and wife)

---

## Feature 1: 911 Emergency Button

### Overview
Large, always-visible button that dials 911 directly. Works on mobile PWA.

### Technical Approach
**Simple HTML `tel:` link**
```html
<a href="tel:911" class="emergency-button">
  🆘 Call 911
</a>
```

### Requirements
- [ ] Big red button (minimum 48px touch target)
- [ ] Always visible on Senior home screen
- [ ] Works on mobile Safari and Chrome
- [ ] Confirm dialog before dialing (prevent accidents)
- [ ] Visual feedback on press
- [ ] High contrast option support

### Browser Support
- ✅ All mobile browsers (auto-dials on tap)
- ✅ Desktop (opens system dialer)
- ✅ PWA compatible

### UX Considerations
- Position near bottom for easy thumb reach
- Make it prominent but not alarming (don't scare users)
- Consider "Hold to call" to prevent accidental calls
- Show confirmation: "Calling 911..."

### Implementation Effort
**~2-4 hours** — Very simple, mostly styling

---

## Feature 2: Voice Commands

### Overview
Allow seniors to control app with voice when they can't touch the screen.

### Commands to Support
| Voice Command | Action |
|---------------|--------|
| "I'm okay" / "I'm fine" | Trigger check-in |
| "Call for help" | Open emergency contacts |
| "Call 911" / "Emergency" | Initiate 911 call flow |
| "Call [family name]" | Call emergency contact |

### Technical Approach
**Web Speech API**
```javascript
const recognition = new webkitSpeechRecognition();
recognition.continuous = false;
recognition.interimResults = false;

recognition.onresult = (event) => {
  const command = event.results[0][0].transcript.toLowerCase();
  handleVoiceCommand(command);
};

// Start listening
recognition.start();
```

### Requirements
- [ ] Microphone permission request (graceful UX)
- [ ] Listen for specific commands
- [ ] Visual feedback ("Listening..." indicator)
- [ ] Fallback for unsupported browsers
- [ ] Works offline (basic commands)
- [ ] Senior-friendly voice prompts ("What would you like to do?")

### Browser Support
| Browser | Support |
|---------|---------|
| Chrome Android | ✅ Full |
| Safari iOS | ✅ Full (14.5+) |
| Chrome Desktop | ✅ Full |
| Safari Desktop | ✅ Full |
| Firefox | ❌ Disabled by default |
| Samsung Internet | ✅ Partial |

### UX Considerations
- Microphone button to activate listening (don't always listen)
- Clear visual state: idle, listening, processing
- Read back command: "You said 'call for help'. Is that correct?"
- Cancel option: "Cancel" voice command
- Timeout after 5 seconds of silence

### Privacy Note
- Only listen when user activates
- No cloud storage of voice
- Process locally when possible

### Implementation Effort
**~8-16 hours** — Moderate complexity, testing needed

---

## Implementation Priority

### Phase 1 (Quick Win)
1. **911 Button** — Implement immediately
   - Add to Senior home screen
   - Style prominently
   - Add confirmation dialog

### Phase 2 (Voice)
2. **Voice Commands** — After 911 is stable
   - Start with "I'm okay" command
   - Add emergency commands
   - Test with real seniors

---

## Pricing Impact

These features could justify a premium tier:

| Tier | Price | Features |
|------|-------|----------|
| Free | $0 | Basic wellness, 1 family member |
| Family | $9.99/mo | 911 button, voice commands, 5 family |
| Premium | $14.99/mo | All features + health data integration |

---

## Design Mockup (911 Button)

```
┌────────────────────────────┐
│  🏥 Wellness Check         │
│                            │
│   [Wellness Score: 64]     │
│                            │
│   ┌────────────────────┐   │
│   │ ✅ I'M OKAY        │   │
│   └────────────────────┘   │
│                            │
│   ┌────────────────────┐   │
│   │ 🆘 EMERGENCY       │   │
│   │    Call 911        │   │
│   │   (Hold 2 sec)     │   │
│   └────────────────────┘   │
│                            │
│   🏠 Home  💊 Meds  📅 Appts │
└────────────────────────────┘
```

---

## Next Steps

1. Create feature branch: `feature/emergency-button`
2. Implement 911 button with hold-to-call
3. Add to home screen (Senior view)
4. Test on mobile devices
5. Add voice commands in Phase 2

---

*Plan created by Girz, 2026-03-05*