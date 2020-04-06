# Wattwin Web Widget

##### Table of Contents

<!-- GEN:toc -->
- [Usage](#usage)
- [class: Application](#class-application)
<!-- GEN:stop -->

## Usage

Add the widget script tag at your page:

```js
<script type="text/javascript" src="SCRIPT_URL"></script>
```

Set the required attributes of the widget and instantiate the class:

```js
var params = {
   accessToken: "API_KEY",
   wizardCode: "WIZARD_CODE"
};
```

- `params` <[Object]>
  - `accessToken` <[string]> the API key to use the widget.
  - `wizardCode` <[string]> the code of the desired wizard to load.
  - `environment` <?[string]> Wattwin application environment.
  - `containerId` <?[string]> HTML div to attach the iframe.
  - `locatorCode` <?[string]> Locator to load a previous saved application.
  - `clientApplication` <?[Application]> Client application data to preload the wizard.
  - `backgroundStyles` <?[Object]> Optional background styles.
    - `background` <?[string]> Optional background color.
    - `backgroundImage` <?[string]> Optional background image url.
    
```js
const widget = new Wattwin.WizardWidget(params);
```

Initialize the widget giving the HTML div where to place the Wattwin widget content.

```js
widget.initWidget("widget-class");
```

## Listen the app events

The widget emits various events (described below) which can be handled using the native addEventListener from **javascript**. The data of the event is inside of `event.detail`.

```js
window.addEventListener("wizard.completed", event => {});
```

- event: **widget.error**

Emitted when the widget fails in any internal call. Returns the error text.

- event: **wizard.ready**

Emitted when the wizard has done all the preparations. Returns the wizard attributes.

- event: **save.application**

Emitted when the user goes to the next step and the application its saved. Returns the saved application.

- event: **wizard.step**

Emitted when the user goes to another step. Returns the name of the step.

- event: **wizard.completed**

Emitted when the user submit the last step of the wizard. Returns the saved application.

### class: Application
- `address` <?[string]> Client address.
- `addressNumber` <?[string]> Client address number.
- `documentNumber` <?[string]> Client document number.
- `documentType` <?[string]> Client document format: (`dni`, `nif`, `nie`, `passport`).
- `door` <?[string]> Client address door.
- `email` <?[string]> Client contact email.
- `floor` <?[string]> Client address floor.
- `lastName` <?[string]> Client lastname if it's an individual.
- `locatorCode` <?[string]> Locator of the application.
- `name` <?[string]> Client name.
- `phoneNumber` <?[string]> Client contact phone.
- `postalCode` <?[string]> Client address postal code.
- `province` <?[string]> Client address province.
- `town` <?[string]> Client address town.
- `notes` <?[string]> Client notes.
- `referenceId` <?[string]> External id.
- `powerPlantData` <?[Object]> Power plant attributes.
    - `supplyPoint` <?[Object]> Client supply point attributes.
        - `contractedPower` <?[number]> Client contracted power.
        - `cups` <?[string]> Client cups number.
        - `tariffName` <?[string]> Client contracted tariff name.
        - `totalConsumption` <?[number]> Client consumption in kWh/year.
    - `map` <?[Object]> Map properties.
        - `coordinates` <?[Coordinate]> Coordinates object of the google marker point.
        - `elevation` <?[number]> Elevation of the given coordinate.
        - `surfaceCoordinates` <?[Array]> Array of every drawn area points.

### class: Coordinate
- `lat` <[string]>
- `lng` <[string]>

[Object]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object "Object"
[Array]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array "Array"
[boolean]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#Boolean_type "Boolean"
[string]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#String_type "String"
[number]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#Number_type "Number"
[Application]: #class-application "Application"
[Coordinate]: #class-coordinate "Coordinate"