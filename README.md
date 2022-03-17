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
### Model Aracitecture
---
![image](https://user-images.githubusercontent.com/62954678/158781743-555f163e-9b9d-4651-8cf5-1ec8a66341da.png)
---
#### Sample 28 Characters
---
![image](https://user-images.githubusercontent.com/62954678/158781900-59c99854-d234-49e3-b3bf-cd1e741cc361.png)
---
### Results
---
![image](https://user-images.githubusercontent.com/62954678/158782059-653f71b5-bae9-48db-9d22-16986dbadabd.png)

![image](https://user-images.githubusercontent.com/62954678/158782154-d98b432d-4c60-4f0c-9be2-54515dd1f560.png)

![image](https://user-images.githubusercontent.com/62954678/158782208-dc8f2c9a-bcd4-49fd-8e93-f285fc96e397.png)

![image](https://user-images.githubusercontent.com/62954678/158782232-f7972eb2-d2d1-4973-9c24-970ea9a2b4b0.png)

### Get Started
---
#### Installation
```bash
conda create --name tutorial-TF python=3.6.8
```
