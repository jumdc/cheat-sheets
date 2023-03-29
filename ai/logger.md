
- [Tensorboard](#tensorboard)
	- [Initialize](#initialize)
	- [Log to tensorboard](#log-to-tensorboard)
- [wandb](#wandb)

# Tensorboard

## Initialize
```bash
tensorboard --logdir=logs --bind_all
```

- `--logdir` : the directory where the logs are stored
- `--bind_all` : bind to all interfaces, so that we can access it from outside the server

Different experiments requiere different log directories. We can use the `project` name as the log directory.

## Log to tensorboard

```python
logger = TensorBoardLogger(
	save_dir="logdir", # directory where the logs are stored
	name=xp_name, # name of the experiment
)
logger.log_hyperparams({"epochs": 5, "optimizer": "Adam"}) # log hyperparameters of the experiment
```


# wandb

 Initialization with Lightning
```python
from pytorch_lightning.loggers import WandbLogger

wandb_logger = WandbLogger(
	project=cfg.logger.project
)
```

