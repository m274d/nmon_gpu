# Change from the original fork:

Press 'a' or 'E' can show GPU status screen:

Use the new version lmon16n.c as base.
1. Fix CPU-wide view numbering issue (0-63,64-127). Not create a new row for 128-192 if you have 128 thread CPU.
2. Increase the max columns. (It seems not very useful.)
3. Improve GPU display with GPU-MHz.
4. Add the new makefile for ubuntu 18.04.

## compile and use on ubuntu 18.04
http://nmon.sourceforge.net/pmwiki.php?n=Site.CompilingNmon
1. Download the lmon.c and the makefile
2. Install the GCC C Compiler, ncurses development library and (if its not already available) Install the make command
  Debian / Ubuntu
    sudo apt-get update
    sudo apt-get install gcc*
    sudo apt-get install ncurses-dev*
    sudo apt-get install make
3. Run make and you have a new version in roughly 4 seconds. Ready to run.

reference: https://nanxiao.gitbooks.io/read-nmon-code-to-learn-analyzing-linux-performan/content/posts/nvidia-gpu-status.html

# nmon_gpu

This is Nigel Griffiths' `nmon` and `nmonchart` utilities updated for monitoring GPU memory.
http://nmon.sourceforge.net/pmwiki.php?n=Main.HomePage

Although the current code includes GPU support, I wanted to see and record GPU memory size rather than utilization. Also, I wanted the ability to show 8 GPUs instead of just 2.

I made some updates to the `16f` version of the code and included them in the `lmon.c` file in this repo.
Also, these changes required updating the `nmonchart` utility as well. Essentially the `GPU-MHz` was replaced with GPU memory stats.

Example screen with 2 GPUs here:

```
┌nmon─16j.dw──────────────────Hostname=dwendt-X299-ARefresh= 8secs ───16:42.
3 NVIDIA GPU Accelerator ──────────────────────────────────────────────────│
│ Driver Version:418.67    NVML Version: 10.418.67                         │
│ GPU  Memory       GPU-Util    Temp      Power                            │
│ No.  MiB          Proc Memory  °C       Watts    Name                    │
│  0     330/32478    0%   0%    40       24.73    Quadro GV100            │
│  1    1433/32470    0%   0%    43       25.90    Quadro GV100            │
│                                                                          │
│                                                                          │
│──────────────────────────────────────────────────────────────────────────│
```

You can build the source using the `build.sh` file.
Dependencies include `ncurses` and the `NVML` library from NVIDIA's installed CUDA/driver.

You can also just try the precompiled version here called `nmon_gpu`.

The `nmonchart` tool requires the `ksh` (Korn shell).

![gpu memory](gpu_memory.png)

