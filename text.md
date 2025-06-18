For the `<Text>` component in LightningJS with SolidJS, you can use the following key properties (props):

**I. Text Content & Styling**

- **`children`**: The actual text content to be displayed within the `<Text>` component.
- **`fontFamily`**, **`fontStyle`**, **`fontWeight`**, **`fontSize`**: Control the font characteristics.
- **`color`**: Sets the text color.
- **`lineHeight`**: Defines the height of the rendered text.
- **`textAlign`**: Aligns the text horizontally within its container (e.g., `'center'`, `'right'`, `'left'`).
- **`contain`**: Controls text wrapping and truncation. Use `'width'` for wrapping and `'both'` for truncation with ellipses (`...`).

**II. Positioning & Layout**

- **`x`**, **`y`**: Position of the text relative to its parent container.
- **`width`**, **`height`**: Dimensions of the text element. In flex containers, `width` can be auto-calculated based on content.
- **`marginLeft`**, **`marginRight`**: Used for padding around the text, especially within flex containers. `margin` can also be used for individual elements within a flex container.

**III. Default Settings (via `Config.fontSettings` in `index.tsx`)**

- **`Config.fontSettings.fontFamily`**: Sets a default font for all `<Text>` nodes.
- **`Config.fontSettings.color`**: Sets a default color for all `<Text>` nodes.
- **`Config.fontSettings.fontSize`**: Can set a default font size.

**IV. Other Properties**

- **`style`**: Accepts an object to group styling properties for the `<Text>` component, similar to CSS. Styles in the `style` object act as defaults and can be overridden by direct props.
- **`announce`**: Provides text for screen readers, useful for accessibility.
- **`id`**: A string identifier for debugging.
- **`data`**: An object prop to add `data-` attributes for debugging.
- **`ref`**: Used to get a direct reference to the underlying Lightning element.

Since `<Text>` is a primitive node like `<View>`, properties like `alpha`, `scale`, `borderRadius`, and focus-related properties (`onFocus`, `onBlur`, `focus` within `style`, `transition`) generally also apply to `<Text>` as they are handled by the underlying renderer.
