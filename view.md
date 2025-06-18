For a `<View>` component in LightningJS with SolidJS, you can add various properties (props) to control its appearance, position, layout, and behavior. These props are largely passed directly to the Lightning 3 renderer.

Here are the key props:

**I. Positioning & Layout**

- **`x`**, **`y`**: Position relative to the parent's top-left (0,0). Overridden by flex layout.
- **`width`**, **`height`**: Dimensions of the View. Can be auto-calculated by flex.
- **`right`**, **`bottom`**: Position relative to parent's right/bottom edge, implicitly setting `mount` to 1.
- **`mount`**, **`mountX`**, **`mountY`**: Define the origin point (0 to 1) for the View's coordinates within itself.
- **`center`**, **`centerX`**, **`centerY`**: Shortcuts to center the View within its parent.
- **`display: 'flex'`**: Enables Flexbox layout for children.
- **`flexDirection`**: Sets the main axis for flex children (e.g., `'row'`, `'column'`).
- **`gap`**: Spacing between direct children in a flex container.
- **`justifyContent`**: Aligns children along the main flex axis (e.g., `'flexStart'`).
- **`alignItems`**: Aligns children along the cross-flex axis (e.g., `'center'`, `'flexEnd'`).
- **`padding`**: Internal spacing around content in a flex container.
- **`margin`**: Applied to child elements in a flex container for spacing (e.g., `marginLeft`, `marginRight`).
- **`onLayout`**: Callback function triggered after layout completion, providing the element.

**II. Visual & Styling**

- **`color`**: Sets background color (e.g., `"#4169e1"`).
- **`borderRadius`**: Applies rounded corners.
- **`alpha`**: Controls transparency (0 to 1).
- **`scale`**: Adjusts size (e.g., `1.1` for 10% larger).
- **`style`**: Accepts an object of styling properties (e.g., `width`, `height`, `color`, `borderRadius`, `alpha`, `scale`, `display`, `gap`, `flexDirection`, `justifyContent`, `alignItems`, `padding`, `margin`, `transition`, `focus`). Properties in `style` can be overridden by direct props.
- **`focus`** (within `style`): Defines styles to apply when the View receives focus (e.g., `alpha: 1`, `scale: 1.1`).
- **`transition`** (within `style`): Specifies properties to animate smoothly (e.g., `{ alpha: true, scale: true }`).

**III. Interactivity & Focus**

- **`autofocus`**: Automatically sets focus to the element upon creation or page load. Only one element per page should have it. Can accept a signal for dynamic focusing.
- **`onEnter`**: Key handler triggered on "Enter" key press when focused.
- **`onLeft`**, **`onRight`**, **`onUp`**, **`onDown`**: Key handlers for directional navigation.
- **`onFocus`**: Callback when the View receives focus.
- **`onBlur`**: Callback when the View loses focus.
- **`onFocusChange`**: Callback on both focus and blur, receiving a boolean `true` for focus, `false` for blur.
- **`forwardFocus`**: Directs focus to a specific child element instead of the parent; a performance optimization.
- **`skipFocus`**: Prevents a child View from receiving focus during navigation within a `Row` or `Column`.
- **`onAnnouncer`**: A top-level key handler for toggling accessibility features.

**IV. Other**

- **`{...props}`**: Spreads all incoming props from a parent onto the View, enabling reusability.
- **`ref`**: Obtains a direct reference to the underlying Lightning element.
- **`id`**: String identifier for debugging, visible in the inspector.
- **`data`**: Object prop (e.g., `data={{ key: value }}`) adds `data-` attributes to the underlying HTML element in the inspector for debugging.
- **`announce`**: Provides text for screen readers for accessibility.
