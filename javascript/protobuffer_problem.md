# Protobuffer Problem
================================

**Author**: Lien Chen  **Date**: 2020-09-24

* Using protobuffer and translate to javascript, deserialize with oneof type, only can get the number from oneof_case, cant get the type of the object.
* My solution:
    * add an enum to record the object is depend on which 
    * Now using getinterfaceCase and interfaceCase to now which type to use