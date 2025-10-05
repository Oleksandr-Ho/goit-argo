# GitOps-репозиторій для ArgoCD

Цей каталог слугує шаблоном репозиторію, який потрібно створити окремо (наприклад, `https://github.com/Oleksandr-Ho/goit-argo`).
Саме на цей репозиторій посилається ArgoCD Application з домашнього завдання №7.

## Структура

```
.
├── application.yaml                # Опис Helm-деплою MLflow
├── namespaces
│   ├── application
│   │   ├── mlflow-config.yaml      # Демонстраційний ресурс у namespace застосунку
│   │   └── ns.yaml                 # Namespace mlflow
│   └── infra-tools
│       └── ns.yaml                 # Namespace для сервісів на кшталт ArgoCD
└── values
    └── mlflow-values.yaml          # Дубль overrides для довідки (основні values вбудовано в application.yaml)
```

## Як використати

1. Створіть на GitHub новий публічний репозиторій `goit-argo`.
2. Скопіюйте вміст цього каталогу та запуште його в гілку `main` нового репозиторію.
3. Переконайтеся, що URL репозиторію збігається з тим, який вказано у файлі `application.yaml`.
4. Після git push ArgoCD (з домашнього завдання №7) автоматично підхопить Application і розгорне MLflow.

## Порт-forward до MLflow

```bash
kubectl port-forward svc/mlflow -n mlflow 5000:5000
```

Після цього інтерфейс буде доступний за адресою <http://localhost:5000>.
