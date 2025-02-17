# React + Vitest Examples

## Componente usa un contexto

```javascript
const TestContext = createContext({ value: "default" });

const ContextComponent = () => {
  const { value } = useContext(TestContext);
  return <div>{value}</div>;
};
```

Prueba de ejemplo

```javascript
import { render, screen } from "@testing-library/react";
import { describe, it, expect } from "vitest";
import UserProfile from "@hooks/UserProfile";

describe("@components/ContextComponent", () => {
  it("Monta el componente correctamente", () => {
    render(
      <TestContext.Provider value={{ value: "contexto activo" }}>
        <ContextComponent />
      </TestContext.Provider>
    );
    expect(screen.getByText("contexto activo")).toBeDefined();
  });
});
```

Prueba de ejemplo con diferentes opciones al renderizar

```javascript
import { afterEach, beforeEach, describe, expect, it, vi } from 'vitest';
import { describe, it, expect } from "vitest";
import UserProfile from "@hooks/UserProfile";

const TestComponent = (value) => {
  return (
    <TestContext.Provider value={value}>
      <ContextComponent />
    </TestContext.Provider>
  )
}

describe("@components/ContextComponent", () => {
  beforeEach(() => {
    cleanup();
  });

  afterEach(() => {
    vi.clearAllMocks();
  });

  it("Monta el componente correctamente", () => {
    render(<TestComponent value={ value: "contexto activo" } />);
    expect(screen.getByText("contexto activo")).toBeDefined();
  });

  it("Monta el componente correctamente", () => {
    render(<TestComponent value={ value: "contexto inactivo" } />);
    expect(screen.getByText("contexto inactivo")).toBeDefined();
  });
});
```
