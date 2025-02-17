# React + Vitest Examples

## Componente usa estados

Sí, es el más básico de todos pero de malas.

```javascript
const StateComponent = () => {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Contador: {count}</p>
      <button onClick={() => setCount(count + 1)}>Incrementar</button>
    </div>
  );
};
```

Prueba de ejemplo

```javascript
import { render, screen } from "@testing-library/react";
import { describe, it, expect } from "vitest";
import StateComponent from "@components/StateComponent";

describe("@components/StateComponent", () => {
  it("actualiza el estado al hacer clic", () => {
    render(<StateComponent />);
    const button = screen.getByText("Incrementar");

    expect(screen.getByText("Contador: 0")).toBeDefined();

    fireEvent.click(button);
    expect(screen.getByText("Contador: 1")).toBeDefined();
  });
});
```
