
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



# Result and Score

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

From this experiment it was found<br>
LGBM is good at a few features that are selected and done through feature engineering. If there are too many features, it will not be good. <br>
AutoGluon is good with a lot of features because it has a lot of options to find its own features. It's not as good at a few features. <br>
LLM was initially created as a pipeline for using feature improtant from Autogluon together with LLM, but when the scores were sent The results were quite bad. So I didn't continue for the LLM.
