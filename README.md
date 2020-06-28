# Cotton-Wool-Spots-Extraction
Cotton Wool Spots Extraction from fundus images

<b>Procedure</b>
<ol>
  <li>Reading the image using PIL library and reshaping the image</li>
  <li>Converting Image object to numpy array to extract layers (red & green) of the RGB image</li>
  <li>Selecting the green layer because it gives a high contrast grayscale image of the fundus image</li>
  <li>Selecting the red layer because in the red layer, the optic disc is clearly distinguishable</li>
  <li>Thresholding the red layer of the fundus image to detect bright regions which may be cotton wool spots and optic disc</li>
  <li>Morphological Closing the thresholded image to fill the small gaps in the thresholded image or to improve the shape of the thresholded regions</li>
  <li>Finding the contours present on the closed thresholded image of the red layer and selecting the contour with maximum area as the optic disc</li>
  <li>With this a rough estimation of the optic disc is obtained which can be used later to remove optic disc from the fundus image, because optic disc is usually confused to be a cotton wool spots because of the similarity in shape and colour</li>
  <li>With this one part of the process is completed, i.e., rough estimation of the optic disc</li>
  <li>Now again enhancing the green layer of fundus image to obtain the cotton wool spots</li>
  <li>First, the green layer of the image is median filtered to remove any salt and pepper noise</li>
  <li>Now, the median filtered image is closed to remove the blood vessels</li>
  <li>Non-linear enhancement of the morphologically closed green layer to enhance the bright regions more. (Gamma correction is performed)</li>
  <li>After gamma correction, entropy function is applied to characterize the texture of the image</li>
  <li>Scaling the entropy of the image and thresholding to obtain a B&W image of possible bright lesions.</li>
  <li>Median filtering the B&W image to remove any unnecessary dot like structures</li>
  <li>Then closing the filtered image to fill the gaps</li>
  <li>Again an estimated optic disc is obtained by performing before mentioned contour analysis.</li>
  <li>Both the optic discs obtained may not be same because of the noise and the effects resulted due to closing the B&W image.</li>
  <li>Both the estimated optic discs obtained are removed from the closed B&W image to obtain the possible cotton wool spots.</li>
  <li>Plotting the cotton wool spots on the original image.</li>
  <li>Results may not be completely accurate. Some non-CWS spots may be detected as CWS also.</li>
</ol>

<b>Things to Note:</b> </br>
* The fundus images have only cotton wool spots present in them but no other abnormalities
