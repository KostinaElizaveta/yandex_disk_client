Linux/OSX	Windows
Build Status	Build Status
This is a gate file to Hunter package manager.

Usage

Copy file HunterGate.cmake to project
Include gate file: include("cmake/HunterGate.cmake")
Put any valid Hunter archive with SHA1 hash:
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.7.0.tar.gz"
    SHA1 "e730118c7ec65126398f8d4f09daf9366791ede0"
)
Usage (custom config)

Optionally custom config.cmake file can be specified. File may has different locations:

GLOBAL. The one from Hunter archive:
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.7.0.tar.gz"
    SHA1 "e730118c7ec65126398f8d4f09daf9366791ede0"
    GLOBAL myconfig
        # load `${HUNTER_SELF}/cmake/configs/myconfig.cmake` instead of
        # default `${HUNTER_SELF}/cmake/configs/default.cmake`
)
LOCAL. Default local config.
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.7.0.tar.gz"
    SHA1 "e730118c7ec65126398f8d4f09daf9366791ede0"
    LOCAL # load `${CMAKE_CURRENT_LIST_DIR}/cmake/Hunter/config.cmake`
)
FILEPATH. Any location.
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.7.0.tar.gz"
    SHA1 "e730118c7ec65126398f8d4f09daf9366791ede0"
    FILEPATH "/any/path/to/config.cmake"
)
Example
Notes

If you're in process of patching Hunter and have a HUNTER_ROOT pointed to git repository location then HunterGate will not use URL and SHA1 values. It means when you update SHA1 of Hunter archive new commits/fixes will not be applied at all. In this case you have to update your git repo manually (i.e. do git pull)
You don't need to specify hunter_config command for all projects. Set version of the package you're interested in - others will be used from default config.cmake.
If you want to get full control of what Hunter-SHA1 root directories you want to auto-install you can set HUNTER_DISABLE_AUTOINSTALL environment variable and use HUNTER_RUN_INSTALL=YES CMake variable to allow installations explicitly.
Effects

Try to detect Hunter:
test CMake variable HUNTER_ROOT (control, shared downloads and builds)
test environment variable HUNTER_ROOT (recommended: control, shared downloads and builds)
test directory ${HOME}/.hunter (shared downloads and builds)
test directory ${SYSTEMDRIVE}/.hunter (shared downloads and builds, windows only)
test directory ${USERPROFILE}/.hunter (shared downloads and builds, windows only)
Set HUNTER_GATE_* variables
Include Hunter master file include("${HUNTER_SELF}/cmake/Hunter")
Flowchart (for developers)

flowchart

Examples

This
Simple
Weather
Links

Hunter
Some packages
