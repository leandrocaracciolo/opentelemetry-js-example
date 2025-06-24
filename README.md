# OpenTelemetry JavaScript Example

This is a simple project to demonstrate the basics of OpenTelemetry with Node.js. It shows how to set up automatic instrumentation to capture and visualize both traces and metrics using an OTel Collector, Jaeger, Prometheus, and Grafana.

This project was built with the assistance of the AI in [Cursor](https://cursor.sh/) as a learning exercise.

## Features

- **Automatic Instrumentation**: Captures telemetry data from a Node.js Express application without manual code changes.
- **Traces**: Visualizes request flows and latency with Jaeger.
- **Metrics**: Collects application metrics (e.g., HTTP request rates and duration) and exposes them via Prometheus.
- **Dashboards**: Visualizes metrics in real-time with Grafana.
- **Containerized Stack**: All observability components (Collector, Jaeger, Prometheus, Grafana) are managed with Docker Compose.

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v16 or higher recommended)
- [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/)

### Installation & Running

1.  **Clone the repository:**
    ```sh
    git clone https://github.com/leandrocaracciolo/opentelemetry-js-example.git
    cd opentelemetry-js-example
    ```

2.  **Install dependencies:**
    ```sh
    npm install
    ```

3.  **Start the observability stack:**
    This command will start the OTel Collector, Jaeger, Prometheus, and Grafana in the background.
    ```sh
    docker-compose up -d
    ```

4.  **Run the application:**
    This starts the Node.js server with the OpenTelemetry tracer and meter providers enabled.
    ```sh
    npm start
    ```

5.  **Generate some telemetry data:**
    Open a new terminal and send a few requests to the application to generate traces and metrics.
    ```sh
    curl http://localhost:3000
    ```

## Visualizing the Data

### 1. View Traces in Jaeger

-   **URL**: [http://localhost:16686](http://localhost:16686)
-   In the Jaeger UI, select the `unknown_service:node` service and click "Find Traces" to see the details of your requests.

### 2. View Metrics in Grafana

-   **URL**: [http://localhost:3001](http://localhost:3001)
-   **Login**: Use `admin` for both username and password.

#### Configure the Prometheus Data Source

1.  Navigate to **Connections** > **Data Sources** from the side menu.
2.  Click **Add new data source** and select **Prometheus**.
3.  Set the **Prometheus server URL** to `http://prometheus:9090`.
4.  Click **Save & test**.

#### Create a Dashboard to View Metrics

1.  Click the **+** icon in the side menu and select **Dashboard**.
2.  Click **Add new panel**.
3.  In the query editor, ensure the **Prometheus** data source is selected.
4.  Use the **Metrics browser** to explore available metrics. For example, to see the average request latency, you can use the following query:
    ```
    http_server_duration_sum / http_server_duration_count
    ```

## Stopping the Environment

1.  **Stop the Node.js application**: Press `Ctrl + C` in the terminal where it's running.
2.  **Stop the Docker containers**:
    ```sh
    docker-compose down
    ``` 