# hydra
## summary
1. [Change variables](#change)
2. [Override settings or special characters](#spe)
3. [Instantiate object or callables](#objects)
4. [Configuration groups](#groups)


# change variable <a name="change"> </a>
```bash
 python src/train.py ++trainer.max_epochs=2
```

To override string, escape the " or ' : 
```bash
python src/train.py ++trainer.max_epochs=2 ++datamodule.videos_id=[[\'13025\',\'13032\'],[\'13212\'],[\'13025\',\'13032\']]
```

# Override characters or special characters <a name="spe"> </a>

### [Primitives](https://hydra.cc/docs/advanced/override_grammar/basic/#primitives "Direct link to heading")

-   `id`  : oompa10, loompa_12
-   `None`: null
-   `int`: 10, -20, 0, 1_000_000.
-   `float`: 3.14, -10e6, inf, -inf, nan.
-   `True, False`: true, false
-   `dot_path`: foo.bar
-   `interpolation`: ${foo.bar}, ${oc.env:USER,me}

# Instantiate objects or callables <a name="objects"></a>
### Easy example
- in the configuration file 
```yaml
model : 
 - _target_: torchvision.models.alexnet
```

- in the .py : 
```python 
import torch
from hydra.utils import instantiate

net = instantiate(cfg.model)
```

⚠️ It's possible to pass parameters by adding additional key to the configuration : 

```yaml
model : 
 - _target_: torchvision.models.alexnet
 - pretrained: True
```

# Group configurations <a name="groups"></a>

In pratice, it's more conveniant to have multiple specifying different types of model.  

In order to do that, we first group the config files in the `config` folder containing the `config.yaml` file and a `model` folder containing the different models `small.yaml` and `large.yaml`.
```
main.py
configs/
|  config.yaml --> Main configuration
|  classifiers/
|  | small.yaml --> Small classifier
|  |  large.yaml --> Large classifier
```

In the `config.yaml` we specify a default value for our classifeir : 
```yaml
defaults: 
 - _self_
 - classifier: small
```

We can override its value at any time :
```bash 
python main.py classifier=large
```
