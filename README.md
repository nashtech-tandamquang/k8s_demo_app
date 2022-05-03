# Deploy NGINX sử dụng Helm

## Điều kiện ban đầu:
Bạn phải có Kubernetes và một loại cluster được cài đặt (trong ví dụ này sử dụng minikube)

## Thực hiện cài đặt

### Bước 1: Khởi chạy cluster

> minikube start

### Bước 2: Kích hoạt NGINX Ingress Controller trong minikube

Để kích hoạt NGINX Ingress Controller, chạy câu lệnh sau:

> minikube addons enable ingress 

Xác thực rằng NGINX Ingress Controller đang chạy:

> kubectl get pods -n ingress-nginx

Đầu ra sau khi chạy lệnh trên như sau:

~~~
NAME                                        READY   STATUS      RESTARTS    AGE
ingress-nginx-admission-create-g9g49        0/1     Completed   0          11m
ingress-nginx-admission-patch-rqp78         0/1     Completed   1          11m
ingress-nginx-controller-59b45fb494-26npt   1/1     Running     0          11m
~~~

### Bước 3: Deploy Hello World app sử dụng Helm

- Đầu tiên cần tạo một Chart bởi Helm sử dụng câu lệnh:

  > helm create <name_of_chart>

- Tiếp theo tạo các resource Kubernestes: Bao gồm các deployments, services, ingress, ... Những manifest tạo các resource này được đăt trong thư mục template.

- Sử dụng helm để deploy ứng dụng, sử dụng câu lệnh:
  > helm upgrade --install <name> <path_to_chart_directory>

