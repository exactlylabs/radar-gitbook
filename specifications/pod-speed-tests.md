# Pod Speed Tests

This document describes the data fields used in internet speed tests collected at Neuranimus clinic locations. These results originate from NDT7 and OOKLA test platforms.

### Speed Test Dictionary

#### CSV Fields

```csv
id, client_id, account, location_name, latitude, longitude, address, style, upload, download, avg_data_used, jitter, latency, created_at(UTC+0)
```

---

### Fields Description

#### General Test Metadata

| Field               | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| `id`                | Unique identifier for the speed test result.                                |
| `client_id`         | Anonymized identifier of the device or user submitting the test.            |
| `account`           | Organizational account label (e.g., "Neuranimus").                          |
| `location_name`     | Human-readable name for the test location.                                  |
| `address`           | Full postal address of the test location.                                   |
| `latitude`          | Geographic latitude where the test was performed.                           |
| `longitude`         | Geographic longitude where the test was performed.                          |
| `created_at(UTC+0)` | Timestamp (UTC+0) when the test was performed, format: `MM/DD/YY HH:mm`.    |

---

#### Test Parameters

| Field           | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| `style`          | Test tool used. Values: `NDT7` or `OOKLA`.                                  |
| `upload`         | Upload speed in Mbps measured during the test.                              |
| `download`       | Download speed in Mbps measured during the test.                            |
| `avg_data_used`  | Volume of data transferred during the test (in MB).                         |
| `jitter`         | Variation in latency (in milliseconds). Only present for `OOKLA` tests.     |
| `latency`        | Measured latency (in milliseconds). May be present for both test styles.    |

---

### Notes

- `NDT7` and `OOKLA` are two different testing tools:
  - `NDT7` is an open platform provided by Measurement Lab.
  - `OOKLA` (e.g., Speedtest.net) provides commercial speed test data and includes jitter metrics.
- `jitter` is consistently empty for NDT7 results as it does not capture this metric.
- Upload and download speeds are expressed in **Megabits per second (Mbps)**.
- Timestamps are recorded in **UTC+0** for uniform comparison across test instances.
- This dataset is structured to support performance tracking, trend analysis, and test validation across time for a fixed site.
- There are more data fields hidden, if your analysis requires more details, contact us and we would be happy to supply more information
