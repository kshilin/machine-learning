# Построить модель без лишних фич

для проверки отобраных признаков 

```python
mask = [...] # укажите список слобцов в отобраных для модели
import pickle
with open('saved_dictionary_с.pkl', 'rb') as f:
    loaded_dict = pickle.load(f)

color_dict = pd.Series(loaded_dict).to_frame().reset_index().sort_values(by=0).reset_index(drop=True)
color = (color_dict['index'].isin(mask)).map({True: 'background-color: yellow', False: ''})
color_dict.style.apply(lambda s: color)
```
