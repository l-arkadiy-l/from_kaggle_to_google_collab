# from_kaggle_to_google_collab
I created this post for people wich can't understand how to install datasets from kaggle to google collab.

Let's get start.

1. ## Create kaggle api and get kaggle.json

![go settings](https://i.ibb.co/K24CXJf/Screenshot-107.png)
![create api](https://i.ibb.co/x3zywVh/Screenshot-108.png)

2. Upload `kaggle.json` in google collab

```python
# upload kaggle.json
from google.colab import files
files.upload()
```

3. Intall kaggle, create folder and setting permissions

```python
!pip install kaggle

!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
```

4. Download kaggle dataset from kaggle api

![](https://i.ibb.co/qmgWVLJ/Screenshot-109.png)

```python
import kaggle
from kaggle.api.kaggle_api_extended import KaggleApi
api = KaggleApi()
api.authenticate()
# api.dataset_download_files('name/dataset_name', 'folder from dataset kaggle (from data explorer)')
api.dataset_download_files('kmader/skin-cancer-mnist-ham10000', 'HAM10000_images_part_2')
```

5. Unzip files

```python
import zipfile
path_to_zip_file = 'HAM10000_images_part_2/skin-cancer-mnist-ham10000.zip'
with zipfile.ZipFile(path_to_zip_file, 'r') as z:
    z.extractall('HAM10000_images_part_1')
```

6. Try downloading your dataset, and if you have any problems with it, you can write them in the questions :)

file settings in **[collab](https://colab.research.google.com/drive/1AcjQi-xzS1m_3dvSYJFoemJRo5KQH1a2?usp=sharing)**
