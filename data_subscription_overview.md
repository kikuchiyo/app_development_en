# Data Subscription Overview
EnOS System provides the data subscription service to improve the API calling efficiency of applications with active data push, which supports subscription to real-time asset data, asset alert data, and asset meta data. Benefiting from the data subscription service, applications do not need to call APIs repeatedly and frequently to get asset data. Instead, applications call APIs only when there are pushed data, thus improving API calling efficiency and reducing costs.

## Features
- **Multiple data source subscription**: Data subscription service supports multiple data sources such real-time asset data, asset alert data, etc.
- **Visualized configuration**: A GUI is available for users to customize the data subscription configuration, such as creating, configuring, starting, stopping, or deleting subscription topics.
- **Data subscription SDK**: Java SDK is provided for application developers to consume subscribed data.

## Advantages
- Decoupling data production and data consumption
- Rich set of data filtering conditions
- Cross-organization data subscription
- Supporting "at-least-once" message delivery semantics
- Pull consumption model, supporting traffic control of the client
- Supporting consumer groups (a topic can be consumed by multiple consumers repeatedly)

For detailed information about subscribing to asset real-time data and asset alert data for application development, see [Data Asset Management](https://www.envisioniot.com/docs/data-asset/en/latest/data_subscription_overview.html). 



