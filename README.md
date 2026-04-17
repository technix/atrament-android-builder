# atrament-android-builder

Android builder for Atrament, based on [hamdifourati/cordova-android-builder](https://github.com/hamdifourati/cordova-android-builder).

### Usage

The `cordova-android-builder` image expects your Cordova project to be mounted into the container at `/app`. You can then execute Cordova commands from within this directory.

First, pull the latest version of the image from Docker Hub:
```
docker pull frenzytechnix/atrament-android-builder:latest
```
Navigate to your Cordova project's root directory on your host machine. Then, run the Docker container, mounting your project and executing the build command:
```
docker run --rm -v "$(pwd):/app" frenzytechnix/cordova-android-builder:latest /bin/bash -c "cd /app && cordova platform add android && cordova build android --release"
```

After the command completes, your generated APK file(s) will be available in your host machine's `platforms/android/app/build/outputs/apk/release/` (or `debug/`) directory within your Cordova project.

### Running Cordova Commands

You can run any Cordova CLI command by replacing `cordova build android` with your desired command.

Example: Prepare the Android platform
```
docker run --rm -v "$(pwd):/app" frenzytechnix/atrament-android-builder:latest /bin/bash -c "cd /app && cordova prepare android"
```
Example: List Cordova plugins
```
docker run --rm -v "$(pwd):/app" frenzytechnix/atrament-android-builder:latest /bin/bash -c "cd /app && cordova plugin ls"
```

### Interactive Shell

If you want to explore the environment or debug, you can open an interactive shell inside the container:
```
docker run --rm -it -v "$(pwd):/app" frenzytechnix/atrament-android-builder:latest /bin/bash
```

Once inside, you can navigate to `/app` and run Cordova commands directly. Type `exit` to leave the shell.

## 🐳 Docker Hub

The `atrament-android-builder` Docker image is publicly available on [Docker Hub](https://hub.docker.com/r/frenzytechnix/atrament-android-builder).

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

