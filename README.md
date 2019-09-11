# Unity preview DXR
This repository contains a preview Unity Project that uses DXR.

You can clone the repository using tools like Git, Github Desktop, or Sourcetree. 

  | IMPORTANT                                                    |
  | ------------------------------------------------------------ |
  | This Project uses Git Large Files Support (LFS) which means that you can not download a zipped version using the green button on Github. Instead, you must Clone the Project with a version of git that has LFS. You can download Git LFS here: <https://git-lfs.github.com/>. |

You can also download the Project zip, with every file (including the LFS files), from the release section: https://github.com/Unity-Technologies/SmallOfficeRayTracing/releases.

This Project uses the real-time ray tracing feature that experimentally released in Unity 2019.3.a2. Use it with HDRP package version 7.1.1 or higher. You can not use this Project for any production work. For more information about ray tracing in HDRP, see the [Documentation](https://docs.unity3d.com/Packages/com.unity.render-pipelines.high-definition@latest/index.html?subfolder=/manual/Ray-Tracing-Getting-Started.html).

Requirements:
- NVIDIA RTX series card with the latest drivers [here](https://www.nvidia.com/Download/index.aspx?lang=com)
- Windows 10 RS5 (Build 1809) or later


Installation:
- Clone the Project or download the Project from the release section of Github and unzip it.
- Launch Unity.exe
- Create a new Project and select DXR High Definition RP (Preview) - Be sure you are to create the Project for at least Unity version 2019.2.0a5.

See usage here: https://github.com/Unity-Technologies/Unity-Experimental-DXR/blob/master/documentation/The%20Experimental%20DXR%20project%20manual.pdf

Unity Forum Link: https://forum.unity.com/threads/unity-experimental-hdrp-dxr.656092/

Note: You can use the binaries available in this repo with this branch from the SRP repo:
https://github.com/Unity-Technologies/ScriptableRenderPipeline/tree/experimental-dxr-release
This is the branch that the template Project includes in case you don't want to install the template Project.

FAQ:
- I get " this application wont work on this computer" when running Unity.exe

You don't have all the files from the repository. This Project uses Git Large Files Support (LFS). Downloading a zip file using the green button on Github **does not work**. You must clone the Project with a version of git that has LFS, or download a zip from the [release section](https://github.com/Unity-Technologies/SmallOfficeRayTracing/releases). You can download Git LFS here: <https://git-lfs.github.com/>.

- When installing the DXR Project template I get this error:

<img src = "https://github.com/Unity-Technologies/Unity-Experimental-DXR/blob/master/documentation/Error0.png" >

This is due to a Windows limitation that can't handle more than 260 character for filename. 
Use a shorter folder and Project name to allow the template to install correctly. Like "C:\DXR".



