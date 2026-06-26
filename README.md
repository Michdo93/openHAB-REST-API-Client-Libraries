# openHAB REST Client Libraries — Overview

A family of client libraries for the [openHAB REST API](https://www.openhab.org/docs/configuration/restdocs.html), available in eight languages: **Python, JavaScript, Node.js, Java, C#, C++, C, and Kotlin/Android**.

All libraries share the same design goals, the same class names, and the same method names. Switching between languages requires as little cognitive effort as possible.

---

## Table of Contents

- [Motivation](#motivation)
- [The Cross-Language Design](#the-cross-language-design)
- [When to Use Which Library](#when-to-use-which-library)
- [Libraries at a Glance](#libraries-at-a-glance)
- [Testing with openHAB Cloud or a Local Instance](#testing-with-openhab-cloud-or-a-local-instance)
- [Python](#python)
- [JavaScript (Browser)](#javascript-browser)
- [Node.js](#nodejs)
- [Java](#java)
- [C#](#c)
- [C++](#c-1)
- [C](#c-2)
- [Android / Kotlin](#android--kotlin)
- [Test Applications on Render.com](#test-applications-on-rendercom)
- [License](#license)

---

## Motivation

When building projects that integrate with openHAB, developers almost always need to talk to its REST API. In practice, this means every project reimplements the same HTTP calls — constructing URLs, setting headers, handling authentication, parsing responses, and wiring up Server-Sent Events — independently and differently from every other project.

As the number of openHAB-based projects grows, this creates a fragmented ecosystem. Someone who wants to contribute to a project, fork it, or build on top of it must first understand how that particular project chose to structure its REST communication. If there are a hundred projects, there are potentially a hundred different approaches.

In software engineering, we strive for **reusability, interoperability, and consistency**. A shared client library solves all three:

- **Reusability** — write the REST integration once, use it everywhere.
- **Interoperability** — any project using the library speaks the same language as every other project using the library.
- **Consistency** — contributors who know the library can immediately be productive in any project that uses it, regardless of which one they pick up first.

The libraries in this family were created precisely to establish that shared foundation. Whether you are writing a Python automation script, a Java desktop tool, a Node.js home dashboard, a C-based embedded controller, or an Android app, you call `items.getItems()`, `items.sendCommand("MySwitch", "ON")`, and `itemEvents.itemStateChangedEvent("MySwitch")` — the same names everywhere.

---

## The Cross-Language Design

Every library in this family follows the same structure:

### Identical class names

| Concept | Class name (all languages) |
|---|---|
| HTTP client | `OpenHABClient` |
| Items endpoint | `Items` |
| Things endpoint | `Things` |
| Rules endpoint | `Rules` |
| Persistence | `Persistence` |
| Voice | `Voice` |
| Item events (SSE) | `ItemEvents` |
| Thing events (SSE) | `ThingEvents` |
| … | … (all 27+ classes identical) |

### Identical method names

```python
# Python
items.getItems()
items.sendCommand("MySwitch", "ON")
items.getItemState("MySwitch")
itemEvents.ItemStateChangedEvent("MySwitch")
```

```javascript
// JavaScript / Node.js
await items.getItems()
await items.sendCommand("MySwitch", "ON")
await items.getItemState("MySwitch")
itemEvents.ItemStateChangedEvent("MySwitch")
```

```java
// Java
items.getItems()
items.sendCommand("MySwitch", "ON")
items.getItemState("MySwitch")
itemEvents.ItemStateChangedEvent("MySwitch")
```

```csharp
// C#
items.GetItems()
items.SendCommand("MySwitch", "ON")
items.GetItemState("MySwitch")
itemEvents.ItemStateChangedEvent("MySwitch")
```

```cpp
// C++
items.getItems()
items.sendCommand("MySwitch", "ON")
items.getItemState("MySwitch")
itemEvents.ItemStateChangedEvent("MySwitch")
```

```c
// C
openhab_items_getItems(c, NULL, NULL, NULL, 0, NULL, 0, NULL)
openhab_items_sendCommand(c, "MySwitch", "ON")
openhab_items_getItemState(c, "MySwitch")
openhab_events_getItemStateChangedEvent(c, "MySwitch", callback, NULL)
```

```kotlin
// Android / Kotlin
openHAB.items.getItems()
openHAB.items.sendCommand("MySwitch", "ON")
openHAB.items.getItemState("MySwitch")
openHAB.itemEvents.itemStateChangedEvent("MySwitch")
```

### Identical authentication model

All libraries support the same two authentication methods:

```
# Basic Auth
OpenHABClient(url, username, password)

# Token Auth
OpenHABClient(url, token="oh.openhab.xxxx")
```

### Identical SSE model

All libraries expose Server-Sent Events for real-time updates. The transport differs by language (callback, iterator, Flow, etc.) but the event class names and topic names are always the same: `ItemEvents`, `ThingEvents`, `InboxEvents`, `LinkEvents`, `ChannelEvents`.

---

## When to Use Which Library

The libraries are not competing alternatives — they are designed to be used together, each in the environment where it naturally belongs.

| Language | Primary environments | Example use cases |
|---|---|---|
| **Python** | Automation scripts, robotics, AI/ML, servers | ROS 1/2 nodes, CrewAI agents, openHAB rule scripts, CLI tools, data analysis pipelines |
| **JavaScript** | Browser-based UIs, dashboards | HABPanel-style dashboards, custom openHAB web UIs, in-browser automation tools |
| **Node.js** | Server-side JS, display systems | [MagicMirror²](https://magicmirror.builders/) modules, Express APIs, Electron desktop apps, Home automation servers |
| **Java** | Desktop apps, Spring backends, Android (non-Kotlin) | Spring Boot microservices, JavaFX GUIs, openHAB rule addons, Android apps (Java) |
| **C#** | .NET applications, game engines, XR | **Unity** (VR/AR smart home experiences), WPF/WinForms desktop apps, ASP.NET Web APIs, [MRTK](https://learn.microsoft.com/en-us/windows/mixed-reality/mrtk-unity/) HoloLens apps |
| **C++** | Embedded Linux, performance-critical systems | Raspberry Pi daemons, robot middleware (ROS 2 nodes), industrial controllers, Qt GUIs |
| **C** | Bare-metal, deeply embedded, firmware | Microcontrollers with libcurl, resource-constrained systems, firmware daemons, C-based RTOS integrations |
| **Android / Kotlin** | Android apps | Native Android smart home apps, Wear OS companions, Android Auto integrations |

### Scenario examples

**ROS 2 robot + Python**
A ROS 2 node subscribes to robot sensor topics and uses the Python library to update openHAB items in real time — for example, updating a temperature item when the robot's LIDAR detects environmental changes, or triggering a light scene when the robot enters a room.

**MagicMirror² module + Node.js**
A custom MagicMirror² module uses the Node.js library to display real-time item states (weather sensor, door contacts, energy meters) on a smart mirror, subscribing to SSE streams for live updates without polling.

**Unity VR experience + C#**
A Unity-based VR application lets users walk through a digital twin of their home. The C# library connects to openHAB so that toggling a virtual light switch sends a real `sendCommand("LivingRoomLight", "ON")` to the physical device.

**HoloLens AR overlay + C#**
A Microsoft HoloLens app overlays item states onto physical objects in the room using MRTK. The C# library provides live state updates via SSE so that the AR labels stay current as devices change state.

**Embedded Linux controller + C/C++**
A Raspberry Pi running a C++ daemon monitors a GPIO sensor and uses the C++ library to update openHAB items directly — no Python interpreter, no JVM, minimal RAM footprint.

**Android smart home app + Kotlin**
A native Android companion app for an openHAB installation uses the Kotlin library to send commands, subscribe to item state changes via Kotlin Flows, and display live device states with full lifecycle awareness.

**Home automation dashboard + JavaScript**
A self-hosted single-page web app loaded in the browser uses the JavaScript library directly in the client — no backend needed — to display and control all devices.

---

## Libraries at a Glance

| Library | Language | Package Manager | Latest Version |
|---|---|---|---|
| [python-openhab-rest-client](https://github.com/Michdo93/python-openhab-rest-client) | Python 3 | PyPI | ![PyPI](https://img.shields.io/pypi/v/python-openhab-rest-client) |
| [js-openhab-rest-client](https://github.com/Michdo93/js-openhab-rest-client) | JavaScript (Browser) | CDN / manual | — |
| [nodejs-openhab-rest-client](https://github.com/Michdo93/nodejs-openhab-rest-client) | Node.js 18+ | npm | — |
| [java-openhab-rest-client](https://github.com/Michdo93/java-openhab-rest-client) | Java 11+ | JitPack / GitHub Packages | — |
| [csharp-openhab-rest-client](https://github.com/Michdo93/csharp-openhab-rest-client) | C# (.NET Standard 2.1 / .NET 8) | NuGet | — |
| [cpp-openhab-rest-client](https://github.com/Michdo93/cpp-openhab-rest-client) | C++17 | CMake / vcpkg | — |
| [c-openhab-rest-client](https://github.com/Michdo93/c-openhab-rest-client) | C11 | CMake | — |
| [android-openhab-rest-client](https://github.com/Michdo93/android-openhab-rest-client) | Kotlin / Android API 21+ | JitPack / GitHub Packages / AAR | — |

For the complete list of classes, methods, and their parameters, see the **README of each individual repository** (linked in the sections below).

---

## Testing with openHAB Cloud or a Local Instance

All libraries support two connection modes:

### myopenhab.org (openHAB Cloud)

If you have an account on [myopenhab.org](https://myopenhab.org), you can use it directly:

```
URL:      https://myopenhab.org
Username: your@email.com
Password: your myopenhab.org password
```

This works for all libraries and all test applications without any additional network configuration.

### Local openHAB Instance

If your openHAB instance runs on your local network (e.g. `http://192.168.1.100:8080`), you can connect to it directly from any library running server-side or natively (Python, Node.js, Java, C#, C++, C, Android).

**Browser-based test applications (JavaScript)** additionally require:

1. **CORS enabled in openHAB** — Add the following to `$OPENHAB_CONF/services/runtime.cfg`:
   ```
   org.openhab.cors:enable=true
   ```
   Or enable it via **Administration → Settings → API** in the openHAB UI.

2. **Browser CORS policy relaxed** — Browsers block cross-origin requests by default. During development you can either:
   - Use a browser extension like **CORS Unblock** or **Allow CORS** to temporarily permit cross-origin requests.
   - Launch Chrome with `--disable-web-security --user-data-dir=/tmp/chrome-dev` (development only, never in production).
   - Serve the test page from the same origin as openHAB (e.g. place it in openHAB's web folder).

> **Note:** The C, C++, Java, C#, Node.js, Python, and Android libraries do not run in a browser and are therefore **not affected by CORS**. They can connect to a local openHAB instance directly without any additional configuration.

---

## Python

**Library:** [github.com/Michdo93/python-openhab-rest-client](https://github.com/Michdo93/python-openhab-rest-client)

The Python library is the most feature-complete in the family. It offers all 27 API classes in both **synchronous** (`requests`) and **asynchronous** (`aiohttp`, `AsyncOpenHABClient`) variants, plus all five SSE event classes.

### Installation

```bash
pip install python-openhab-rest-client
```

### Quick start

```python
from openhab import OpenHABClient, Items

client   = OpenHABClient("http://127.0.0.1:8080", username="openhab", password="habopen")
items    = Items(client)

print(items.getItems())
items.sendCommand("MyLightSwitch", "ON")
```

### Async quick start

```python
import asyncio
from openhab import AsyncOpenHABClient, AsyncItems

async def main():
    async with AsyncOpenHABClient("http://127.0.0.1:8080", username="openhab", password="habopen") as client:
        items = AsyncItems(client)
        print(await items.getItems())

asyncio.run(main())
```

### Test Application

| | |
|---|---|
| **Repository** | [github.com/Michdo93/python-openhab-rest-client-test-app](https://github.com/Michdo93/python-openhab-rest-client-test-app) |
| **Live Demo** | [michdo93.github.io/python-openhab-rest-client-test-app](https://michdo93.github.io/python-openhab-rest-client-test-app/) |

The test application runs a Python backend on Render.com (Free Tier) and a GitHub Pages frontend. See [Test Applications on Render.com](#test-applications-on-rendercom) for important notes about performance.

### Full documentation

See the [README](https://github.com/Michdo93/python-openhab-rest-client/blob/main/README.md) in the library repository for all classes, methods, parameters, and examples.

---

## JavaScript (Browser)

**Library:** [github.com/Michdo93/js-openhab-rest-client](https://github.com/Michdo93/js-openhab-rest-client)

A zero-dependency single-file library (`openhab.js` / `openhab.min.js`) for use directly in the browser. All methods are Promise-based. Includes the `Async` prefixed variants for naming consistency with Python.

### Installation

```html
<!-- CDN (recommended) -->
<script src="https://cdn.jsdelivr.net/gh/Michdo93/js-openhab-rest-client@main/openhab.min.js"></script>

<!-- Via GitHack -->
<script src="https://rawcdn.githack.com/Michdo93/js-openhab-rest-client/main/openhab.min.js"></script>
```

Or download `openhab.js` from the repository and host it locally:

```html
<script src="./openhab.js"></script>
```

### Quick start

```html
<script src="https://cdn.jsdelivr.net/gh/Michdo93/js-openhab-rest-client@main/openhab.min.js"></script>
<script>
  const { OpenHABClient, Items } = openHAB;
  const client = new OpenHABClient("http://127.0.0.1:8080", "openhab", "habopen");
  const items  = new Items(client);

  items.getItems().then(result => console.log(result));
  items.sendCommand("MyLightSwitch", "ON");
</script>
```

> **CORS note:** When connecting to a local openHAB instance from the browser, CORS must be enabled in openHAB and permitted in your browser. See [Testing with openHAB Cloud or a Local Instance](#testing-with-openhab-cloud-or-a-local-instance). The test application only connects to [myopenhab.org](https://myopenhab.org) by default for this reason.

### Full documentation

See the [README](https://github.com/Michdo93/js-openhab-rest-client/blob/main/README.md) for all import variants (ESM, CommonJS, CDN, local), all classes and methods.

---

## Node.js

**Library:** [github.com/Michdo93/nodejs-openhab-rest-client](https://github.com/Michdo93/nodejs-openhab-rest-client)

The Node.js library is a server-side version with the same API as the browser JS library, published as an npm package with full ESM, CommonJS, and TypeScript support.

### Installation

```bash
npm install nodejs-openhab-rest-client
```

### Quick start (ESM)

```javascript
import { OpenHABClient, Items } from "nodejs-openhab-rest-client";

const client = new OpenHABClient("http://127.0.0.1:8080", "openhab", "habopen");
await client.login();

const items = new Items(client);
const all   = await items.getItems();
console.log(all);
```

### Quick start (CommonJS)

```javascript
const { OpenHABClient, Items } = require("nodejs-openhab-rest-client");
```

### Test Application

| | |
|---|---|
| **Repository** | [github.com/Michdo93/nodejs-openhab-rest-client-test-app](https://github.com/Michdo93/nodejs-openhab-rest-client-test-app) |
| **Live Demo** | [michdo93.github.io/nodejs-openhab-rest-client-test-app](https://michdo93.github.io/nodejs-openhab-rest-client-test-app/) |

The Node.js test application runs entirely client-side on GitHub Pages — no backend required. Because it runs in the browser, the same CORS note as for the JS library applies.

### Full documentation

See the [README](https://github.com/Michdo93/nodejs-openhab-rest-client/blob/main/README.md) for all import variants, TypeScript usage, SSE streaming, and all classes and methods.

---

## Java

**Library:** [github.com/Michdo93/java-openhab-rest-client](https://github.com/Michdo93/java-openhab-rest-client)

A pure Java 11 library with zero external dependencies — built on `java.net.HttpURLConnection`. SSE is exposed via the `SSEConnection` class, which implements `Iterable<String>` and works with try-with-resources.

### Installation

**JitPack (Maven):**

```xml
<repositories>
  <repository>
    <id>jitpack.io</id>
    <url>https://jitpack.io</url>
  </repository>
</repositories>

<dependency>
  <groupId>com.github.Michdo93</groupId>
  <artifactId>java-openhab-rest-client</artifactId>
  <version>1.0.1</version>
</dependency>
```

**JitPack (Gradle):**

```kotlin
repositories { maven("https://jitpack.io") }

dependencies {
    implementation("com.github.Michdo93:java-openhab-rest-client:1.0.1")
}
```

**GitHub Packages** and **manual JAR** options are also available — see the [README](https://github.com/Michdo93/java-openhab-rest-client/blob/main/README.md) for details.

### Quick start

```java
import io.github.michdo93.openhab.*;

OpenHABClient client = new OpenHABClient("http://127.0.0.1:8080", "openhab", "habopen");
Items items = new Items(client);

System.out.println(items.getItems());
items.sendCommand("MyLightSwitch", "ON");
```

### Test Application & Backend

| | |
|---|---|
| **Backend Repository** | [github.com/Michdo93/java-openhab-rest-client-backend](https://github.com/Michdo93/java-openhab-rest-client-backend) |
| **Backend (Live)** | `https://java-openhab-rest-client-backend.onrender.com` |
| **Frontend Repository** | [github.com/Michdo93/java-openhab-rest-client-test-app](https://github.com/Michdo93/java-openhab-rest-client-test-app) |
| **Frontend (Live Demo)** | [michdo93.github.io/java-openhab-rest-client-test-app](https://michdo93.github.io/java-openhab-rest-client-test-app/) |

The backend is a Spring Boot application running on Render.com (Free Tier). See [Test Applications on Render.com](#test-applications-on-rendercom) for important notes.

### Full documentation

See the [README](https://github.com/Michdo93/java-openhab-rest-client/blob/main/README.md) for all installation options, all classes, all method overloads, and SSE examples.

---

## C\#

**Library:** [github.com/Michdo93/csharp-openhab-rest-client](https://github.com/Michdo93/csharp-openhab-rest-client)

A .NET library targeting `netstandard2.1` and `net8.0`, with zero external dependencies. Every method exists in both a synchronous and an `Async` variant. SSE is exposed as `IEnumerable<string>` (sync) and `IAsyncEnumerable<string>` (async, C# 8+).

### Installation

**.NET CLI:**

```bash
dotnet add package CSharpOpenHABRestClient
```

**Package Manager Console (Visual Studio):**

```powershell
Install-Package CSharpOpenHABRestClient
```

**`.csproj` PackageReference:**

```xml
<PackageReference Include="CSharpOpenHABRestClient" Version="1.0.0" />
```

Manual DLL, source project reference, and ASP.NET Core DI integration options are also available — see the [README](https://github.com/Michdo93/csharp-openhab-rest-client/blob/main/README.md).

### Quick start

```csharp
using OpenHABRestClient;

using var client = new OpenHABClient("http://127.0.0.1:8080", "openhab", "habopen");
var items = new Items(client);

Console.WriteLine(items.GetItems());
await items.SendCommandAsync("MyLightSwitch", "ON");
```

### Test Application & Backend

| | |
|---|---|
| **Backend Repository** | [github.com/Michdo93/csharp-openhab-rest-client-backend](https://github.com/Michdo93/csharp-openhab-rest-client-backend) |
| **Backend (Live)** | `https://csharp-openhab-rest-client-backend.onrender.com` |
| **Frontend (Live Demo)** | Served from the backend repository's GitHub Pages |

The backend is an ASP.NET Core application running on Render.com (Free Tier). See [Test Applications on Render.com](#test-applications-on-rendercom).

### Full documentation

See the [README](https://github.com/Michdo93/csharp-openhab-rest-client/blob/main/README.md) for all NuGet installation variants, ASP.NET Core DI setup, sync/async method tables, SSE with `CancellationToken`, and all classes.

---

## C++

**Library:** [github.com/Michdo93/cpp-openhab-rest-client](https://github.com/Michdo93/cpp-openhab-rest-client)

A C++17 library built on libcurl and [nlohmann/json](https://github.com/nlohmann/json) (auto-downloaded by CMake). Returns `nlohmann::json` objects directly — no manual JSON parsing needed. SSE uses a blocking `forEach(callback)` pattern.

### Building

```bash
# Ubuntu / Debian
sudo apt-get install -y libcurl4-openssl-dev cmake build-essential
git clone https://github.com/Michdo93/cpp-openhab-rest-client.git
cd cpp-openhab-rest-client && mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
cmake --build . -- -j$(nproc)
```

Windows (MSVC + vcpkg), MinGW, macOS, and cross-compilation for ARM are also documented in the [README](https://github.com/Michdo93/cpp-openhab-rest-client/blob/main/README.md).

### Adding to your CMake project

```cmake
# Option A: FetchContent (auto-download)
include(FetchContent)
FetchContent_Declare(openhab_rest_client
    GIT_REPOSITORY https://github.com/Michdo93/cpp-openhab-rest-client.git
    GIT_TAG main)
FetchContent_MakeAvailable(openhab_rest_client)
target_link_libraries(myapp PRIVATE openhab_rest_client_static ${CURL_LIBRARIES} nlohmann_json::nlohmann_json)

# Option B: add_subdirectory (local copy)
add_subdirectory(libs/openhab)
target_link_libraries(myapp PRIVATE openhab_rest_client_static ${CURL_LIBRARIES} nlohmann_json::nlohmann_json)
```

### Quick start

```cpp
#include <openhab/openhab.h>
#include <iostream>
using namespace openhab;

int main() {
    OpenHABClient client("http://127.0.0.1:8080", "openhab", "habopen");
    Items items(client);

    std::cout << items.getItems().dump(2) << std::endl;
    items.sendCommand("MyLightSwitch", "ON");
}
```

### Test Application & Backend

| | |
|---|---|
| **Backend Repository** | [github.com/Michdo93/cpp-openhab-rest-client-backend](https://github.com/Michdo93/cpp-openhab-rest-client-backend) |
| **Backend (Live)** | `https://cpp-openhab-rest-client-backend.onrender.com` |
| **Frontend Repository** | [github.com/Michdo93/cpp-openhab-rest-client-test-app](https://github.com/Michdo93/cpp-openhab-rest-client-test-app) |
| **Frontend (Live Demo)** | [michdo93.github.io/cpp-openhab-rest-client-test-app](https://michdo93.github.io/cpp-openhab-rest-client-test-app/) |

The backend is a C++ httplib server running on Render.com (Free Tier). See [Test Applications on Render.com](#test-applications-on-rendercom).

### Full documentation

See the [README](https://github.com/Michdo93/cpp-openhab-rest-client/blob/main/README.md) for all platform-specific build instructions, CMake integration options, and all classes.

---

## C

**Library:** [github.com/Michdo93/c-openhab-rest-client](https://github.com/Michdo93/c-openhab-rest-client)

A pure C11 library built on libcurl. No external JSON library required — all responses are raw JSON `char*` strings that the caller parses with any C JSON library (cJSON, jansson, jsmn, …). The only runtime dependency is libcurl. SSE uses a function pointer callback (`openhab_sse_callback_t`). **The caller must `free()` every returned `char*`.**

Functions follow the naming convention `openhab_<class>_<methodName>(client, ...)`.

### Building

```bash
# Ubuntu / Debian
sudo apt-get install -y libcurl4-openssl-dev cmake build-essential
git clone https://github.com/Michdo93/c-openhab-rest-client.git
cd c-openhab-rest-client && mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
cmake --build . -- -j$(nproc)
```

Windows (MSVC + vcpkg, MinGW), macOS, Raspberry Pi, and AArch64 cross-compilation with the included toolchain file are documented in the [README](https://github.com/Michdo93/c-openhab-rest-client/blob/main/README.md).

### Adding to your CMake project

```cmake
# Option A: FetchContent
FetchContent_Declare(c_openhab_rest_client
    GIT_REPOSITORY https://github.com/Michdo93/c-openhab-rest-client.git
    GIT_TAG main)
FetchContent_MakeAvailable(c_openhab_rest_client)
target_link_libraries(myapp PRIVATE openhab_rest_client_static ${CURL_LIBRARIES})

# Option B: add_subdirectory
add_subdirectory(libs/openhab)
target_link_libraries(myapp PRIVATE openhab_rest_client_static ${CURL_LIBRARIES})
```

### Quick start

```c
#include <openhab/openhab.h>
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    openhab_client_t* c = openhab_client_create(
        "http://127.0.0.1:8080", "openhab", "habopen", NULL);

    char* items = openhab_items_getItems(c, NULL, NULL, NULL, 0, NULL, 0, NULL);
    if (items) { printf("%s\n", items); free(items); }

    char* r = openhab_items_sendCommand(c, "MyLightSwitch", "ON");
    if (r) free(r);

    openhab_client_destroy(c);
    return 0;
}
```

### Test Application & Backend

| | |
|---|---|
| **Backend Repository** | [github.com/Michdo93/c-openhab-rest-client-backend](https://github.com/Michdo93/c-openhab-rest-client-backend) |
| **Backend (Live)** | `https://c-openhab-rest-client-backend.onrender.com` |
| **Frontend Repository** | [github.com/Michdo93/c-openhab-rest-client-test-app](https://github.com/Michdo93/c-openhab-rest-client-test-app) |
| **Frontend (Live Demo)** | [michdo93.github.io/c-openhab-rest-client-test-app](https://michdo93.github.io/c-openhab-rest-client-test-app/) |

The backend is a C++ httplib server with a `extern "C"` interface wrapping the C library, running on Render.com (Free Tier). See [Test Applications on Render.com](#test-applications-on-rendercom).

### Full documentation

See the [README](https://github.com/Michdo93/c-openhab-rest-client/blob/main/README.md) for all platform build instructions, `OPENHAB_STATIC` macro, memory management rules, SSE callback pattern, and all functions.

---

## Android / Kotlin

**Library:** [github.com/Michdo93/android-openhab-rest-client](https://github.com/Michdo93/android-openhab-rest-client)

A Kotlin-exclusive Android library (API 21+) built on OkHttp and Kotlin Coroutines. All REST methods are `suspend` functions. SSE streams are exposed as Kotlin `Flow<String>` via `SseSession.collect()`. The `OpenHAB` facade class provides lazy access to all 27 API classes and 6 event classes through a single entry point.

### Installation

**JitPack** (simplest, no login required):

```kotlin
// settings.gradle.kts
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven("https://jitpack.io")
    }
}
```

```kotlin
// app/build.gradle.kts
dependencies {
    implementation("com.github.Michdo93:android-openhab-rest-client:1.0.5")
}
```

**GitHub Packages** (requires a GitHub PAT with `read:packages`) and **manual AAR** installation are also supported — see the [README](https://github.com/Michdo93/android-openhab-rest-client/blob/main/README.md) for full instructions including credential management and transitive dependency listing.

### AndroidManifest.xml

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

### Quick start

```kotlin
import io.github.michdo93.openhab.OpenHAB
import io.github.michdo93.openhab.client.OpenHABException

val openHAB = OpenHAB(
    url      = "http://192.168.1.100:8080",
    username = "openhab",
    password = "habopen",
    debug    = BuildConfig.DEBUG,
)

// In a coroutine scope (Activity or ViewModel):
lifecycleScope.launch {
    try {
        openHAB.items.sendCommand("LivingRoomLight", "ON")
        val state = openHAB.items.getItemState("LivingRoomLight")
        Log.d("openHAB", "State: $state")
    } catch (e: OpenHABException) {
        Log.e("openHAB", "HTTP ${e.statusCode}: ${e.message}")
    }
}

// SSE — live state changes via Kotlin Flow:
lifecycleScope.launch {
    openHAB.itemEvents
        .itemStateChangedEvent("LivingRoomLight")
        .collect()
        .catch { e -> Log.e("openHAB", "SSE error: ${e.message}") }
        .collect { data -> Log.d("openHAB", "Event: $data") }
}
```

> **Note:** There is no web-based test application for the Android library — the `app-example` module in the repository is the equivalent, demonstrating all features in a native Android Activity. The Android library is exclusively for Android devices and cannot be tested via a browser or backend.

### Full documentation

See the [README](https://github.com/Michdo93/android-openhab-rest-client/blob/main/README.md) for all three installation options, Network Security Configuration, Hilt/Koin DI examples, and all classes and methods.

---

## Test Applications on Render.com

The test applications for Python, Java, C#, C++, and C consist of two parts:

- A **backend** deployed on [Render.com](https://render.com/) (Free Tier) that acts as a stateless proxy, accepting credentials from the frontend and forwarding requests to openHAB.
- A **frontend** hosted on [GitHub Pages](https://pages.github.com/) that provides an interactive HTML test suite.

### Why a separate backend?

The Python, Java, C#, C++, and C libraries are designed for server-side or native use, **not** for direct execution in the browser. A backend proxy is therefore required to make them accessible from a web-based test suite. In contrast, the JavaScript and Node.js libraries can run in the browser directly (or from a Node.js server), so their test applications have no separate backend.

### ⚠ Performance limitations of the Free Tier

Render.com's Free Tier spins down containers after a period of inactivity. Each test application includes a **wake-up mechanism** that sends a ping to the backend when the page loads and waits for it to become available. This typically takes **30–60 seconds** on the first request.

Beyond the startup delay, the Free Tier has limited CPU and memory. Requests that return large responses — such as **querying all items at once** — may exceed the available resources and cause the request to time out or fail. If this happens:

- Try requesting individual items by name instead of all items at once.
- Reduce the number of simultaneous requests.
- Wait a moment and retry — the container may have been mid-startup.

This is a limitation of the hosting environment, **not** of the libraries themselves. Running the same libraries against a local openHAB instance or a production server will not exhibit these constraints.

### Wake-up tip

All test frontends display a status indicator while waiting for the backend to wake up. If the backend does not respond within the timeout, a manual retry button is provided. Allow **up to 60 seconds** on first load before concluding that something is wrong.

### Summary of all test infrastructure

| Language | Backend Repo | Backend Live URL | Frontend Repo | Frontend Live URL |
|---|---|---|---|---|
| Python | [python-openhab-rest-client-test-app](https://github.com/Michdo93/python-openhab-rest-client-test-app) | _(included in test-app repo)_ | same repo | [michdo93.github.io/python-openhab-rest-client-test-app](https://michdo93.github.io/python-openhab-rest-client-test-app/) |
| JavaScript | — | — | [js-openhab-rest-client](https://github.com/Michdo93/js-openhab-rest-client) | [michdo93.github.io/js-openhab-rest-client](https://michdo93.github.io/js-openhab-rest-client/) |
| Node.js | — | — | [nodejs-openhab-rest-client-test-app](https://github.com/Michdo93/nodejs-openhab-rest-client-test-app) | [michdo93.github.io/nodejs-openhab-rest-client-test-app](https://michdo93.github.io/nodejs-openhab-rest-client-test-app/) |
| Java | [java-openhab-rest-client-backend](https://github.com/Michdo93/java-openhab-rest-client-backend) | `java-openhab-rest-client-backend.onrender.com` | [java-openhab-rest-client-test-app](https://github.com/Michdo93/java-openhab-rest-client-test-app) | [michdo93.github.io/java-openhab-rest-client-test-app](https://michdo93.github.io/java-openhab-rest-client-test-app/) |
| C# | [csharp-openhab-rest-client-backend](https://github.com/Michdo93/csharp-openhab-rest-client-backend) | `csharp-openhab-rest-client-backend.onrender.com` | same repo | [michdo93.github.io/csharp-openhab-rest-client-backend](https://michdo93.github.io/csharp-openhab-rest-client-backend/) |
| C++ | [cpp-openhab-rest-client-backend](https://github.com/Michdo93/cpp-openhab-rest-client-backend) | `cpp-openhab-rest-client-backend.onrender.com` | [cpp-openhab-rest-client-test-app](https://github.com/Michdo93/cpp-openhab-rest-client-test-app) | [michdo93.github.io/cpp-openhab-rest-client-test-app](https://michdo93.github.io/cpp-openhab-rest-client-test-app/) |
| C | [c-openhab-rest-client-backend](https://github.com/Michdo93/c-openhab-rest-client-backend) | `c-openhab-rest-client-backend.onrender.com` | [c-openhab-rest-client-test-app](https://github.com/Michdo93/c-openhab-rest-client-test-app) | [michdo93.github.io/c-openhab-rest-client-test-app](https://michdo93.github.io/c-openhab-rest-client-test-app/) |
| Android | — | — | [android-openhab-rest-client](https://github.com/Michdo93/android-openhab-rest-client) (app-example) | — (native Android app) |

---

## License

All libraries and test applications in this family are licensed under the **MIT License**. See the `LICENSE` file in each repository for details.
