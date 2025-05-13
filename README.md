# ter-homeworks-01
##### 1.1

![](https://github.com/raeeduard/ter-homeworks-01-/blob/main/1.png?raw=true)

##### 1.2 

personal.auto.tfvars

#####  1.3 

"bcrypt_hash": "$2a$10$TwR00dQK1wtNI2q0TBs6iOSaKGC70/wjwG0eAZFxexWko44PxIgdO"

"result": "BRjtKXv28qv4soJE"
#####  1.4

 Первая ошибка заключалась в наименовании ресурса "1nginx". Такого не существует
 
 Вторая ошибка заключалась в строке name  = "example_${random_password.random_string_FAKE.resulT}". Не существует имени andom_string_FAKE.resulT. Вместо этого есть random_string.result
 
 И третья ошибка в том, что указан тип ресурса "docker image", но не указано имя nginx

#####  1.5
 
 resource "docker_image" "nginx" {
 
  name         = "nginx:latest"
  
  keep_locally = true

}

resource "docker_container" "nginx" {
  
  image = docker_image.nginx.image_id
  
  name  = "example_${random_password.random_string.result}"

  
  ports {
    
    internal = 80
    
    external = 9090
  }
}

![](https://github.com/raeeduard/ter-homeworks-01-/blob/main/1.5.png?raw=true)

#####  1.6 

Опасность -auto-approve:
Ключ -auto-approve автоматически подтверждает применение изменений без ручного подтверждения пользователем. Основные риски:

Неожиданные изменения инфраструктуры - Terraform применит все изменения без предупреждения

Удаление ресурсов - может случайно удалить критически важные компоненты

Отсутствие ревью - пропускает этап проверки изменений

Когда полезен -auto-approve:
В CI/CD пайплайнах для автоматического деплоя

Для регулярных apply в тестовых средах

В скриптах автоматического управления инфраструктурой

![](https://github.com/raeeduard/ter-homeworks-01-/blob/main/1.6.png?raw=true)

#####  1.7

{
  
  "version": 4,
  
  "terraform_version": "1.9.0",
  
  "serial": 17,
  
  "lineage": "70e75e2d-afd6-f354-760c-045a701675f1",
  
  "outputs": {},
  
  "resources": [],
  
  "check_results": null

}

1.8

keep_locally (Boolean) If true, then the Docker image won't be deleted on destroy operation. 

If this is false, it will delete the image from the docker local storage on destroy operation.

В этой строчке причина того, что образ не удален. 

keep_locally = true установлено в нашем случае.
