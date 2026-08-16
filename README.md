# 🥷 Kata Annalyn's Infiltration: Lógica Booleana en Java

> Aquí no hay término medio: o el guardia duerme, o te descubre. Todo se decide con un `true` o un `false`.

Ejercicio de **Exercism** en **Java 21 con Maven**, centrado en modelar decisiones booleanas puras a partir del estado de varios personajes, para determinar qué acciones de infiltración son posibles en cada situación. Desarrollado sobre los tests dados (**JUnit 5 + Hamcrest**), con cobertura de tests medida con **JaCoCo**.

---

## 📑 Índice

- [Descripción](#-descripción)
- [Cómo reproducir el proyecto](#-cómo-reproducir-el-proyecto)
- [Tecnologías](#-tecnologías)
- [Autora](#-autora)

---

## 📋 Descripción

**Annalyn's Infiltration** es un ejercicio que parte de la clase `AnnalynsInfiltration`, que expone 4 métodos estáticos para decidir, a partir del estado (despierto/dormido) del caballero, el arquero y la prisionera, y de si el perro de Annalyn está presente, qué acciones de infiltración son posibles: un ataque rápido, espiar al grupo, señalizar a la prisionera o liberarla.

- **`canFastAttack(knightIsAwake)`** — devuelve `true` si el caballero está dormido
- **`canSpy(knightIsAwake, archerIsAwake, prisonerIsAwake)`** — devuelve `true` si al menos uno de los tres (caballero, arquero o prisionera) está despierto
- **`canSignalPrisoner(archerIsAwake, prisonerIsAwake)`** — devuelve `true` si la prisionera está despierta y el arquero dormido
- **`canFreePrisoner(knightIsAwake, archerIsAwake, prisonerIsAwake, petDogIsPresent)`** — devuelve `true` si se cumple alguna de las dos formas de rescate: con el perro presente y el arquero dormido, o sin perro con la prisionera despierta y el caballero y el arquero dormidos

> **Nota:** la clase solo expone métodos estáticos, así que se cierra con un constructor privado de modo que no puede ser instanciada directamente desde fuera

<details>
<summary><strong>Enunciado completo</strong></summary>

**Annalyn's Infiltration**

**Description**

In this exercise, you'll be implementing the quest logic for a new RPG game a friend is developing. The game's main character is Annalyn, a brave girl with a fierce and loyal pet dog. Unfortunately, disaster strikes, as her best friend was kidnapped while searching for berries in the forest. Annalyn will try to find and free her best friend, optionally taking her dog with her on this quest.

After some time spent following her best friend's trail, she finds the camp in which her best friend is imprisoned. It turns out there are two kidnappers: a mighty knight and a cunning archer.

Having found the kidnappers, Annalyn considers which of the following actions she can engage in:

Fast attack: a fast attack can be made if the knight is sleeping, as it takes time for him to get his armor on, so he will be vulnerable.

Spy: the group can be spied upon if at least one of them is awake. Otherwise, spying is a waste of time.

Signal prisoner: the prisoner can be signalled using bird sounds if the prisoner is awake and the archer is sleeping, as archers are trained in bird signaling, so they could intercept the message.

Free prisoner: Annalyn can try sneaking into the camp to free the prisoner. This is a risky thing to do and can only succeed in one of two ways:

    If Annalyn has her pet dog with her she can rescue the prisoner if the archer is asleep. The knight is scared of the dog and the archer will not have time to get ready before Annalyn and the prisoner can escape.

    If Annalyn does not have her dog then she and the prisoner must be very sneaky! Annalyn can free the prisoner if the prisoner is awake and the knight and archer are both sleeping, but if the prisoner is sleeping they can't be rescued: the prisoner would be startled by Annalyn's sudden appearance and wake up the knight and archer.

You have four tasks: to implement the logic for determining if the above actions are available based on the state of the three characters found in the forest and whether Annalyn's pet dog is present or not.

**1. Check if a fast attack can be made**

Implement the (static) AnnalynsInfiltration.canFastAttack() method that takes a boolean value that indicates if the knight is awake. This method returns true if a fast attack can be made based on the state of the knight. Otherwise, returns false:

```
boolean knightIsAwake = true;
AnnalynsInfiltration.canFastAttack(knightIsAwake);
// => false
```

**2. Check if the group can be spied upon**

Implement the (static) AnnalynsInfiltration.canSpy() method that takes three boolean values, indicating if the knight, archer and the prisoner, respectively, are awake. The method returns true if the group can be spied upon, based on the state of the three characters. Otherwise, returns false:

```
boolean knightIsAwake = false;
boolean archerIsAwake = true;
boolean prisonerIsAwake = false;
AnnalynsInfiltration.canSpy(knightIsAwake, archerIsAwake, prisonerIsAwake);
// => true
```

**3. Check if the prisoner can be signalled**

Implement the (static) AnnalynsInfiltration.canSignalPrisoner() method that takes two boolean values, indicating if the archer and the prisoner, respectively, are awake. The method returns true if the prisoner can be signalled, based on the state of the two characters. Otherwise, returns false

```
boolean archerIsAwake = false;
boolean prisonerIsAwake = true;
AnnalynsInfiltration.canSignalPrisoner(archerIsAwake, prisonerIsAwake);
// => true
```

**4. Check if the prisoner can be freed**

Implement the (static) AnnalynsInfiltration.canFreePrisoner() method that takes four boolean values. The first three parameters indicate if the knight, archer and the prisoner, respectively, are awake. The last parameter indicates if Annalyn's pet dog is present. The method returns true if the prisoner can be freed based on the state of the three characters and Annalyn's pet dog's presence. Otherwise, it returns false:

```
boolean knightIsAwake = false;
boolean archerIsAwake = true;
boolean prisonerIsAwake = false;
boolean petDogIsPresent = false;
AnnalynsInfiltration.canFreePrisoner(knightIsAwake, archerIsAwake, prisonerIsAwake, petDogIsPresent);
// => false
```

**Source**

- https://exercism.org/tracks/java/exercises/annalyns-infiltration

</details>

---

## 🚀 Cómo reproducir el proyecto

### Requisitos previos

| Herramienta                                                   | Requisito                | Guía de instalación                                                                                       |
| ------------------------------------------------------------- | ------------------------ | --------------------------------------------------------------------------------------------------------- |
| [JDK 21](https://www.oracle.com/java/technologies/downloads/) | Instalado y en el `PATH` | [Ver guía](https://docs.oracle.com/en/java/javase/21/install/overview-jdk-installation.html)              |
| [Apache Maven](https://maven.apache.org/download.cgi)         | Instalado y en el `PATH` | [Ver guía](https://maven.apache.org/install.html)                                                         |
| [Git](https://git-scm.com/downloads)                          | Instalado                | [Ver guía](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Instalaci%C3%B3n-de-Git) |

### Pasos

**1. Comprueba que tienes Java y Maven instalados** (si algún comando no se reconoce, instálalo desde los enlaces de _Requisitos previos_):

```bash
java --version
mvn --version
```

**2. Clona el repositorio:**

```bash
git clone https://github.com/Jennydev-25/kata-java-annalyns-infiltration.git
```

**3. Entra en la carpeta del proyecto:**

```bash
cd kata-java-annalyns-infiltration
```

**4. Ejecuta los tests** (compila y genera el reporte de cobertura de JaCoCo):

```bash
mvn test
```

El reporte de cobertura se genera en `target/site/jacoco/index.html`, que puedes abrir en el navegador

[Volver al índice](#-índice)

---

## 🛠️ Tecnologías

- **[Java 21](https://www.oracle.com/java/technologies/downloads/)** — Lenguaje de programación del proyecto
- **[Apache Maven](https://maven.apache.org/)** — Gestor de dependencias y construcción del proyecto
- **[JUnit 5](https://junit.org/junit5/)** — Framework de tests unitarios
- **[Hamcrest](https://hamcrest.org/JavaHamcrest/)** — Librería de matchers para aserciones legibles
- **[JaCoCo](https://www.jacoco.org/jacoco/)** — Medición de la cobertura de tests
- **[Visual Studio Code](https://code.visualstudio.com/)** — Editor usado para desarrollar y gestionar el proyecto
- **[Markdown](https://www.markdownguide.org/)** — Lenguaje de marcado para el README
- **[Git](https://git-scm.com/)** / **[GitHub](https://github.com/)** — Control de versiones y alojamiento del proyecto

---

## 👩‍💻 Autora

**[Jenny Sánchez Requejo](https://github.com/Jennydev-25)**

[Volver arriba](#-kata-annalyns-infiltration-lógica-booleana-en-java)
