# comlet Embedded Library (cEL)

A cEL is a pure software library that extends the capability of the [control environment](../control_env/index.md)
and therefore the possibilities for test automation[^1].
This can be done by providing interfaces to additional tools[^2] or implementing additional protocol layer to communicate
with the SUT[^3].

Each cEL brings along a well-defined, low-level keyword library for Robot Framework on top of which new (user) keyword libraries
may be implemented.

??? example "Examples for already available cEL"
    - OCR Library: Extends test cases with the power of text recognition (by [Tesseract](https://github.com/tesseract-ocr/tesseract){target="_blank"})
    - MAVLink Library: Extends test cases to communicate with airborne drones by [MAVLink](https://mavlink.io/){target="_blank"} protocol
    - SCPI Library: Extends test cases to be able to talk to various [SCPI protocol](https://en.wikipedia.org/wiki/Standard_Commands_for_Programmable_Instruments){target="_blank"}
      enabled hardware measurement devices
    - ADB Library: Extends test cases to be able to talk to mobile devices by [ADB](https://developer.android.com/tools/adb?hl=en){target="_blank"}
    - Qt Squish Library: Extends test cases to be able to utilize [Qt's Squish GUI testing tool](https://www.qt.io/quality-assurance/squish)
    - MQTT Library: Extends test cases to be able to talk to IIoT devices via MQTT
    - NETIO M2M JSON API Library: Extends test cases to be able to talk to [NETIO devices](https://www.netio-products.com/en)
      via their [M2M JSON API](https://www.netio-products.com/en/software/open-api){target="_blank"}
    - Cleware USB Multiplexer Library: Extends test cases to be able to control USB Multiplexer [by Cleware](https://www.cleware-shop.de/epages/63698188.sf/en_GB/?ViewObjectPath=%2FShops%2F63698188){target="_blank"}
    - Public Transport Protocol Library: Extends test cases to be able to communicate with IBIS-IP[^4] and ITxPT devices
    - XLM Schema Validation Library: Extends test cases to be able to validate XML strings against an XML schema

??? info "Do you need a library implemented?"
    We are happy to help you out if you have the need for a particular library implementation.
    Feel free to contact [our sales](mailto:sales@comlet.de?subject=cEL Inquiry) for further details.

[^1]: Besides the already available Robot Framework ecosystem
[^2]: Those tools need to run in the control environment as well
[^3]: Either via hardware interface already available (only on premise) and/or [cESD](../cesd/index.md)
[^4]: [VDV 301 Standard](https://www.vdv.de/ip-kom-oev.aspx){target="_blank"}