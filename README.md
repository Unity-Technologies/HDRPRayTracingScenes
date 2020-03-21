# Unity startup DXR project
This repository contains a startup Unity Project that uses DXR. It allows you to start with Unity HDRP DXR.

You can clone the repository using tools like Git, Github Desktop, or Sourcetree. 

  | IMPORTANT                                                    |
  | ------------------------------------------------------------ |
  | This Project uses Git Large Files Support (LFS) which means that you can not download a zipped version using the green button on Github. Instead, you must Clone the Project with a version of git that has LFS. You can download Git LFS here: <https://git-lfs.github.com/>. |

You can also download the Project zip, with every file (including the LFS files), from the release section: https://github.com/Unity-Technologies/SmallOfficeRayTracing/releases.

# Unity version
This Project uses the real-time ray tracing feature released in preview in Unity. You can not use this Project for any production work. For more information about ray tracing in HDRP, see the [Documentation](https://docs.unity3d.com/Packages/com.unity.render-pipelines.high-definition@latest/index.html?subfolder=/manual/Ray-Tracing-Getting-Started.html).

Please use branch
- master for internal Unity development - works with the development version of Unity - HDRP 8.0.1 or higher
- release/2019.3 for Unity 2019.3.6f1 or higher and HDRP 7.3.1 or higher

# Requirements
NVIDIA RTX series card with the latest drivers [here](https://www.nvidia.com/Download/index.aspx?lang=com)
Windows 10 RS5 (Build 1809) or later

Ray tracing hardware acceleration is only available on certain graphics cards. The graphics cards with full support are:

NVIDIA Volta (Titan X)
NVIDIA Turing RTX (2060, 2070, 2080, and their TI variants)
NVIDIA also provides a ray tracing fallback for some other generation graphics cards:

NVIDIA Turing GTX (1660 and 1660 Ti)
NVIDIA Pascal (1060, 1070, 1080 and their TI variants)
If your computer has one of these graphics cards, it can run ray tracing in Unity.

Before you open Unity, make sure to update your NVIDIA drivers to the latest version, and also make sure your Windows version is at least 1809.

FAQ:
- I get "this application won't work on this computer" when running Unity.exe

You don't have all the files from the repository. This Project uses Git Large Files Support (LFS). Downloading a zip file using the green button on Github **does not work**. You must clone the Project with a version of git that has LFS, or download a zip from the [release section](https://github.com/Unity-Technologies/SmallOfficeRayTracing/releases). You can download Git LFS here: <https://git-lfs.github.com/>.



