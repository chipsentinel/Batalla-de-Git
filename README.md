# Batalla de Git — Trabajo por parejas

## Objetivo

Trabajaréis **dos personas sobre el mismo proyecto de C# utilizando Git**.

El objetivo principal de este ejercicio es practicar:

- Trabajo con un repositorio remoto compartido.
- Clonado de un repositorio.
- Creación y cambio de ramas.
- Commits.
- `push` y `pull`.
- Integración de cambios mediante `merge`.
- Resolución de varios conflictos.
- Trabajo con versiones locales desactualizadas.
- Comprobación del resultado después de cada integración.

> **En este ejercicio queremos que aparezcan problemas y conflictos.**
> Algunos serán provocados intencionadamente para aprender a identificarlos y resolverlos.

---

## Preparación del repositorio

Antes de comenzar debéis preparar un repositorio compartido entre los dos integrantes de la pareja.

1. Uno de los integrantes creará un repositorio en GitHub.
2. Desde `Settings > Collaborators`, añadirá al compañero como colaborador.
3. El segundo integrante deberá aceptar la invitación.
4. Subid el proyecto inicial al repositorio.
5. El segundo integrante deberá clonarlo:

```bash
git clone URL_DEL_REPOSITORIO
```

6. Comprobad que ambos podéis acceder al repositorio.

Durante toda la práctica trabajaréis sobre **el mismo repositorio remoto**, pero cada integrante tendrá su propia copia local.

No debéis intercambiaros archivos para combinar vuestro trabajo. Utilizad Git.

---

## Proyecto inicial

Partid de esta sencilla aplicación:

```csharp
Console.WriteLine("========================");
Console.WriteLine("      EQUIPO DAW");
Console.WriteLine("========================");

string equipo = "Los programadores";
int puntos = 100;
double presupuesto = 50;

Console.WriteLine($"Equipo: {equipo}");
Console.WriteLine($"Puntos: {puntos}");
Console.WriteLine($"Presupuesto: {presupuesto} €");

Console.WriteLine("========================");
Console.WriteLine("       FIN");
Console.WriteLine("========================");
```

---

## Ronda 1 — Cambios sin conflicto

Antes de provocar conflictos, vamos a comprobar que **dos personas pueden trabajar simultáneamente sin generar necesariamente un conflicto**.

Cada integrante crea su propia rama.

### Alumno A

```text
feature/alumno-a
```

### Alumno B

```text
feature/alumno-b
```

El Alumno A añadirá al principio del programa:

```csharp
string alumnoA = "Laura";
Console.WriteLine($"Desarrollador 1: {alumnoA}");
```

El Alumno B añadirá al final:

```csharp
string alumnoB = "Carlos";
Console.WriteLine($"Desarrollador 2: {alumnoB}");
```

Cada alumno realiza un `commit`.

Integrad ambas ramas.

### Pregunta

¿Ha aparecido algún conflicto?
No
¿Por qué Git ha podido integrar automáticamente ambos cambios?
Porque venian de dos ramas distintas y tocamos cosas diferentes. Lo cual no creo conflicto por trabajar exactamente en lo mismo. Tambien hicimos un pull de la rama dev antes de mergear de las feature para asegurarnos.
---

## Ronda 2 — Primer conflicto: mismo texto

Ambos alumnos modificarán esta línea:

```csharp
Console.WriteLine("      EQUIPO DAW");
```

### Alumno A

```csharp
Console.WriteLine("      EQUIPO C#");
```

### Alumno B

```csharp
Console.WriteLine("      DAW DEVELOPERS");
```

Cada alumno realiza su `commit`.

Integrad primero una rama y posteriormente la otra.

Deberá aparecer vuestro **primer conflicto**.

Resolvedlo entre los dos y elegid cuál será el título definitivo.

Ejecutad el programa y comprobad que funciona.

---

## Ronda 3 — Segundo conflicto: mismo valor

Partiendo nuevamente de una versión común, ambos modificaréis:

```csharp
int puntos = 100;
```

### Alumno A

```csharp
int puntos = 200;
```

### Alumno B

