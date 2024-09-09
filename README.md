# CURSO: APRENDE BLAZOR

# LECCIÓN 32: Servicio NavigationManager (Parte 3)

1. Abrir la aplicación con Visual Studio 2022 o VSCode

2. Cómo obtener los "query string parameters" de una ruta 

Primero obtenemos la ruta del componente y la guardamos en la variable uri, y porsteriomente obtenemos la querystring de la variable uri y mostramos el valor del parámetro en un elemento HTML paragraph

```razor
@page "/"
@* Example URL: https://localhost:7246/?id1=125&id2=300 *@

@inject NavigationManager Navigation

<p>Query Parameter 1 Value: @queryParam1</p>
<p>Query Parameter 2 Value: @queryParam2</p>

@code {
    string? queryParam1;
    string? queryParam2;

    protected override void OnInitialized()
    {
        var uri = new Uri(Navigation.Uri);
        var query = Microsoft.AspNetCore.WebUtilities.QueryHelpers.ParseQuery(uri.Query);

        // Get the value of "id1" from the query parameters
        if (query.TryGetValue("id1", out var value1))
        {
            queryParam1 = value1;
        }

        // Get the value of "id2" from the query parameters
        if (query.TryGetValue("id2", out var value2))

        {
            queryParam2 = value2;
        }
    }
}
```
