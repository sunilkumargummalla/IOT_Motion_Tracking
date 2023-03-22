```
{
  "id": 7,
  "gridPos": {
    "h": 8,
    "w": 12,
    "x": 0,
    "y": 0
  },
  "type": "timeseries",
  "title": "Gyroscope- Motion Detection",
  "datasource": {
    "uid": "yQaDxsF4z",
    "type": "mysql"
  },
  "pluginVersion": "9.3.1",
  "fieldConfig": {
    "defaults": {
      "custom": {
        "drawStyle": "line",
        "lineInterpolation": "linear",
        "barAlignment": 0,
        "lineWidth": 3,
        "fillOpacity": 0,
        "gradientMode": "none",
        "spanNulls": false,
        "showPoints": "auto",
        "pointSize": 5,
        "stacking": {
          "mode": "none",
          "group": "A"
        },
        "axisPlacement": "auto",
        "axisLabel": "",
        "axisColorMode": "text",
        "scaleDistribution": {
          "type": "linear"
        },
        "axisCenteredZero": false,
        "hideFrom": {
          "tooltip": false,
          "viz": false,
          "legend": false
        },
        "thresholdsStyle": {
          "mode": "off"
        }
      },
      "color": {
        "mode": "palette-classic"
      },
      "mappings": [],
      "thresholds": {
        "mode": "absolute",
        "steps": [
          {
            "color": "green",
            "value": null
          },
          {
            "color": "red",
            "value": 80
          }
        ]
      }
    },
    "overrides": []
  },
  "options": {
    "tooltip": {
      "mode": "single",
      "sort": "none"
    },
    "legend": {
      "showLegend": true,
      "displayMode": "list",
      "placement": "bottom",
      "calcs": []
    }
  },
  "targets": [
    {
      "dataset": "motiondb",
      "datasource": {
        "type": "mysql",
        "uid": "yQaDxsF4z"
      },
      "editorMode": "code",
      "format": "table",
      "rawQuery": true,
      "rawSql": "SELECT tstamp, XGyro, YGyro, ZGyro FROM motiondb.mpudata1 LIMIT 1000 ",
      "refId": "A",
      "sql": {
        "columns": [
          {
            "parameters": [
              {
                "name": "tstamp",
                "type": "functionParameter"
              }
            ],
            "type": "function"
          },
          {
            "parameters": [
              {
                "name": "XGyro",
                "type": "functionParameter"
              }
            ],
            "type": "function"
          },
          {
            "parameters": [
              {
                "name": "YGyro",
                "type": "functionParameter"
              }
            ],
            "type": "function"
          },
          {
            "parameters": [
              {
                "name": "ZGyro",
                "type": "functionParameter"
              }
            ],
            "type": "function"
          }
        ],
        "groupBy": [
          {
            "property": {
              "type": "string"
            },
            "type": "groupBy"
          }
        ],
        "limit": 50
      },
      "table": "mpudata1"
    }
  ]
}
```
