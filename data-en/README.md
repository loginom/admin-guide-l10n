# Loginom — Administrator Manual

The [Loginom](https://loginom.ru) analytical platform can be operated in server mode for teamwork, and as a desktop application for personal analytics.

## Teamwork

Server mode is available in Team, Standard and Enterprise editions.

![Editions for the teamwork](./lg_group.svg)

| Component | Designation |
|:----------|:-----------|
| [Server](./server/README.md) | Key platform element. It must be installed and can be used as a Windows service. Interaction of all platform components is performed by means of the Loginom Server. |
| [Integrator](./integrator/README.md) | The component required for publication of web services. It is operated with the Loginom Server. It must be installed and can be used as a Microsoft IIS service. |
| [Adapter](./adapter/README.md) | The component required for integration with non-standard web services. It must be installed and can be used as a Microsoft IIS service. |
| [Studio](./studio/README.md) | The client web application implementing user interface of the platform operation. Installation is not required, as interaction is provided through use of a browser. |

## Personal Analytics

Desktop components designated for stand-alone data processing using personal computers. Academic and Personal editions are available. They contain only one component - [Loginom Desktop](./desktop/README.md).

![Editions for Personal Work.](./lg_personal.svg)

They must be installed and can be used as Windows applications. 32-bit and 64-bit versions are available.
