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
import { test, mock } from "node:test";
import assert from 'node:assert/strict';
import { apiClient, fetchUser } from "#plugins/axios";

test("fetchUser debería hacer una petición GET y devolver los datos", async () => {
  // Simular `apiClient.get`
  mock.method(apiClient, "get", async (url) => {
    assert.strict(url, "/users/123"); // Verificar que la URL es la correcta
    return { data: { id: 123, name: "John Doe" } };
  });

  // Ejecutar la función y validar el resultado
  const user = await fetchUser(123);
  assert.strict(user.id, 123);
  assert.strict(user.name, "John Doe");
});
```
