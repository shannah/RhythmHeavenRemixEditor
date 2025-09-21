# jDeploy Configuration for RHRE3

This project is configured to use [jDeploy](https://www.jdeploy.com) for creating cross-platform desktop app installers.

## What is jDeploy?

jDeploy is a tool that creates native installers for Java applications across Windows, macOS, and Linux platforms without requiring users to install Java separately.

## Current Configuration

The project includes:

- **package.json**: jDeploy configuration file
- **icon.png**: Application icon (256x256 PNG)
- **.github/workflows/jdeploy.yml**: GitHub Actions workflow for automatic builds

## Configuration Details

- **JAR Path**: `desktop/build/libs/RHRE-3.20.7.jar` (Shadow JAR)
- **Java Version**: 11+ (compatible with jDeploy)
- **Memory**: 1024MB (-Xmx1024m)
- **Main Class**: `io.github.chrislo27.rhre3.desktop.DesktopLauncher`
- **Framework**: libGDX (not JavaFX)

## Building Locally

To test the jDeploy setup locally:

1. Build the shadow JAR:
   ```bash
   ./gradlew :desktop:shadowJar
   ```

2. Install jDeploy (if not already installed):
   ```bash
   npm install -g jdeploy
   ```

3. Package the application:
   ```bash
   jdeploy package
   ```

## GitHub Actions

The project includes automated builds that:
1. Build the Java application
2. Create cross-platform installers
3. Publish to GitHub releases

### Optional DMG Creation

To enable macOS DMG creation with code signing:
1. Set the repository variable `JDEPLOY_CREATE_DMG` to `true`
2. Add the required secrets for code signing (see workflow file)

## Publishing

When tags are pushed, the GitHub Actions workflow will:
1. Build the application
2. Create platform-specific installers
3. Upload them to the GitHub release

## Installation Methods

Users can install RHRE3 in several ways:

1. **Direct Download**: Download platform-specific installers from GitHub releases
2. **NPM**: `npm install -g rhythm-heaven-remix-editor-3`
3. **jDeploy CLI**: `jdeploy install rhythm-heaven-remix-editor-3`

## Support

For jDeploy-specific issues, see:
- [jDeploy Documentation](https://www.jdeploy.com/docs)
- [jDeploy GitHub](https://github.com/shannah/jdeploy)