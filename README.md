
# SPAI-Home-Credit-KBTG
Super AI engineer ss4 level2

### Contributor

- 402882-วชิรวิทย์ (me) <br />
- 402569-เลิศบุญ <br />
- 405988-ปภาพินท์ <br />
- 403104-ชินาธิป <br />
- 401658-ปฐวี <br />

# Resource
- **LightGBM** <br>
 - **AutoGluon**

# LightGBM Pipe Line
- 1 Feature Selection
    - in  [Feature Selection Notebook](https://github.com/wachawich/SPAI-Home-Credit-KBTG/blob/main/LGBM/feature-selection.ipynb)
    - Cut the column NULL 50-70% , Select only A, P, L
 - 2 Take that feature train for train LGBM
	 -  in [train/test fuature kub Notebook](https://github.com/wachawich/SPAI-Home-Credit-KBTG/blob/main/LGBM/train-feature-kub.ipynb)
- 3 Training Gridserch and Training LGBM
	- in [pipe line Notebook](https://github.com/wachawich/SPAI-Home-Credit-KBTG/blob/main/LGBM/pine_line_credit.ipynb)

# AutoGluon Pipe Line
- 1 Preprocess
    - in  [Preprocess Notebook](https://github.com/wachawich/SPAI-Home-Credit-KBTG/blob/main/AutoGluon/Preprocess.ipynb)
    - Feature engineering
    - such as frequency of data, NULL columns, add Max of column
 - 2 Take that data from (1)
	 -  in [AutoGluon Notebook](https://github.com/wachawich/SPAI-Home-Credit-KBTG/blob/main/AutoGluon/AutoGluon.ipynb)
	 - training autogluon with data that already preprocess	



## Result and Score

**The results of my experiment**
* feature   
	* Panda -> feature engineering my team call panda in this [Notebook](https://github.com/wachawich/SPAI-Home-Credit-KBTG/blob/main/AutoGluon/Preprocess.ipynb)
	

|        Use     |              feature          	 |  Public | Private |
|----------------|-----------------------------------|---------|---------|
|LGBM            | My rule base select feature   	 | 0.66334 | 0.72450 |
|AutoGluon       | My rule base select feature   	 | 0.67884 | 0.70361 |
|LGBM+Grid Search| Using A, P, L and cut 50% NULL	 | 0.75616 | 0.80412 |
|AutoGluon       | Using A, P, L and cut 50% NULL	 | 0.73217 | 0.77119 |
|LGBM            | Panda Engineering             	 | 0.59335 | 0.57992 |
|AutoGluon       | Panda Engineering             	 | `0.89226` | `0.89069` |
|LGBM            | Using A, P, L and All file        | 0.79132 | 0.83188 |
|LGBM            | feature important from auto gluon | 0.67751 | 0.73527 |

จากการทดลองนี้พบว่า
LGBM จะเก่งกับ feature น้อยๆที่ select และผ่านการทำ feature engineering แล้ว ถ้า feature เยอะเกินไป จะไม่เก่ง
AutoGluon จะเก่งกับ feature เยอะๆ เพราะจะมีตัวเลือกเยอะในการหา feature ของมันเอง  ฟีเจอร์น้อยๆจะไม่ค่อยเก่ง
LLM ตอนแรกจะทำเป็น pipeline สำหรับการนำ feature improtant จาก autogluon มาใช้ร่วมกับ LLM แต่พอส่งคะแนนไป ผลก็ค่อนข้างแย่ เลยไม่ได้ไปต่อสำหรับ LLM
