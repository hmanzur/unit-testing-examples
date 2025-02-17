# Node Built In Test

## Axios

```javascript
import axios from "axios";

export const apiClient = axios.create({
  baseURL: "https://api.example.com",
  timeout: 5000,
});

export async function fetchUser(userId) {
  const response = await apiClient.get(`/users/${userId}`);
  return response?.data;
}
```

```javascript
import { describe, it, expect, vi } from "vitest";
import { apiClient, fetchUser } from "@plugins/axios";

describe("@plugins/axios", () => {
  it("fetchUser debería hacer una petición GET y devolver los datos", async () => {
    vi.mocked(axios.get).mockResolvedValue({
      data: { id: 123, name: "John Doe" },
    });

    const user = await fetchUser(123);

    // Validar el resultado
    expect(user).toStrictEqual({ id: 123, name: "John Doe" });
  });
});
```
