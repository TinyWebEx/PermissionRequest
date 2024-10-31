# PermissionRequest

Helper module to interactively request permission from the user on a static page.

It uses the [message handler](https://github.com/TinyWebEx/MessageHandler) module to guide the user with message boxes to confirm a requested permission.

## Usage

1. Register one or more message boxes for a permission with `registerPermissionMessageBox`.
2. Show the permission with `requestPermission`.

Afterwards, it handles the permission box and permission request dialog by itself.
However, you can still cancel it (with some caveats with `cancelPermissionPrompt`) and check the current status with `isPermissionGranted`.

### Reaction

`requestPermission` returns a promise.
In contrast to the original [`browser.permissions.request`](https://developer.mozilla.org/docs/Mozilla/Add-ons/WebExtensions/API/permissions/request) API, the promise only resolves _if_ the user accepted the permission request. Otherwise it just rejects with an `PermissionError`.

### Required translation

You need to add these resources to your translation `message.json` in order to have all translations for this library:
```json
  "buttonRequestPermission": {
    "message": "Berechtigung erteilen",
    "description": "The button label, used for requesting a permission that is missing."
  },
  "couldNotRequestPermission": {
    "message": "Konnte Berechtigung nicht erfragen.",
    "description": "When the permission request fails."
  },
```

In addition, you obviously need to have the translation for the `messageText` you register when calling `registerPermissionMessageBox` added, too.
