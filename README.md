# OpenTelemetry JavaScript Example

This is a simple project created to understand the basics of OpenTelemetry with Node.js and Express. It demonstrates how to set up automatic instrumentation to capture and visualize traces using an OTel Collector and Jaeger.

This project was built with the assistance of the AI in [Cursor](https://cursor.sh/), as a learning exercise.

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

3.  **Start the observability stack (OTel Collector + Jaeger):**
    This will run the services in the background.
    ```sh
    docker-compose up -d
    ```

4.  **Run the application:**
    ```sh
    npm start
    ```

5.  **Generate some traces:**
    - Open your browser and navigate to `http://localhost:3000`.
    - Refresh the page a few times.

6.  **View the traces in Jaeger:**
    - Open your browser and navigate to `http://localhost:16686`.
    - Select the `unknown_service:node` service from the dropdown and click "Find Traces".

## Stopping the environment

- To stop the Node.js application, press `Ctrl + C` in the terminal where it's running.
- To stop the Docker containers (Collector and Jaeger), run:
  ```sh
  docker-compose down
  ``` 