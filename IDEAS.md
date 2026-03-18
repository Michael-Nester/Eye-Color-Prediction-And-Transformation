# Theory
This project was created in 2024 during my fall semester at URI. I consider this to be the closest that I had to a capstone project, and it's what I am most proud of from my undergraduate studies.

Towards the end of the project, my team and I began to work on developing a basic eye color classification model, because our professor said our original idea was 'beyond the scope of the course'. We weren't able to finish this model in time. 

I'm coming back to this with some new ideas how I can use classification models to potentially improve the image reconstruction capabilities of the autoencoder. Thinking further on this, it may be more beneficial to train models to classify the images based on the subject label themselves, rather than just the color, because if identifying the subject reuires fine details in the entire image, rather than just the iris color. 

## Hypothesis
If an autoencoder is able to preserve fine details of an image, then a classification model trained solely on the original dataset will maintain a comparable of accuracy and confidence when inferring on the iris color of the reconstructed data. The difference in classification will serve as a qunatitative metric of feature-loss.

If the subject classification confidence delta between original and reconstructed images is minimized, then the overall image-reconstruction abilities of the autoencoder will be improved because the autoencoder is being explicitly forced to preserve the fine-grained details that the classifier relies on.


The basic idea is as follows:

1. Develop and train a classification model to be able to classify the color of eyes based on the original dataset (UBIRIS V2), to some percentage success threshold.
2. Run the dataset through the autoencoder, encoding the images into latent vectors, and reconstructing images from that data.
3. Train the same classification model on the reconstructed images. Or, create a new one, I'm not sure which would be best. Obtain the highest confidence interval possible without overfitting.
4. I assume (and hope) that the model will not be able to correctly classify the reconstructed images as well as it is with the originals. If this is the case, then the goal is the minimize the difference between the confidence interval for the originals and for the reconstructed images.
