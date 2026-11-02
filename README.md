# Práctica de XR Interaction Toolkit - Cambio de Color y UI

Breve descripción de la práctica realizada en Unity para configurar un entorno de Realidad Virtual con interacciones a distancia (Ray Interactor) y de proximidad (Direct Interactor).

## Descripción de lo que hemos hecho
1. **Configuración del entorno y URP:** Vinculación del Render Pipeline Asset (`PC_RPAsset` y `PC_Renderer`) y limpieza de errores en la consola.
2. **Sistema de Jugador XR:** Sustitución de la cámara por defecto por el prefab `XR Origin (XR Rig)` y conexión con el `XR Interaction Manager`.
3. **Interacción por Rayo (Ray Interactor):** Creación de un cubo y una esfera que detectan el puntero láser y cambian de color mediante eventos al seleccionarlos y soltarlos.
4. **Interacción Directa (Direct Interactor) y UI:** Configuración de un objeto interactuable cercano que actualiza un texto en un Canvas de tipo World Space al ser agarrado físicamente por el usuario.

## Códigos utilizados

### CambioColor
```csharp
using UnityEngine;

public class CambioColor : MonoBehaviour
{
    public Color colorSeleccionado = Color.red;

    private Renderer rend;
    private Color colorOriginal;

    void Start()
    {
        rend = GetComponent<Renderer>();
        colorOriginal = rend.material.color;
    }

    public void Seleccionado()
    {
        rend.material.color = colorSeleccionado;
    }

    public void Soltado()
    {
        rend.material.color = colorOriginal;
    }
}
```

### UIText
```csharp
using UnityEngine;
using TMPro;

public class ActualizarUI : MonoBehaviour
{
    public TMP_Text texto;

    public void Agarrado()
    {
        texto.text = "Objeto agarrado";
    }

    public void Soltado()
    {
        texto.text = "Nada agarrado";
    }
}
```

## Ejemplo de funcionamiento
![gif](https://github.com/guillrl1/XR-Interaction-Toolkit/blob/main/gifs/PracticaVR.gif)
