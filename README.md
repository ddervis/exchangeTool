# vue-cryptoexchange

> madebydervis

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

# Eksiklikler

## Para Çevirici
İlk açıldığında btc birimi dönüşmemektedir. Yapıda USD ve EUR değeri girildikten sonra dönüşüm yapmaktadır.

## İnput Kontrolleri
 Manuel yapılmıştır. Kütüphane kullanılmamıştır. 25 - 25000 aralık kontrolü, USD ve EUR girişi yapılırken yapılmaktadır. BTC girişinde yapılmamaktadır. 

## Submit Etme Durumu
Süre yetişmemiştir. 

# Mimari Hakkında

İnputlar farklı iki component olarak tasarlandı. Data erişimi App.vue (parent) içerisinden gerçekleşti. API gereği BTC işlenerek ayrı bir mehtod içerisinde USD ve EUR ayrı bir method içerisinden gönderildi. 
İnputlardan gelen veriler önce App.vue'ya(parent'a) sonrasında ilgili component'e iletildi. Ancak olması gerekenin business katmanı ve dataAccess katmanı ile yapmak olduğunu düşünüyorum. 
Uğraşmaktan çok keyif aldım. Teşekkürler

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).
