# Conda Recipe for libctl Nightly Build

## Steps to update

Whenever a new official `libctl` tarball is released on GitHub, `recipe/meta.yaml` requires the following changes:

1. Increment the version number (the `version` jinja variable). The nightly build should be one minor version above the most recent official release, followed by `.dev`. For example, if the current nightly package version is `4.3.1.dev`, and a new libctl `4.4.0` is released, the the nightly package version should become `4.4.1.dev`.

2. Reset the `buildnumber` jinja variable to `0`.

3. Verify that all `build`, `host`, and `run` dependencies are up to date in the `requirements` section.

4. Verify that the build steps in `recipe/build.sh` are up to date.

## Travis Cron Jobs

Every day, Travis CI will  run the job in https://github.com/Simpetus/trigger-nightly-builds. It will check for updates to libctl, and automatically push to this repository, bumping the `buildnumber`, if it finds any. That will in turn trigger a new package upload when CI for this repo runs. Manual updating is only required when a new version of libctl is released.

