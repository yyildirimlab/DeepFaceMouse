# DeepFaceMouse
Directory to two software tools used in ["DeepFace: A High-Precision and Scalable Deep Learning Pipeline for Predicting Large-Scale Brain Activity from Facial Dynamics in Mice"](https://pubmed.ncbi.nlm.nih.gov/40661434/).

Publish in Dr. Murat Yildirim's Lab at the Department of Neurosciences at the Cleveland Clinic Lerner Research Institute

<img width="1804" height="784" alt="image" src="https://github.com/user-attachments/assets/03cb4b01-2f87-4caf-9a33-62aa60626b6f" />


## [`mediaGUI`](https://github.com/khicken/mediaGUI)
Use this tool to preprocess gigabytes of facial video data to a single concatenated video, which is used to train DeepFace.

**Please see [mediaGUI](https://github.com/khicken/mediaGUI) for installation instructions.**

## [`sleapGUI`](https://github.com/khicken/sleapGUI)
This tool incorporates the optimized parameter combination specifically identified for large scale facial video analysis, enabling accurate and efficient large-scale orofacial data processing beyond the default SLEAP GUI.

**Please see [sleapGUI](https://github.com/khicken/sleapGUI) for installation instructions.**

## Comparision Video Between DeepFace Mouse, DeepLabCut (DLC), Facemap Basemodel, and Facemap Refined

https://github.com/user-attachments/assets/117a0c51-73cd-4746-b103-a9a76d137932

## Usage Demo
Tutorial Videos to Replicate DeepFace Mouse using your data:


[DeepFaceMouse Tutorial Playlist](https://youtube.com/playlist?list=PLdt5kwsCtktyiuk0OApIQvmhf9sebUfou&si=Aw92YegW4PX1jOuB)

## HPC Code
Attached here is the SLEAP based command lines that was used to do high performance computing analysis at Cleveland Clinic Lerner Research Institute using its avaliable GPU Type (A100) and Node Number (n = 2). 

[DeepFaceMouse_HPC_Script.txt](https://github.com/user-attachments/files/24003486/DeepFace_Mouse_HPC_Script.txt)


## Troubleshoot
If you have a technical question with either [`mediaGUI`](https://github.com/khicken/mediaGUI) or [`sleapGUI`](https://github.com/khicken/sleapGUI), then feel free to request a "New Issue" in the "Issues" section for the respective GUI. The issue will be addressed accordingly. 

## Citation
If you use any components from this repository in your research, please cite the DeepFaceMouse Publication.
