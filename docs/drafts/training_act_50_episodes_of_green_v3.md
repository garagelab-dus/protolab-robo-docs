# Command output from notebook

## Variables


```shell
output_dir: outputs/train/pap_green_foam_in_box-v3
hf_user: garagelab-duesseldorf
dataset_name: pap_green_foam_in_box
job_name: pap_green_foam_in_box
dataset_repo_id: garagelab-duesseldorf/pap_green_foam_in_box
policy_repo_id: garagelab-duesseldorf/pap_green_foam_in_boxpolicy-v3
```

## Command

```ipynb
!lerobot-train \
  --dataset.repo_id='{dataset_repo_id}' \
  --policy.type=act \
  --output_dir='{output_dir}' \
  --job_name='{job_name}' \
  --policy.device=cuda \
  --wandb.enable=False \
  --policy.repo_id='{policy_repo_id}' \
  --num_workers=2 \
  --batch_size=8 \
  --save_checkpoint_to_hub=true \
  --save_freq=1000 \
  --steps=20000
```

## Output


INFO 2026-08-02 15:43:39 ot_train.py:272 

```json
{'batch_size': 8,
 'checkpoint_path': None,
 'cudnn_deterministic': False,
 'dataloader_multiprocessing_context': 'spawn',
 'dataset': {'depth_output_unit': 'mm',
             'episodes': None,
             'eval_split': 0.0,
             'image_transforms': {'enable': False,
                                  'max_num_transforms': 3,
                                  'random_order': False,
                                  'tfs': {'affine': {'kwargs': {'degrees': [-5.0,
                                                                            5.0],
                                                                'translate': [0.05,
                                                                              0.05]},
                                                     'type': 'RandomAffine',
                                                     'weight': 1.0},
                                          'brightness': {'kwargs': {'brightness': [0.8,
                                                                                   1.2]},
                                                         'type': 'ColorJitter',
                                                         'weight': 1.0},
                                          'contrast': {'kwargs': {'contrast': [0.8,
                                                                               1.2]},
                                                       'type': 'ColorJitter',
                                                       'weight': 1.0},
                                          'hue': {'kwargs': {'hue': [-0.05,
                                                                     0.05]},
                                                  'type': 'ColorJitter',
                                                  'weight': 1.0},
                                          'saturation': {'kwargs': {'saturation': [0.5,
                                                                                   1.5]},
                                                         'type': 'ColorJitter',
                                                         'weight': 1.0},
                                          'sharpness': {'kwargs': {'sharpness': [0.5,
                                                                                 1.5]},
                                                        'type': 'SharpnessJitter',
                                                        'weight': 1.0}}},
             'repo_id': 'garagelab-duesseldorf/pap_green_foam_in_box',
             'return_uint8': False,
             'revision': None,
             'root': None,
             'streaming': False,
             'use_imagenet_stats': True,
             'video_backend': 'torchcodec'},
 'env': None,
 'env_eval_freq': 20000,
 'eval': {'batch_size': 1,
          'n_episodes': 50,
          'recording': False,
          'recording_private': False,
          'recording_repo_id': None,
          'use_async_envs': True},
 'eval_steps': 0,
 'job': {'detach': False,
         'image': 'huggingface/lerobot-gpu:latest',
         'tags': [],
         'target': None,
         'timeout': '2d'},
 'job_name': 'pap_green_foam_in_box',
 'log_freq': 200,
 'max_eval_samples': 0,
 'num_workers': 3,
 'optimizer': {'betas': [0.9, 0.999],
               'eps': 1e-08,
               'grad_clip_norm': 10.0,
               'lr': 1e-05,
               'type': 'adamw',
               'weight_decay': 0.0001},
 'output_dir': 'outputs/train/pap_green_foam_in_box-v3',
 'peft': None,
 'persistent_workers': True,
 'policy': {'chunk_size': 100,
            'device': 'cuda',
            'dim_feedforward': 3200,
            'dim_model': 512,
            'dropout': 0.1,
            'feedforward_activation': 'relu',
            'input_features': {},
            'kl_weight': 10.0,
            'latent_dim': 32,
            'license': None,
            'n_action_steps': 100,
            'n_decoder_layers': 1,
            'n_encoder_layers': 4,
            'n_heads': 8,
            'n_obs_steps': 1,
            'n_vae_encoder_layers': 4,
            'normalization_mapping': {'ACTION': <NormalizationMode.MEAN_STD: 'MEAN_STD'>,
                                      'STATE': <NormalizationMode.MEAN_STD: 'MEAN_STD'>,
                                      'VISUAL': <NormalizationMode.MEAN_STD: 'MEAN_STD'>},
            'optimizer_lr': 1e-05,
            'optimizer_lr_backbone': 1e-05,
            'optimizer_weight_decay': 0.0001,
            'output_features': {},
            'pre_norm': False,
            'pretrained_backbone_weights': 'ResNet18_Weights.IMAGENET1K_V1',
            'pretrained_path': None,
            'pretrained_revision': None,
            'private': None,
            'push_to_hub': True,
            'replace_final_stride_with_dilation': False,
            'repo_id': 'garagelab-duesseldorf/pap_green_foam_in_boxpolicy-v3',
            'tags': None,
            'temporal_ensemble_coeff': None,
            'type': 'act',
            'use_amp': False,
            'use_peft': False,
            'use_vae': True,
            'vision_backbone': 'resnet18'},
 'prefetch_factor': 4,
 'rename_map': {},
 'resume': False,
 'reward_model': None,
 'sample_weighting': None,
 'save_checkpoint': True,
 'save_checkpoint_to_hub': True,
 'save_freq': 1000,
 'scheduler': None,
 'seed': 1000,
 'steps': 20000,
 'tolerance_s': 0.0001,
 'use_policy_training_preset': True,
 'wandb': {'add_tags': True,
           'disable_artifact': False,
           'enable': False,
           'entity': None,
           'mode': None,
           'notes': None,
           'project': 'lerobot',
           'run_id': None}
}
```

