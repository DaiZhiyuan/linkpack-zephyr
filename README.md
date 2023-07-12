# About

linkpack code is a copy of netlib.org which can be found at the [netlib.org](https://netlib.org/benchmark), but ported to work using Zephyr OS.

Zephyr OS is the closest environment to run the linkpack in baremetal environment.

## How to run it

1. Install [Zephyr OS](https://github.com/zephyrproject-rtos/zephyr).

2. Clone/copy this repository inside of the `zephyrproject/zephyr`

3. In the above folder, type `west build -p always -b fvp_base_revc_2xaemv8a linkpack-zephyr && west build -t run`

Running linkpack-zephyr on ARM FVP:
```
$ west build -p always -b fvp_base_revc_2xaemv8a linkpack-zephyr
-- west build: making build dir /home/jerrydai/zephyr_project/zephyr/build pristine
-- west build: generating a build system
Loading Zephyr default modules (Zephyr base).
-- Application: /home/jerrydai/zephyr_project/zephyr/linkpack-zephyr
-- CMake version: 3.21.1
-- Found Python3: /home/jerrydai/zephyr_project/.venv/bin/python3 (found suitable exact version "3.8.10") found components: Interpreter
-- Cache files will be written to: /home/jerrydai/.cache/zephyr
-- Zephyr version: 3.4.0-rc3 (/home/jerrydai/zephyr_project/zephyr)
-- Found west (found suitable version "1.1.0", minimum required is "0.14.0")
-- Board: fvp_base_revc_2xaemv8a
-- ZEPHYR_TOOLCHAIN_VARIANT not set, trying to locate Zephyr SDK
-- Found host-tools: zephyr 0.16.1 (/home/jerrydai/zephyr-sdk-0.16.1)
-- Found toolchain: zephyr 0.16.1 (/home/jerrydai/zephyr-sdk-0.16.1)
-- Found Dtc: /home/jerrydai/zephyr-sdk-0.16.1/sysroots/x86_64-pokysdk-linux/usr/bin/dtc (found suitable version "1.6.0", minimum required is "1.4.6")
-- Found BOARD.dts: /home/jerrydai/zephyr_project/zephyr/boards/arm64/fvp_base_revc_2xaemv8a/fvp_base_revc_2xaemv8a.dts
-- Generated zephyr.dts: /home/jerrydai/zephyr_project/zephyr/build/zephyr/zephyr.dts
-- Generated devicetree_generated.h: /home/jerrydai/zephyr_project/zephyr/build/zephyr/include/generated/devicetree_generated.h
-- Including generated dts.cmake file: /home/jerrydai/zephyr_project/zephyr/build/zephyr/dts.cmake
Parsing /home/jerrydai/zephyr_project/zephyr/Kconfig
Loaded configuration '/home/jerrydai/zephyr_project/zephyr/boards/arm64/fvp_base_revc_2xaemv8a/fvp_base_revc_2xaemv8a_defconfig'
Merged configuration '/home/jerrydai/zephyr_project/zephyr/linkpack-zephyr/prj.conf'
Configuration saved to '/home/jerrydai/zephyr_project/zephyr/build/zephyr/.config'
Kconfig header saved to '/home/jerrydai/zephyr_project/zephyr/build/zephyr/include/generated/autoconf.h'
-- Found GnuLd: /home/jerrydai/zephyr-sdk-0.16.1/aarch64-zephyr-elf/bin/../lib/gcc/aarch64-zephyr-elf/12.2.0/../../../../aarch64-zephyr-elf/bin/ld.bfd (found version "2.38")
-- The C compiler identification is GNU 12.2.0
-- The CXX compiler identification is GNU 12.2.0
-- The ASM compiler identification is GNU
-- Found assembler: /home/jerrydai/zephyr-sdk-0.16.1/aarch64-zephyr-elf/bin/aarch64-zephyr-elf-gcc
-- Configuring done
-- Generating done
-- Build files have been written to: /home/jerrydai/zephyr_project/zephyr/build
-- west build: building application
[1/111] Preparing syscall dependency handling

[2/111] Generating include/generated/version.h
-- Zephyr version: 3.4.0-rc3 (/home/jerrydai/zephyr_project/zephyr), build: v3.4.0-rc3-72-ge1efafa31db9
[101/111] Linking C executable zephyr/zephyr_pre0.elf

[105/111] Linking C executable zephyr/zephyr_pre1.elf

[111/111] Linking C executable zephyr/zephyr.elf
Memory region         Used Size  Region Size  %age Used
           FLASH:          0 GB        64 KB      0.00%
             RAM:      137604 B         2 MB      6.56%
        IDT_LIST:          0 GB         2 KB      0.00%

$ west build -t run
-- west build: running target run
[0/1] FVP_Base_RevC-2xAEMvA:
terminal_0: Listening for serial connection on port 5000
terminal_1: Listening for serial connection on port 5001
terminal_2: Listening for serial connection on port 5002
terminal_3: Listening for serial connection on port 5003
*** Booting Zephyr OS build v3.4.0-rc3-72-ge1efafa31db9 ***
LINPACK benchmark, Double precision.
Machine precision:  15 digits.
Array size 100 X 100.
Memory required:  79K.
Average rolled and unrolled performance:

    Reps Time(s) DGEFA   DGESL  OVERHEAD    KFLOPS
----------------------------------------------------
      64   0.54  80.89%   4.82%  14.29%  24473.304
     128   1.08  80.78%   4.92%  14.30%  24499.819
     256   2.15  80.74%   4.83%  14.43%  24526.392
     512   4.31  80.74%   4.83%  14.43%  24533.044
    1024   8.62  80.73%   4.81%  14.46%  24536.371
    2048  17.24  80.77%   4.80%  14.43%  24529.718

LINPACK benchmark end.

Stopping simulation...

Info: /OSCI/SystemC: Simulation stopped by user.
```
