[image1]: ./WriteUpImages/colorthresh_1.png
[image2]: ./WriteUpImages/rock_finder_2.png



# Search and Sample Return
## Readme includes:
- Project Objective
- Code Location
- Code Analysis
- Video of code implementation
- Autonomous Results

## Project Objective:
 - Generate code to autonimously map a simulated enivroment
 - Search and identify samples of interest (rocks)
 - Bonus: Pick Rocks up
## Code Location:
 Completed code for his project can be found [here](https://github.com/ejbkdb/RoboND-Rover-Project/tree/master/code)

## Code Analysis:
 
- Obstacle Detection:
    Navigable areas were detected by utilizing a color threshold. Land > rgb(160,160,160) was determined to be navigable. 
    Non-Navigable areas are considered to be the inverse of navigable. 
    ![alt text][image1]
    
    Left image: Raw Input
    
    Right Image: output of navigable terrain (white) vs. Non-navigable terrain (black)
- Sample Detection:
   Created a new function that found pixels within a specific color range that was appropriate for rock detection (rock_finder).
   Utilized a HSV filter with the range H(0:179), S(130:255), V(51:255)
   
   ![alt text][image2]
 - Process Image Function Chain
   To complete the process image function chain the following steps were completed:
      - Filtered out the navigable terrain, obstacles, and samples
      - Converted the filtered image to rover coordinates
      - Converted Rover coordinates to world coordinates (based on robots pose)
      - Updated world map 
      - Video can be found [linkname](https://youtu.be/w0A5LTPbveA)
  
 ## Autonomous Navigation and Mapping
  - Perception_Step()
    The perception_step() process flow closely follows for process image function chain. The logic used allows the rover to identify
    identify navigable terrain, find obstacles, look for rocks and map its world. It does all of this while the rover is in 
    a 'flat' condition to avoid mapping issues.
 
    The perception_step() includes a limited amount of logic to bias the rovers movements to one side so it follows the wall. 
    This ensures that all areas are mapped effectively.
 
  - Autonomous Results
     Simulator was operated at 1024x768. FPS during simulation were 25FPS
 
     The rover completed the tasks of manuevering through its world, mapping its traversed path and identifying rocks of interest.
     Future improvements to the code can be made to attempt to pick up rocks and return them to home base. Smaller improvements 
     can be made to implement a steering alogorithm to reduce 'swaying' of rover.
     
     Video Results can be found [linkname](https://youtu.be/YJyuWVE5AOc)
  
  
