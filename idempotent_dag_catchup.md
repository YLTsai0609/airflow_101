# Idempotent DAG Implementation

* keyword : [`airflow idempotent with pendulum now`](https://www.google.com/search?q=airflow+idempotent+with+pendulum+now&sxsrf=APwXEdfqouFJ1SL8Ir6tF_P6AX9JJljEhQ%3A1687833835260&ei=60yaZI_ID5PS-QaqrangBA&ved=0ahUKEwjP6cKBt-L_AhUTad4KHapWCkwQ4dUDCBA&uact=5&oq=airflow+idempotent+with+pendulum+now&gs_lp=Egxnd3Mtd2l6LXNlcnAiJGFpcmZsb3cgaWRlbXBvdGVudCB3aXRoIHBlbmR1bHVtIG5vdzIFECEYoAEyBRAhGKABSKUoUK0DWLsncAF4AZABAJgBaaABjhCqAQQyNC4yuAEDyAEA-AEBwgIKEAAYRxjWBBiwA8ICBxAjGLACGCfCAgcQABgNGIAEwgIGEAAYBxgewgIIEAAYBxgeGBPCAgYQABgeGBPCAggQABiABBjLAcICBBAAGB7CAgcQIRigARgKwgIFEAAYogTiAwQYACBBiAYBkAYK&sclient=gws-wiz-serp)


* idempotent DAG - 無論何時跑，給定一樣的輸入，就輸出一樣的資料
* 使用 datetime.today(), ... 來跑，並不 idempotent， 函數會跟著 scheduler heartbeat
* airflow 有提供模板來給定 execution date (logical date , airflow < 2.2)

```
yesterday = {{ yesterday_ds_nodash }}
```

[What does execution_date mean?](https://airflow.apache.org/docs/apache-airflow/stable/faq.html#faq-what-does-execution-date-mean)

各種 [built-in variables and marcos](https://airflow.apache.org/docs/apache-airflow/stable/templates-ref.html)

[DAG writing best practices in Apache Airflow](https://docs.astronomer.io/learn/dag-best-practices?tab=good-practice#avoid-top-level-code-in-your-dag-file)

# Catchup

if catchup = True

    dag 起始日 - 1201

    修正後 dag 執行日 1230，會把 1201 一路跑到 1230
else:

    只跑 1230 之後