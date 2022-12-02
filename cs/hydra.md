# hydra
## summary
1. [Change variables](#change)
2. [Override settings or special characters](#spe)


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

