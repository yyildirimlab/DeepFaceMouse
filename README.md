# DeepFaceMouse
Directory to two software tools used in [DeepFaceMouse enables scalable prediction of large-scale brain activity from facial dynamics in mice](https://www.cell.com/cell-reports-methods/fulltext/S2667-2375(26)00180-3).

Published in Dr. Murat Yildirim's [Lab](https://www.lerner.ccf.org/neurosciences/yildirim/) at the Department of Neurosciences at  Cleveland Clinic Research

<img width="1804" height="784" alt="image" src="https://github.com/user-attachments/assets/03cb4b01-2f87-4caf-9a33-62aa60626b6f" />


## [`mediaGUI`](https://github.com/khicken/mediaGUI)
Use this tool to preprocess gigabytes of facial video data to a single concatenated video, which is used to train DeepFace.

**Please see [mediaGUI](https://github.com/khicken/mediaGUI) for installation instructions.**

## [`sleapGUI`](https://github.com/khicken/sleapGUI)
This tool incorporates the optimized parameter combination specifically identified for large scale facial video analysis, enabling accurate and efficient large-scale orofacial data processing beyond the default SLEAP GUI.

**Please see [sleapGUI](https://github.com/khicken/sleapGUI) for installation instructions.**

## DeepFaceMouse Pretrained Model

[Download Here](https://doi.org/10.5281/zenodo.20583481)

Note: Make sure you have the SLEAP Version 1.4.1 downloaded 

## Getting Started 
Tutorial Videos to Replicate DeepFace Mouse using your data:

[DeepFaceMouse Tutorial Playlist](https://youtube.com/playlist?list=PLdt5kwsCtktyiuk0OApIQvmhf9sebUfou&si=Aw92YegW4PX1jOuB)

**Video Part 1 Summary - Concatenation**

1. Open the Downloaded **mediaGUI**
 
2. Select the **Add Video** button to add a video

3. Repeat this step for all of the data intended for analysis.
   
4. Choose the specific number of frames needed to be extracted. Total number of frames that can be concatenated is 30k.
   Note: In the video, 5 videos were used to create a custom model. 30k frames / 5 videos = 6k frames per video was extracted evenly.
         Adjust the specific number of evenly extracted frames to how many videos you want to analyze.
   
5. Make the output fps match that of the frame speed of the raw video.
   Note: In the video, the data's frame rate was 30 fps. Adjust the frame rate depending on your experimental video acquistion speed.

6. Click **Process Videos** and save the output to the desired location

**Video Part 2 Summary - Face Model Creation**

1. Open Anaconda Prompt

2. Activate SLEAP enviornment

<pre>
<code>conda activate sleap</code>
</pre>


3. Open default SLEAP GUI for Labeling
  
<pre>
<code>sleap-label</code>
</pre>


4. Insert the Concatenated Video, which was created in Video Part 1

5. Go to the **Skeleton** Tab on the Bottom Right, and add 4 nodes/keypoints
6. Name the points the following: Top, Bottom, Right, Left, Nose_Top, Nose_Bottom, Mouth_Top, Mouth_Bottom, Whisker_T_L, Whisker_T_R, Whisker_B_R, Whisker_B_L
7. Click the **Edges** Tab on the Top Right, and add 2 edges from the keypoints by selecting the desired edge pairs below, then click the button **Add Edge**.

   Top - Bottom

   Right - Left

   Nose_Top - Nose_Bottom

   Mouth_Top - Mouth_Bottom

   Whisker_T_L - Whisker_T_R

   Whisker_B_R - Whisker_B_L

  
9. Next, go to **Labeling Suggestions** to extract the images needed to label. Use the default **sample** method so that it extracts the desired frame number evenly.

Note: In the tutorial, 5 videos were used to make the concatenated video. Therefore, 100 images are needed to be labeled (20 images per video, shown in the paper). So in the GUI, specify 99 frames (100 total frames - 1) to pick the first 99 frames, then scroll to the very last frame in the concatenated video, and select **Add current frame** to add the last frame. Total images labeled will remain at 100, ensuring that the frames are equally selected for training.

In the paper, 90 videos were used to create a concatenated video for DeepFaceMouse data, therefore 1800 images were used to label. 

9. Go to the fist blue box on the bottom left part of the GUI, which selects the first image that is needed to be labeled. Click **New Instance** on the bottom right, then it will show the points that have the edge connections. Drag the points to the desired location of the face.

10. Click the next blue box and select **New Instance**, it will generate the keypoints that were used in the previous frame. Just drag them to the new facial location, and continue this process until all of the blue boxes have the labeled images.

11. Once all of the frames are finished, save the SLEAP .slp file to the desired location.

12. Click **Predict**, then **Run Training**

13. Go to **Single Instance Model Configuration**, and select **baseline_large_rf.single(baseline_large_rf.single.json)** file on the top.

14. In the Model section on the Top Right, set the **Max Stride** and **Filters** to **64**

15. Put the **Input Scaling Factor** to **0.75** to capture the entire frame. Keep the other parameters the same.

16. Once the model parameters are set, click **Run** on the Bottom Right.

**Video Part 3 Summary - Large Scale Face Data Analysis**

1. Open Anaconda Prompt

2. Activate SLEAP enviornment

<pre>
<code>conda activate sleap</code>
</pre>


3. Open Custom GUI for Large Scale Orofacial Data Analysis
  
<pre>
<code>sleapgui face</code>
</pre>


4. Go to **Model Directory** to select the trained DeepFaceMouse model (Refer to Part 2 Video on how to create the DeepFaceMouse model)

5. Click **Add Videos** to add the raw orofacial video data (avi or mp4 video input) for anlaysis. Mutiple videos can be added for analysis. 

6. Once the video analysis is ready, click **Run All** to do the data analysis.

7. The output will be the following: SLEAP (.slp) file, Face Keypoint CSV file for further processing, and labeled video.


## HPC Code
Attached here is the SLEAP based command lines that was used to do high performance computing analysis at Cleveland Clinic Research using its avaliable GPU Type (A100) and Node Number (n = 2). 

[DeepFaceMouse_HPC_Script.txt](https://github.com/user-attachments/files/24003486/DeepFace_Mouse_HPC_Script.txt)


## Data Accessibility

DOI links to the data used in the paper.

[Figure 1b](https://doi.org/10.5281/zenodo.19636408)

[Figure 1c and d](https://doi.org/10.5281/zenodo.19635401)

[Figure 2c 6s DeepFaceMouse Results](https://doi.org/10.5281/zenodo.19636758)

[Figure 2c 6s DeepLabCut Results](https://doi.org/10.5281/zenodo.19636860)

[Figure 2c 6s Facemap Basemodel Results](https://doi.org/10.5281/zenodo.19636875)

[Figure 2c 6s Facemap Refined Results](https://doi.org/10.5281/zenodo.19636972) 

[Figure 2c 6f DeepFaceMouse Results](https://doi.org/10.5281/zenodo.19636979)

[Figure 2c 6f DeepLabCut Results](https://doi.org/10.5281/zenodo.19637002)

[Figure 2c 6f Facemap Basemodel Results](https://doi.org/10.5281/zenodo.19646814)

[Figure 2c 6f Facemap Refined Results](https://doi.org/10.5281/zenodo.19637463)

[Figure 2c 8m DeepFaceMouse Results](https://doi.org/10.5281/zenodo.19637052)

[Figure 2c 8m DeepLabCut Results](https://doi.org/10.5281/zenodo.19637502)

[Figure 2c 8m Facemap Basemodel Results](https://doi.org/10.5281/zenodo.19637094)

[Figure 2c 8m Facemap Refined Results](https://doi.org/10.5281/zenodo.19637132)

[Figure 3 DeepFaceMouse 180 Image Model](https://doi.org/10.5281/zenodo.19644500)

[Figure 3 DeepFaceMouse 900 Image Model](https://doi.org/10.5281/zenodo.19644438)

[Figure 3 DeepFaceMouse 1800 Image Model](https://doi.org/10.5281/zenodo.19644510)

[Figure 2c DeepFaceMouse 100Hz Model](https://doi.org/10.5281/zenodo.19644562)

[Figure 3 6s Brain Activity Results](https://doi.org/10.5281/zenodo.19637197)

[Figure 3 6f Brain Activity Results](https://doi.org/10.5281/zenodo.19637200)

[Figure 3 8m Brain Activity Results](https://doi.org/10.5281/zenodo.19644431)

[Figure 3 6s Brain Activity Data 20 Hz](https://doi.org/10.5281/zenodo.19646884)

[Figure 3 6f Brain Activity Data 20 Hz](https://doi.org/10.5281/zenodo.19637233)

[Figure 3 8m Brain Activity Data 20 Hz](https://doi.org/10.5281/zenodo.19637381)

[Figure 3 8m Brain Activity Data 100 Hz](https://doi.org/10.5281/zenodo.19637396)

[Figure 4 Disease Animal Results](https://doi.org/10.5281/zenodo.19637137) 

[Figure 4 DeepFaceMouse Social Interaction Model](https://doi.org/10.5281/zenodo.19644730) 

[Main Code Repository](https://doi.org/10.5281/zenodo.19644866) 


## Troubleshoot
If you have a technical question with either [`mediaGUI`](https://github.com/khicken/mediaGUI) or [`sleapGUI`](https://github.com/khicken/sleapGUI), then feel free to request a "New Issue" in the "Issues" section for the respective GUI. The issue will be addressed accordingly. 

## Citation
If you use any components from this repository in your research, please cite the DeepFaceMouse Publication.
