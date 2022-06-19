#  お試し

https://cloud.google.com/run/docs/quickstarts/jobs/build-create-go?hl=ja

## コマンド

### デプロイ

```bash
$ gcloud builds submit --pack image=gcr.io/PROJECT_ID/logger-job
```


### 実行

```bash
$ gcloud beta run jobs create job-quickstart \
    --image gcr.io/PROJECT_ID/logger-job \
    --tasks 50 \
    --set-env-vars SLEEP_MS=10000 \
    --set-env-vars FAIL_RATE=0.5 \
    --max-retries 5 \
    --region REGION
```

### ローカルテスト

```bash
$ docker run --rm -e FAIL_RATE=0.9 -e SLEEP_MS=1000 gcr.io/PROJECT_ID/logger-job
```


## スケジュール登録

https://cloud.google.com/run/docs/execute/jobs-on-schedule?hl=ja#console

```
https://REGION-run.googleapis.com/apis/run.googleapis.com/v1/namespaces/PROJECT-ID/jobs/JOB-NAME:run
```


