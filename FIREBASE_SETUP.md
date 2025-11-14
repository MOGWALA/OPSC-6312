# Firebase Cloud Messaging Setup

This app includes realtime notification support via Firebase Cloud Messaging (FCM). To enable push notifications, you need to set up Firebase for your project.

## Setup Steps

**Note:** A placeholder `google-services.json` file is included to allow the app to build without Firebase configured. Local notifications will work immediately. Replace this file with your actual Firebase configuration when you're ready to enable push notifications.

1. **Create a Firebase Project**
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Create a new project or select an existing one
   - Add an Android app to your project

2. **Replace google-services.json**
   - Download the `google-services.json` file from Firebase Console
   - Replace the placeholder file in the `app/` directory (same level as `build.gradle.kts`)

3. **Enable Firebase Cloud Messaging**
   - In Firebase Console, go to Project Settings > Cloud Messaging
   - Enable Cloud Messaging API if not already enabled

4. **Test Notifications**
   - The app will automatically request notification permissions on first launch (Android 13+)
   - Local notifications (achievements, daily puzzles) will work immediately
   - Push notifications require the FCM token to be sent to your backend server

## Notification Types

The app supports the following notification types:

- **Achievements**: Shown when a user unlocks an achievement
- **Daily Puzzles**: Shown when a new daily puzzle is available
- **Game Moves**: Shown when an opponent makes a move (for multiplayer)
- **Game Complete**: Shown when a game ends

## Local Notifications

Local notifications work immediately without Firebase setup:
- Achievement unlocks
- Daily puzzle availability

## Push Notifications

For push notifications from a server, you'll need to:
1. Implement token registration in your backend
2. Send the FCM token from `EvoChessMessagingService.onNewToken()` to your server
3. Send notifications from your server using the FCM API

## Notification Channels

The app creates the following notification channels:
- **General**: Default notifications
- **Achievements**: Achievement-related notifications (high priority)
- **Games**: Game-related notifications (high priority)
- **Puzzles**: Puzzle-related notifications (default priority)

Users can customize notification settings for each channel in Android Settings.

