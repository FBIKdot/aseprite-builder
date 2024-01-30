# aseprite-window-x64-builder

Language: English | [中文](./locales/zh-cn.md)

These are 2 GitHub Workflow that builds Aseprite for Windows x64 bit, either building a specified version or automatically building of the lastest version. By using GitHub Actions, there is no need for manual compilation, and it does not include any malicious software.

Please review the [Aseprite EULA](https://github.com/aseprite/aseprite/blob/main/EULA.txt) before using it.

To comply with the Aseprite EULA, this workflow will not upload the compiled binary files to a publicly accessible space. The compiled binary files will be stored in the Releases as draft and only visible to the repository owner.

The compiled binary files cannot run without `libcrypto-1_1-x64.dll`, and currently, I don't know how to resolve this during compilation. The workflow will retrieve this missing DLL from https://github.com/feenkcom/libopenssl/releases and package it together. If you don't need it, you can replace, delete, or modify it according to your needs.

Star this repository if you think it is useful!
![](https://moe-counter.glitch.me/get/@FBIK.aseprite-window-x64-builder)

# Usage

Fork this repository and go to the Settings-Actions-General page of the forked repository.

Ensure these GitHub repository settings are configured correctly:

-   `Workflow permissions` is set to `Read and write permissions`
-   Allow all actions and reusable workflows

## Build a specified version

Visit https://github.com/aseprite/aseprite/releases to get the `tag`, whose release is your need. Then, open the Actions page of the forked repository, select `Build a specified version` on the left side, click Run workflow, and fill in the tags under the `the tag(version) of the Aseprite`. After clicking Run workflow, wait for the workflow to complete. Go to the Code-Releases of the forked repository and download the attachment under the newly generated draft.

## Automatic check update and Build

This workflow will check the lastest tag from local repository and Aseprite Offical repository. If the current version of the forked repository is different from the latest Aseprite Releases, it will automatically retrieve the latest tags and perform the compilation. It will generate a draft in the Code-Releases of the forked repository.

This workflow will automatically execute at Beijing time (UTC+8) 8:00. To enable it, edit .github/workflows/auto-build.yml and uncomment lines 3 to 5:

```
on:
  schedule:
  - cron: '0 0 * * *'
```
