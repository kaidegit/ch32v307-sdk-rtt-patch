import rtconfig
from building import *

# get current directory
cwd = GetCurrentDir()

# The set of source files associated with this SConscript file.

tag = cwd.split("-")[-1]

sdk_path = os.path.join(cwd, f"../ch32v307_sdk-{tag}/EVT/EXAM/SRC")
if not os.path.exists(sdk_path):
    print(f"Error: SDK path {sdk_path} does not exist.")
    Exit(1)

src = Glob(os.path.join(sdk_path, "Core", "*.c")) + \
    Glob(os.path.join(sdk_path, "Peripheral", "src", "*.c")) + \
    Glob("*.c") + Glob("*.S")

path = [
    os.path.join(sdk_path, "Core"),
    os.path.join(sdk_path, "Peripheral", "inc"),
    cwd
    ]

group = DefineGroup('Libraries', src, depend = ['PKG_USING_CH32V307_SDK_RTT_PATCH', 'PKG_USING_CH32V307_SDK'], CPPPATH = path)

Return('group')

