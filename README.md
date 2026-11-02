# React Components in TypeScript

This project shows how to convert two React components from JavaScript to
TypeScript. Save files that contain JSX with the `.tsx` extension.

## Conversion steps

1. Use `.tsx` files so TypeScript can check both the component code and JSX.
2. Define a props interface for `Greeting` to specify that `name` is a string.
3. Define a state interface for `Counter` and pass it to `Component` as its
   state type.
4. Update the counter with the functional form of `setState`, which uses the
   latest state value.
5. Keep `return (` together in `render`; a line break after `return` can cause
   JavaScript to return early.

## Code 01: Greeting

Save as `Greeting.tsx`:

```tsx
import React from 'react';

// Describes the props that must be passed to Greeting.
interface GreetingProps {
  name: string;
}

const Greeting: React.FC<GreetingProps> = ({ name }) => {
  return <div>Hello, {name}!</div>;
};

export default Greeting;
```

## Code 02: Counter

Save as `Counter.tsx`:

```tsx
import React, { Component } from 'react';

// Describes the state managed by Counter.
interface CounterState {
  count: number;
}

class Counter extends Component<{}, CounterState> {
  // Initialize the counter when the component is created.
  state: CounterState = {
    count: 0,
  };

  // Use the latest state value when incrementing the counter.
  increment = () => {
    this.setState((previousState) => ({
      count: previousState.count + 1,
    }));
  };

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}

export default Counter;
```
