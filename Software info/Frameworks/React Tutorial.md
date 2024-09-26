## DOM
![[Pasted image 20230614132343.png]]
## Thinking in React component

To build applications with React, we think of the user interface as a bunch of encapsulated, isolated, and reusable code snippets called components.
![[Pasted image 20230614130851.png]]
1. **TodoApp**: the parent or root component. It holds two direct child components.
2. **Header**: display the todos heading text.
3. **TodosLogic**: contains the application logic. It includes two direct child components.
4. **InputTodo**: will take the user’s input.
5. **TodosList**: serves as a container for the todos items.
6. **TodoItem**: renders the individual todos item.

## Props

‘Prop’ is shorthand for properties, and this is the one source of data in our component. It can be used to pass data to different components


## Event Listeners

In React, event listeners are like ears that listen to what you do on a web page. When you interact with something, like clicking a button or typing on a keyboard, the event listener hears it and can do something in response.

For example, let's say you have a button on a web page. When you click that button, you want something to happen, like showing a message. The button has an event listener attached to it, and when you click it, the event listener hears the click and does what it's supposed to do.

```javascript
function MyComponent() {
  const handleClick = () => {
    // This is what happens when the button is clicked
    alert("Button clicked!");
  };

  return (
    <button onClick={handleClick}>Click me</button>
  );
}
```

In this example, the `handleClick` function is the event listener. It listens for the `onClick` event, which happens when the button is clicked. When the button is clicked, the `handleClick` function is called, and it shows an alert message saying "Button clicked!".

## State

A state is like a special place where the component keeps important information. This information can change over time, just like how the toy car can go from being parked to moving.

Let's say we have a component that shows a counter on a web page. The counter can start at 0 and go up by 1 each time you click a button. The state of the component keeps track of the current number on the counter.

```js
import React, { useState } from 'react';

function Counter() {
  // setState(updater, [callback])
  const [count, setCount] = useState(0);
  
  const handleButtonClick = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={handleButtonClick}>Click me</button>
    </div>
  );
}
```

In this example, the state is represented by the `count` variable. It starts at 0 because that's the initial state. Whenever you click the button, the `handleButtonClick` function is called, and it updates the state by adding 1 to the current count using the `setCount` function.

The updated state is then shown on the web page as the new count.

So, in simple terms, state in React is like the different states of a toy car. It's a special place where a component keeps important information that can change over time. Just like you can make your toy car move or stop, components in React can have different states that can change and affect what you see on the web page.

*setState is asynchronus*

## Modal

In React, a modal refers to a component or UI element that is typically used to display content or interact with the user in a pop-up window or overlay. Modals are commonly used for displaying additional information, capturing user input, or confirming actions.

Modal components are designed to appear on top of the rest of the application's content, creating a temporary overlay that focuses the user's attention on the modal itself. They often have a distinct appearance, such as a centered window with a backdrop that obscures the background content, indicating that the modal is the primary focus.

Modals in React can be created using a combination of React components, state management, and CSS. The modal component typically encapsulates its content and provides functionality for opening, closing, and handling user interactions within the modal.

Here's a simplified example of a modal component in React:

```jsx
import React, { useState } from 'react';

function Modal() {
  const [isOpen, setIsOpen] = useState(false);

  const openModal = () => {
    setIsOpen(true);
  };

  const closeModal = () => {
    setIsOpen(false);
  };

  return (
    <div>
      <button onClick={openModal}>Open Modal</button>

      {isOpen && (
        <div className="modal">
          <div className="modal-content">
            <h2>Modal Content</h2>
            <p>This is the content of the modal.</p>
            <button onClick={closeModal}>Close</button>
          </div>
        </div>
      )}
    </div>
  );
}

export default Modal;

```

In this example, the `Modal` component maintains its own state with the `isOpen` variable. When the user clicks the "Open Modal" button, the `openModal` function is called, setting `isOpen` to `true` and rendering the modal content. The modal is closed by calling the `closeModal` function, which sets `isOpen` to `false`.

The CSS classes `modal` and `modal-content` define the appearance and positioning of the modal. These classes can be customized to achieve the desired styling.

Please note that this is a basic example, and in practice, modal components may have additional features like passing and manipulating data, handling animations, or incorporating accessibility considerations. Various libraries, such as react-modal or Material-UI, provide pre-built modal components with additional features and customization options.