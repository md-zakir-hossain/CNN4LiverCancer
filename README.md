# Predicting and Staging Hepatocellular Carcinoma from Contrast CT Scans. Accepted at the **25th International Conference on Digital Image Computing: Techniques and Applications (DICTA 2024)**. Codes are primarily developed by Patrick Buckley.

Paper link: yet to be published

**Author**: Md Zakir Hossain, Patrick Buckley, Himadri Shekhar Mondal, Md Rakibul Hasan, Tom Gedeon <br>

**Abstract:** Hepatocellular carcinoma (HCC) is a common and
deadly form of liver cancer for which early detection and
staging can be integral to patient survival. Medical imaging is
an usual method of diagnosis, either using contrast Computed
Tomography (CT) scans or Magnetic Resonance Imaging (MRI)
scans. We introduce a new deep learning model that aims to take
advantage of the information in two different stages of contrast
CT scans to predict the presence and severity of HCC tumours
in the images. Our model is trained and tested on a dataset
of 307 labelled dual image input slices. On testing, the model
achieves an accuracy of 96.8% and a sensitivity of 87.8%. These
results indicate that using a dual image input of contrast CT
scans provides a significant boost in performance to the model.
Such a model prove to be a valuable tool to assist doctors in the
diagnosis and staging of HCC, saving them time in the manual
examination of scans. Implementation is publicly available at link
will be added after acceptance.

## Environment Setup

Please be aware that this code is meant to be run with Python 3 under Linux (MacOS may work, Windows probably not). Download the packages from `requirements.txt`:

```bash
python -m pip install -r requirements.txt
```
We use the [ABIDE I dataset](http://fcon_1000.projects.nitrc.org/indi/abide/). We use the pre-processing method from the [preprocessed-connectomes-project](https://github.com/preprocessed-connectomes-project/abide).


## Run Experiments

We put all the experiment command and the result in the `Experiments.ipynb` file. As an example, we prepare the hdf5 files in advance of the CC200, AAL, EZ atlas data from the NYU site, and show the entire experiment on this data as followings:

1. Run `download_abide.py` to download the raw data.

We use the command below:

```bash
#download_abide.py [--pipeline=cpac] [--strategy=filt_global] [<derivative> ...]
python download_abide.py
```

2. To show the demographic Information of ABIDE I.

```bash
python pheno_info.py
```

3. Run `prepare_data.py` to compute the correlation. Then we can get the hdf5 files. The dataset (hdf5) can be downloaded from [link](https://drive.google.com/file/d/1-WyQ7IOqSxaGcoA6MR4ydJdazlqzKYMY/view?usp=drive_link); you need to put it in the "data" folder. Or you can simply run the code as:

```bash
#download_abide.py [--folds=N] [--whole] [--male] [--threshold] [--leave-site-out] [--NYU-site-out] [<derivative> ...]

python prepare_data.py --folds=10 --whole cc200 aal ez
```

4. Using Stacked Sparse Denoising Autoencoder (SSDAE) to perform Multi-atlas Deep Feature Representation, and using multilayer perceptron (MLP) and ensemble learning to classify the ASD and TC.

```bash
#nn.py [--whole] [--male] [--threshold] [--leave-site-out] [<derivative> ...]

rm ./data/models/*mlp*
python nn.py --whole cc200 aal ez
```  

5. Evaluating the MLP model on test dataset. You can use the saved models from provious or download the models from the [link](https://drive.google.com/drive/folders/1rIZpXdafzI-nb0YonkL0XQs6pOSSxRUf?usp=drive_link), and **can run this command directly without running previous steps**.

```bash
#nn_evaluate.py [--whole] [--male] [--threshold] [--leave-site-out] [--NYU-site-out] [<derivative> ...]

python nn_evaluate.py --whole cc200 aal ez
```
        
## Quality Analysis and Visualisation

All the analysis for the subset and the visualisation of top ROIs, which mentioned in our work, are included in the `analysis_and_visulaisation.ipynb` file.

## Citation
If you find this repository useful in your research, please cite our paper:
```bibtex
@article{liu2024made,
    title = {{MADE}-for-{ASD}: A Multi-Atlas Deep Ensemble Network for Diagnosing Autism Spectrum Disorder},
    author = {Xuehan Liu and Md Rakibul Hasan and Tom Gedeon and Md Zakir Hossain},
    journal = {Computers in Biology and Medicine},
    volume = {182},
    pages = {109083},
    year = {2024},
    issn = {0010-4825},
    doi = {10.1016/j.compbiomed.2024.109083}
}
```
