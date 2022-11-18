## Ludio - a better way to onboard

### Usage

Once you have a unique `guideId` and an `apiKey`, you can use our script:

```js
<script src="https://unpkg.com/@ludio/player@^0/dist/main.js" />
```

Once the script is loaded, you access `ludio` globally, and trigger your guide:

```js
ludio.start({ configId: "yourGuideIdHere", apiKey: "yourApiKeyHere" });
```

You can also trigger everything programatically:

```js
const script = document.createElement("script");
script.src = "https://unpkg.com/@ludio/player@^0/dist/main.js";
document.body.appendChild(script);
script.addEventListener("load", function () {
  ludio.start({ configId: "yourGuideIdHere", apiKey: "yourApiKeyHere" });
});
```

The `start` will render an entry point - and later the actual ludio player - inside a a shadow root - to make sure ludio styles won't conflict with your page styles.
