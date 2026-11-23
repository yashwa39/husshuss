# SafeSense – Workplace Gas & Sound Sensor Dashboard

**ET-201 · Team 23 · University Prototype**

A single-file, self-contained workplace monitoring dashboard demonstrating OOP principles in JavaScript, mirroring Java design patterns.

---

## 🚀 Quick Start

**No installation required. No server needed.**

1. Download `safesense.html`
2. Double-click to open in any modern browser
3. Login with demo credentials: `aisha@demo.com` / `Demo@123`  
   _(Or click "Skip to dashboard")_

---

## 📋 Features

### Dashboard (Real-time Monitoring)
- **4 live sensors**: Sound Level (dB), Carbon Monoxide (ppm), Hydrogen Sulfide (ppm), Methane (ppm)
- **Demo modes**: Auto (drifting + spikes), Normal, Warning, Critical
- **Visual indicators**: Color-coded status banner, threshold bars with smooth marker animation
- **SVG line chart**: Last 60 seconds of readings with warning/critical limit lines
- **Alert system**: Latest 5 alerts, toast notifications on critical events
- **Updates every 2 seconds**

### Test Results
- **48 test cases** across 7 categories: Unit, Threshold, Dashboard, Alerts, Login, Edge, API
- **100% pass rate** (35 passed + 1 fixed after retest)
- **Expandable rows** with detailed inputs/outputs
- **BUG-01 documentation**: T8 shows the boundary condition bug (H₂S 50.0 ppm) + fix
- **Run live tests**: Execute actual JS classes in-browser with timing

### OOP Code Reference
- **5 Java source tabs**: Sensor (parent), GasSensor, SoundSensor, Threshold, Main test
- **Concept panels**: Each tab explains the OOP principle being demonstrated
- **Run demo**: See polymorphism + exception handling in action

---

## 🎓 OOP Principles Demonstrated

| Concept | Implementation |
|---|---|
| **Encapsulation** | Private fields (`#gasLevel`, `#sensorName`) with validated getters/setters |
| **Inheritance** | `GasSensor extends Sensor`, `SoundSensor extends Sensor` with `super()` |
| **Method Overriding** | Each child overrides `checkSafetyStatus()` with sensor-specific logic |
| **Object Creation** | `SensorManager` creates all 4 sensor objects in its constructor |
| **Exception Handling** | `setGasLevel(-5)` → catch → log error + set to 0 + mark sensor error |
| **Polymorphism** | Single loop `sensors.map(s => s.checkSafetyStatus())` dispatches to correct override |
| **Interface** | `SimulatedDataSource.readAll()` — swappable with `HardwareDataSource` in Semester 4 |

**50+ `// OOP:` comments** throughout the code mark every demonstration.

---

## 🛠️ Technical Stack

- **HTML5** – semantic structure, ARIA labels for accessibility
- **CSS3** – design tokens, flexbox/grid, responsive breakpoints, animations
- **Vanilla JavaScript** – ES6 classes with private fields (`#`), no libraries
- **Inline SVG** – icons, line chart with gradient fills + dashed threshold lines
- **No dependencies** – works offline, no CDN, no build step

---

## 📐 Classification Rules

| Sensor | Warning Limit | Critical Limit | Unit |
|---|---|---|---|
| Sound Level | 85 | 100 | dB |
| Carbon Monoxide | 35 | 200 | ppm |
| Hydrogen Sulfide | 10 | 50 | ppm |
| Methane | 1000 | 5000 | ppm |

**Classification logic**: `value >= critical` → CRITICAL; `value >= warning` → WARNING; else NORMAL.

---

## 🧪 Test Coverage

```
Unit tests       8   │ Setters, getters, super(), polymorphism loop
Threshold tests 12   │ All boundary values (84.9, 85.0, 50.0, etc.)
Dashboard tests  4   │ Banner states for each mode
Alert tests      6   │ Escalation, deduplication, latest 50 kept
Login tests      6   │ Auth flow, validation, skip link
Edge tests       7   │ Negative input, rapid mode switching, responsive
API tests        5   │ DataSource.readAll(), mode switching
────────────────────┼─────────────────────────────────────────────
Total           48   │ 47 PASS + 1 FIXED = 100% pass rate
```

---

## 🎨 Design

- **Minimal, stylised** – no clutter, generous spacing, 12–16px border radius
- **Colour palette**:
  - Navy text `#14243F`, Primary blue `#2748D8`
  - Green `#1B7F55`, Amber `#B7791F`, Red `#C62828`
  - Each status has a tinted background (`--green-bg`, `--amber-bg`, `--red-bg`)
- **Animations**: Smooth threshold marker transition (0.4s cubic-bezier), critical pill pulse
- **Responsive**: Sidebar collapses to top menu below 768px, single-column cards below 480px
- **Accessible**: Status always shown as text, visible focus rings, good contrast

---

## 📝 Demo Script (for Faculty)

1. **Login** → `aisha@demo.com` / `Demo@123` (or click "Skip to dashboard")
2. **Demo modes** → Top-right switch: Auto | Normal | Warning | Critical — watch cards/banner update
3. **Critical toast** → Switch to Critical → red toast appears bottom-right
4. **Test T8** → Sidebar → "Test results" → Click row T8 → BUG-01 card expands
5. **OOP code** → Sidebar → "OOP code" → Browse 5 tabs → Click "Run demo" → see console output

---

## 📦 File Structure

```
safesense.html                    2,358 lines
├─ <style>                        CSS (design tokens, layout, responsive)
├─ HTML screens
│  ├─ Login                       Email/password form + skip link
│  ├─ Dashboard                   Sidebar + 4 sensor cards + chart + alerts
│  ├─ Test Results                48 rows + expandable + Run live tests
│  └─ OOP Code                    5 tabs with Java source + Run demo
└─ <script>
   ├─ OOP Classes                 Sensor, GasSensor, SoundSensor, Threshold,
   │                              Alert, AlertService, ZoneStatusService,
   │                              SimulatedDataSource, SensorManager,
   │                              AuthenticationError
   ├─ Services & Test Data        DEMO_USER, TEST_DATA (48 rows)
   ├─ UI Rendering                renderSensorCards, renderBanner, renderChart, etc.
   └─ Event Handlers              Login, logout, nav, demo mode switch, live tests
```

---

## 🔒 Security Note

**This is a front-end prototype for demonstration only.**  
Login credentials are compared in plain JavaScript. A production system would:
- Hash passwords server-side (bcrypt, Argon2)
- Use HTTPS + secure session tokens
- Validate all inputs server-side
- Implement rate limiting + CSRF protection

---

## 🌐 Browser Compatibility

Tested on:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

Requires ES6 support (private class fields `#`).

---

## 📄 License

University project prototype. For educational purposes.

---

## 👥 Team

**ET-201 · Team 23**  
SafeSense — Workplace Gas & Sound Sensor Monitoring Dashboard

---

**Questions?** Open the file and check the in-code comments — 50+ `// OOP:` markers explain every principle.
