\# Rainbow16 code map



This document tracks code areas relevant to Rainbow16 support.



Important naming note:

Names used here are planning examples only. Final function, class, option and file names must follow OrcaSlicer naming style and any Rainbow16 code already implemented in this repository.



\## Confirmed strategy



Rainbow16 must not globally turn Snapmaker U1 into a BBL/Bambu printer.



Correct direction:

\- Keep Snapmaker U1 as Snapmaker U1.

\- Add optional Rainbow16 mode.

\- Borrow/adapt AMS-style filament mapping only where needed.

\- Do not enable Bambu networking, Bambu device tab, Bambu upload logic or Bambu-specific printer behavior for Snapmaker U1.



\## Important files and findings



\### src/libslic3r/PresetBundle.hpp



Relevant area:



\- `VendorType get\_current\_vendor\_type();`

\- `bool is\_bbl\_vendor()`

\- `bool use\_bbl\_network();`

\- `bool use\_bbl\_device\_tab();`



Potential future place for a Rainbow16 helper function.



Example planning names only:

\- `is\_rainbow16\_enabled()`

\- `use\_rainbow16\_mapping()`

\- `use\_rainbow16\_filament\_mapping()`



Final names must be adjusted to match OrcaSlicer style.



\### src/libslic3r/PresetBundle.cpp



Relevant area:



\- `PresetBundle::use\_bbl\_network()`

\- `PresetBundle::use\_bbl\_device\_tab()`



Important:

Do not extend these functions to Rainbow16.



These functions are Bambu network/device related and should remain BBL-only.



\### src/slic3r/GUI/Plater.cpp



Relevant area:



\- `Sidebar::should\_show\_SEMM\_buttons()`



Current logic:

\- show SEMM buttons when `single\_extruder\_multi\_material` is enabled or vendor is BBL.



Future Rainbow16 idea:

\- Rainbow16 mode may need these add/delete filament controls for Snapmaker U1 without pretending Snapmaker is BBL.



\### src/libslic3r/GCode/ToolOrdering.cpp



Relevant area around `reorder\_filaments\_for\_minimum\_flush\_volume(...)`.



Current logic:

\- BBL printers use `filament\_maps`.

\- non-BBL printers use `maps\_without\_group`.



Current comment:

\- non-bbl printers do not support filament group yet.



This is a likely core place for Rainbow16 later.



Future Rainbow16 idea:

\- allow Rainbow16-enabled Snapmaker U1 to use filament grouping / filament maps without enabling all BBL behavior.



\### Other relevant search targets



\- `filament\_map`

\- `filament\_map\_mode`

\- `sync\_ams\_list`

\- `AMSMapInfo`

\- `SyncAmsInfoDialog`

\- `DevMappingUtil::ams\_filament\_mapping`

\- `SnapmakerPrinterAgent`



\## Safety rule



Do not replace broad `is\_bbl\_vendor()` checks globally.



Only replace or extend checks where the feature is specifically about filament mapping / logical filament grouping.



Never extend Bambu network/device/upload code to Rainbow16.