INFO 2026-08-02 15:43:39 ot_train.py:280 Logs will be saved locally.
INFO 2026-08-02 15:43:39 ot_train.py:298 Creating dataset

INFO 2026-08-02 15:43:39 ot_train.py:324 Creating policy
INFO 2026-08-02 15:43:40 ot_train.py:402 Creating optimizer and scheduler
INFO 2026-08-02 15:43:40 ot_train.py:434 Output dir: outputs/train/pap_green_foam_in_box-v3
INFO 2026-08-02 15:43:40 ot_train.py:441 cfg.steps=20000 (20K)
INFO 2026-08-02 15:43:40 ot_train.py:442 dataset.num_frames=71471 (71K)
INFO 2026-08-02 15:43:40 ot_train.py:443 dataset.num_episodes=52
INFO 2026-08-02 15:43:40 ot_train.py:446 Effective batch size: 8 x 1 = 8
INFO 2026-08-02 15:43:40 ot_train.py:447 num_learnable_params=51597190 (52M)
INFO 2026-08-02 15:43:40 ot_train.py:448 num_total_params=51597190 (52M)

### Training sequence

```txt
Training:   0% 0/20000 [00:00<?, ?step/s]INFO 2026-08-02 15:43:40 ot_train.py:597 Start offline training on a fixed dataset, with effective batch size: 8
Training:   1% 200/20000 [02:32<3:13:45,  1.70step/s]INFO 2026-08-02 15:46:13 ot_train.py:641 step:200 smpl:2K ep:1 epch:0.02 loss:7.175 grdn:161.603 lr:1.0e-05 updt_s:0.565 data_s:0.196 smp/s:11 mem_gb:3.74 l1_loss:0.588 kld_loss:0.659
Training:   2% 400/20000 [04:36<3:21:29,  1.62step/s]INFO 2026-08-02 15:48:17 ot_train.py:641 step:400 smpl:3K ep:2 epch:0.04 loss:3.060 grdn:91.839 lr:1.0e-05 updt_s:0.613 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.437 kld_loss:0.262
Training:   3% 600/20000 [06:38<3:17:39,  1.64step/s]INFO 2026-08-02 15:50:19 ot_train.py:641 step:600 smpl:5K ep:3 epch:0.07 loss:2.543 grdn:78.814 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.388 kld_loss:0.215
Training:   4% 800/20000 [08:40<3:17:13,  1.62step/s]INFO 2026-08-02 15:52:21 ot_train.py:641 step:800 smpl:6K ep:5 epch:0.09 loss:2.257 grdn:73.184 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.366 kld_loss:0.189
Training:   5% 1000/20000 [10:43<3:13:31,  1.64step/s]INFO 2026-08-02 15:54:24 ot_train.py:641 step:1K smpl:8K ep:6 epch:0.11 loss:2.029 grdn:68.419 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.346 kld_loss:0.168

INFO 2026-08-02 15:54:24 ot_train.py:687 Checkpoint policy after step 1000
Training:   6% 1200/20000 [13:06<3:12:02,  1.63step/s]INFO 2026-08-02 15:56:47 ot_train.py:641 step:1K smpl:10K ep:7 epch:0.13 loss:1.824 grdn:63.236 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.323 kld_loss:0.150
Training:   7% 1400/20000 [15:08<3:10:57,  1.62step/s]INFO 2026-08-02 15:58:49 ot_train.py:641 step:1K smpl:11K ep:8 epch:0.16 loss:1.687 grdn:60.667 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.301 kld_loss:0.139
Training:   8% 1600/20000 [17:10<3:06:24,  1.65step/s]INFO 2026-08-02 16:00:51 ot_train.py:641 step:2K smpl:13K ep:9 epch:0.18 loss:1.528 grdn:56.952 lr:1.0e-05 updt_s:0.606 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.294 kld_loss:0.123
Training:   9% 1800/20000 [19:12<3:05:44,  1.63step/s]INFO 2026-08-02 16:02:53 ot_train.py:641 step:2K smpl:14K ep:10 epch:0.20 loss:1.399 grdn:53.269 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.292 kld_loss:0.111
Training:  10% 2000/20000 [21:15<3:03:35,  1.63step/s]INFO 2026-08-02 16:04:56 ot_train.py:641 step:2K smpl:16K ep:12 epch:0.22 loss:1.287 grdn:51.856 lr:1.0e-05 updt_s:0.610 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.284 kld_loss:0.100

INFO 2026-08-02 16:04:56 ot_train.py:687 Checkpoint policy after step 2000
Training:  11% 2200/20000 [23:39<3:04:28,  1.61step/s]INFO 2026-08-02 16:07:20 ot_train.py:641 step:2K smpl:18K ep:13 epch:0.25 loss:1.167 grdn:48.010 lr:1.0e-05 updt_s:0.611 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.279 kld_loss:0.089
Training:  12% 2400/20000 [25:42<3:01:08,  1.62step/s]INFO 2026-08-02 16:09:23 ot_train.py:641 step:2K smpl:19K ep:14 epch:0.27 loss:1.070 grdn:46.834 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.273 kld_loss:0.080
Training:  13% 2600/20000 [27:44<2:57:41,  1.63step/s]INFO 2026-08-02 16:11:25 ot_train.py:641 step:3K smpl:21K ep:15 epch:0.29 loss:0.962 grdn:43.641 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.262 kld_loss:0.070
Training:  14% 2800/20000 [29:47<2:55:00,  1.64step/s]INFO 2026-08-02 16:13:28 ot_train.py:641 step:3K smpl:22K ep:16 epch:0.31 loss:0.896 grdn:41.677 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.264 kld_loss:0.063
Training:  15% 3000/20000 [31:49<2:53:03,  1.64step/s]INFO 2026-08-02 16:15:30 ot_train.py:641 step:3K smpl:24K ep:17 epch:0.34 loss:0.809 grdn:39.580 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.257 kld_loss:0.055

INFO 2026-08-02 16:15:30 ot_train.py:687 Checkpoint policy after step 3000
Training:  16% 3200/20000 [34:21<2:54:12,  1.61step/s]INFO 2026-08-02 16:18:02 ot_train.py:641 step:3K smpl:26K ep:19 epch:0.36 loss:0.743 grdn:37.976 lr:1.0e-05 updt_s:0.612 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.245 kld_loss:0.050
Training:  17% 3400/20000 [36:24<2:48:54,  1.64step/s]INFO 2026-08-02 16:20:05 ot_train.py:641 step:3K smpl:27K ep:20 epch:0.38 loss:0.671 grdn:35.022 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.236 kld_loss:0.044
Training:  18% 3600/20000 [38:26<2:47:04,  1.64step/s]INFO 2026-08-02 16:22:07 ot_train.py:641 step:4K smpl:29K ep:21 epch:0.40 loss:0.627 grdn:34.279 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.230 kld_loss:0.040
Training:  19% 3800/20000 [40:28<2:44:47,  1.64step/s]INFO 2026-08-02 16:24:09 ot_train.py:641 step:4K smpl:30K ep:22 epch:0.43 loss:0.575 grdn:32.625 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.225 kld_loss:0.035
Training:  20% 4000/20000 [42:31<2:44:45,  1.62step/s]INFO 2026-08-02 16:26:12 ot_train.py:641 step:4K smpl:32K ep:23 epch:0.45 loss:0.535 grdn:30.652 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.223 kld_loss:0.031

INFO 2026-08-02 16:26:12 ot_train.py:687 Checkpoint policy after step 4000
Training:  21% 4200/20000 [44:54<2:43:09,  1.61step/s]INFO 2026-08-02 16:28:35 ot_train.py:641 step:4K smpl:34K ep:24 epch:0.47 loss:0.493 grdn:28.584 lr:1.0e-05 updt_s:0.611 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.212 kld_loss:0.028
Training:  22% 4400/20000 [46:57<2:38:42,  1.64step/s]INFO 2026-08-02 16:30:38 ot_train.py:641 step:4K smpl:35K ep:26 epch:0.49 loss:0.470 grdn:28.426 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.213 kld_loss:0.026
Training:  23% 4600/20000 [49:00<2:36:51,  1.64step/s]INFO 2026-08-02 16:32:41 ot_train.py:641 step:5K smpl:37K ep:27 epch:0.51 loss:0.441 grdn:27.257 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.211 kld_loss:0.023
Training:  24% 4800/20000 [51:02<2:36:13,  1.62step/s]INFO 2026-08-02 16:34:43 ot_train.py:641 step:5K smpl:38K ep:28 epch:0.54 loss:0.413 grdn:25.866 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.203 kld_loss:0.021
Training:  25% 5000/20000 [53:04<2:34:19,  1.62step/s]INFO 2026-08-02 16:36:45 ot_train.py:641 step:5K smpl:40K ep:29 epch:0.56 loss:0.391 grdn:25.303 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.202 kld_loss:0.019

INFO 2026-08-02 16:36:45 ot_train.py:687 Checkpoint policy after step 5000
Training:  26% 5200/20000 [55:38<2:31:45,  1.63step/s]INFO 2026-08-02 16:39:19 ot_train.py:641 step:5K smpl:42K ep:30 epch:0.58 loss:0.374 grdn:24.231 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.200 kld_loss:0.017
Training:  27% 5400/20000 [57:41<2:28:17,  1.64step/s]INFO 2026-08-02 16:41:22 ot_train.py:641 step:5K smpl:43K ep:31 epch:0.60 loss:0.361 grdn:24.277 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.199 kld_loss:0.016
Training:  28% 5600/20000 [59:44<2:26:17,  1.64step/s]INFO 2026-08-02 16:43:25 ot_train.py:641 step:6K smpl:45K ep:33 epch:0.63 loss:0.342 grdn:22.972 lr:1.0e-05 updt_s:0.611 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.195 kld_loss:0.015
Training:  29% 5800/20000 [1:01:46<2:26:32,  1.62step/s]INFO 2026-08-02 16:45:27 ot_train.py:641 step:6K smpl:46K ep:34 epch:0.65 loss:0.331 grdn:22.369 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.194 kld_loss:0.014
Training:  30% 6000/20000 [1:03:48<2:22:42,  1.64step/s]INFO 2026-08-02 16:47:29 ot_train.py:641 step:6K smpl:48K ep:35 epch:0.67 loss:0.317 grdn:21.770 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.187 kld_loss:0.013

INFO 2026-08-02 16:47:29 ot_train.py:687 Checkpoint policy after step 6000
Training:  31% 6200/20000 [1:06:29<2:24:26,  1.59step/s]INFO 2026-08-02 16:50:10 ot_train.py:641 step:6K smpl:50K ep:36 epch:0.69 loss:0.304 grdn:21.354 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.183 kld_loss:0.012
Training:  32% 6400/20000 [1:08:31<2:17:28,  1.65step/s]INFO 2026-08-02 16:52:12 ot_train.py:641 step:6K smpl:51K ep:37 epch:0.72 loss:0.296 grdn:20.537 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.182 kld_loss:0.011
Training:  33% 6600/20000 [1:10:34<2:15:14,  1.65step/s]INFO 2026-08-02 16:54:15 ot_train.py:641 step:7K smpl:53K ep:38 epch:0.74 loss:0.286 grdn:20.440 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.178 kld_loss:0.011
Training:  34% 6800/20000 [1:12:36<2:15:03,  1.63step/s]INFO 2026-08-02 16:56:17 ot_train.py:641 step:7K smpl:54K ep:40 epch:0.76 loss:0.275 grdn:19.839 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.176 kld_loss:0.010
Training:  35% 7000/20000 [1:14:39<2:13:58,  1.62step/s]INFO 2026-08-02 16:58:20 ot_train.py:641 step:7K smpl:56K ep:41 epch:0.78 loss:0.271 grdn:19.493 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.177 kld_loss:0.009

INFO 2026-08-02 16:58:20 ot_train.py:687 Checkpoint policy after step 7000
Training:  36% 7200/20000 [1:17:42<2:10:16,  1.64step/s]INFO 2026-08-02 17:01:23 ot_train.py:641 step:7K smpl:58K ep:42 epch:0.81 loss:0.260 grdn:18.889 lr:1.0e-05 updt_s:0.610 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.170 kld_loss:0.009
Training:  37% 7400/20000 [1:19:44<2:08:51,  1.63step/s]INFO 2026-08-02 17:03:25 ot_train.py:641 step:7K smpl:59K ep:43 epch:0.83 loss:0.256 grdn:18.510 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.171 kld_loss:0.009
Training:  38% 7600/20000 [1:21:47<2:05:27,  1.65step/s]INFO 2026-08-02 17:05:28 ot_train.py:641 step:8K smpl:61K ep:44 epch:0.85 loss:0.248 grdn:18.653 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.166 kld_loss:0.008
Training:  39% 7800/20000 [1:23:49<2:04:07,  1.64step/s]INFO 2026-08-02 17:07:30 ot_train.py:641 step:8K smpl:62K ep:45 epch:0.87 loss:0.245 grdn:18.155 lr:1.0e-05 updt_s:0.606 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.169 kld_loss:0.008
Training:  40% 8000/20000 [1:25:51<2:01:35,  1.64step/s]INFO 2026-08-02 17:09:32 ot_train.py:641 step:8K smpl:64K ep:47 epch:0.90 loss:0.239 grdn:17.804 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.167 kld_loss:0.007

INFO 2026-08-02 17:09:32 ot_train.py:687 Checkpoint policy after step 8000
Training:  41% 8200/20000 [1:28:46<2:00:23,  1.63step/s]INFO 2026-08-02 17:12:27 ot_train.py:641 step:8K smpl:66K ep:48 epch:0.92 loss:0.235 grdn:17.356 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.167 kld_loss:0.007
Training:  42% 8400/20000 [1:30:48<1:57:18,  1.65step/s]INFO 2026-08-02 17:14:29 ot_train.py:641 step:8K smpl:67K ep:49 epch:0.94 loss:0.226 grdn:16.822 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.161 kld_loss:0.007
Training:  43% 8600/20000 [1:32:50<1:55:41,  1.64step/s]INFO 2026-08-02 17:16:31 ot_train.py:641 step:9K smpl:69K ep:50 epch:0.96 loss:0.223 grdn:16.357 lr:1.0e-05 updt_s:0.606 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.160 kld_loss:0.006
Training:  44% 8800/20000 [1:34:52<1:53:23,  1.65step/s]INFO 2026-08-02 17:18:33 ot_train.py:641 step:9K smpl:70K ep:51 epch:0.99 loss:0.223 grdn:16.598 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.163 kld_loss:0.006
Training:  45% 9000/20000 [1:37:00<1:53:39,  1.61step/s]INFO 2026-08-02 17:20:41 ot_train.py:641 step:9K smpl:72K ep:52 epch:1.01 loss:0.215 grdn:16.342 lr:1.0e-05 updt_s:0.630 data_s:0.006 smp/s:13 mem_gb:3.74 l1_loss:0.156 kld_loss:0.006

INFO 2026-08-02 17:20:41 ot_train.py:687 Checkpoint policy after step 9000
Training:  46% 9200/20000 [1:39:41<1:51:34,  1.61step/s]INFO 2026-08-02 17:23:22 ot_train.py:641 step:9K smpl:74K ep:54 epch:1.03 loss:0.210 grdn:15.934 lr:1.0e-05 updt_s:0.612 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.154 kld_loss:0.006
Training:  47% 9400/20000 [1:41:44<1:49:02,  1.62step/s]INFO 2026-08-02 17:25:25 ot_train.py:641 step:9K smpl:75K ep:55 epch:1.05 loss:0.211 grdn:15.935 lr:1.0e-05 updt_s:0.610 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.158 kld_loss:0.005
Training:  48% 9600/20000 [1:43:46<1:45:59,  1.64step/s]INFO 2026-08-02 17:27:27 ot_train.py:641 step:10K smpl:77K ep:56 epch:1.07 loss:0.206 grdn:15.339 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.154 kld_loss:0.005
Training:  49% 9800/20000 [1:45:48<1:42:31,  1.66step/s]INFO 2026-08-02 17:29:29 ot_train.py:641 step:10K smpl:78K ep:57 epch:1.10 loss:0.199 grdn:15.211 lr:1.0e-05 updt_s:0.606 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.150 kld_loss:0.005
Training:  50% 10000/20000 [1:47:51<1:42:12,  1.63step/s]INFO 2026-08-02 17:31:32 ot_train.py:641 step:10K smpl:80K ep:58 epch:1.12 loss:0.194 grdn:14.792 lr:1.0e-05 updt_s:0.610 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.146 kld_loss:0.005

INFO 2026-08-02 17:31:32 ot_train.py:687 Checkpoint policy after step 10000
Training:  51% 10200/20000 [1:50:45<1:41:02,  1.62step/s]INFO 2026-08-02 17:34:26 ot_train.py:641 step:10K smpl:82K ep:59 epch:1.14 loss:0.195 grdn:15.066 lr:1.0e-05 updt_s:0.610 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.149 kld_loss:0.005
Training:  52% 10400/20000 [1:52:47<1:37:54,  1.63step/s]INFO 2026-08-02 17:36:28 ot_train.py:641 step:10K smpl:83K ep:61 epch:1.16 loss:0.191 grdn:15.118 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.145 kld_loss:0.005
Training:  53% 10600/20000 [1:54:50<1:35:17,  1.64step/s]INFO 2026-08-02 17:38:31 ot_train.py:641 step:11K smpl:85K ep:62 epch:1.19 loss:0.187 grdn:14.481 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.145 kld_loss:0.004
Training:  54% 10800/20000 [1:56:52<1:32:57,  1.65step/s]INFO 2026-08-02 17:40:33 ot_train.py:641 step:11K smpl:86K ep:63 epch:1.21 loss:0.189 grdn:14.140 lr:1.0e-05 updt_s:0.610 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.147 kld_loss:0.004
Training:  55% 11000/20000 [1:58:55<1:31:42,  1.64step/s]INFO 2026-08-02 17:42:36 ot_train.py:641 step:11K smpl:88K ep:64 epch:1.23 loss:0.185 grdn:14.046 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.146 kld_loss:0.004

INFO 2026-08-02 17:42:36 ot_train.py:687 Checkpoint policy after step 11000
Training:  56% 11200/20000 [2:01:41<1:30:45,  1.62step/s]INFO 2026-08-02 17:45:22 ot_train.py:641 step:11K smpl:90K ep:65 epch:1.25 loss:0.182 grdn:13.792 lr:1.0e-05 updt_s:0.611 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.144 kld_loss:0.004
Training:  57% 11400/20000 [2:03:43<1:28:56,  1.61step/s]INFO 2026-08-02 17:47:24 ot_train.py:641 step:11K smpl:91K ep:66 epch:1.28 loss:0.182 grdn:13.991 lr:1.0e-05 updt_s:0.606 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.143 kld_loss:0.004
Training:  58% 11600/20000 [2:05:46<1:26:41,  1.61step/s]INFO 2026-08-02 17:49:27 ot_train.py:641 step:12K smpl:93K ep:68 epch:1.30 loss:0.180 grdn:13.345 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.144 kld_loss:0.004
Training:  59% 11800/20000 [2:07:48<1:24:06,  1.62step/s]INFO 2026-08-02 17:51:29 ot_train.py:641 step:12K smpl:94K ep:69 epch:1.32 loss:0.177 grdn:13.397 lr:1.0e-05 updt_s:0.605 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.142 kld_loss:0.003
Training:  60% 12000/20000 [2:09:50<1:21:56,  1.63step/s]INFO 2026-08-02 17:53:31 ot_train.py:641 step:12K smpl:96K ep:70 epch:1.34 loss:0.178 grdn:13.211 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.144 kld_loss:0.003

INFO 2026-08-02 17:53:31 ot_train.py:687 Checkpoint policy after step 12000
Training:  61% 12200/20000 [2:12:56<1:19:32,  1.63step/s]INFO 2026-08-02 17:56:37 ot_train.py:641 step:12K smpl:98K ep:71 epch:1.37 loss:0.173 grdn:13.086 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.141 kld_loss:0.003
Training:  62% 12400/20000 [2:14:58<1:17:33,  1.63step/s]INFO 2026-08-02 17:58:39 ot_train.py:641 step:12K smpl:99K ep:72 epch:1.39 loss:0.171 grdn:13.179 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.139 kld_loss:0.003
Training:  63% 12600/20000 [2:17:01<1:15:06,  1.64step/s]INFO 2026-08-02 18:00:41 ot_train.py:641 step:13K smpl:101K ep:73 epch:1.41 loss:0.169 grdn:12.581 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.139 kld_loss:0.003
Training:  64% 12800/20000 [2:19:04<1:13:14,  1.64step/s]INFO 2026-08-02 18:02:45 ot_train.py:641 step:13K smpl:102K ep:75 epch:1.43 loss:0.164 grdn:12.475 lr:1.0e-05 updt_s:0.611 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.134 kld_loss:0.003
Training:  65% 13000/20000 [2:21:06<1:11:47,  1.62step/s]INFO 2026-08-02 18:04:47 ot_train.py:641 step:13K smpl:104K ep:76 epch:1.46 loss:0.171 grdn:12.681 lr:1.0e-05 updt_s:0.605 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.143 kld_loss:0.003

INFO 2026-08-02 18:04:47 ot_train.py:687 Checkpoint policy after step 13000
Training:  66% 13200/20000 [2:24:11<1:09:46,  1.62step/s]INFO 2026-08-02 18:07:52 ot_train.py:641 step:13K smpl:106K ep:77 epch:1.48 loss:0.167 grdn:12.538 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.139 kld_loss:0.003
Training:  67% 13400/20000 [2:26:14<1:07:50,  1.62step/s]INFO 2026-08-02 18:09:55 ot_train.py:641 step:13K smpl:107K ep:78 epch:1.50 loss:0.163 grdn:12.360 lr:1.0e-05 updt_s:0.610 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.136 kld_loss:0.003
Training:  68% 13600/20000 [2:28:15<1:05:44,  1.62step/s]INFO 2026-08-02 18:11:56 ot_train.py:641 step:14K smpl:109K ep:79 epch:1.52 loss:0.162 grdn:11.997 lr:1.0e-05 updt_s:0.605 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.136 kld_loss:0.003
Training:  69% 13800/20000 [2:30:18<1:03:23,  1.63step/s]INFO 2026-08-02 18:13:59 ot_train.py:641 step:14K smpl:110K ep:80 epch:1.54 loss:0.160 grdn:12.189 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.134 kld_loss:0.003
Training:  70% 14000/20000 [2:32:21<1:00:41,  1.65step/s]INFO 2026-08-02 18:16:01 ot_train.py:641 step:14K smpl:112K ep:81 epch:1.57 loss:0.154 grdn:11.350 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.130 kld_loss:0.002

INFO 2026-08-02 18:16:01 ot_train.py:687 Checkpoint policy after step 14000
Training:  71% 14200/20000 [2:35:12<59:11,  1.63step/s]INFO 2026-08-02 18:18:53 ot_train.py:641 step:14K smpl:114K ep:83 epch:1.59 loss:0.161 grdn:11.771 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.137 kld_loss:0.002
Training:  72% 14400/20000 [2:37:14<56:55,  1.64step/s]INFO 2026-08-02 18:20:55 ot_train.py:641 step:14K smpl:115K ep:84 epch:1.61 loss:0.156 grdn:11.713 lr:1.0e-05 updt_s:0.606 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.133 kld_loss:0.002
Training:  73% 14600/20000 [2:39:17<55:17,  1.63step/s]INFO 2026-08-02 18:22:58 ot_train.py:641 step:15K smpl:117K ep:85 epch:1.63 loss:0.156 grdn:11.206 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.134 kld_loss:0.002
Training:  74% 14800/20000 [2:41:20<53:05,  1.63step/s]INFO 2026-08-02 18:25:01 ot_train.py:641 step:15K smpl:118K ep:86 epch:1.66 loss:0.152 grdn:11.322 lr:1.0e-05 updt_s:0.611 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.131 kld_loss:0.002
Training:  75% 15000/20000 [2:43:23<50:50,  1.64step/s]INFO 2026-08-02 18:27:04 ot_train.py:641 step:15K smpl:120K ep:87 epch:1.68 loss:0.150 grdn:11.391 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.128 kld_loss:0.002

INFO 2026-08-02 18:27:04 ot_train.py:687 Checkpoint policy after step 15000
Training:  76% 15200/20000 [2:46:30<48:43,  1.64step/s]INFO 2026-08-02 18:30:11 ot_train.py:641 step:15K smpl:122K ep:88 epch:1.70 loss:0.151 grdn:11.165 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.130 kld_loss:0.002
Training:  77% 15400/20000 [2:48:32<46:33,  1.65step/s]INFO 2026-08-02 18:32:13 ot_train.py:641 step:15K smpl:123K ep:90 epch:1.72 loss:0.147 grdn:10.896 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.127 kld_loss:0.002
Training:  78% 15600/20000 [2:50:34<44:59,  1.63step/s]INFO 2026-08-02 18:34:15 ot_train.py:641 step:16K smpl:125K ep:91 epch:1.75 loss:0.150 grdn:11.130 lr:1.0e-05 updt_s:0.605 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.130 kld_loss:0.002
Training:  79% 15800/20000 [2:52:36<42:53,  1.63step/s]INFO 2026-08-02 18:36:17 ot_train.py:641 step:16K smpl:126K ep:92 epch:1.77 loss:0.147 grdn:10.937 lr:1.0e-05 updt_s:0.606 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.128 kld_loss:0.002
Training:  80% 16000/20000 [2:54:38<40:41,  1.64step/s]INFO 2026-08-02 18:38:19 ot_train.py:641 step:16K smpl:128K ep:93 epch:1.79 loss:0.148 grdn:10.847 lr:1.0e-05 updt_s:0.606 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.129 kld_loss:0.002

INFO 2026-08-02 18:38:19 ot_train.py:687 Checkpoint policy after step 16000
Training:  81% 16200/20000 [2:57:42<38:51,  1.63step/s]INFO 2026-08-02 18:41:23 ot_train.py:641 step:16K smpl:130K ep:94 epch:1.81 loss:0.146 grdn:10.500 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.129 kld_loss:0.002
Training:  82% 16400/20000 [2:59:45<36:40,  1.64step/s]INFO 2026-08-02 18:43:26 ot_train.py:641 step:16K smpl:131K ep:95 epch:1.84 loss:0.144 grdn:10.622 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.126 kld_loss:0.002
Training:  83% 16600/20000 [3:01:47<34:34,  1.64step/s]INFO 2026-08-02 18:45:28 ot_train.py:641 step:17K smpl:133K ep:97 epch:1.86 loss:0.144 grdn:10.339 lr:1.0e-05 updt_s:0.609 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.127 kld_loss:0.002
Training:  84% 16800/20000 [3:03:50<32:36,  1.64step/s]INFO 2026-08-02 18:47:30 ot_train.py:641 step:17K smpl:134K ep:98 epch:1.88 loss:0.143 grdn:9.959 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.127 kld_loss:0.002
Training:  85% 17000/20000 [3:05:52<30:40,  1.63step/s]INFO 2026-08-02 18:49:33 ot_train.py:641 step:17K smpl:136K ep:99 epch:1.90 loss:0.141 grdn:10.061 lr:1.0e-05 updt_s:0.606 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.126 kld_loss:0.002

INFO 2026-08-02 18:49:33 ot_train.py:687 Checkpoint policy after step 17000
Training:  86% 17200/20000 [3:08:35<28:24,  1.64step/s]INFO 2026-08-02 18:52:16 ot_train.py:641 step:17K smpl:138K ep:100 epch:1.93 loss:0.141 grdn:9.943 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.125 kld_loss:0.002
Training:  87% 17400/20000 [3:10:37<26:18,  1.65step/s]INFO 2026-08-02 18:54:18 ot_train.py:641 step:17K smpl:139K ep:101 epch:1.95 loss:0.140 grdn:9.907 lr:1.0e-05 updt_s:0.606 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.125 kld_loss:0.001
Training:  88% 17600/20000 [3:12:39<24:20,  1.64step/s]INFO 2026-08-02 18:56:20 ot_train.py:641 step:18K smpl:141K ep:102 epch:1.97 loss:0.134 grdn:9.872 lr:1.0e-05 updt_s:0.604 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.119 kld_loss:0.001
Training:  89% 17800/20000 [3:14:41<22:19,  1.64step/s]INFO 2026-08-02 18:58:22 ot_train.py:641 step:18K smpl:142K ep:104 epch:1.99 loss:0.137 grdn:9.966 lr:1.0e-05 updt_s:0.605 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.122 kld_loss:0.001
Training:  90% 18000/20000 [3:16:43<20:18,  1.64step/s]INFO 2026-08-02 19:00:24 ot_train.py:641 step:18K smpl:144K ep:105 epch:2.01 loss:0.137 grdn:9.923 lr:1.0e-05 updt_s:0.606 data_s:0.006 smp/s:13 mem_gb:3.73 l1_loss:0.123 kld_loss:0.001

INFO 2026-08-02 19:00:24 ot_train.py:687 Checkpoint policy after step 18000
Training:  91% 18200/20000 [3:19:44<18:21,  1.63step/s]INFO 2026-08-02 19:03:25 ot_train.py:641 step:18K smpl:146K ep:106 epch:2.04 loss:0.133 grdn:9.578 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.120 kld_loss:0.001
Training:  92% 18400/20000 [3:21:47<16:11,  1.65step/s]INFO 2026-08-02 19:05:28 ot_train.py:641 step:18K smpl:147K ep:107 epch:2.06 loss:0.132 grdn:9.744 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.118 kld_loss:0.001
Training:  93% 18600/20000 [3:23:49<14:14,  1.64step/s]INFO 2026-08-02 19:07:30 ot_train.py:641 step:19K smpl:149K ep:108 epch:2.08 loss:0.133 grdn:9.548 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.120 kld_loss:0.001
Training:  94% 18800/20000 [3:25:51<12:09,  1.64step/s]INFO 2026-08-02 19:09:32 ot_train.py:641 step:19K smpl:150K ep:109 epch:2.10 loss:0.130 grdn:9.481 lr:1.0e-05 updt_s:0.606 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.117 kld_loss:0.001
Training:  95% 19000/20000 [3:27:53<10:07,  1.65step/s]INFO 2026-08-02 19:11:34 ot_train.py:641 step:19K smpl:152K ep:111 epch:2.13 loss:0.133 grdn:9.535 lr:1.0e-05 updt_s:0.604 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.120 kld_loss:0.001

INFO 2026-08-02 19:11:34 ot_train.py:687 Checkpoint policy after step 19000
Training:  96% 19200/20000 [3:30:46<08:05,  1.65step/s]INFO 2026-08-02 19:14:27 ot_train.py:641 step:19K smpl:154K ep:112 epch:2.15 loss:0.130 grdn:9.058 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.119 kld_loss:0.001
Training:  97% 19400/20000 [3:32:48<06:04,  1.65step/s]INFO 2026-08-02 19:16:29 ot_train.py:641 step:19K smpl:155K ep:113 epch:2.17 loss:0.133 grdn:9.486 lr:1.0e-05 updt_s:0.606 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.121 kld_loss:0.001
Training:  98% 19600/20000 [3:34:50<04:04,  1.63step/s]INFO 2026-08-02 19:18:31 ot_train.py:641 step:20K smpl:157K ep:114 epch:2.19 loss:0.129 grdn:8.901 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.118 kld_loss:0.001
Training:  99% 19800/20000 [3:36:53<02:02,  1.63step/s]INFO 2026-08-02 19:20:34 ot_train.py:641 step:20K smpl:158K ep:115 epch:2.22 loss:0.127 grdn:8.739 lr:1.0e-05 updt_s:0.608 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.117 kld_loss:0.001
Training: 100% 20000/20000 [3:38:55<00:00,  1.63step/s]INFO 2026-08-02 19:22:36 ot_train.py:641 step:20K smpl:160K ep:116 epch:2.24 loss:0.129 grdn:9.123 lr:1.0e-05 updt_s:0.607 data_s:0.003 smp/s:13 mem_gb:3.73 l1_loss:0.118 kld_loss:0.001

INFO 2026-08-02 19:22:36 ot_train.py:687 Checkpoint policy after step 20000
Training: 100% 20000/20000 [3:39:51<00:00,  1.52step/s]

INFO 2026-08-02 19:23:32 ot_train.py:770 End of training
```

## Policy 

INFO 2026-08-02 19:23:40 etrained.py:338 Model pushed to huggingface: [pap_green_foam_in_boxpolicy-v3](https://huggingface.co/garagelab-duesseldorf/pap_green_foam_in_boxpolicy-v3)

