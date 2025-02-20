# Expo Linking.getInitialURL() Intermittent Null Return

This repository demonstrates a bug encountered with Expo's `Linking.getInitialURL()` API.  The method inconsistently returns `null`, even when a deep link is successfully passed to the application. The issue appears to be related to the timing of the `getInitialURL` call, often resolving to `null` if called too early in the app's lifecycle.

## Steps to Reproduce

1. Clone the repository.
2. Run the app on a physical device or emulator.
3. Launch the app via a deep link (instructions in `bug.js`)
4. Observe the console output.  You'll likely see `null` reported some of the time.

## Solution

A potential solution involves using `Linking.addEventListener` to listen for URL changes asynchronously.  This allows the app to react to the deep link even if `getInitialURL` fails immediately. The solution demonstrates this using `useEffect` hook in React.  Check `bugSolution.js` for the improved implementation.