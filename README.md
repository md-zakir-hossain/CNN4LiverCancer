# Predicting and Staging Hepatocellular Carcinoma from Contrast CT Scans. 
Accepted at the **25th International Conference on Digital Image Computing: Techniques and Applications (DICTA 2024)**. Codes are primarily developed by Patrick Buckley.

Paper link: [IEEE Xplore](https://doi.org/10.1109/DICTA63115.2024.00044)

**Author**: Md Zakir Hossain, Patrick Buckley, Himadri Shekhar Mondal, Md Rakibul Hasan, Tom Gedeon <br>

**Abstract:** Hepatocellular carcinoma (HCC) is a common and deadly form of liver cancer for which early detection and staging can be integral to patient survival. Medical imaging is an usual method of diagnosis, either using contrast Computed Tomography (CT) scans or Magnetic Resonance Imaging (MRI) scans. We introduce a new deep learning model that aims to take advantage of the information in two different stages of contrast CT scans to predict the presence and severity of HCC tumours in the images. Our model is trained and tested on a dataset of 307 labelled dual image input slices. On testing, the model achieves an accuracy of 96.8% and a sensitivity of 87.8%. These results indicate that using a dual image input of contrast CT scans provides a significant boost in performance to the model. Such a model prove to be a valuable tool to assist doctors in the diagnosis and staging of HCC, saving them time in the manual examination of scans.

## File Structure

```bash
TCGA-XX-XXXX/
├───Arterial/
    ├───x-xx.dcm
├───Venous/
├───Dict.txt
```

We used a publicly available dataset, namely [TCGA-LIHC]([URL](https://github.com/hasan-rakibul/CNN-Cancer-CT-Scan?tab=readme-ov-file)) (contains 97 medical scans). The dataset was collected from The Cancer Imaging Archive (TCIA), which is a subset of data from the Cancer Genome Atlas. 


## Environment Setup

This repository is developed using Tensorflow 2.13.1 framework in a Google Colab environment. Refer to the Cancer_Prediction_Model.ipynb (primarily developed by Patrick Buckley (@patrickjbuckley01)).


## Citation
If you find this repository useful in your research, please cite our paper:
```bibtex
@InProceedings{hossain2024predicting,
    author={Hossain, Md Zakir and Buckley, Patrick and Mondal, Himadri Shekhar and Hasan, Md Rakibul and Gedeon, Tom},
    booktitle={2024 International Conference on Digital Image Computing: Techniques and Applications (DICTA)}, 
    title={Predicting and Staging Hepatocellular Carcinoma from Contrast CT Scans}, 
    year={2024},
    pages={238-243},
    doi={10.1109/DICTA63115.2024.00044}
}
```
