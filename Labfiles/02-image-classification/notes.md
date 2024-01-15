# Classifying Images

## Azure AI Custom Vision 

Enables you to build your own computer vision models for image classification or object detection.

Creating an Azure AI Custom Vision solution involves two tasks:

* Use existing (labeled) images to train an Azure AI Custom Vision model.

* Create a client application that submits new images to your model to generate predictions.

To use the Azure AI Custom Vision service, you must provision two kinds of Azure resource:

1. A training resource (used to train your models). This can be:
    
    * An Azure AI Services resource.
    
    * An Azure AI Custom Vision (Training) resource.

2. A prediction resource, used by client applications to get predictions from your model. This can be:

    *An Azure AI Services resource.

    *An Azure AI Custom Vision (Prediction) resource.
    
You can use a single Azure AI Services resource for both training and prediction, and you can mix-and-match resource types (for example, using an Azure AI Custom Vision (Training) resource to train a model that you then publish using an Azure AI Services resource).

## Understand image classification

Image classification is a computer vision technique in which a model is trained to predict a class label for an image based on its contents. Usually, the class label relates to the main subject of the image.

For example, the following images have been classified based on the type of fruit they contain.

Images of fruit, classified as Apple, Banana, and Orange

Models can be trained for multiclass classification (in other words, there are multiple classes, but each image can belong to only one class) or multilabel classification (in other words, an image might be associated with multiple labels).

## Train an Image Classification Model

To train an image classification model with the Azure AI Custom Vision service, you can use the Azure AI Custom Vision portal, the Azure AI Custom Vision REST API or SDK, or a combination of both approaches.

In most cases, you'll typically use the Azure AI Custom Vision portal to train your model.

The Azure AI Custom Vision portal

The portal provides a graphical interface that you can use to:

    
    1. Create an image classification project for your model and associate it with a training resource.
    
    2. Upload images, assigning class label tags to them.
    
    3. Review and edit tagged images.
    
    4. Train and evaluate a classification model.
    
    5. Test a trained model.
    
    6. Publish a trained model to a prediction resource.
    
**`The REST API and SDKs enable you to perform the same tasks by writing code, which is useful if you need to automate model training and publishing as part of a DevOps process.`**

## Detect Objects (Azure AI Custom Vision)
---

Object detection is used to locate and identify objects in images. You can use Azure AI Custom Vision to train a model to detect specific classes of object in images.

Learning objectives

After completing this module, you will be able to:


    * Provision Azure resources for Azure AI Custom Vision

    * Understand object detection

    * Train an object detector

    * Consider options for labeling images

There are two components to an object detection prediction:


    * The class label of each object detected in the image. For example, you might ascertain that an image contains one apple and two oranges.

    * The location of each object within the image, indicated as coordinates of a bounding box that encloses the object.

You can use the Azure AI Custom Vision service to train an object detection model. To use the Azure AI Custom Vision service, you must provision two kinds of Azure resource:

* A training resource (used to train your models). This can be:
    * An Azure AI Services resource.
    * An Azure AI Custom Vision (Training) resource.

A prediction resource, used by client applications to get predictions from your model. This can be:
    * An Azure AI Services resource.
    * An Azure AI Custom Vision (Prediction) resource.

**`You can use a single Azure AI Services resource for both training and prediction, and you can mix-and-match resource types (for example, using an Azure AI Custom Vision (Training) resource to train a model that you then publish using an Azure AI Services resource).`**

### Train an object detector

To train an object detection model, you can use the Azure AI Custom Vision portal to upload and label images before training, evaluating, testing, and publishing the model; or you can use the REST API or SDK to write code that performs the training tasks.

The most significant difference between training an image classification model and training an object detection model is the labeling of the images with tags. While image classification requires one or more tags that apply to the whole image, object detection requires that each label consists of a tag and a region that defines the bounding box for each object in an image. The Azure AI Custom Vision portal provides a graphical interface that you can use to label your training images.

# Detect, Analyze and Recognize Faces
---

Face detection, analysis, and recognition are all common computer vision challenges for AI systems. The ability to detect when a person is present, identify a person's facial location, or recognize an individual based on their facial features is a key way in which AI systems can exhibit human-like behavior and build empathy with users.

In this module, you'll learn how to detect, analyze, and recognize faces using Azure AI Services.

After completing this module, you’ll be able to:


    * Identify options for face detection analysis.

    * Describe considerations for face analysis.

    * Detect faces with the Azure AI Vision service.

    * Describe the capabilities of the Face service.

    * Learn about facial recognition.

## There are two Azure AI services that you can use to build solutions that detect faces or people in images.

The Azure AI Vision and Face services offer facial analysis capabilities

The Azure AI Vision service

    * The Azure AI Vision service enables you to detect people in an image, as well as returning a bounding box for its location.

The Face service
The Face service offers more comprehensive facial analysis capabilities than the Azure AI Vision service, including:
 
    * Face detection (with bounding box).
 
    * Comprehensive facial feature analysis (including head pose, presence of spectacles, blur, facial landmarks, occlusion and others).
 
    * Face comparison and verification.
 
    * Facial recognition.

While all applications of artificial intelligence require considerations for responsible and ethical use, system that rely on facial data can be particularly problematic.

