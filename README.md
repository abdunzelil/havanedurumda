# Hava Ne Durumda

Bu uygulama temelde API'lerle nasıl çalışılır, API'den veri nasıl `GET` edilir gibi işlemleri anlamak için yapılmıştır.

Uygulama fotoğrafları:

<img title="" src="https://github.com/devEge/havanedurumda/blob/master/images/ss1.png" alt="image1" width="211"> <img title="" src="https://github.com/devEge/havanedurumda/blob/master/images/ss2.png" alt="image2" width="211" data-align="inline"> <img title="" src="https://github.com/devEge/havanedurumda/blob/master/images/ss3.png" alt="image3" width="211">

Uygulamada API servisi olarak https://collectapi.com servisini kullandım. Siz de hava durumu API'ne erişmek için aşağıdaki linke tıklayabilirsiniz.

https://collectapi.com/tr/api/weather/hava-durumu-api

---

Bilmeyen arkadaşlar için; API'den veri çekerken sitenin size verdiği `authorization`

keyini header kısmında yollamanız gerekmektedir, aksi takdirde aşağıdaki hatayı alacaksınız:

![unAuthorizedError](https://github.com/devEge/havanedurumda/blob/master/images/unAuthorized.png)

Bunu düzeltmek için `GET` metodunda şunlardan birini yazabilirsiniz:

```dart
await http.get(Uri.parse("https://api.collectapi.com/weather/getWeather?data.lang=tr&data.city=$city"), headers: {
      HttpHeaders.authorizationHeader: 'apikey YOURAPIKEYHEREYOURAPIKEYHEREYOURAPIKEYHERE',
      HttpHeaders.contentTypeHeader: 'application/json'
    });
```

Ya da

```dart
await http.get(Uri.parse("https://api.collectapi.com/weather/getWeather?data.lang=tr&data.city=$city"), headers: {
      "authorization": 'apikey YOURAPIKEYHEREYOURAPIKEYHEREYOURAPIKEYHERE',
      "content": 'application/json'
    });
```
