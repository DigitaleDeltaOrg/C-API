# Introduction

In the world of measurements many standards and software-specific interfaces exist, suited for specific circumstances.

To name a few in the water domain-world in the Netherlands:

* [DD-API](https://github.com/DigitaleDeltaOrg/dd-api) for timeseries-based measurements
* [DD-ECO-API](https://github.com/DigitaleDeltaOrg/dd-eco-api) for observation-based measurements
* [Z-INFO](https://www.hetwaterschapshuis.nl/z-info) for waste-water management, also observation-based

These standards and systems allow retrieval of measurement data in some form.

Timeseries-based measurements are used in (mostly) automated measurement systems.
Observation-based measurements are used in situations where the measurements are not performed with fixed time intervals, or where measurements need extra steps, i.e. laboratory situations.

These systems deal with water-management in some form.
In our connected world, the data from these diverse systems needs to be combined to be able to produce meaningful data.

But combining the data from these systems is not a trivial task. The systems have different query interfaces, different naming conventions, different export formats, etc. Some provide data in smaller sections (paging).
Manually combining the data is error-prone, and since decisions may be made based on that data, this can potentially be harmful.
