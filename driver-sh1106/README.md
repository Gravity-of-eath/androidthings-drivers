SH1106 display driver for Android Things
=========================================

This driver supports OLED screen peripherals built on the SH1106 chip.

NOTE: these drivers are not production-ready. They are offered as sample
implementations of Android Things user space drivers for common peripherals
as part of the Developer Preview release. There is no guarantee
of correctness, completeness or robustness.

This driver is based on the [SSD1306 display driver for Android Things](https://github.com/androidthings/contrib-drivers/tree/master/ssd1306) 

How to use the driver
---------------------

### Gradle dependency

To use the `sh1106` driver, simply add the line below to your project's `build.gradle`,
where `<version>` matches the last version of the driver available on [jcenter][jcenter].

```
dependencies {
    compile 'com.leinardi.androidthings:driver-sh1106:<version>'
}
```

### Sample usage

```java
import com.leinardi.androidthings.driver.sh1106.Sh1106;

// Access the display:

Sh1106 mDisplay;

try {
    mDisplay = new Sh1106(i2cBusName);
} catch (IOException e) {
    // couldn't configure the display...
}

// Draw on the screen:

try {
    for (int i = 0; i < mDisplay.getLcdWidth(); i++) {
        for (int j = 0; j < mDisplay.getLcdHeight(); j++) {
            // checkerboard
            mDisplay.setPixel(i, j, (i % 2) == (j % 2));
        }
    }
    mDisplay.show(); // render the pixel data

    // You can also use BitmapHelper to render a bitmap instead of setting pixels manually
} catch (IOException e) {
    // error setting display
}

// Close the display when finished:

try {
    mDisplay.close();
} catch (IOException e) {
    // error closing display
}
```

License
-------

Copyright 2017 Roberto Leinardi

Licensed to the Apache Software Foundation (ASF) under one or more contributor
license agreements.  See the NOTICE file distributed with this work for
additional information regarding copyright ownership.  The ASF licenses this
file to you under the Apache License, Version 2.0 (the "License"); you may not
use this file except in compliance with the License.  You may obtain a copy of
the License at

  http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.  See the
License for the specific language governing permissions and limitations under
the License.

[jcenter]: https://bintray.com/leinardi/androidthings/driver-sh1106/_latestVersion