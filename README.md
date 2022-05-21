## Flutter Chrome Extension

## Steps
Follow the Following step to generate Flutter web app as Chrome Extension

### 1. Remove Extra Scripts from `web/index.html`
Remove all the `<script>` tags from `web/index.html` and replace with the below code.

```html
<body>
  <script src="main.dart.js" type="application/javascript"></script>
</body>
```

### 2. Add the Following to top `<html>` tag

```html
<!DOCTYPE html>
<html style="height: 600px; width: 350px">
```

### 3. Replace the `web/manifest.json` with following code

```json
{
    "name": "flutter_chrome_extension",
    "description": "Flutter Chrome Extension",
    "version": "1.0.0",
    "content_security_policy": {
        "extension_pages": "script-src 'self' ; object-src 'self'"
    },
    "action": {
        "default_popup": "index.html",
        "default_icon": "icons/Icon-192.png"
    },
    "manifest_version": 3
}
```

### 4. Build web app with `--web-renderer html --csp`

```
flutter build web --web-renderer html --csp
```

## Adding to Chrome Extension
Follow the following steps:

### 1. Open `chrome://extensions`
Or if you are using edge then `edge://extensions`

Enable **Developer Mode**

### 2. Load Unpacked
Click on load unpacked and open the `build/web` folder

## 🥳 Your extension is now avaialable!!