```csharp
int puntos = 500;
```

Realizad vuestros respectivos commits e intentad integrar los cambios.

Deberá aparecer vuestro **segundo conflicto**.

Esta vez no podéis elegir simplemente uno de los valores.

El resultado acordado deberá ser:

```csharp
int puntos = 350;
```

Resolved el conflicto y completad el `merge`.

---

## Ronda 4 — Tercer conflicto: modificar una operación

Añadid previamente esta línea al proyecto:

```csharp
double precioFinal = presupuesto * 1.5;
```

Los dos alumnos deben partir de esta misma versión.

### Alumno A

```csharp
double precioFinal = presupuesto * 2;
```

### Alumno B

```csharp
double precioFinal = presupuesto + 25;
```

Cada alumno realiza su `commit`.

Intentad integrar ambas ramas.

Deberá aparecer vuestro **tercer conflicto**.

Decidid conjuntamente qué cálculo queréis conservar, resolved el conflicto y comprobad que el programa sigue funcionando.

---

## Ronda 5 — Cuarto conflicto: varias líneas

El programa contiene:

```csharp
Console.WriteLine("========================");
Console.WriteLine("       FIN");
Console.WriteLine("========================");
```

### Alumno A

Lo sustituye por:

```csharp
Console.WriteLine("========================");
Console.WriteLine("   PROGRAMA TERMINADO");
Console.WriteLine("   Gracias por jugar");
Console.WriteLine("========================");
```

### Alumno B

Lo sustituye por:

```csharp
Console.WriteLine("------------------------");
Console.WriteLine("       GAME OVER");
Console.WriteLine("------------------------");
```

Realizad los commits e intentad integrar ambas ramas.

Deberá aparecer vuestro **cuarto conflicto**.

La solución final deberá contener alguna aportación de ambos alumnos.

---

## Ronda 6 — Mi compañero ha avanzado y yo no lo sabía

En esta ronda vamos a simular una situación muy habitual trabajando en equipo.

Los dos integrantes parten inicialmente de la misma versión.

### Paso 1 — Solo trabaja el Alumno A

El Alumno A modifica el proyecto, por ejemplo añadiendo:

```csharp
string lenguaje = "C#";
Console.WriteLine($"Lenguaje: {lenguaje}");
```

Realiza:

```text
commit → push → integración
```

El cambio queda integrado en la rama principal del repositorio remoto.

### Paso 2 — El Alumno B NO actualiza su repositorio

El Alumno B no realizará todavía ningún `pull`.

Su copia local, por tanto, **ya no contiene la última versión del proyecto**.

Sin actualizarse, crea una nueva rama:

```text
feature/nuevo-cambio-b
```

y realiza una nueva modificación.

Por ejemplo:

```csharp
string lenguaje = "Java";
Console.WriteLine($"Lenguaje favorito: {lenguaje}");
```

Realiza un `commit`.

### Paso 3 — Comparad las versiones

Antes de continuar, comprobad:

- Qué código tiene el Alumno A.
- Qué código tiene el Alumno B.
- Qué código aparece actualmente en GitHub.

¿Son iguales las tres versiones?
No

¿Por qué?
Dado a que la version del alumno B está en una rama totalmente diferente y el alumno A es el que ha estado trabajando y ha hecho el merge.

### Paso 4 — Intentad integrar el trabajo

El Alumno B deberá intentar incorporar su trabajo al estado actual del proyecto.

Observad qué ocurre.

Dependiendo de los cambios realizados, Git podrá:

- Integrar automáticamente los cambios.
- Solicitar que se resuelva algún conflicto.

Si aparece un conflicto, resolvedlo.

El resultado final deberá conservar correctamente el trabajo realizado por ambos alumnos.

### Preguntas

1. ¿Por qué el Alumno B estaba trabajando con una versión antigua?
Por no hacer el pull de la dev para mergear a feature/nuevo-cambio-raul

2. ¿Haber realizado un `commit` significa que tenemos la última versión del proyecto?
No tiene porque, porque no hemos pulleado. En caso de no haber puleado podemos estar trabajando en una version antigua.

