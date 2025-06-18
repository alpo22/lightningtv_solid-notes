Handling focus in LightningJS with SolidJS involves managing which element is "active" at any given time and how user input (like remote control presses) interacts with it. Only one element has focus at any given time, known as the active element, and this creates a "focus path" up through its parent elements.

Here are concise instructions for focus handling:

**I. Setting Initial Focus**

- **`autofocus`**: Apply this prop to a single element on a page to automatically give it initial focus when the page loads. It can also take a SolidJS signal to dynamically control when focus is applied.
- **`setFocus()`**: Programmatically call `setFocus()` on an element to give it focus.

**II. Moving Focus (Navigation)**

- **Row & Column Components**:
  - The `<Row>` component automatically manages horizontal focus changes among its children using `onLeft` and `onRight` key presses.
  - The `<Column>` component handles vertical focus changes among its children with `onUp` and `onDown` key presses.
  - These components have a `selected` property (an index) to track the currently focused child.
- **Key Handlers on Elements**:
  - Use `onEnter`, `onLeft`, `onRight`, `onUp`, `onDown` props directly on `<View>` or `<Text>` components to handle specific key presses when that element is focused.
  - Key events "bubble up" the DOM tree; if a child doesn't handle a key event (by returning `false`), its parent will attempt to handle it.
- **`useFocusManager` Hook**: This hook, typically in your `App.tsx`, sets up the main key event handling, mapping specific keys (e.g., 'a' for Announcer, Arrow keys for navigation) to global callbacks.

**III. Controlling Focus Behavior**

- **`forwardFocus`**: On a parent element, this prop directs focus to a specific child instead of the parent itself. It's a performance optimization that changes focus before blur/focus events are called on intermediate elements. You can set it to a number (the child's index) or a function.
- **`skipFocus`**: Add this prop to a child component within a `Row` or `Column` to prevent it from receiving focus during navigation. The `Row`/`Column` will skip over it to the next eligible child.
- **`onSelectedChange` (on Row/Column)**: This callback is triggered when the selected child within a `Row` or `Column` changes, providing the new selected index and active element. Useful for updating UI based on the selected item.

**IV. Reacting to Focus Changes (Visuals & Logic)**

- **`onFocus`**: A callback function executed when an element receives focus.
- **`onBlur`**: A callback function executed when an element loses focus.
- **`onFocusChange`**: A versatile callback that fires on both focus and blur. It receives a boolean argument (`true` for focus, `false` for blur). This is particularly useful with SolidJS signals to dynamically update an element's properties based on its focus state.
- **Styling with `focus` and `transition`**:
  - Within an element's `style` object, define a `focus` property (e.g., `focus: { alpha: 1, scale: 1.1 }`) to apply styles when the element receives focus.
  - Use the `transition` property within the `style` object (e.g., `transition: { alpha: true, scale: true }`) to smoothly animate changes to specified properties when focus is gained or lost. The default values for the animated properties (e.g., `alpha: 0.8`, `scale: 1`) must be set in the main `style` object.

**V. Debugging Focus**

- **`Config.focusDebug`**: Set this flag to `true` in your `index.tsx` configuration to display a visual border around the currently focused element and its focus path. (Note: A source indicates a temporary bug might affect its functionality.)
- **Browser Inspector**: In the console, you can select an element in the inspector (`$0`) and access its underlying Lightning node using `$0.element` to inspect or manipulate its properties directly.
