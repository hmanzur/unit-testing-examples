# React + Vitest Examples

## Componente usa React Router

```javascript
const RouterComponent = () => (
  <Routes>
    <Route path="/" element={<div>Inicio</div>} />
    <Route path="/about" element={<div>Acerca de</div>} />
  </Routes>
);
```

Prueba de ejemplo

```javascript
import { render, screen } from "@testing-library/react";
import { describe, it, expect } from "vitest";
import RouterComponent from "@components/RouterComponent";

describe("@components/RouterComponent", () => {
  it("Monta el componente correctamente", () => {
    render(
      <MemoryRouter initialEntries={["/about"]}>
        <RouterComponent />
      </MemoryRouter>
    );
    expect(screen.getByText("Acerca de")).toBeDefined();
  });
});
```

Prueba de ejemplo con diferentes opciones al renderizar

```javascript
import { afterEach, beforeEach, describe, expect, it, vi } from 'vitest';
import { describe, it, expect } from "vitest";
import RouterComponent from "@components/RouterComponent";

const TestComponent = (initialEntries = ["/about"]) => {
  return (
    <MemoryRouter initialEntries={initialEntries}>
      <RouterComponent />
    </MemoryRouter>
  )
}

describe("@components/RouterComponent", () => {
  beforeEach(() => {
    cleanup();
  });

  afterEach(() => {
    vi.clearAllMocks();
  });

  it("Monta el componente correctamente", () => {
    render(<TestComponent />);
    expect(screen.getByText("Acerca de")).toBeDefined();
  });

  it("Monta el componente correctamente con otro valor", () => {
    render(<TestComponent initialEntries={["/"]} />);
    expect(screen.getByText("Inicio")).toBeDefined();
  });
});
```
