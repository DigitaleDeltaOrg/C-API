# Implementation differences

There are differences between DD-API implementations.

The DD-API installation used at HvD was not capable of filtering on parameters (not implemented), quantities (not implemented) or observation types (bugged).

To combat this problem, the plug-in must be fed with sufficient information regarding these to solve the differences.

The same applies to any other API or system. When implementation differences arise, the Connector is responsible for providing the plug-in with the required information.
