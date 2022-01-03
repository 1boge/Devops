### Домашняя работа к занятию “MLOps/DataOps”
Цель задания

На основе полученных знаний необходимо настроить окружение и провести обучение модели.
Задание:

    Устанавливаем и настраиваем conda
    Устанавливаем и настраиваем python3
    Устанавливаем и настраиваем mlflow
    Настраиваем переменные: export MLFLOW_TRACKING_URI=http://localhost export MLFLOW_S3_ENDPOINT_URL=http://localhost:9000
    Настраиваем MinIO
    Берём модель отсюда https://github.com/sachua/mlflow-docker-compose
    Проводим её обучение: mlflow models serve -m S3://mlflow/0/98bdf6ec158145908af39f86156c347f/artifacts/model -p 1234

Домашнее задание выполните в файле readme.md в github репозитории.
### Результат:

1) ![изображение](https://user-images.githubusercontent.com/67161186/147962912-c17022d0-3a7a-43b9-9c50-cba5bce4bc61.png)
2) ![изображение](https://user-images.githubusercontent.com/67161186/147962976-bf885b0b-fadb-4b6c-958f-1e930a991bfa.png)
3) ![изображение](https://user-images.githubusercontent.com/67161186/147963019-b4c3852c-4d38-4cff-ad4e-cd374e9b2ff3.png)
4) Запуск модели с последующим ее хранением в с3:
![изображение](https://user-images.githubusercontent.com/67161186/147963152-751fe8ef-8218-4290-a3bd-a8c5ca676c54.png)
5) Minio:
![изображение](https://user-images.githubusercontent.com/67161186/147963222-aaa2f73e-cd2e-41b8-8cd7-db7066016ee9.png)
![изображение](https://user-images.githubusercontent.com/67161186/147963266-bf51ed80-146c-4166-a927-30ac1b23d974.png)
6) Контейнеры и запущенный ран модели:
![изображение](https://user-images.githubusercontent.com/67161186/147963455-d2165ffe-0a67-4352-acce-17a07cebf4cb.png)
![изображение](https://user-images.githubusercontent.com/67161186/147963403-b000fef3-de94-4069-8374-9c1bf03daa3c.png)
7) Модель не удается обучить, постоянно ругается на модуль в склерне: sklearn.linear_model.coordinate_descent Я уже перепробовал разные версии конды, питона, переустанавливал пакеты во всех окружениях, но все время ругается на этот модуль.
Лог:
(mlflow-3bacde36ad7490a004a00adbe06cfdc218396015) alexey@alexey-ThinkCentre-M900:~$ mlflow models serve -m s3://mlflow/0/3e08bf1b36d64d8fac79823e0aecf214/artifacts/model -p 1234
2022/01/03 18:48:39 INFO mlflow.models.cli: Selected backend for flavor 'python_function'
2022/01/03 18:48:40 INFO mlflow.pyfunc.backend: === Running command 'source /home/alexey/miniconda3/bin/../etc/profile.d/conda.sh && conda activate mlflow-3bacde36ad7490a004a00adbe06cfdc218396015 1>&2 && gunicorn --timeout=60 -b 127.0.0.1:1234 -w 1 ${GUNICORN_CMD_ARGS} -- mlflow.pyfunc.scoring_server.wsgi:app'
[2022-01-03 18:48:40 +0100] [6987] [INFO] Starting gunicorn 20.1.0
[2022-01-03 18:48:40 +0100] [6987] [INFO] Listening at: http://127.0.0.1:1234 (6987)
[2022-01-03 18:48:40 +0100] [6987] [INFO] Using worker: sync
[2022-01-03 18:48:40 +0100] [6995] [INFO] Booting worker with pid: 6995
[2022-01-03 18:48:41 +0100] [6995] [ERROR] Exception in worker process
Traceback (most recent call last):
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/gunicorn/arbiter.py", line 589, in spawn_worker
    worker.init_process()
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/gunicorn/workers/base.py", line 134, in init_process
    self.load_wsgi()
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/gunicorn/workers/base.py", line 146, in load_wsgi
    self.wsgi = self.app.wsgi()
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/gunicorn/app/base.py", line 67, in wsgi
    self.callable = self.load()
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/gunicorn/app/wsgiapp.py", line 58, in load
    return self.load_wsgiapp()
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/gunicorn/app/wsgiapp.py", line 48, in load_wsgiapp
    return util.import_app(self.app_uri)
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/gunicorn/util.py", line 359, in import_app
    mod = importlib.import_module(module)
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/importlib/__init__.py", line 127, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
  File "<frozen importlib._bootstrap>", line 1006, in _gcd_import
  File "<frozen importlib._bootstrap>", line 983, in _find_and_load
  File "<frozen importlib._bootstrap>", line 967, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 677, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 728, in exec_module
  File "<frozen importlib._bootstrap>", line 219, in _call_with_frames_removed
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/mlflow/pyfunc/scoring_server/wsgi.py", line 6, in <module>
    app = scoring_server.init(load_model(os.environ[scoring_server._SERVER_MODEL_PATH]))
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/mlflow/pyfunc/__init__.py", line 670, in load_model
    model_impl = importlib.import_module(conf[MAIN])._load_pyfunc(data_path)
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/mlflow/sklearn/__init__.py", line 459, in _load_pyfunc
    return _load_model_from_local_file(path=path, serialization_format=serialization_format)
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/mlflow/sklearn/__init__.py", line 417, in _load_model_from_local_file
    return cloudpickle.load(f)
### ModuleNotFoundError: No module named 'sklearn.linear_model.coordinate_descent'
[2022-01-03 18:48:41 +0100] [6995] [INFO] Worker exiting (pid: 6995)
[2022-01-03 18:48:42 +0100] [6987] [INFO] Shutting down: Master
[2022-01-03 18:48:42 +0100] [6987] [INFO] Reason: Worker failed to boot.
Traceback (most recent call last):
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/bin/mlflow", line 8, in <module>
    sys.exit(cli())
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/click/core.py", line 1128, in __call__
    return self.main(*args, **kwargs)
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/click/core.py", line 1053, in main
    rv = self.invoke(ctx)
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/click/core.py", line 1659, in invoke
    return _process_result(sub_ctx.command.invoke(sub_ctx))
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/click/core.py", line 1659, in invoke
    return _process_result(sub_ctx.command.invoke(sub_ctx))
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/click/core.py", line 1395, in invoke
    return ctx.invoke(self.callback, **ctx.params)
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/click/core.py", line 754, in invoke
    return __callback(*args, **kwargs)
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/mlflow/models/cli.py", line 59, in serve
    ).serve(model_uri=model_uri, port=port, host=host, enable_mlserver=enable_mlserver)
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/mlflow/pyfunc/backend.py", line 79, in serve
    conda_env_path, command, self._install_mlflow, command_env=command_env
  File "/home/alexey/miniconda3/envs/mlflow-3bacde36ad7490a004a00adbe06cfdc218396015/lib/python3.7/site-packages/mlflow/pyfunc/backend.py", line 168, in _execute_in_conda_env
    "Command '{0}' returned non zero return code. Return code = {1}".format(command, rc)
Exception: Command 'source /home/alexey/miniconda3/bin/../etc/profile.d/conda.sh && conda activate mlflow-3bacde36ad7490a004a00adbe06cfdc218396015 1>&2 && gunicorn --timeout=60 -b 127.0.0.1:1234 -w 1 ${GUNICORN_CMD_ARGS} -- mlflow.pyfunc.scoring_server.wsgi:app' returned non zero return code. Return code = 3
