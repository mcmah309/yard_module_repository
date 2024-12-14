```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Android utils"
args:
  optional:
    - android_platform
    - android_build_tools
    - include_volumes
```
```Dockerfile
# https://docs.flutter.dev/reference/supported-platforms
# https://developer.android.com/tools/releases/platform-tools

## For all the latest configs use `sdkmanager --list`

# https://developer.android.com/tools/releases/platforms
# e.g. "android-34"
ARG android_platform={{ android_platform | default (value="android-34") }} 
# https://developer.android.com/tools/releases/build-tools
# e.g. "34.0.0"
ARG android_build_tools={{ android_build_tools | default (value="34.0.0") }}

# Update the SDK manager and install necessary Android SDK components https://developer.android.com/tools/sdkmanager
RUN sdkmanager --update \
    && sdkmanager \
        # Install the Android SDK for the specified platform version (API level).
        "platforms;${android_platform}" \
        # Install platform-tools like adb (Android Debug Bridge)
        # This appear to not take a version
        "platform-tools" \
        # Install the specified version of build tools for compiling Android apps
        "build-tools;${android_build_tools}" \
        # Install the latest version of command-line tools for general SDK management tasks
        "cmdline-tools;latest"
        ## Extra
        # Install the latest version of the NDK (Native Development Kit) for compiling native code. Cant use "latest" here
        #"ndk;26.2.11394342"
        # Install the latest version of CMake. Cant use "latest" here
        #"cmake;3.22.1"

{% if include_volumes %}
VOLUME ["/root/.gradle/caches", "/opt/android-sdk"]
{% endif %}
```
