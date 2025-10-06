This is a method of object identification in images. It is an artesianal method of computer vision. [opencv documentation](https://docs.opencv.org/3.4/da/df5/tutorial_py_sift_intro.html)

**Key Steps**
- Identify key points and their descriptors(things that may uniquely define that point)
- Match key points
After processing the template image an identify key points, key points in the query images are identified. Key points are identified with a difference of Gaussian scheme which approximates the Laplacian of Gaussian's. 

Key points are identified with their position, scale, and its descriptors. Larger DoG will have larger scale key points

All of the key points and their descriptors are stored in lists associated with their own images. The descriptors of the key points are the local gradients of the pixels
>[!question]
>Does it have to be gray scaled if we are only interested in the intensity gradients

#### Descriptors
Find all of the gradients at each point in the local area. Unravel and concatenate the local area in to a list. From there generate a histogram which is a sum of the magnitude of the gradients for each discrete direction.

>[!question]
>How do you pick the size of the bins at each angle. This might naturally happen too because of the discretization of the intensity from 0-255

To make the identification invariant to rotation, the orientation of the descriptor is oriented such that the direction with the largest magnitude is reset to zero degrees.

>[!question]
>Is this form of identification immune to changes in lighting? I would assume that different lighting would result in different magnitudes of the local gradients. 

>[!solution]
>Since we are not looking directly at the intensity but at the changes in intensity, it becomes slightly more immune to noise.

### Matching Key Points

Going through key points, you find Euclidean distances between other key points
$$
(T_{d} - Q_{d})^T(T_{d} - Q_{d})
$$
A brute force approach would be to compare each point with every other point, but it is very computationally expensive.


Once we have found the smallest euclidean distances between the two key points,  a match listing is created where key points in each image are matched.

To identify where the object is in the query image,  an affine transform (accounts for any rotation, scaling, translation, or skewing of the object in the query image) is created between the matched key points in the template to the query. Given four of the key points, we need to find the best homography that results in the best mapping (the euclidean distance between the known matched key points is minimized).

**RANSAC** is able to select 4 key points and create a homography. It will find how many inliers and outliers the homography produces.
