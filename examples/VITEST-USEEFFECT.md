# React + Vitest Examples

## Componente con useEffect

Implementación difícil de probar

```javascript
const UserProfile = () => {
  const [user, setUser] = useState(null);

  useEffect(() => {
    fetch("/api/user")
      .then((res) => res.json())
      .then((data) => setUser(data))
      .catch((error) => console.error(error));
  }, []);

  if (!user) return <p>Cargando...</p>;

  return <div>{user.name}</div>;
};
```

Implementación correcta del componente

```javascript
const useUser = (fetcher = fetch) => {
  const [user, setUser] = useState(null);

  useEffect(() => {
    fetcher("/api/user")
      .then((res) => res.json())
      .then((data) => setUser(data))
      .catch((error) => console.error(error));
  }, [fetcher]);

  return user;
};

const UserProfile = ({ fetcher }) => {
  const user = useUser(fetcher);

  if (!user) return <p>Cargando...</p>;

  return <div>{user.name}</div>;
};
```

Prueba de ejemplo

```javascript
import { render, screen, waitFor } from "@testing-library/react";
import { describe, it, expect, vi } from "vitest";
import UserProfile from "@hooks/UserProfile";

describe("@components/UserProfile", () => {
  it("Monta el componente correctamente", async () => {
    const mockFetch = vi.fn(() =>
      Promise.resolve({
        json: () => Promise.resolve({ name: "Juan Pérez" }),
      })
    );

    render(<UserProfile fetcher={mockFetch} />);

    await waitFor(() => expect(screen.getByText("Juan Pérez")).toBeDefined());
  });
});
```
