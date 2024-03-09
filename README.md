# Currency Transfer Image Recognition

## Abstract
In today's digital era, there is a growing demand for efficiently calculating the total amount transferred through images captured from transaction screens. Not all banking applications offer a service that automatically sums up the amounts debited and credited to an account on a monthly basis, as exemplified by the case of BIDV. Moreover, even when such services exist, they may not extend to calculating the total amounts for specific transactions. While manual calculations are feasible, the need for automation becomes increasingly evident when dealing with a large volume of transactions.

This project encompasses two pivotal stages. Firstly, there is the object detection phase, which involves pinpointing the location of the transferred amount using the medion YOLO version 8 model (i.e. [YOLOv8m](https://github.com/ultralytics/ultralytics?tab=readme-ov-file)). Subsequently, the system extracts the relevant portion of the image containing the transferred amount and utilizes easyOCR for accurate recognition.

By combining object detection and optical character recognition, this project seeks to provide an automated solution for swiftly and accurately summing up transferred amounts from transaction images. This approach not only addresses the limitations of existing banking applications but also streamlines the calculation process for users, particularly when dealing with a high volume of transactions.

Nevertheless, **it is not only limited to recognizing images of money transfers**; this project can be customized to adapt to your specific data sources, as long as yours aligns with the two-stage approach.

## Data Preparation
Since all text is in typewritten format, without blurriness or tilting, we decided to focus mainly on training the model for the object detection task. The input data comprises 400 images of money transfers in Momo and BIDV Smart Banking applications, each accompanied by an individual text file containing labels corresponding to the [YOLO training data format](https://docs.cogniflow.ai/en/article/how-to-create-a-dataset-for-object-detection-using-the-yolo-labeling-format-1tahk19/). Unfortunately, due to privacy terms, I can not public the specifics of the dataset.

Label Studio serves as our labeling tool of choice, primarily because it offers flexible labeling capabilities for a variety of machine learning/deep learning tasks and provides a user-friendly interface. For more information on installing Label Studio, you can refer to this [repository](https://github.com/HumanSignal/label-studio?tab=readme-ov-file#try-out-label-studio).

The labeling interface is illustrated below:

<img width="200" alt="hinh1momo" src="https://github.com/motcapbovit/Currency-Transfer-Image-Recognition/assets/72774923/aca2fd65-c7a9-43e8-bcbb-8fd0b53b6474">   <img width="200" alt="hinh2nganhang" src="https://github.com/motcapbovit/Currency-Transfer-Image-Recognition/assets/72774923/60f2cec8-5d5c-42ff-aae1-864732d2da54">

_Note: Due to the presence of sensitive information, certain areas on the images will be redacted before being displayed._

## Model Evaluation

Due to the nature of this project, we did not employ multiple models for a single task and conduct comparisons. Therefore, in this section (model evaluation), I will perform error analysis. Surprisingly (or perhaps not), after training on 400 and predicting on 200 money transfer images, we encountered a notable error — despite the transaction occurring only once, the transferred amount appeared multiple times in the image.

<img width="200" alt="image_0257" src="https://github.com/motcapbovit/Currency-Transfer-Image-Recognition/assets/72774923/0dfe9490-caff-4c1e-ab52-51a16a6dfbeb">

Specifically, for money transfers through the Momo application, the transferred amount is typically displayed at the top of the image. However, the system subsequently presents this amount below when generating the transfer receipt. Consequently, the object detection system bifurcated these two regions into distinct images and performed OCR for each, resulting in the amount being duplicated.

For future development, the incorporation of additional training data and epochs may be promising in solving this misidentification. Observating the error closely indicate a higher propensity for predicting the location above rather than below. This comes from the fact that in the majority of Momo transfer images, the transferred amount is located at the top most of the time.

## Contact
Chi Thanh Dang

chithanhdang74@gmail.com
