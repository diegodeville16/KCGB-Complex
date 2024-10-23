# KCGB-Complex
It contains images of four Sebastes rockfishes and codes for training and testing a VGGNet16 architecture to discriminate images.
1105 images retrieved from iNaturalist. Images were retrieved per species using the codes in XXXXX and inspected for their inclusion in the final dataset of 1105 images. The respective accession link, geographic coordinate, day of capture, and observer name for each photo can be found in the Excel file XXXXX. 
There are 263, 275, 283, and 284 images of Sebastes atrovirens, S. carnatus, S. caurinus, and S. chrysomelas, respectively. 
Fish bodies were delimitated by polygons or bounding boxes and each photo was labeled under one of the four species. These tasks were performed in VGG Image Annotator.
The code for creating masks from the original images of iNaturalist, resizing, normalizing, and sorting them by species is found in the "Processing and VGGNET16.ipynb" file.
The final 6000 masks used for training and testing the VGGNet16 can be downloaded from google drive: 
1) Training dataset of 6000 masks 
  https://drive.google.com/drive/folders/1i_9xdl58TJ3ejudxmFPkga5YWvZ49dy2?usp=drive_link
2) Test dataset of 1200 masks:
  https://drive.google.com/drive/folders/1iZQxeLXC1SWUskPrR-b0YEf0S2uAZUri?usp=drive_link
