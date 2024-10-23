# KCGB-Complex
It contains images of four _Sebastes_ rockfishes ( _Sebastes atrovirens_, _S. carnatus_, _S. caurinus_, and _S. chrysomelas_) and codes for training and testing a VGGNet16 architecture for image discrimination. Here I describe the steps I took to generate the final dataset used for training and testing species discrimination with the VGGNet16. The description includes the input and output files for each step.

(1) Images per species were retrieved using the codes in the file _**Download_images.ipynb**_

(2) The images were then checked for inclusion in the final dataset of 1105 images. The accession link, geographic coordinates, date of capture, and observer name for each selected image can be found in the Excel file **_Photos_information.xslx_**

(3) As the download process in iNaturalist is in chronological order of submission, the photos retrieved will vary with time. I downloaded them on 10 October 2024. Here is the link to download the set of 1105 images I selected from iNaturalist on that day:
https://drive.google.com/drive/folders/1DE3Yj17RHk_OxubzQ6KLp6KWFuEU8hfc?usp=drive_link

There are 263, 275, 283, and 284 images of _Sebastes atrovirens_, _S. carnatus_, _S. caurinus_ and _S. chrysomelas_ respectively. 

(4) In each selected photo, fish bodies were delineated by polygons or bounding boxes, and species labels were added. These tasks were performed in the VGG Image Annotator. The coordinates of the bounding boxes, polygons, and species labels can be found in the file _**masks_and_labels.json**_

(5) The resulting JSON file from VGG Image Annotator was edited, as this tool appends the photo size to the photo name, resulting in something like "atrovirens_1.jpg123135". The photo sizes were removed from each photo using regular expressions in Notepad++.

(6) The 1105 selected images and the JSON file were uploaded to Google Drive for processing and analysis. From here, the following steps can be replicated by running the code in the file _**Processing_and_VGGNET16.ipynb**_

(7) The bounding box and polygon coordinates were used to create masks from each photo. These masks retain all pixel information within the area bounded by the polygons and bounding boxes. 

(8) The resulting masks were resized and sorted by species.

(9) Five augmentations (rotation, flip, random cropping, blur, and brightness) were performed on each of the 1105 masks. The resulting augmentations were also sorted by species.

(10) The augmentations were merged with the 1105 masks, resulting in a total of 6630 masks sorted by species.

(11) The 6630 normalized masks were used to create several trial datasets (600, 1800, and 3200 masks) for training and testing the VGGNet16 architecture.

(12) These trial datasets were sorted into training (80%) and testing (20%) subsets for the analyses. These trial datasets were used to evaluate the performance of the VGGNet16 architecture under different parameter settings before performing analyses with 6000 masks (4800 training and 1200 testing). The training datasets were divided into a training set (80%) and a validation set (20%) in each analysis.  The final 6000 masks used to train and test the VGGNet16 can be downloaded from Google Drive: 

** A) Training dataset of 4800 masks**
https://drive.google.com/drive/folders/1i_9xdl58TJ3ejudxmFPkga5YWvZ49dy2?usp=drive_link

**   B) Test dataset of 1200 masks**
  https://drive.google.com/drive/folders/1iZQxeLXC1SWUskPrR-b0YEf0S2uAZUri?usp=drive_link
  
(13) The _**Processing_and_VGGNET16.ipynb**_ file also contained results of one of the largest runs. 
