# Prime Number Application with Datadog Integration

This repository contains a Dockerized Python Flask application that checks if a number is prime. The application is integrated with Datadog for monitoring and logging.

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Setup and Installation](#setup-and-installation)
  - [Clone the Repository](#clone-the-repository)
  - [Build the Docker Image](#build-the-docker-image)
  - [Run the Docker Containers](#run-the-docker-containers)
- [Application Details](#application-details)
  - [Prime Number Application](#prime-number-application)
  - [Datadog Integration](#datadog-integration)
- [Configuration](#configuration)
  - [Environment Variables](#environment-variables)
  - [Datadog YAML Configuration](#datadog-yaml-configuration)
- [Logging and Monitoring](#logging-and-monitoring)
  - [View Logs in Datadog](#view-logs-in-datadog)
  - [View Metrics in Datadog](#view-metrics-in-datadog)
- [Common Issues and Troubleshooting](#common-issues-and-troubleshooting)
  - [Missing `system-probe.yaml` File](#missing-system-probe-yaml-file)
  - [No Logs in Datadog](#no-logs-in-datadog)
  - [Docker File Sharing Issues](#docker-file-sharing-issues)
- [License](#license)
- [Contributing](#contributing)

## Overview

This project demonstrates how to create a simple Flask application that checks if a number is prime and integrates with Datadog for monitoring and logging. The application is containerized using Docker.

## Prerequisites

- Docker and Docker Compose installed on your machine.
- A Datadog account with an API key.

## Setup and Installation

### Clone the Repository

## Application Details

### Prime Number Application

This application provides a simple web interface where users can input a number to check if it's prime.

### Datadog Integration

The application is integrated with Datadog to collect metrics and logs. This includes tracking the number of prime number requests and logging different levels of application logs.

## Configuration

### Environment Variables

Ensure the following environment variables are set:  Secure Environment Variables

Instead of hardcoding your Datadog API key and app key in the Dockerfile, you should pass them securely when you run the container.

* `DD_API_KEY`: Your Datadog API key.
* `DD_APP_KEY`: Your Datadog Application key (if needed).

### Datadog YAML Configuration

Update the `datadog.yaml` file as needed, for example:

### Running the Application Container

`docker run -d --name prime-app-number-dd prime-app-number-dd`

### Running the Datadog Agent Container

Reference page https://app.datadoghq.eu/signup/agent#docker update the API Key

```docker
docker run -d --name dd-agent \
-e DD_API_KEY=YOUR_API_KEY \
-e DD_SITE="datadoghq.eu" \
-e DD_LOGS_ENABLED=true \
-e DD_LOGS_CONFIG_LOGS_ENABLED=true \
-v /var/run/docker.sock:/var/run/docker.sock:ro \
-v /proc/:/host/proc/:ro \
-v /sys/fs/cgroup/:/host/sys/fs/cgroup:ro \
-v /var/lib/docker/containers:/var/lib/docker/containers:ro \
-v /path/to/your/logs:/app:ro \
gcr.io/datadoghq/agent:7

```

### Splunk Configuration

Update `docker-compose.yml`

* **HEC Token** : Replace `YOUR_SPLUNK_HEC_TOKEN` with your actual Splunk HTTP Event Collector (HEC) token in the `docker-compose.yml`.
* **Splunk Web Interface** : Open your browser and go to `http://localhost:8082/`.

## Logging and Monitoring

### View Logs in Datadog

To view the logs collected from the application, navigate to the **Logs** section in your Datadog dashboard.

### View Metrics in Datadog

Metrics such as CPU usage, memory usage, and custom application metrics can be viewed in the **Metrics** section of the Datadog dashboard.

## Common Issues and Troubleshooting

### Missing `system-probe.yaml` File

If you encounter a missing `system-probe.yaml` file error, follow the steps outlined in the [Common Issues](#common-issues-and-troubleshooting) section.

### No Logs in Datadog

Ensure that the logging path is correct and that the Datadog Agent is configured to collect logs from that path.

### Docker File Sharing Issues

If running Docker on macOS, ensure that the necessary directories are shared with Docker.

 **Configure Shared Paths**

1. **Open Docker Desktop Preferences:**

* Click on the Docker icon in your system tray (usually at the top-right of the screen on
  macOS).
* Select **Preferences **or **Settings** on Windows).

2. **Go to File Sharing:**

* On macOS, navigate to **Resources** >  **File Sharing** .
* On Windows, go to **Shared Drives** or **Resources** depending on your Docker Desktop version.

3. **Add the Directory:**

* Add the path to the directory you want Docker to access. For instance, if your logs are located at `<span>/Users/yourusername/logs</span>`, you would add this path.
* Click **Apply & Restart** or **Save** to update the settings and restart Docker.

## License


## Contributing

Contributions are welcome! Please fork this repository and submit a pull request for review.

`This `README.md ` file provides a comprehensive overview of the project, instructions on setup and usage, and a section on troubleshooting common issues. You can adjust the content as necessary to fit your specific project.`
