# June 2025

---

## Friday, 27th June 2025

### Primary Query

`How do we effectively analyze app crashes in production, and what are the common reasons why crashes might not be reported by Firebase Crashlytics?`

```
You are an iOS app development veteran with two decades of hands-on experience building and maintaining applications for Apple platforms. Your deep expertise spans the entire development lifecycle, from initial concept to post-launch support and optimization.

A junior developer on your team has approached you with a common yet critical production issue: **"How do we effectively analyze app crashes in production, and what are the common reasons why crashes might not be reported by Firebase Crashlytics?"**

Draft a comprehensive, detailed answer addressing both parts of their question. Your response should cover the following aspects:

**1. Analyzing Crashes in Production:**
    * **The Importance of Crash Reporting:** Why is it non-negotiable to have robust crash reporting in production?
    * **Primary Tools & Approaches:** Discuss the essential tools and methods available for collecting and analyzing crash reports for iOS apps in a production environment. This should include:
        * **Apple's Built-in Mechanisms:**
            * App Store Connect (Crashes Organizer)
            * MetricKit (for system-level diagnostics and performance)
            * Device Logs (retrieving `.ips` files from users)
        * **Third-Party Crash Reporting Services:** Beyond Firebase Crashlytics, briefly mention other prominent services and their key differentiators (e.g., Sentry, Instabug, Bugsnag), highlighting why a blend of tools can be beneficial.
    * **Interpreting Crash Reports:** Explain how to read and understand the critical information within a crash report:
        * **Stack Traces (Symbolication):** Emphasize the crucial role of dSYM files and the symbolication process.
        * **Exception Types and Codes:** Common crash types (e.g., `EXC_BAD_ACCESS`, `SIGABRT`, `NSSegmentFault`) and what they typically indicate.
        * **Thread States and Backtraces:** Understanding the state of all threads at the time of the crash.
        * **Contextual Information:** App version, OS version, device model, user actions/breadcrumbs leading to the crash.
    * **Debugging Strategies:** Practical approaches to reproduce and debug production crashes, even without direct debugger attachment.

**2. Reasons for Unreported Crashes in Firebase Crashlytics:**
    * **Common Integration Issues:**
        * Incorrect or incomplete Firebase SDK setup (e.g., missing run script for dSYM upload, `GoogleService-Info.plist` issues).
        * SDK version compatibility issues.
    * **Symbolication Problems:**
        * Missing or incorrect dSYMs in Firebase.
        * Bitcode implications.
    * **Network and Data Collection Settings:**
        * User privacy settings (opt-in/opt-out for analytics data).
        * Network connectivity issues preventing report upload.
        * App lifecycle: Crashes occurring before Crashlytics initializes or immediately upon launch without a subsequent relaunch.
    * **Specific Crash Types:** Certain low-level or watchdog-related crashes that might be missed by user-space crash reporters like Crashlytics, and how MetricKit or direct device logs can capture these.
    * **Testing and Debugging Environments:** Crashes only occurring in release builds or outside of Xcode's debugger.

Throughout your answer, adopt a tone that reflects your 20 years of experience – authoritative, practical, and insightful, offering best practices and common pitfalls to avoid. Use clear, concise language and leverage Markdown effectively to structure your response with headings, subheadings, bullet points, and code snippets where appropriate.
```

### TODOs
- [ ] Check MetricKit
- [x] Add notes for crashes debugging
    - Added at https://github.com/saurabh1088/notes/blob/main/iOS/Debug/Crashes.md

---

## Saturday, 28th June 2025

- Updated QnA at https://github.com/saurabh1088/notes/blob/main/iOS/Debug/Crashes.md
- Added clipboard to Journal group in repo https://github.com/saurabh1088/notes
    - https://github.com/saurabh1088/notes/blob/main/Journal/clipboard.md
- Node.js


---

## Sunday, 29th June 2025

- Node.js
- Updated notes at : https://github.com/saurabh1088/notes/blob/main/react/NodeJS.md

### TODOs
- [ ] If NodeJS is single-threaded, then how does it handle concurrency?

---

## Monday, 30th June 2025

