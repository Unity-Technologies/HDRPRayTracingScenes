# Unity preview DXR
This repository contains a preview DXR project.

You can clone the repository using the tool of your preference (Git, Github Desktop, Sourcetree, ...). 

  | IMPORTANT                                                    |
  | ------------------------------------------------------------ |
  | This project uses Git Large Files Support (LFS). Downloading a zip file using the green button on Github **will not work**. You must clone the project with a version of git that has LFS. You can download Git LFS here: <https://git-lfs.github.com/>. |

Project zip with all files (including LFS files) can be downloaded from the release section https://github.com/Unity-Technologies/SmallOfficeRayTracing/releases.

The Preview DXR project is a Unity custom version with binaries based on the 2019.2a5 version of Unity, enhanced with DXR support and version 5.8.0 of HDRP enhanced with DXR support. It is a Windows 10 (64 bit) only version with DX12 API.

This project is a sandbox in which you can  play with real time ray tracing features in Unity. This is a prototype and the final implementation of DXR will be different from this version. This project can not be used to do any production work.

Requirements:
- NVIDIA RTX series card with the latest drivers [here](https://www.nvidia.com/Download/index.aspx?lang=com)
- Windows 10 RS5 (Build 1809) or later


Install step:
Download the project from Github in the release section, unzip/Clone the project.
Launch Unity.exe
Create a new project and select DXR High Definition RP (Preview) - Be sure you are to create project for Unity 2019.2.0a5.

See usage here: https://github.com/Unity-Technologies/Unity-Experimental-DXR/blob/master/documentation/The%20Experimental%20DXR%20project%20manual.pdf

Unity Forum Link: https://forum.unity.com/threads/unity-experimental-hdrp-dxr.656092/

Note: The binaries available on this github can be use with this branch from SRP github:
https://github.com/Unity-Technologies/ScriptableRenderPipeline/tree/experimental-dxr-release
This is the branch that is included inside the template in case users want to avoid to install the template project.

FAQ:
- I get " this application wont work on this computer" when running Unity.exe

You don't have all the files from the repository. This project uses Git Large Files Support (LFS). Downloading a zip file using the green button on Github **will not work**. You must clone the project with a version of git that has LFS. You can download Git LFS here: <https://git-lfs.github.com/>. 

- When installing the DXR project template I get this error:

<img src = "https://github.com/Unity-Technologies/Unity-Experimental-DXR/blob/master/documentation/Error0.png" >

This is due to Windows limitation that can't handle more than 260 character for filename. 
Please use a shorter folder and project name to allow the template to install correctly. Like "C:\DXR"



