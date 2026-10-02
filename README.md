# ARK STM32 projects

CubeMX and Keil MDK projects for the sibling ark_sdk repository. Clone both repositories into the same workspace; no symbolic links are used.

```text
workspace/
  ark_sdk/
  ark_stm32_projects/
    c8t6_demo/
    c8t6_microcar_soil/
    c8t6_usb_cdc/
    c8t6_xiaoyan_net/
```

The source snapshot retains .ioc/.mxproject, Core, Drivers, Middlewares, USB_DEVICE where applicable, startup assembly, .uvprojx, .uvoptx, RTE and debug configuration. .uvoptx is required by the SDK probe and flashing tools. CMSIS precompiled .lib/.a files are vendor inputs, not local output; keep their original licenses. SDK code remains in ark_sdk and is referenced by relative paths.

## Current workflow

Use c8t6_microcar_soil or c8t6_xiaoyan_net (SDK App c8t6_ark_net) with the maintained DTS workflow:

```powershell
cd ../ark_sdk
python -m studio.cli configure app/c8t6_microcar_soil --dry-run
python -m studio.cli configure app/c8t6_ark_net --dry-run
```

After editing a DTS, run configure without --dry-run to regenerate OF data and synchronize the selected source closure. Keil MDK, the required device packs and ARM compiler are needed for firmware builds. c8t6_demo and c8t6_usb_cdc retain legacy JSON-based application examples; their source references have been refreshed from the current SDK catalogs, but they are not maintained DTS Apps.

Generated Keil output directories, object files, firmware images, reports, local IDE sessions and logs are ignored. CubeMX-generated C/H files are versioned build inputs and must not be hand-edited. Third-party code retains its own licenses.

## Verification status

The network firmware rebuild passes. The soil-probe car currently exceeds configured Flash at link time; legacy demo/USB Apps still require DTS/API migration. These limitations are preserved and documented in [SOURCE-VERIFICATION.md](SOURCE-VERIFICATION.md), rather than changing hardware capacity or application behavior during source publication.
