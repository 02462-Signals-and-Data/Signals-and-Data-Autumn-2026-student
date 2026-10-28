# Issues installing fasttext

Previously, there have been problems with installing fasttext...

As with all problems of the same caliber, these have been focused on Mac and Windows users, though this *may* be one that the Mac users can actually solve easier.

There appears to be two main problems during installation:

1. Error caused by missing C++ compiler:
```
      RuntimeError: Unsupported compiler -- at least C++17 support is needed!

      hint: This usually indicates a problem with the package or the build environment.
  help: If you want to add the package regardless of the failed resolution, provide the `--frozen` flag to skip locking and syncing.
```
2. Error caused by fucky-wucky fasttext stuff:
```
         44 | #include <Python.h>
            |          ^~~~~~~~~~
      compilation terminated.
      error: command '/usr/bin/x86_64-linux-gnu-g++' failed with exit code 1

      hint: This error likely indicates that you need to install a library that provides "Python.h" for `fasttext@0.9.3`
  help: If you want to add the package regardless of the failed resolution, provide the `--frozen` flag to skip locking and syncing.
```

---

## Both errors potentially addressed by this:

Using `fasttext-wheel`, instead of `fasttext`. This has resolved the missing `Python.h` error; it may also help with compiler-related installation failures. So `uv add fasttext-wheel`, `pip install fasttext-wheel` and whatnot...

---

## Otherwise, look here:

1.  is addressed linux- and mac-wise [here](https://stackoverflow.com/questions/76528152/pip-install-error-runtimeerror-unsupported-compiler-at-least-c11-support). Basically, one or more of two commands need to be run:

```bash
sudo apt install build-essential
```

```bash
sudo apt install g++
```

For windows, this is mentioned [here](https://stackoverflow.com/questions/40504552/how-to-install-visual-c-build-tools). It appears to needs to be done through the "Microsoft Visual C++ Build Tools". Guide on installation found [here](https://github.com/bycloudai/InstallVSBuildToolsWindows?tab=readme-ov-file). They need to be downloaded from [here](https://visualstudio.microsoft.com/visual-cpp-build-tools/). Run an installer and then choose to install them afterwards.

Update: [Alternate download link](https://visualstudio.microsoft.com/downloads/#title-build-tools-for-visual-studio-2022)

2. This issue appears to be a mixture of [outdated build reqiurements on the side of fasttext](https://github.com/astral-sh/uv/issues/12437) and [fasttext 'secretly' depending on pip](https://github.com/astral-sh/uv/issues/1446). Most issues appear to be focused on Poetry users. Changing build tools did not resolve the issue during earlier troubleshooting.

   - **Using `fasttext-wheel` appears to solve the issue.**
   - **As does installing pip "natively", I.E. `sudo apt install python3-pip`, On Windows, ensure pip is installed in the Python environment you are using.**
     - **Conda environments have not been verified for this workaround; using UV’s pip alone did not resolve the issue during earlier troubleshooting.**

## If installation fails

Try `fasttext-wheel` first, then use the platform-specific troubleshooting steps above if needed.