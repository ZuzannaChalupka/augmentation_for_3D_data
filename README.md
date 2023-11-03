# augmentation_for_3D_data
***each photo has been blurred at the request of the principal***


I had a problem with too small a dataset to effectively learn neuronal networks. In my dataset were two types of pictures .png with RGB pictures and .tiff with the point cloud. If I connect these two files, I have an RGBD picture. I had to do an artificial dataset which is augmentation.

Input:
* background photo ->two files with the same name but different extensions (RGB and Deep photo)
* object photo ->two files with the same name but different extensions (RGB and Deep photo)
* mask to object

When I want to make augmentation with RGBD data is very important to remember about scale of the product, when I want to paste a big object in a very deep place in the background photo this big object will become small. I made a diagram of what is happening in the program:
1. draw by lot for the background photo
2. draw by lot how many objects will be placed on the background (1-5)
3. draw by lot for random objects in different folders with masks for them 
4. check the original measurements of the object (height, width and deep)
5. draws by lot a point in a deep picture, where paste a new object, next check deep in this point and draw by a lot of 50 to 300 value. The value is used to subtract it from the deep value at this point in the original background. This is very important because if I don't check it I can blend the object into the background 
6.  use a matrix camera to calculate new measurements of the object

 <p align="center">
  <img src="https://github.com/ZuzannaChalupka/augmentation_for_3D_data/assets/50628242/5e9c7f0e-941a-4418-9035-cf08c4f5e1c7" alt="Opis obrazka" />
</p>

7. add new point cloud of object to point cloud of background

<p align="center">
  <img src="https://github.com/ZuzannaChalupka/augmentation_for_3D_data/assets/50628242/92abe413-53eb-4872-92a0-738ebe8f3a45" alt="Opis obrazka" />
</p>

8. when I know a new new measurements of the object, I resize an RGB photo object and paste it to the same place like a deep photo place
photo 
<p align="center">
  <img src="https://github.com/ZuzannaChalupka/augmentation_for_3D_data/assets/50628242/6828d5c2-0af3-495e-9021-f89b0565dea7" alt="Opis obrazka" />
</p>

Outpu:
* RGB photo with new object

<p align="center">
  <img src="https://github.com/ZuzannaChalupka/augmentation_for_3D_data/assets/50628242/6828d5c2-0af3-495e-9021-f89b0565dea7" alt="Opis obrazka" />
</p>

  
* Deep photo with new object
  
<p align="center">
  <img src="https://github.com/ZuzannaChalupka/augmentation_for_3D_data/assets/50628242/92abe413-53eb-4872-92a0-738ebe8f3a45" alt="Opis obrazka" />
</p>

* RGBD photo with new object

<p align="center">
  <img src="https://github.com/ZuzannaChalupka/augmentation_for_3D_data/assets/50628242/f82958d9-e0f2-44a7-9b4a-eb242069ad4a" alt="Opis obrazka" />
</p>


* Photos with masks, each type of object had its own dedicated value for the mask

