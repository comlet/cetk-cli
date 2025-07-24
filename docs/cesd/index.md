# comlet Embedded Simulation Device (cESD)

A cESD is an embedded device, provided by comlet, that extends the control environment's capabilities to connect to and
communicate with the SUT interfaces. It is used whenever a pure software library like a [cEL](../cel/index.md) is not enough
(e.g., because the physical layer is missing or a certain timing is needed).

## On Premise

With the [on premise control environment](../control_env/index.md), the cESD is mainly used to connect to the SUT
by a low level hardware interface that is not available through the on premise host (or any kind of third-party adapter).

Communication between the control environment and SUT is established by REST API that is unique and specialized
for the respective hardware interface.

??? example "Examples for already available cESD"
    - Relay: This cESD offers up to three relais to be opened and closed
    - DAC: This cESD offers up to two 8 channel 12 Bit digital analog converter

## Cloud

For the [cloud service control environment](../control_env/cloud.md), the cESD is the bridge between the public network
to the cloud service and the internal company network where the SUT is usually part of. Therefore, a cESD is also the only
connection to the SUT's interfaces.

The communication protocol in this context is MQTTS.

---

??? info "Do you need an interface engineered?"
    We are happy to help you out if you have the need for a particular interface implementation.
    Feel free to contact [our sales](mailto:sales@comlet.de?subject=cESD Inquiry) for further details.