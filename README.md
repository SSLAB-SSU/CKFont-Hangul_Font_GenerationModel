# CKFont : Hangul_Font_Generation_Model
## 한글 조합성에 기반한 최소 글자를 사용하는 한글 폰트 생성 모델 (2021. 11.)
## Few-Shot Korean Font Generation based on Hangul Composability

#### J. Park, A. U. Hassan and J. Choi, "Few-Shot Korean Font Generation based on Hangul Composability," KIPS Transactions on Software and Data Engineering, vol. 10, no. 11, pp. 473-482, 2021. DOI: https://doi.org/10.3745/KTSDE.2021.10.11.473.

 [KIPS](http://ktsde.kips.or.kr/digital-library/25120)
 KIPS Transactions on Software and Data Engineering, Vol. 10, No. 11, pp. 473-482, Nov. 2021
 [PDF](http://ktsde.kips.or.kr/digital-library/25120)
 
 ### 51개 구성요소를 모두 포함하는 최소 글자 28글자로 모든 한글을 다양한 폰트 스타일로 생성 가능
---
### Abstract  

Although several Hangul generation models using deep learning have been introduced, they require a lot of data, have a complex structure, requires considerable time and resources, and often fail in style conversion. This paper proposes a model CKFont using the components of the initial, middle, and final components of Hangul as a way to compensate for these problems. The CKFont model is an end-to-end Hangul generation model based on GAN, and it can generate all Hangul in various styles with 28 characters and components of first, middle, and final components of Hangul characters. By acquiring local style information from components, the information is more accurate than global information acquisition, and the result of style conversion improves as it can reduce information loss.  This is a model that uses the minimum number of characters among known models, and it is an efficient model that reduces style conversion failures, has a concise structure, and saves time and resources. The concept using components can be used for various image transformations and compositing as well as transformations of other languages.

---

- 폰트 디자이너가 새로운 폰트를 만들 때 알파벳을 기본으로 하는 로마자는 대소문자 52개만 디자인하면 되지만 한글은 11,172자를 디자인하여야 한다.  이는 30분에 한 글자씩 만들어도 하루 8시간 작업 시 700일이 소요되는 노동 집약적인 작업이다.  그러나 오늘날 인공지능을 이용한 딥러닝 모델을 이용하면 256자만 디자인 하면 30분 만에 새로운 폰트 하나를 만들 수 있다.  
- 또한 더 빠르고 더 효율적인 방법으로 목표를 달성하기 위하여, 새로운 폰트를 생성하는 것뿐 만아니라 보다 적은 글자 수를 사용하여 시간과 자원을 절약할 수 있는 방법에 대한 연구가 진행되고 있다. 
- 한글은 14개의 자음과 10개의 모음을 기반으로, 모든 한글은 19개의 초성과 21개 중성, 그리고 27개의 종성 등 모두 67개 (19+21+27)의 구성요소가 초성, 중성, 그리고 종성의 순서대로 조합되어 모두 11,172자 (19x21x28, 종성이 없는 경우 포함)의 조합형 형태의 글자를 생성한다. 이 67개 구성요소가 모든 한글 생성의 근본 요소이며, 이것으로 모든 글자를 생성할 수 있다.  또한 이 67개 구성요소를 모두 포함하는 최소 글자 수는 28개 글자이며, 이론적으로 28개의 글자로부터 구성 요소들을 추출하여 모든 글자를 생성할 수 있다.
- 본 논문에서는 이러한 한글의 조합적인 특성을 이용하여 28개의 최소 글자와 67개의 구성요소로 모든 한글을 생성할 수 있는 I2I 변환 방법의 cGAN (conditional GAN)을 기반으로 새로운 한글 자동 생성 모델인 CKFont (Component-based Korean Font Generation Model)를 제안한다.
---

### 한글 구성요소
---
 > <img src = "https://user-images.githubusercontent.com/62954678/160042485-a7ddb4d4-031a-435c-95f4-402842a74d88.png" width="900" height = "200">
---

#### Sample 28 Characters
---
 > <img src = "https://user-images.githubusercontent.com/62954678/160011303-6534d8d9-9b0a-49d5-9d62-3823ad409b9a.png" width="800" height = "150"> 
---

### Model Architecture
---
> <img src = "https://user-images.githubusercontent.com/62954678/160014081-029fe0e8-97be-4314-aa4b-7c3656f0749f.png" width="900" height = "400">
---

### Results
---
> <img src = "https://user-images.githubusercontent.com/62954678/160014538-fe90929d-fa03-4e24-a57e-e1cefa89ae63.png" width="1000" height = "400">   

>   <img src = "https://user-images.githubusercontent.com/62954678/160014871-b4d6603a-e242-477f-a883-a4b013c34f78.png" width="300" height = "300"> >>    <img src = "https://user-images.githubusercontent.com/62954678/160014967-1c5b88df-05db-4dc2-95dd-517878c3be10.png" width="300" height = "300">   >>      <img src = "https://user-images.githubusercontent.com/62954678/160014802-ffae9d93-e0d5-426e-80d4-9e94f4b01830.png" width="250" height = "300">
 
### Get Started
---
#### Installation
```bash
 >> conda create --name tutorial-TF python=3.6.8
 >> conda activate tutorial-TF or activate tutorial-TF
 >> conda install -c anaconda tensorflow-gpu=1.13.1
```
#### Datasets
---  
1. Generate Source font and split chars images
```bash
 >> python ./tools/src-font-image-generator.py
 >> python ./tools/src-split-font-image-generator.py  
```  

2. Generate Target font and split chars images
```bash
 >> python ./tools/tgt-font-image-generator.py
 >> python ./tools/tgt-split-font-image-generator.py
```  
3. Combine source, target, and target split imgs
```bash
 >> python ./tools/combine_images.py --input_dir src-image-data/images --b_dir tgt-image-data/images --c_dir tgt-split-image-data/images --operation combine
```  

4. Convert images to TFRecords
```bash
 >> python ./tools/images-to-tfrecords.py
```  
---  
### Training the model
---
#### Pre-training the model
```bash
 >> python main.py --mode train --output_dir trained_model --max_epochs 25 
```
#### Finetuning the model
---
```bash
 >> python main.py --mode train --output_dir finetuned_model --max_epochs 500 --checkpoint trained_model/ 
```
### Testing the model
---  
Convert images to TFRecords
```bash
 >> python ./tools/test-images-to-tfrecords.py
```  
### Generating results
```bash
 >> python main.py --mode test --output_dir testing_results --checkpoint finetuned_model
```
### Acknowledgements
---
This code is inspired by the pix2pix tensorflow project.
Special thanks to the following works for sharing their code and dataset.

- tensorflow-hangul-recognition
- pix2pix
---
### Citation
---
J. Park, A. U. Hassan and J. Choi, "Few-Shot Korean Font Generation based on Hangul Composability," KIPS Transactions on Software and Data Engineering, vol. 10, no. 11, pp. 473-482, 2021. DOI: https://doi.org/10.3745/KTSDE.2021.10.11.473.  

---
### Copyright
---
The code and other helping modules are only allowed for PERSONAL and ACADEMIC usage.
