# Computer-Vision-

Consider the problem where you have a sequence of images, for example pictures of some  geographical areas  (forests, urban area, ice packs) taken from a plane or drone at different moments in time, and you need to detect changes in these areas.  

It could be changes due to deforestation, construction of new buildings, growth of transport infrastructure, natural hazards.

The position and camera angle at which the images have been taken are known approximately with an error that may vary within a certain range. Some patterns of the image can be repetitive (for example the groups of similar houses of urban area).​ 

The challenge is then to find the algorithm to overlay two images (taken at time t1, t2), corresponding to the same region of interest and then reveals the areas which changed over time. 

The second problem is to find groups of regions that have evolved in a similar way over time. For example, the similar complexes of new buildings or swimming pools, forests destroyed by fire or exploited by the logging industry etc. 

Here is an approach we want to try to solve the problem:

1. Split both images into tiles (similar to pixels)
2. For both images calculate the set of features, which can be: SURF, SIFT, FPFH etc.
To calculate the FPFH features use the brightness of given pixel as a 3-rd dimension in addition to x and y coordinates. Each pixel consider then as a point in 3D space  (x,y, normalized brightness).
3. Each feature assosiate with the tile, containing it. For each tile keep only one most representative feature.
Each tile  is then represented by the point in multi-dimensional  fetature-space.  (128 dimensional  for SIFT, 33-dimensional for FPFH)
5. Find the transformation matrix that overlays the two images in such a way, that maximizes the number of overlapping tiles with the same profiles in feature space. 
