# esp-idf-console-components
Components to add a serial console to ESP IDF projects

Include this as a submodule into the base of an ESP IDF project.  Then set `EXTRA_COMPONENT_DIRS` in the base CMakeLists.txt to use it.

To setup an run the console, add the `serial_console cmd_nvs cmd_system` components to the `REQUIRES` list in `idf_component_register`.
In main.c:
```
#include "serial_console.h"
#include "cmd_system.h"
#include "cmd_nvs.h"

void app_main() {

    // Setup and launch the serial console last
    init_serial_console();
    register_system();
    register_nvs();

    // This should never return
    run_serial_console();
}

```
