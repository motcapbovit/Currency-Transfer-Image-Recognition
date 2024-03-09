# Currency-Transfer-Image-Recognition

## Abstract
In today's digital era, there is a growing demand for efficiently calculating the total amount transferred through images captured from transaction screens. Not all banking applications offer a service that automatically sums up the amounts debited and credited to an account on a monthly basis, as exemplified by the case of BIDV. Moreover, even when such services exist, they may not extend to calculating the total amounts for specific transactions. While manual calculations are feasible, the need for automation becomes increasingly evident when dealing with a large volume of transactions.

This project encompasses two pivotal stages. Firstly, there is the object detection phase, which involves pinpointing the location of the transferred amount using the medion YOLO version 8 model (i.e. [YOLOv8m](https://github.com/ultralytics/ultralytics?tab=readme-ov-file)). Subsequently, the system extracts the relevant portion of the image containing the transferred amount and utilizes easyOCR for accurate recognition.

By combining object detection and optical character recognition, this project seeks to provide an automated solution for swiftly and accurately summing up transferred amounts from transaction images. This approach not only addresses the limitations of existing banking applications but also streamlines the calculation process for users, particularly when dealing with a high volume of transactions.

Nevertheless, **it is not only limited to recognizing images of money transfers**; this project can be customized to adapt to your specific data sources, as long as yours aligns with the two-stage approach.
