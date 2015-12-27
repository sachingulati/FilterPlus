# DOM-Unity

DOM-Unity is a jQuery plugin. The basic idea revolves around unifying the DOM elements on page.

### Basic Terminologies: 
1. **Namespace**: Default namespace of this application is `du`. This is modifiable.
2. **Prefix**: Information like group name, event, etc for an element can be provided in class attribute of that element. For that class names goes like this: `[namespace]-[prefix]-[information]`. Example: <input type='text' class='du-group-groupName' id='attributeName'/>. 
Prefixes are stored in prefix json object. Prefixes are modifiable. But use it with caution.
3. **Groups:** DOM elements playing any role in functioning are provided group(s). Events trigger by any of such elements trigger the event on group(s) associated with them and they collectively perform some action. 
Default prefix for group is `group`. Example: du-group-groupName. 
Example usecase: searching or filtering a list based on search parameters such as name, country, etc. Every group has group object which has properties associated with that group only
4. **Event:** Events in application are jQuery events, events can also be custom jquery events. You can add any number of events. Default events are keyup and change, you can change default events of application/group using `events` property. You can also specify event for an element with prefix. Default prefix for event property is `event`. Example: du-event-click.
Events added with prefix are in addition with default or group events. if you want to remove any default event from an element you can do it with `no-event` prefix. Example: du-no-event-change 
After updating events you will have to re-initialize that element, group or application as per the scope of that event using `initEvents()`. 
Events are associated with name: `[event name].[namespace]`. Example: click.du

### Plugin Properties summary: 
> All properties specified here are modifiable by user. 
> Group properties if specified in group objects, override Global properties

###### Global Properties:

| Property Name | Type | Overview |
| ------------- | ---- | -------- |
| config | object/function  | User Defined configs, this overrides default configs |
| data | object/function  | this is additional data which is also sent with every request, this is overrided by element values on page and importantData |
| getConfig | function | returns all configurations including default config |
| getConfig(groupName) | function | returns all configurations including default config of group |
| getElements | function | returns all elements associated with any group on page |
| getElements(groupName) | function | returns all elements associated with group specified |
| getGroupNames | function | returns all group names on page |
| getGroupNames(element) | function | returns group names associated with element |
| getGroups | function | returns all group objects on page |
| getGroups(element) | function | returns all group objects associated with element. |
| importantData | object/function  | Same as data, this is additional data which is also sent with every request, this overrides element values on page and data |
---


###### Group Properties:

| Property Name | Type | Overrides | Overview |
| ------------- | ---- | --------- | -------- |
| config | object/function | config | User Defined configs |
| data | object/function  | data | this is additional data which is also sent with every request, this is overrided by element values on page and importantData |
| getElements | function | --- | get all elements associated with group |
| importantData | object/function | importantData | Same as data, this is additional data which is also sent with every request, this overrides element values on page and data |

---

### Private properties summary:

> These are private properties of plugin which are not accessible to user. But these can be modified by modifying plugin code (not recommended).

###### Global Properties:

| Property Name | Type | Overview |
| ------------- | ---- | -------- |
| apiInstance | object | plugin instance for internal use |
| defaultConfig | object/function | default configs of plugin |
| init | function | initializes the plugin on $(document).ready() |
| getClassInfo(element, prefix) | function | extracts the information from class attribute of element and returns array of String. i.e. group name, event name, etc. |
| getJsonObject(object) | function | returns json object, argument object can be a json object or a function which returns json object |
| merge(objArray) | function | objArray is an array of json objects or function which returns json object, this function returns merged json object. |
| namespace | String | namespace used in application, default value is `du` |
| requestNum | object | this is a map which stores groupName as key and request number as its value, used for rendering latest requests only.

---

###### Group Properties:

| Property Name | Type | Overview |
| ------------- | ---- | -------- |

---
