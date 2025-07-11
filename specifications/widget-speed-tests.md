# Widget Speed Tests

This is a list of fields which would appear from either https://speed.radartoolkit.com or the "Radar Speed Test" mobile applications

### Speed Test Dictionary

#### Mobile App fields

```json
    {
      "result": {"raw": LIST},
      "speed_test": {           
        "tested_at": STRING,
        "latitude": DOUBLE,
        "longitude": DOUBLE,
        "accuracy": DOUBLE,
        "altitude": DOUBLE,
        "floor": INT,
        "heading": DOUBLE,
        "speed": DOUBLE,
        "speed_accuracy": DOUBLE,
        "address": STRING,
        "city": STRING,
        "street": STRING,
        "state": STRING,
        "postal_code": STRING,
        "house_number": STRING,
        "network_type": STRING,
        "network_location": STRING,
        "network_cost": STRING,
        "latitude_before": DOUBLE,
        "longitude_before": DOUBLE,
        "accuracy_before": DOUBLE,
        "altitude_before": DOUBLE,
        "floor_before": INT,
        "heading_before": DOUBLE,
        "speed_before": DOUBLE,
        "speed_accuracy_before": DOUBLE,
        "longitude_after": DOUBLE,
        "latitude_after": DOUBLE,
        "accuracy_after": DOUBLE,
        "altitude_after": DOUBLE,
        "floor_after": INT,
        "heading_after": DOUBLE,
        "speed_after": DOUBLE,
        "speed_accuracy_after": DOUBLE,
        "version_number": STRING,
        "build_number": STRING,
        "session_id": STRING,
        "background_mode": BOOL,
      },
      "connection_data": {
        "platform": STRING,
        "connectionType": STRING,
        "connectionInfo": MAP,
        "rssi": INT,
        },
      "timestamp": STRING,
    };
```

### Fields description

#### result

| Field    | Description                                                                |
| -------- | -------------------------------------------------------------------------- |
| `result` | All raw data exchanged during the speed test between the client and server |

#### speed\_test

Bellow, "BMT" specifically refers to tests preformed on the mobile application when the test is defined as a Background Mode Test.

