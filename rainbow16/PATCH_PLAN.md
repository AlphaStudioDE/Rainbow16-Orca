\# Rainbow16 patch plan



This folder contains Rainbow16 planning notes and future patch documentation.



Important naming note:

Names used in planning documents are examples only.

When implementing code, final function, class, option and file names must follow the naming style already present in OrcaSlicer and in the existing Rainbow16 project.



Current implementation strategy:

1\. Keep Snapmaker U1 as Snapmaker U1.

2\. Do not globally treat Snapmaker U1 as a BBL/Bambu printer.

3\. Add Rainbow16 as an optional mode.

4\. When Rainbow16 is disabled, OrcaSlicer must behave normally.

5\. When Rainbow16 is enabled, Snapmaker U1 should expose 16 logical colors.

6\. Rainbow16 logical colors should map to 4 physical U1 toolheads and Rainbow16 lanes.

7\. Use AMS mapping only as a reference, not as a full Bambu behavior copy.

8\. Keep Bambu networking, Bambu device tab and Bambu-specific upload logic disabled for Snapmaker U1.

9\. Prefer small isolated patches that are easy to rebase on future OrcaSlicer releases.

