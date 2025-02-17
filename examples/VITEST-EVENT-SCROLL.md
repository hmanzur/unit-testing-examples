# React + Vitest Examples

## Componente hace scroll

Sí, es el más básico de todos pero de malas.

```javascript
const ScrollComponent = () => {
  return (
    <div style={{ height: "200vh" }}>
      <p id="final">Final de la página</p>
    </div>
  );
};
```

Prueba de ejemplo

```javascript
import { act, render, screen } from "@testing-library/react";
import { describe, it, expect } from "vitest";
import ScrollComponent from "@components/ScrollComponent";

describe("@components/ScrollComponent", () => {
  it("Monta el componente correctamente", () => {
    render(<ScrollComponent />);
    act(() => {
      window.scrollTo(0, document.body.scrollHeight);
    });

    expect(screen.getByText("Final de la página")).toBeDefined();
  });
});
```
