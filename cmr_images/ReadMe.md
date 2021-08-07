# Cardiac MR Image (Short-Axis) Dataset for Pulmonary Arterial Hypertension Diagnosis

This dataset consists of the CMR images acquired from 179 subjects. The images have been processed in size (64x64) and (32x32). The images are shared in DICOM format.
The files are organized in the following structure:

|-- DICOM \
|--|-- Subject_1 \
|--|--|-- Phase_1.dcm \
|--|--|-- Phase_2.dcm \
|--|--|-- ... \
|--|--|-- Phase_20.dcm \
|--|-- Subject_2 \
|--|-- Subject_3 \
|--|-- … \
|--|-- Subject_179 \
|-- Mask \
|--|-- Mask_WxH \
|--|--|-- Phase_1.dcm \
|-- Landmarks_WxH.csv

W, H denotes width and height of processed images, e.g. 64 or 32.

## Reference

Swift, A.J., Lu, H., Uthoff, J., Garg, P., Cogliano, M., Taylor, J., Metherall, P., Zhou, S., Johns, C.S., Alabed, S. and Condliffe, R.A., 2021. A machine learning cardiac magnetic resonance approach to extract disease features and automate pulmonary arterial hypertension diagnosis. *European Heart Journal-Cardiovascular Imaging*, 22(2), pp.236-245.
