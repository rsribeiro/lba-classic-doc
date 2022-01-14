Compile
=======

Prerequisites
-------------

- `Open Watcom v2 <https://github.com/open-watcom/open-watcom-v2>` - C/C++ Compiler capable of building DOS applications
- `MASM (Microsoft Macro Assembler)` - For compiling assembler files

Getting prerequisites and sources
---------------------------------

https://visualstudio.microsoft.com/pt-br/vs/community/

The prerequisites are freely available, MASM as part of `Visual Studio Community <https://visualstudio.microsoft.com/pt-br/vs/community/>` (Tested with version 2022). Both can be installed at their default locations.

For Open Watcom, be sure to select full instalation and to modify environment variables later.

To get the sources, clone https://github.com/2point21/lba1-classic-community into some folder.

Environment configuration
-------------------------

Create or edit the file ``SETENV.BAT`` on the ``lba1-classic-community`` repository folder, with the following content, making sure to double check if the Microsoft Visual Studio Community and Open Watcom folders are the same on your system.

::
   @echo off
   echo LBA Build Environment
   call "C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Auxiliary\Build\vcvarsamd64_x86.bat"
   call C:\WATCOM\owsetenv.bat
   SET LIB386_PATH=%CD%\LIB386
   SET INCLUDE=%LIB386_PATH%;%INCLUDE%

Build
-----

In a Windows command prompt inside the ``lba1-classic-community`` repository folder, run

::
   cd LIB386\LIB_3D
   wmake

   cd ..\LIB_CD
   wmake

   cd ..\LIB_MENU
   wmake

   cd ..\LIB_MIDI
   wmake

   cd ..\LIB_MIX
   wmake

   cd ..\LIB_SAMP
   wmake

   cd ..\LIB_SVGA
   wmake

   cd ..\LIB_SYS
   wmake

   cd ..\..\SOURCES
   wmake
   link

The expected output is the ``LBA0.exe`` executable inside the SOURCES folder.

Run
---

To run the game, you will need some assets of the original game and the ``LBA0.exe`` executable.

-  copy HQR files,
-  copy ``M_SB16.DLL``, ``S3.DLL``, and ``W_SB16.DLL``,
-  copy ``LBA.CFG``,
-  ``LBA0.exe``,

into some directory. The compiled file was verified to run with ``DOSBox Staging <https://dosbox-staging.github.io/>``.