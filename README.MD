# Pia Homework 3

## Çalıştırma Adımları

1. Öncelikle ingress-nginx'i helm ile indiriyoruz. İndirirken sorun yaşarsanız [dokümantasyon](https://kubernetes.github.io/ingress-nginx/deploy/#quick-start)

   `helm upgrade --install ingress-nginx ingress-nginx --repo https://kubernetes.github.io/ingress-nginx --namespace ingress-nginx --create-namespace`

2. Ardından deploymentta kullanılan domaini etc/hosts'u düzenleyerek 127.0.0.1 kubernetes.docker.internal domainini ekliyoruz. Normalde docker desktop kurulum sırasında bu domaini otomatik olarak hostlara ekliyor ancak kontrol etmekte fayda var. etc/hosts windowsta windows/system32/drivers/etc/hosts adresindedir. Mac içinse [bakınız](https://www.ninjaone.com/blog/how-to-edit-hosts-file/)

3. sırasıyla yaml dosyalarımızı deploy ediyoruz.

   `cd infra
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f ingress.yaml`

4. Ardından tarayıcımızda tarayıcımızda [bu adrese](http://kubernetes.docker.internal) gidiyoruz. Ssl sertifikası olmaması sebebiyle tarayıcı uyarı verebilir. Güveniyorum diyerek geçtikten sonra ilgili sayfa yüklenecektir.

5. Hello world yazan bir sayfa açılmış olacaktır.

6. Replica sayısını değiştirmek içinse aşağıdaki örnek komutu çalıştırabilirsiniz.

   `kubectl scale deployment node-app-deployment --replicas=5`
