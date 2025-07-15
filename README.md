# GardenAPP

La aplicación GardenApp tiene algunos errores que deben ser corregidos:

1- En la lista no se muestra correctamente la imagen de cada planta (2 puntos)

2- No importa que planta seleccione siempre se accede a la misma (2 puntos)

3- El buscador no muestra ningun resultado (2 puntos)

4- Los textos donde deberian mostrarse los cuidados de la planta no son correctos (2 puntos)

5- El color de la barra de navegacion en el detalle no es el correcto (2 puntos)


## ✅ Correcciones implementadas

### 1. Imagen de planta no se mostraba correctamente
- ❌ Se usaba un `painterResource` fijo (`R.drawable.i008`) para todas las plantas.
- ✅ Solución: se utilizó `planta.ilustrationId` para mostrar la imagen correspondiente a cada planta individualmente.

### 2. Siempre se accedía a la misma planta en el detalle
- ❌ Aunque se seleccionara una planta diferente, siempre se mostraban los datos del Lirio.
- ✅ Solución: se paso de usar siempre el detalle del lirio: 
`uiState = DetalleEstado.Resultado(cuidado = repositorio.cuidadoLirio)`
a mostrar el de la planta seleccionada:
`uiState = DetalleEstado.Resultado(cuidado = planta) `

### 3. El buscador no mostraba ningún resultado
- ❌ El uiState se actualizaba con una lista vacía en todos los casos.
- ✅ Solución: se modifico el uiState para no retornar siempre un emptyState
  `uiState = PlantasEstado.Resultado(searchResult,searchText)`

### 4. Los textos de cuidados estaban incorrectos
- ❌ En PrediccionView(...), se mostraba un texto hardcodeado: "aca deberia haber un texto no harcodeado".
- ✅ Solución: se reemplazó por el valor dinámico que viene en el parámetro descripcion

`Text(
modifier = Modifier
.fillMaxWidth(),
style = MaterialTheme.typography.bodyMedium,
text = descripcion
)`

### 5. El color de la barra de navegación en el detalle era incorrecto
- ❌ Se usaba tertiaryContainer, distinto al de la pantalla principal.
- ✅ Solución: se unificó con primaryContainer y se aplicó también a la flecha de retroceso.

## 🎥 Demo

![Demo de GardenApp](demo.gif)
