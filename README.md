# Machine Learning Engineer Nanodegree
## Capstone Proposal
Michael Virgo  
February 12, 2017

## Using Deep Learning to Detect Lane Lines

### Domain Background

One of my primary areas of focus, and in fact the reason I decided to do the Machine Learning nanodegree originally, is self-driving cars. Although autonomous vehicles have been fantasized about and even attempted almost since the advent of the automobile, they have really began to pick up steam in the past couple of years, with both the incumbent players making moves as well as many technology companies. Self-driving cars use a blend of machine learning, computer vision and various other areas in order to take over the actions of a human driver, providing for safer and more reliable travel. There are many other important benefits, including potential easing of traffic congestion and potential to lower pollution if concepts like ride-sharing continue to increase in use.

As part of the first term of the separate self-driving car nanodegree program, I was tasked with using many different computer vision techniques that require a decent amount of manual input and selection to arrive at the end result (see my Advanced Lane Lines project [here](https://github.com/mvirgo/Advanced-Lane-Lines)). With the knowledge gained from the Machine Learning nanodegree, and some of the Deep Learning course on Udacity's website, I wondered if there might be a better approach to this problem - one directly involving deep learning. Deep learning involves utilizing multiple-layered neural networks, which use mathematical properties to minimize losses from predictions vs. actuals to converge toward a final model, effectively learning as they train on data.

####Why this matters

You may say that a fully autonomous vehicle might not necessarily need to directly identify the lane lines - it might otherwise just learn that there are boundaries it is not meant to cross, but not see them as much different from other types of boundaries. If we're skipping straight to a fully autonomous vehicle, this may be true. However, for many consumers, they will likely see more step-by-step changes, and showing them (potentially on an in-vehicle screen) that the car can always sense the lanes will go a long way in getting them comfortable with a computer doing the driving for them. Even short of this, enhanced lane detection could alert an inattentive driver when they drift from their lane.

### Problem Statement

Human beings, when fully attentive, do quite well at identifying lane line markings under most driving conditions. Computers are not inherently good at doing the same. However, humans have a disadvantage of not always being attentive (whether it be because of changing the radio, talking to another passenger, being tired, under the influence, etc.), while a computer is. As such, if we can train a computer to get as good as a human at detecting lane lines, since it is already significantly better at paying attention full-time, the computer can take over this job from the human driver. From the computer's perspective, the problem is around detecting a line to fit for both the left and right lane lines.

### Datasets and Inputs

The datasets I plan to use will be image frames from video I take from my smartphone. I plan to film in 720p in horizontal/landscape mode, with 720 pixels on the y-axis and 1280 pixels on the x-axis, at 30 fps. There will definitely be some manual pre-processing involved in order to train my model. As such, I will be calculating the polynomial coefficients for a second-order polynomial for each line (the three outputs per line, times two lines, means each image will have six "labels") in each image. Depending on the size of the neural network used, the dataset will likely end up being quite large - at 30 fps, just 5 minutes of video would be 9,000 images, which would be a lot of labelling. I will try a subset of the data first with my labelling technique to ensure the process seems to work before performing the labelling on the full dataset.

I will try to use a mix of both straight lines and various curved lines, as well as various conditions (night vs. day, shadows, rain vs. sunshine) in order to help with the model's overall generalization. I believe these will help to cover more of the real conditions that drivers see every day. 

### Solution Statement

As I mentioned briefly before, I plan to use deep learning toward the final solution. The reason for this is that a deep learning model may be more effective at determining the important features in a given image than a human being using manual gradient and color thresholds in typical computer vision techniques, as well as other manual programming needed within that process. Specifically, I plan to use a convolutional neural network (CNN), which are very effective at finding patterns within images by using filters to find specific pixel groupings that are important. My aim is for the end result to be both more effective at detecting the lines as well as faster at doing so than common computer vision techniques.

### Benchmark Model

I plan to compare the results of the CNN versus the output of the computer vision-based model I used in my SDC nanodegree project (linked to above). I will compare the accuracy/mean-squared error of the lines to each other to see which is more effective, as well as compare the speed of the two techniques (after training, in the case of the CNN). I will also visually compare the output onto the project video from the Advanced Lane Lines project, including attempting to use the CNN on the challenge and harder challenge videos in that project, which my computer vision-based model failed to work on.

### Evaluation Metrics

My CNN will be being trained similarly to a regression-type problem, in which it will be given the polynomial coefficients on the training images, and attempt to learn how to extract those values from the given road images. The loss it will minimize is the difference between those actual coefficients and what it predicts (likely using mean-squared error). It will then use only limited computer vision techniques in order to draw the lane back onto the image. As noted above regarding benchmarking against my computer vision-based result, I will also evaluate it directly against that model in both accuracy and speed, as well as on even more challenging videos than my CV-based model was capable of doing.


### Project Design
_(approx. 1 page)_

In this final section, summarize a theoretical workflow for approaching a solution given the problem. Provide thorough discussion for what strategies you may consider employing, what analysis of the data might be required before being used, or which algorithms will be considered for your implementation. The workflow and discussion that you provide should align with the qualities of the previous sections. Additionally, you are encouraged to include small visualizations, pseudocode, or diagrams to aid in describing the project design, but it is not required. The discussion should clearly outline your intended workflow of the capstone project.

-----------

**Before submitting your proposal, ask yourself. . .**

- Does the proposal you have written follow a well-organized structure similar to that of the project template?
- Is each section (particularly **Solution Statement** and **Project Design**) written in a clear, concise and specific fashion? Are there any ambiguous terms or phrases that need clarification?
- Would the intended audience of your project be able to understand your proposal?
- Have you properly proofread your proposal to assure there are minimal grammatical and spelling mistakes?
- Are all the resources used for this project correctly cited and referenced?
