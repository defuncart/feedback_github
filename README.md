# feedback_github

## 🚀 Getting Started

### Setup

First, you will need to add `feedback_github` to your `pubspec.yaml`.

```yaml
dependencies:
  flutter:
    sdk: flutter
  feedback: ^3.0.0
  feedback_github:
    git: 
      url: https://github.com/defuncart/feedback_github/
      ref: main
```

Then, run `flutter pub get` in your terminal.

### Use it

Just wrap your app in a `BetterFeedback` widget.
To show the feedback view just call `BetterFeedback.of(context).show(...);`.
The callback gets called when the user submits his feedback. 

```dart
import 'package:feedback/feedback.dart';
import 'package:flutter/material.dart';

void main() {
  runApp(
    BetterFeedback(
      child: const MyApp(),
    ),
  );
}
```

Provide a way to show the feedback panel by calling 
```dart
BetterFeedback.of(context).showAndUploadToGitHub(
  username: 'username',
  repository: 'repository',
  authToken: 'github_pat_',
  labels: ['feedback'],
  assignees: ['username'],
  customMarkdown: '**Hello World**',
  imageId: Uuid().v4(),
);
```
Provide a way to hide the feedback panel by calling  `BetterFeedback.of(context).hide();` 

## Personal Access Token

A Personal Access Token with the following 
- issues (write)
- content (write)
- metadata (read)

It is recommended that you create a *fine-grained* Personal Access Token which only has access to the repository in which you'd like to create issues for.Moreover, consider adding a separate repository for your collected feedback.

## Repository Setup

The github repository `repository` for user `username` requires a `issue_images` branch where the images for issue can be uploaded to.
