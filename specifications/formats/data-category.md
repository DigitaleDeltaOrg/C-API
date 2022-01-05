# Data category

Measurements are diverse: the can consist of different elements wrapped together into a measurement.
To categorise this information, the C-API uses data classes, a typing of an element of a measurement.

The C-API supports by default:


## Data categories
| Data category     | Description                                                                                                                          |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| Quantity          | Quantity defines what was measured. I.e. count, volume, acidity, current.                                                            |
| Parameter         | Parameter defines what the subject under measurement was.<br />I.e. chloride, chlorofyl a, Goniada maculata.                         |
| MeasurementObject | Defines where the measurement took place.                                                                                            |
| MeasurementDate   | When the measurement took place.                                                                                                     |
| Value             | The observed or measured value.<br />There can be more than one value per measurement (i.e. observed and calculated).                |
| Unit              | The unit in which the measured value was expressed.<br />Each value in the measurement will have a different unit.                   |
| Compartment       | A measurement object can be divided into compartments to specify more where the data was taken.<br />I.e. air, surface water, organ. |
| AdditionalData    | Additional data, beyond the items above.<br />I.e. what apparatus used, length-class, analysis methods, life-form.                   |
