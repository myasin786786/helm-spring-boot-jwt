# Usage
1. Update the values.yaml file for deployment in dev cluster
    1.1 image
    1.2 tag
    1.3 service type to NodePort if want to expose on worker node port, LoadBalancer if using load balancer. If using ingresss then service type as ClusterIP
    1.4 for ingress usage enabled: true, provide a domain name in hosts section

2. to apply in different env
helm upgarde --install release-name spring-boot-jwt/ -f spring-boot-jwt/values.yaml
helm upgarde --install release-name spring-boot-jwt/ -f spring-boot-jwt/staging-values.yaml
helm upgarde --install release-name spring-boot-jwt/ -f spring-boot-jwt/prod-values.yaml

3. To uninstall
helm uninstall release-name


4. Send a post request to /authenticate to get a bearer token that can be used with rest calls
  ```
  curl --location --request POST 'http://springboot-jwt.rnssolutions.com/authenticate' \
  --header 'Content-Type: application/json' \
  --data-raw '{"username": "javainuse", "password": "password"}'

  ```

5.Copy the Token from above command and use with /hello url
  ```
  curl --location --request GET 'http://springboot-jwt.rnssolutions.com:8080/hello' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJqYXZhaW51c2UiLCJleHAiOjE2NjkwNzgzNTIsImlhdCI6MTY2OTA2MDM1Mn0.Xd4rxqvAvv1SP_ydvwfI8yFntFY6fvHCMbaVFueeo7ysb67f8RfP0V_p0tJmwWVBjT9Le33UEvhOgQcVe5N98Q'

  ```