When building a solution that uses facial data, considerations include (but are not limited to):

    * Data privacy and security. Facial data is personally identifiable, and should be considered sensitive and private. You should ensure that you have implemented adequate protection for facial data used for model training and inferencing.

    * Transparency. Ensure that users are informed about how their facial data will be used, and who will have access to it.

    * Fairness and inclusiveness. Ensure that you face-based system cannot be used in a manner that is prejudicial to individuals based on their appearance, or to unfairly target individuals.

## The Face Service

The Face service provides functionality that you can use for:


    * Face detection - for each detected face, the results include an ID that identifies the face and the bounding box coordinates indicating its location in the image.

    * Face attribute analysis - you can return a wide range of facial attributes, including:

    * Head pose (pitch, roll, and yaw orientation in 3D space)

    * Glasses (NoGlasses, ReadingGlasses, Sunglasses, or Swimming Goggles)

    * Blur (low, medium, or high)

    * Exposure (underExposure, goodExposure, or overExposure)

    * Noise (visual noise in the image)

    * Occlusion (objects obscuring the face)

    * Accessories (glasses, headwear, mask)

    * QualityForRecognition (low, medium, or high)

    * Facial landmark location - coordinates for key landmarks in relation to facial features (for example, eye corners, pupils, tip of nose, and so on)

    * Face comparison - you can compare faces across multiple images for similarity (to find individuals with similar facial features) and verification (to determine that a face in one image is the same person as a face in another image)

    * Facial recognition - you can train a model with a collection of faces belonging to specific individuals, and use the model to identify those people in new images.

    * Facial liveness - liveness can be used to determine if the input video is a real stream or a fake to prevent bad intentioned individuals from spoofing the recognition system.

**`You can provision Face as a single-service resource, or you can use the Face API in a multi-service Azure AI Services resource.`**

## Compare and match detected faces

When a face is detected by the Face service, an ID is assigned to it and retained in the service resource for 24 hours. The ID is a GUID, with no indication of the individual's identity other than their facial features.

While the detected face ID is cached, subsequent images can be used to compare the new faces to the cached identity and determine if they are similar (in other words, they share similar facial features) or to verify that the same person appears in two images.

This ability to compare faces anonymously can be useful in systems where it's important to confirm that the same person is present on two occasions, without the need to know the actual identity of the person. For example, by taking images of people as they enter and leave a secured space to verify that everyone who entered leaves.

## Implement facial recognition

For scenarios where you need to positively identify individuals, you can train a facial recognition model using face images.

As mentioned in the previous unit, recognition models will require getting approved through a Limited Access policy.

To train a facial recognition model with the Face service:
    
    * Create a Person Group that defines the set of individuals you want to identify (for example, employees).
    
    * Add a Person to the Person Group for each individual you want to identify.
    
    * Add detected faces from multiple images to each person, preferably in various poses. The IDs of these faces will no longer expire after 24 hours (so they're now referred to as persisted faces).
    
    * Train the model.

The trained model is stored in your Face (or Azure AI Services) resource, and can be used by client applications to:

    
    * Identify individuals in images.
    
    * Verify the identity of a detected face.
    
    * Analyze new images to find faces that are similar to a known, persisted face.

Now that you've completed this module, you can:

    
    * Identify options for face detection analysis.
    
    * Describe considerations for face analysis.
    
    * Detect people with the Azure AI Vision service.
    
    * Describe the capabilities of the Face service.
    
    * Understand facial recognition.

# Read text in images and documents with Azure AI Vision Service

Suppose you are given thousands of images and asked to transfer the text on the images to a computer database. The scanned images have text organized in different formats and contain multiple languages. What are some ways you could complete the project in a reasonable time frame and make sure the data is entered with a high degree of accuracy?

Companies around the world are tackling similar scenarios every day. Without AI services, it would be challenging to complete the project, especially if it were to change in scale.

Using AI services, we can treat this project as an Azure AI Vision scenario and apply Optical Character Recognition (OCR). OCR allows you to extract text from images, such as photos of street signs and products, as well as from documents — such as handwritten or unstructured documents.

To build an automated AI solution, you need to train machine learning models to cover many use cases. Azure AI Vision service gives access to advanced algorithms for processing images and returns data to secure storage.

In this module, you'll learn how to:

    * Identify how the Azure AI Vision service enables you to read text from images
    * Use the Azure AI Vision service with SDKs and the REST API
    * Develop an application that can read printed and handwritten text

Azure AI provides two different features that read text from documents and images, one in the Azure AI Vision Service, the other in Azure AI Document Intelligence. There is overlap in what each service provides, however each is optimized for results depending on what the input is.

Image Analysis Optical character recognition (OCR):
    
    * Use this feature for general, unstructured documents with smaller amount of text, or images that contain text.
    
    * Results are returned immediately (synchronous) from a single API call.
    
    * Has functionality for analyzing images past extracting text, including object detection, describing or categorizing an image, generating smart-cropped thumbnails and more.
    
    * Examples include: street signs, handwritten notes, and store signs.

Document Intelligence:
    
    * Use this service to read small to large volumes of text from images and PDF documents.
    
    * This service uses context and structure of the document to improve accuracy.
    
    * The initial function call returns an asynchronous operation ID, which must be used in a subsequent call to retrieve the results.
    
    * Examples include: receipts, articles, and invoices.
    
You can access both technologies via the REST API or a client library. In this module, we'll focus on the OCR feature in Image Analysis. If you'd like to learn more about Document Intelligence, reading this module will provide a good introduction.