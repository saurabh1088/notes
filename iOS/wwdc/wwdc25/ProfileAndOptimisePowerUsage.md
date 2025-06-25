# Profile and optimize power usage

Source : https://developer.apple.com/videos/play/wwdc2025/226/


## 🔋 Profile and Optimize Power Usage in Your App

### 🧭 Overview

- Power efficiency is a critical factor in delivering high-quality app experiences.
- Apps that consume less power:
    - Extend battery life
	- Improve app performance
	- Result in higher user satisfaction and engagement


### 🛠️ Power Profiling Tools

#### 🔍 Instruments – Power Profiler - New this year

- Captures and visualizes power consumption metrics.
- Enables developers to record and analyze power traces.
- Displays:
    - System-level metrics (overall energy consumption)
    - Per-app power impact broken down by subsystems:
    - CPU
    - GPU
    - Display
    - Networking

#### 🔍 Instruments – Time Profiler

- Identifies the functions consuming the most CPU time.
- Crucial for pinpointing inefficient or overly frequent method calls.

#### 🧪 Other Tools
- Xcode Energy Gauge – Instant feedback during development.
- XCTest – Catch regressions early via automated testing.
- Xcode Organizer – Post-shipping analytics including power usage.
- MetricKit – On-device diagnostics at scale.
- App Store Connect API – Remote access to diagnostics and metrics.


## 🧪 Reproducing and Fixing Issues Locally

### Case Study: Destination Video App (Video Streaming App)

🧾 Problem
- Added a new Library pane to browse video content.
- After release, CPU usage spiked, degrading performance and battery life.

🧰 Profiling Steps
	1.	Use Instruments > Power Profiler + CPU Profiler.
	2.	Reproduce the issue by navigating to the Library pane.
	3.	Analyze power impact metrics.
- System usage: ~10.5%/hr
- CPU power spike from 1 → 21

📌 Root Cause
- App was using VStack to render hundreds/thousands of thumbnails at once.
- Resulted in:
    - High CPU usage
    - UI freeze
    - Power inefficiency

✅ Optimization

API Mentioned: LazyVStack (SwiftUI)

- Replaced VStack with LazyVStack.
- LazyVStack renders only visible (or soon-to-be visible) views.
- Reduces unnecessary view and thumbnail generation.
- After optimization, CPU power dropped from 21 → 4.3


## 🌐 Profiling Real-World Usage

On-Device Power Profiling

Feature Mentioned: Performance Trace with Power Profiler

Why?
- Some bugs or power issues occur only in real-world scenarios (e.g., while driving or walking).
- Xcode-connected profiling cannot capture those.

Setup Steps:
	1.	Enable Developer Mode in iOS Settings (after connecting to Xcode once).
	2.	Navigate to Settings > Developer > Performance Trace.
	3.	Enable Power Profiler and select the target app (must be installed via Xcode/TestFlight/Enterprise).
	4.	Add the Performance Trace icon to Control Center.
	5.	Start recording trace manually during real-world usage.
	6.	Stop recording → Export trace → Analyze in Instruments on Mac.

Real-World Case Study
- The Destination Video app showed periodic spikes in CPU usage.
- Root cause traced to:
    - videoSuggestionsForLocation() being called too frequently.
    - Each call performed expensive operations:
    - Reading RecommendationRules JSON from disk.
    - Decoding via JSONDecoder on every location change.

Optimization
- Load and parse the rules once (lazy-loading and caching).
- Reduced unnecessary file I/O and decoding.
- Addressed energy and performance regression.


## ⚖️ Comparing Optimization Strategies

Sometimes multiple implementations are proposed. Example:
- Approach 1: Fast with small datasets, but scales poorly.
- Approach 2: Slower for small data, but efficient for large sets.

How to Decide?
	1.	Profile both implementations using Power Profiler.
	2.	Run tests under different real-world conditions (network, thermals, background tasks).
	3.	Capture multiple traces and average results.
	4.	Use data to make informed decisions about energy/performance tradeoffs.

⸻

## 🧩 Best Practices & Strategy

Phase	Tools/Techniques
Development	Xcode Energy Gauge, XCTests, Lazy APIs (e.g., LazyVStack)
Profiling	Instruments (Power Profiler, Time Profiler), On-device Performance Trace
Validation	Compare traces of different implementations
Post-Shipping	Xcode Organizer, MetricKit, App Store Connect API

Developer Guidance
- Profile early and often.
- Let power metrics guide architectural choices.
- Continuously test and revalidate performance after changes.
- Use on-device tracing to address edge cases that are hard to reproduce in dev environments.
- Always confirm fixes by comparing traces before and after the change.

⸻

## ✅ Key APIs and Tools Mentioned

API/Tool	Purpose
Power Profiler	Analyze power consumption and identify subsystem-level impact
Time Profiler	Identify CPU-heavy functions
LazyVStack (SwiftUI)	Efficient rendering of large lists/views
Xcode Energy Gauge	Live energy impact estimation during development
XCTest	Automated tests to catch power regressions early
MetricKit	Aggregate diagnostic reports from users in production
App Store Connect API	Access metrics programmatically post-release
Performance Trace	On-device data collection for remote diagnostics


## 💡 Final Takeaways
- Power efficiency is not just optimization — it’s essential UX.
- Profiling should be integrated into your regular dev workflow.
- Use on-demand rendering, caching, and lazy-loading to avoid unnecessary work.
- Real-world testing reveals what desk-testing can’t.
- Combine profiling, testing, and metrics to ship robust, battery-efficient apps.


## 📌 Developer Action Item

Try this now: Run your app, collect a power trace using Power Profiler, and examine what you discover. Start building intuition for energy impact before issues appear in production.
