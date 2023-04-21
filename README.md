# CPU Utilization VS Power Consumption

This tool builds a model to predict CPU energy consumption from CPU utilization using InfluxDB time series.

## Requirements

You need to install the following libraries:

```python
pip install influxdb-client pandas numpy scikit-learn matplotlib
```

## Configuration

Before using this tool you must configure the InfluxDB server from which the metrics will be exported, as well as the timestamps of the time series you want to obtain from that server.

### InfluxDB server

To modify your InfluxDB server simply modify the following code variables:

```python
influxdb_url = "influxdb-server:port"
influxdb_token = "your-token"
influxdb_org = "your-org"
influxdb_bucket = "your-bucket"
```

It is assumed that this server stores Glances and RAPL metrics in a proper format.

### Options

```shell
usage: main.py [-h] [-t TIMESTAMPS_FILE] [-r REGRESSION_PLOT_PATH] [-d DATA_PLOT_PATH]

Modeling CPU power consumption from InfluxDB time series.

options:
  -h, --help            show this help message and exit
  -t TIMESTAMPS_FILE, --timestamps-file TIMESTAMPS_FILE
                        File storing time series timestamps. By default is log/stress.timestamps. Timestamps must be stored in the following format:
                             <some-text-or-nothing> start: '%Y-%m-%d %H:%M:%S%z'
                             <some-text-or-nothing> stop: '%Y-%m-%d %H:%M:%S%z'
                         Example:
                             Spread_P&L (cores = 0,16) start: 2023-04-18 14:26:01+0000
                             Spread_P&L (cores = 0,16) stop: 2023-04-18 14:28:01+0000
  -r REGRESSION_PLOT_PATH, --regression-plot-path REGRESSION_PLOT_PATH
                        Specifies the path to save the regression plot. By default is 'img/regression.png'.
  -d DATA_PLOT_PATH, --data-plot-path DATA_PLOT_PATH
                        Specifies the path to save the data plot. By default is 'img/data.png'.
```
