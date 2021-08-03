# Helm Chart Repository

1. git clone this repo

    ```
    git clone https://github.com/bookmanj/helm-chart.git
    ```

2. add charts under the helm-chart-sources folder
    
    ```
    helm-chart-sources
    └───my-service
        ├───charts
        └───templates
            └───tests
    ```

3. outside of the helm-chart-sources folder package the added chart

    ```
    helm package .\helm-chart-sources\my-service
    
    Successfully packaged chart and saved it to: C:\Users\jpu\CloudStation\_2021\poc\k8sStuff\helmStuff\chart_to_git\helm-chart\my-service-0.1.0.tgz
    ```

4. generate the index.yaml file to include all created helm chart packages

    ```
    helm repo index --url https://bookmanj.github.io/helm-chart/ .
    ```

5. validate helm chart package has been added to index.yaml file

    ```
    cat .\index.yaml

    apiVersion: v1
    entries:
        my-service:
        - apiVersion: v2
          appVersion: "1.0"
          created: "2021-08-03T08:43:59.3951809-05:00"
          description: A helm chart for my-service example
          digest: 878c88326d50c57a56305ec2e7043889c5ca339d28d5095f74904b9c5e9fb1c4
          name: my-service
          type: application
          urls:
          - https://bookmanj.github.io/helm-chart/my-service-0.1.0.tgz
          version: 0.1.0
    generated: "2021-08-03T08:43:59.3940497-05:00"
    ```

6. add, commit and push newly added helm chart files, package and index.yaml to main branch

    ```
    git add .
    ```
    ```
    git commit -m “Initial commit”
    ```
    ```
    git push
    
    Enumerating objects: 15, done.
    Counting objects: 100% (15/15), done.
    Delta compression using up to 12 threads
    Compressing objects: 100% (12/12), done.
    Writing objects: 100% (14/14), 4.10 KiB | 1.37 MiB/s, done.
    Total 14 (delta 0), reused 0 (delta 0), pack-reused 0
    To https://github.com/bookmanj/helm-chart.git
        a0cb6d6..966a100  main -> main
    ```

## Add and Search Helm Chart repo

- Add repo

    ```
    helm repo add myhelmrepo https://bookmanj.github.io/helm-chart/
    
    "myhelmrepo" has been added to your repositories
    ```

- Search repo

    ```
    helm search repo my-service
    
    NAME                    CHART VERSION   APP VERSION     DESCRIPTION
    myhelmrepo/my-service   0.1.0           1.0             A helm chart for my-service example
    ```