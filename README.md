# JMeter Script with Plugins Demo

This repository contains a JMeter test plan (`JMeter_Script_Plugins.jmx`) designed to demonstrate the use of JMeter plugins, scripting, and load simulation techniques **without hitting a real server**. It uses Dummy Samplers, Groovy scripting, and a Constant Throughput Timer to create a flexible, controlled mock load test.

---

## Features

- **Dummy Samplers** simulate HTTP requests and responses
- **Dynamic path selection** using Groovy scripting
- **Randomized error simulation** based on configurable thresholds
- **Constant Throughput Timer** to control request rate
- **Parameterizable** via JMeter properties

---

## Prerequisites

- **Apache JMeter 5.3** or newer
- **JMeter Plugins Manager** (recommended)
- **Dummy Sampler plugin** (install via Plugins Manager)

---

## How It Works

- The test dynamically selects a path from a predefined list (`login`, `home`, `logout`, `signin`, `path`, `vector`, `matrix`, `integral`) before each request.
- It generates randomized request and response payloads of varying sizes.
- It simulates successful requests (HTTP 200) by default.
- It uses a random variable (`Error`) to occasionally trigger an error condition:
  - When `Error > 995`, it simulates a failed request (HTTP 503 Service unavailable).
- The load is controlled to approximately **60 requests per minute** using a Constant Throughput Timer.
- The test runs with default parameters:
  - **Threads:** 10
  - **Ramp-up:** 10 seconds
  - **Duration:** 120 seconds
  - These can be overridden via JMeter command-line properties.

---

## Usage

### Open in JMeter GUI

1. Launch JMeter.
2. Open `JMeter_Script_Plugins.jmx`.
3. Adjust thread count, duration, or other parameters as needed.
4. Add listeners (e.g., Summary Report) to view results.
5. Run the test.

### Run via CLI

```bash
jmeter -n -t JMeter_Script_Plugins.jmx -Jthreads=20 -Jrampup=30 -Jduration=300
```

- `-Jthreads` — Number of virtual users (default 10)
- `-Jrampup` — Ramp-up time in seconds (default 10)
- `-Jduration` — Test duration in seconds (default 120)

---

## Customization

- **Paths:** Edit the `paths` user variable in the Test Plan to simulate different endpoints.
- **Error threshold:** Modify the `If Controller` condition or `RandomVariableConfig` range.
- **Request rate:** Adjust the Constant Throughput Timer value.
- **Add real HTTP samplers:** Replace Dummy Samplers with actual HTTP Request samplers to test real endpoints.

---

## License

This project is provided for demonstration purposes. Add your license information here.