# KCGB-Complex
It contains images of four _Sebastes_ rockfishes ( _Sebastes atrovirens_, _S. carnatus_, _S. caurinus_, and _S. chrysomelas_) and codes for training and testing a VGGNet16 architecture to discriminate images. Here, I described the steps I followed to generate the final dataset used for training and testing species discrimination with the VGGNet16. The description includes the input and resulting files for each step.
(1) Images were retrieved per species using the codes in the file Dowload_images.ipynb. 
(2) Then, the images were inspected for their inclusion in the final dataset of 1105 images. The respective accession link, geographic coordinate, day of capture, and observer name for each selected photo can be found in the Excel file Photos_information.xslx 
(3) Since the downloading process is performed in chronological order of submission in iNaturalist, the photos retrieved will vary according to time. I downloaded them on 10th October 2024. Here, I provided the link to download the set of the 1105 images I selected from iNaturalist on that day:
https://drive.google.com/drive/folders/1DE3Yj17RHk_OxubzQ6KLp6KWFuEU8hfc?usp=drive_link

There, you can find 263, 275, 283, and 284 images of _Sebastes atrovirens_, _S. carnatus_, _S. caurinus_, and _S. chrysomelas_, respectively. 

(4) In each selected photo, fish bodies were delimitated by polygons or bounding boxes, and species labels were added. These tasks were performed in the VGG Image Annotator. The coordinates of the bounding boxes, polygons, and species labels are found in the file masks_and_labels.json
(5) The resulting JSON file from VGG Image Annotator was edited since this tool attaches the photo size to the photo name, resulting in something like "atrovirens_1.jpg123135. The photo sizes were erased from each photo using regular expressions in Notepad++.
(6) The 1105 selected images and the JSON file were uploaded to Google Drive for processing and analysis. From here, the following steps can be replicated by running the codes in the file Processing_and_VGGNET16.ipynb
(7) The coordinates of the bounding boxes and polygon were used to create masks from each photo. These masks keep all the pixel information in the delimited area by the polygons and bounding boxes. 
(8) The resulting masks were resized and sorted by species.
(9) Five augmentations (rotation, flip, random cropping, blur, and brightness) were performed for each of the 1105 masks. The resulting augmentations were also sorted by species.
(10) The augmentations were merged with the 1105 masks, obtaining a total of 6630 masks sorted by species.
(11) The 6630 normalized masks were normalized and used to create several trial datasets (600, 1800, and 3200 masks) for training and testing the VGGNet16 architecture.
(12) These trial datasets were sorted in training (80%) and testing (20%) subsets for the analyses. These trial datasets were used to assess the performance of the VGGNet16 architecture under different parameter settings before performing analyses with 6000 masks (4800 training and 1200 testing). The training datasets were divided into a train (80%) and validation (20%) set in each analysis.  The final 6000 masks used for training and testing the VGGNet16 can be downloaded from Google Drive: 
1) Training dataset of 4800 masks 
  https://drive.google.com/drive/folders/1i_9xdl58TJ3ejudxmFPkga5YWvZ49dy2?usp=drive_link
2) Test dataset of 1200 masks:
  https://drive.google.com/drive/folders/1iZQxeLXC1SWUskPrR-b0YEf0S2uAZUri?usp=drive_link
(13) The Processing_and_VGGNET16.ipynb file also contained results of one of the largest runs. 
