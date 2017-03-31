[![Build Status](https://travis-ci.org/advanced-rest-client/api-designer-nav.svg?branch=stage)](https://travis-ci.org/advanced-rest-client/api-designer-nav)  

# api-designer-nav

A bottom navigation for the API console for the API designer application.

It provides a way to call the main navigation (which is hidden by default),
go to the starting page (probably the summary view for the API), go to "try it"
screen or to pin the current view.

This element is event based and application hosting this element should
handle all events fired by this element. See events docs for more details.

### Example
```
<api-designer-nav></api-designer-nav>
```

The element fires HTML events to inform parent elements(s) or application about
user intention. It doesn't control the flow itself.

In case of API designer, the view displayed in the documentation view (the API
console view area) depends on current user's cursor position and it changes when
user context change (HTTP method viewer will be displayed when the cursor in
the code are is in context of method and so on). To hold current view and
prohibit this behavior the user can use "pin view" option to inform the
application to not change the view until user request it by navigating to
different view.

Application can add it's own actions. Each action element (button, icon etc)
must have `action` attribute to be included in the actions list.

```
<api-designer-nav>
  <button action>Click me!</button>
</api-designer-nav>
```
The "click me" button will be rendered after all primary actions but before
pin action.

See demo page source for complete example of how to implement this element
alongside the `raml-path-selector` with the API designer.

### Styling
`<api-designer-nav>` provides the following custom properties and mixins for styling:

Custom property | Description | Default
----------------|-------------|----------
`--api-designer-nav` | Mixin applied to the element | `{}`
`--api-designer-nav-background-color` | Background color of the bottom navigation | `--anypoint-color-aluminum3`
`--api-designer-nav-tryit-background-color` | The "try it" button backgound color | `--anypoint-color-primary`
`--api-designer-nav-tryit-color` | The "try it" button font color | `--anypoint-color-tertiary`
`--api-designer-nav-icon-color` | Color of the icon buttons | `rgba(0, 0, 0, 0.54)`
`--api-designer-nav-icon-color-active` | Color of the active (toggled) icon button | `--anypoint-color-primary`



### Events
| Name | Description | Params |
| --- | --- | --- |
| api-console-home-requested | Fired when the user click on the "home" button. The application should display default view (probably summary view). | __none__ |
| api-console-menu-opened-changed | Fired when the user toggles the menu. Note that the element will change the icon state whether the app handle the event or not. | value **Boolean** - Current state of the `menuOpened` property. |
| api-console-pinned-state-changed | Fired when the user selectes the "pinner" option. Note that the icon state will change to selected / deselected whether the app handle the event or not. | value **Boolean** - Current state of the `pinned` property. |
| api-console-tryit-requested | Fired when the user click on the "try it" button. The application should read current path / selected object and display the `raml-request-panel` panel view. | __none__ |
