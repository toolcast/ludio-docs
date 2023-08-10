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

The `start` method will render an entry point and later the actual ludio player inside a a shadow root, to make sure ludio styles won't conflict with your page styles.

### BI Logger

We provide an API to inject your own BI Logger to collect analytics data about the guide using the `biLogger` prop:

```js
  ludio.start({
     configId: "yourGuideIdHere",
     apiKey: "yourApiKeyHere",
     biLogger: {
      clickedReplay: (data) => {},
      clickedPlay: (data) => {},
      ...
    }
  })
```

The following events are supported. Note "toolcast" is how we call a single step in a guide.

Event name to data mapping:

```typescript
declare type IAnalyticsEventsDataMapping = {
  clickedReplay: {
    minutes?: number;
    stepIdentifier?: string;
  };
  clickedPlay: {
    stepIdentifier?: string;
  };
  exitDoItWithMeFromUnsupportedElementModal: {
    stepIdentifier?: string;
  };
  toolcastTryToLoad: {
    stepIdentifier?: string;
  };
  controllerChangePlaybackSpeed: {
    playRate?: string;
    stepIdentifier?: string;
  };
  guideTryToLoad: {};
  clickedOnUnsupportedElement: {
    elementSelector?: string;
    stepIdentifier?: string;
  };
  controllerChangeVolumeSlider: {
    stepIdentifier?: string;
  };
  controllerJumpBackward: {
    stepIdentifier?: string;
  };
  completedGoal: {
    goalName?: string;
    stepIdentifier?: string;
  };
  clickedOnTranscript: {
    clickedToOpen?: boolean;
    stepIdentifier?: string;
  };
  controllerJumpForward: {
    stepIdentifier?: string;
  };
  controllerMute: {
    configIdentifier?: string;
    stepIdentifier?: string;
  };
  clickedMainExitButton: {
    stepIdentifier?: string;
  };
  clickedOnGoals: {
    clickedToOpen?: boolean;
    stepIdentifier?: string;
  };
  controllerUnmute: {
    stepIdentifier?: string;
  };
  clickedOnSubtitle: {
    clickedToOpen?: boolean;
    stepIdentifier?: string;
  };
  resumeToolcastFromUnsupportedElementModal: {
    stepIdentifier?: string;
  };
  startedGuide: {};
  errorMessagePopUp: {
    errorData?: string;
    errorType?: string;
    stepIdentifier?: string;
  };
  toolcastEnded: {
    stepIdentifier?: string;
  };
  clickedPause: {
    minutes?: number;
    stepIdentifier?: string;
  };
  completedGuide: {};
  startedANewToolcast: {
    stepIdentifier?: string;
  };
};
```
