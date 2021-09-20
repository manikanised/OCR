# OCR
 Building a word recognition and a page segmentation program in google colab

The whole process of Handwritten image to text is seperated into two parts:
1) Segmentation
2) Recognition


Methodology segmentation- 

->Preprocessing image-> 
Convert image to greyscale and threshold into black and white values

->Make a horizontal sum-> 
Find the sum of all horizontal pixal lines

->Find gaps in horizontal sum->
gaps in horizontal sum define lines

->Find vertical sum->
Set a threshold for minimum gap
find gap between words and not letters using this threshold 
output each word into a list

->Feed each word to model created in recognition to get prediction.

Methodology Recognition-

->Import IAM word dataset->
IAM word is a huge handwritten words dataset with about 87000 words. For the pupose of this project demonstration only 8700 words were taken, all within a gap of 10.

->Each word image is preprocessed->
images were resized to have a fixed size by including padding of blank pixels in each image

->Matching labels with images->
In IAM words dataset, the given words.txt file has multiple lines in it, each line represents the address of the image along with the label in the end

->Creating batches for training-> 
Batch size of 64 was defined and during each epoch, a new batch of 64 was passed to the model

->Making model->
Models we are trying to make is LSTM- Long short Term Memory 
Custom Loss function is defined, here only y_pred[:,2:,:] is used to define loss because before 2nd, the model was just outputing a garbage symbol/value

-> Training model->
model was trained for 24 epochs and output was saved for use after segmentation.