3. ¿Haber realizado un `push` significa que tenemos los cambios realizados por nuestro compañero?
Si no hemos hecho el pull antes, no.

4. ¿Qué operación permite obtener los cambios del repositorio remoto?
git pull origin (rama que deseas) y si es una hija seria:
git checkout feature/""
git merge develop

5. ¿Qué habría sido recomendable hacer antes de comenzar la nueva funcionalidad?
pullear, mergear y comenzar a trabajar.
---

## Buena práctica descubierta

Después de realizar la ronda anterior, ya podéis establecer una regla de trabajo para el resto de la práctica:

> **Antes de comenzar nuevo trabajo, comprobad que vuestra copia local está actualizada respecto al repositorio remoto.**

En un flujo sencillo, esto implicará habitualmente actualizar la rama desde la que vais a crear vuestra nueva rama de trabajo.

Por ejemplo:

```bash
git switch main
git pull
git switch -c feature/nueva-funcionalidad (o git checkout -b feature/nueva-funcionalidad  que es lo que usamos nosotros)
```

De esta forma, la nueva rama parte de una versión actualizada del proyecto.

Esto **no garantiza que nunca aparezcan conflictos**. Otro compañero puede modificar posteriormente el mismo código.

Lo que conseguimos es evitar comenzar deliberadamente una nueva funcionalidad sobre una versión que ya sabemos que está desactualizada.

---

## Ronda final — Conflicto libre

Ahora cada integrante deberá realizar una modificación por su cuenta.

La única condición es intentar provocar **un nuevo conflicto sin indicar al compañero exactamente qué línea vais a modificar**.

Realizad el proceso completo utilizando lo aprendido durante la práctica.

Si aparece un conflicto, resolvedlo conjuntamente.

Si no aparece, explicad por qué Git ha podido combinar los cambios automáticamente.

---

## Resultado final

Al terminar debéis haber realizado:

- [X] Trabajo sobre un repositorio compartido.
- [X] Varias ramas.
- [X] Varios commits por persona.
- [X] Integraciones sin conflictos.
- [X] Al menos 4 conflictos provocados y resueltos.
- [X] Una resolución conservando el cambio del Alumno A.
- [X] Una resolución conservando el cambio del Alumno B.
- [X] Una resolución creando una solución diferente a las dos originales.
- [X] Una resolución combinando aportaciones de ambos.
- [X] Una situación en la que un alumno trabaje sobre una versión local desactualizada.
- [X] Actualización posterior respecto al repositorio remoto.
- [X] El programa final compila.
- [X] El programa final se ejecuta correctamente.

---

## Preguntas finales

1. ¿Por qué dos personas pueden modificar el mismo archivo sin generar necesariamente un conflicto?
Porque si hay dos partes que no se solapan entre si, no tiene porque haber ningun conflicto entre ellas.

2. ¿Qué provoca que Git considere que existe un conflicto?
Que ambas personas toquen la misma linea de codigo de manera diferente.

3. ¿Un conflicto significa que alguien ha hecho algo mal?
No tiene por que, un conflicto puede venir de una diferencia de ideas sin necesidad de que una de las ideas esté mal.

4. ¿Quién debe decidir cuál debe ser el código definitivo?
El ultimo que haga la merge, habiendo llegado a un acuerdo previo entre el equipo.

5. ¿Qué diferencia existe entre `commit`, `push` y `pull`?
- Commit es para guardar los cambios sin necesidad de subirlo aun a github (posterior a un git add).
- Push es para subir los cambios al repositorio de github.
- Pull es para actualizar el repositorio local con la ultima version de github.

6. ¿Por qué es importante actualizar nuestra copia antes de comenzar nuevo trabajo?
Para evitar posibles conflictos en las ramas.

7. ¿Actualizar antes de empezar garantiza que nunca tendremos conflictos?
No tiene por que. Pueden haber varias personas tocando la misma linea de codigo al mismo tiempo resolviendo un problema de manera diferente.

8. ¿Por qué debemos comprobar que el programa funciona después de resolver un conflicto?
Para asegurarnos de que todo funciona correctamente.
