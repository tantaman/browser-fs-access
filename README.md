# Browser-NativeFS

This module allows you to either use the
[Native File System API](https://wicg.github.io/native-file-system/) on supporting browsers,
with a transparent fallback to the `<input type="file">` and `<a download>` legacy methods.

## Usage

The module feature-detects support for the Native File System API and
only loads the actually relevant code.

```js
import {
  fileOpen,
  fileSave,
} from 'https://unpkg.com/browser-nativefs';

(async () => {
  // These methods will use the Native File System API or a fallback implementation.

  // Open a file.
  const blob = await fileOpen({mimeTypes: ['image/*']});
  // Open multiple files
  const blobs = await fileOpen({mimeTypes: ['image/*'], multiple: true});
  // Save a file.
  await fileSave(blob, {fileName: 'Untitled.png'});
})();
```

## API

```js
const options = {
  mimeTypes: ['image/*'],
  extensions: ['png', 'jpg', 'jpeg', 'webp'],
  multiple: true,
  description: 'Image files',
};
const blobs = await fileOpen(options);
```

```js
const options = {
  fileName: 'Untitled.txt',
};
await fileSave(someBlob, options);
```

## License

Apache 2.0.
