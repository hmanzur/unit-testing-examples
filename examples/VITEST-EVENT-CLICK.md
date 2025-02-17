# React + Vitest Examples

## Componente hace click

Sí, es el más básico de todos pero de malas.

```javascript
const ClickComponent = () => {
  const [clicked, setClicked] = useState(false);
  return (
    <button onClick={() => setClicked(true)}>
      {clicked ? "Clickeado" : "Haz clic"}
    </button>
  );
};
```

Prueba de ejemplo

```javascript
import { render, screen } from "@testing-library/react";
import { describe, it, expect } from "vitest";
import ClickComponent from "@components/ClickComponent";

describe("@components/ClickComponent", () => {
  it("Monta el componente correctamente", () => {
    render(<ClickComponent />);
    const button = screen.getByText("Haz clic");

    fireEvent.click(button);
    expect(screen.getByText("Clickeado")).toBeDefined();
  });
});
```
