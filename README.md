# Unity startup DXR project
This repository contains a startup Unity Project that uses DXR. It allows you to start with Unity HDRP DXR.

You can clone the repository using tools like Git, Github Desktop, or Sourcetree. 

  | IMPORTANT                                                    |
  | ------------------------------------------------------------ |
  | This Project uses Git Large Files Support (LFS) which means that you can not download a zipped version using the green button on Github. Instead, you must Clone the Project with a version of git that has LFS. You can download Git LFS here: <https://git-lfs.github.com/>. |

You can also download the Project zip, with every file (including the LFS files), from the release section: https://github.com/Unity-Technologies/SmallOfficeRayTracing/releases.

This Project uses the real-time ray tracing feature that experimentally released in Unity 2019.3b1. Use it with HDRP package version 7.1.1 or higher. You can not use this Project for any production work. For more information about ray tracing in HDRP, see the [Documentation](https://docs.unity3d.com/Packages/com.unity.render-pipelines.high-definition@latest/index.html?subfolder=/manual/Ray-Tracing-Getting-Started.html).

Caution: The master branch of this project works with the development version of Unity, please use branch release/2019.3 for gettting a version that is compatible with Unity 2019.3

Requirements:
- NVIDIA RTX series card with the latest drivers [here](https://www.nvidia.com/Download/index.aspx?lang=com)
- Windows 10 RS5 (Build 1809) or later


Installation:
- Install latest Unity 2019.3
- Clone the Project
- Launch Unity.exe
- The project is pre-configured to work with HDRP DXR

FAQ:
- I get "this application won't work on this computer" when running Unity.exe

You don't have all the files from the repository. This Project uses Git Large Files Support (LFS). Downloading a zip file using the green button on Github **does not work**. You must clone the Project with a version of git that has LFS, or download a zip from the [release section](https://github.com/Unity-Technologies/SmallOfficeRayTracing/releases). You can download Git LFS here: <https://git-lfs.github.com/>.



