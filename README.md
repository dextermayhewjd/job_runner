# job_runner
不让显卡空转，本地的作业提交系统


## 一个job应该的样子

```yaml
name: cs336_a1_ts
workdir: /myworkstation/projects/assignment1-basics 
# 应该是项目的目录 使用uv的地方
entrypoint:
  - uv
  - run
  - python
  - cs336_basics/train_llm/debug_train.py
gpus: 1
# 这个是资源请求 1个gpu
# 这个不是代表cuda使用的是哪个 好像已经放在了omegaconf yaml里了
env:
  WANDB_MODE: offline
# 考虑日后是否需要加上去

args:
  lr: 0.001
  batch_size: 32
  max_steps: 100
# 这里应该是parser的部分 但是目前还没有这个需求 作业全部通过omegaconf的要求来修改
# 通过parser 传入config的目录
``` 