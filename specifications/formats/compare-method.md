# CompareMethod

The following, standard, compare methods are defined:


## Method details
| Method     | Description                                    | Works on data formats                 | QueryTypes                                 |
|------------|------------------------------------------------|---------------------------------------|--------------------------------------------|
| eq         | Equals (If StringType: case-**sensitive**)     | StringType, DateType, NumericType     | StringExact, StringWildCard, Numeric, Date |
| ne         | Not equals                                     | StringType, DateType, NumericType     | StringExact, StringWildCard, Numeric, Date |
| lt         | Less than                                      | StringType, DateType, NumericType     | StringExact, StringWildCard, Numeric, Date |
| le         | Less than or equal to                          | DateType, NumericType                 | Date, Numeric                              |
| gt         | Greater than                                   | DateType, NumericType                 | Date, Numeric                              |
| ge         | Greater than or equal to                       | DateType, NumericType                 | Date, Numeric                              |
| in         | List contains                                  | ArrayOfStringType, ArrayOfNumericType | StringExact, Numeric                       |
| notin      | List does not contain                          | ArrayOfStringType, ArrayOfNumericType | StringExact, Numeric                       |
| startswith | String starts with text (case-**insensitive**) | StringType                            | StringWildCard                             |
| like       | String contains text (case-**insensitive**)    | StringType                            | StringWildCard                             |
| endswith   | String ends with text (case-**insensitive**)   | StringType                            | StringWildCard                             |
