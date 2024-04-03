``` json
{
  "name": "dpo train",
  "type": "debugpy",
  "request": "launch",
  "module": "deepspeed.launcher.runner",
  "console": "integratedTerminal",
  "justMyCode": false,
  "subProcess": true,
  "env": {
      "OMP_NUM_THREADS": "16"
  },
  "cwd": "${workspaceFolder}/LLM42/train",
  "args": [
      "--include=localhost:0,1,2,3,4,5,6,7",
      "--master_port=61000",
      "./train_dpo.py",
      "--output_dir=./outputs/bart-test",
      "--max_length=2048",
      "--num_train_epochs=1",
      "--per_device_train_batch_size=16",
      "--learning_rate=5e-7",
      "--lr_scheduler_type=cosine",
      "--warmup_ratio=0.1",
      "--gradient_accumulation_steps=1",
      "--evaluation_strategy=no",
      "--save_strategy=epoch",
      "--logging_strategy=steps",
      "--logging_steps=1",
      "--save_total_limit=4",
      "--report_to=none",
      "--remove_unused_columns=False",
      "--gradient_checkpointing=True",
      "--torch_compile=True",
      "--bf16",
      "--tf32=True",
      "--deepspeed=./config/zero3_adafactor_30b_batch1_24GB.json"
  ]
}
```