| Field                   | Description                                                                                                                                                                                                                                       |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `tested_at`             | The time at which the speed test was performed.                                                                                                                                                                                                   |
| `latitude`              | <p>The latitude of the position where the speed test was performed.<br>Same as latitude_before in <strong>BMT</strong>.</p>                                                                                                                       |
| `longitude`             | <p>The longitude of the position where the speed test was performed.<br>Same as longitude_before in <strong>BMT</strong>.</p>                                                                                                                     |
| `altitude`              | <p>The altitude of the device (used to perform the speed test).<br>Same as longitude_before in <strong>BMT</strong>.</p>                                                                                                                          |
| `accuracy`              | <p>The estimated horizontal accuracy of the position where the speed test was performed.<br>Same as longitude_before in <strong>BMT</strong></p>                                                                                                  |
| `floor`                 | <p>Floor of the building on which the device was when the speed test was performed.<br>Same as longitude_before in <strong>BMT</strong>.</p>                                                                                                      |
| `heading`               | <p>The heading in which the device was traveling when the speed test was performed.<br>Same as longitude_before in <strong>BMT</strong>.</p>                                                                                                      |
| `speed`                 | <p>The speed at which the device was traveling when the speed test was performed.<br>Same as longitude_before in <strong>BMT</strong>.<br>Value in m/s.</p>                                                                                       |
| `speed_accuracy`        | <p>The estimated speed accuracy of the device when the speed test was performed.<br>Same as speed_accuracy_before in <strong>BMT</strong>.<br>Value in m/s.</p>                                                                                   |
| `address`               | <p>Address associated to the position where the speed test was performed.<br>From latitude &#x26; longitude.<br><em>Null</em> in <strong>BMT</strong>.</p>                                                                                        |
| `city`                  | <p>City associated to the position where the speed test was performed.<br>From latitude &#x26; longitude.<br><em>Null</em> in <strong>BMT</strong>.</p>                                                                                           |
| `street`                | <p>Street associated to the position where the speed test was performed.<br>From latitude &#x26; longitude.<br><em>Null</em> in <strong>BMT</strong>.</p>                                                                                         |
| `state`                 | <p>State associated to the position where the speed test was performed.<br>From latitude &#x26; longitude.<br><em>Null</em> in <strong>BMT</strong>.</p>                                                                                          |
| `postal_code`           | <p>Postal code associated to the position where the speed test was performed.<br>From latitude &#x26; longitude.<br><em>Null</em> in <strong>BMT</strong>.</p>                                                                                    |
| `house_number`          | <p>House number associated to the position where the speed test was performed.<br>From latitude &#x26; longitude.<br><em>Null</em> in <strong>BMT</strong>.</p>                                                                                   |
| `network_type`          | <p>Type of the network used to run the speed test.<br>Alternatives: <strong>Wired, Wifi or Cellular</strong>.<br>Same as <em>connectionType</em> from <em>connection_data</em> in <strong>BMT</strong>.<em>Null</em> in <strong>BMT</strong>.</p> |
| `network_location`      | <p>Location of the network used to run the speed test.<br>Alternatives: <strong>Home, Work, Other or I don’t have.</strong><br><em>Null</em> in <strong>BMT</strong>.</p>                                                                         |
| `network_cost`          | <p>Monthly cost of the network used to perform the speed test.<br><em>Null</em> in <strong>BMT</strong>.</p>                                                                                                                                      |
| `latitude_before`       | <p>The latitude of the position right before the speed test was performed.<br>Same as latitude in <strong>BMT</strong>.</p>                                                                                                                       |
| `longitude_before`      | <p>The longitude of the position right before the speed test was performed.<br>Same as longitude in <strong>BMT</strong>.</p>                                                                                                                     |
| `altitude_before`       | <p>The altitude of the device right before the speed test was performed.<br>Same as altitude in <strong>BMT</strong>.</p>                                                                                                                         |
| `accuracy_before`       | <p>The estimated horizontal accuracy of the position right before the speed test was performed.<br>Same as accuracy in <strong>BMT</strong>.</p>                                                                                                  |
| `floor_before`          | <p>Floor of the building on which the device was right before the speed test was performed.<br>Same as floor_before in <strong>BMT</strong>.</p>                                                                                                  |
| `heading_before`        | <p>The heading in which the device was traveling right before the speed test was performed.<br>Same as heading in <strong>BMT</strong>.</p>                                                                                                       |
| `speed_before`          | <p>The speed at which the device was traveling right before the speed test was performed.<br>Same as speed in <strong>BMT</strong>.</p>                                                                                                           |
| `speed_accuracy_before` | <p>The estimated speed accuracy of the device before the speed test was performed.<br>Same as speed_accuracy in <strong>BMT</strong>.</p>                                                                                                         |
| `latitude_after`        | The latitude of the position right after the speed test was performed.                                                                                                                                                                            |
| `longitude_after`       | The longitude of the position right after the speed test was performed.                                                                                                                                                                           |
| `altitude_after`        | The altitude of the device right after the speed test was performed.                                                                                                                                                                              |
| `accuracy_after`        | The estimated horizontal accuracy of the position right after the speed test was performed.                                                                                                                                                       |
| `floor_after`           | Floor of the building on which the device was right after the speed test was performed.                                                                                                                                                           |
| `heading_after`         | <p>The heading in which the device was traveling right after the speed test was performed.<br>Same as heading in <strong>BMT</strong>.</p>                                                                                                        |
| `speed_after`           | <p>The speed at which the device was traveling right after the speed test was performed.<br>Same as speed in <strong>BMT</strong>.</p>                                                                                                            |
| `speed_accuracy_after`  | <p>The estimated speed accuracy of the device after the speed test was performed.<br>Same as speed_accuracy in <strong>BMT</strong>.</p>                                                                                                          |
| `version_number`        | Version number of the app used to run the speed test.                                                                                                                                                                                             |
| `build_number`          | Build number of the app used to run the speed test.                                                                                                                                                                                               |
| `session_id`            | Unique identifier of the session during which the speed test was performed.                                                                                                                                                                       |
| `background_mode`       | Indicates if the speed test was performed in background mode.                                                                                                                                                                                     |

#### connection\_data (Android only)

| Field            | Description                                                                                                                                                                                   |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `platform`       | <p>Platform of the device used to run the speed test.<br>Alternatives: <strong>Android or iOS</strong>.</p>                                                                                   |
| `connectionType` | <p>Type of the network used to run the speed test.<br>Alternatives: <strong>WIFI or CELLULAR</strong>.<br>Same as <em>network_type</em> from <em>speed_test</em> in <strong>BMT</strong>.</p> |
| `connectionInfo` | Information about the network used to run the speed test.                                                                                                                                     |
| `rssi`           | <p>Received Signal Strength Indicator of the network used to run the speed test.<br>Same as <em>rssi</em> from <em>connection_data</em> in <strong>BMT</strong>.</p>                          |

#### timestamp

| Field       | Description                                     |
| ----------- | ----------------------------------------------- |
| `timestamp` | The time at which the speed test was performed. |
