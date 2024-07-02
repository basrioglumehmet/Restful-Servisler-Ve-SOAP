
![alt text](young-happy-woman-drinking-coffee-by-car_1303-22430.jpg)
# Giriş
Selam! Bu repository içerisinde RESTful servisler ve SOAP nedir gibi konulara değineceğim. Bu konuları daha detaylı öğrenmek ve araştırmak için birçok kaynak bulunmaktadır. Bu kaynaklardan biri de yazmış olduğum bu repository'dir. Elbette, başka kaynaklara da yer vereceğim.

## REST

- Representational State Transfer olarak bilinir
- Sistemler arası iletişim kolaydır
- Http üzerinden tanımlanır ve manipüle edilir
- Rest mimarisine uygun olan apilere Rest Api servisi denir
- Xml veya JSON dahil istenilen formatta response edilir

### RESTful API Nedir

- Cihazlar arası sistemin internet üzerinden  bilgi alışverişi yapmak için kullanılan birimdir.

### RESTful API Avantajları

- Ölçeklenebilir
- Esneklik
- Bağımsızlık

### RESTful API Çalışma Mantığı

- Client Server'a istek atar
- Server Client'a istek doğrultusunda response verir. Bu response içerisinde body vb. önemli bilgileri içerir.

### RESTful API Durum Kodları

- 200 OK (Genel Başarılı)
- 201 Created (Frontend tarafından gelen body verisi serverda db kayıdı oluşturma durumu örnek verilebilir)
- 204 No Content (Veri bulunmadığı durum örnek verilebilir)
- 400 Bad Request (İstenilen model doğru olmayabilir bu duruma örnek verilebilir)
- 401 Unauthorized (Api güvenliği örnek verilebilir)
- 409 Conflict (Varolan veriyi tekrar oluşturmaya çalışmak örnek verilebilir)
- 403 Forbidden (Rol  veya token yetkilendirmeleri örnek verilebilir)

> [!IMPORTANT]
> 200,201,400,401,409,403 En çok kullanacağımız durum kodlarıdır

## SOAP
- Simple Object Access Protocol olarak bilinir
- Veri formatı XML'dir
- Bazen HTTP bazen de TCP/IP protokolleri kullanılır
- Kurumsal şirketler ağırlıklı kullanır
- Üst düzey güvenliklidir
- 4 Bölümden oluşmaktadır:
    - Envelope (Zarf): SOAP mesajının en dıştaki elemanıdır ve mesajın bir SOAP mesajı olduğunu belirler. Diğer tüm bölümleri içerir.
    - Header (Başlık): Bu isteğe bağlı bölüm, mesajın işlenmesine ilişkin başlık bilgilerini içerir. Örneğin, kimlik doğrulama veya işlem detayları gibi bilgiler olabilir.
    - Body (Gövde): Mesajın ana bölümüdür ve aslında değiştirilen verileri içerir. İstek veya yanıt mesajlarını ve ilgili parametrelerini içerir.
    - Fault (Hata): Bu isteğe bağlı bölüm, mesajın işlenmesinde meydana gelen hataları gösterir. Hata kodunu ve hata açıklamasını içerir.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope/">
  <soap:Header>
    <auth:Authentication xmlns:auth="http://example.com/auth">
      <username>johnDoe</username>
      <password>password123</password>
    </auth:Authentication>
  </soap:Header>
  <soap:Body>
    <get:GetUserDetails xmlns:get="http://example.com/getuserdetails">
      <userId>12345</userId>
    </get:GetUserDetails>
  </soap:Body>
</soap:Envelope>
```
### Response
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope/">
  <soap:Body>
    <get:GetUserDetailsResponse xmlns:get="http://example.com/getuserdetails">
      <userDetails>
        <name>John Doe</name>
        <email>johndoe@example.com</email>
        <phoneNumber>123-456-7890</phoneNumber>
      </userDetails>
    </get:GetUserDetailsResponse>
  </soap:Body>
</soap:Envelope>
```

## WSDL
- Web Service Description Language olarak bilinir
- Soap isteklerinde WSDL kullanılır
- Soap isteklerin kaydını tutmakla ve XML servis oluşturmakla yükümlüdür
- W3C Standardını kullanır: Web standardı topluluğu olarak bilinir
- WSDL dosyaları, genellikle.wsdl uzantılı dosyalar olarak kaydedilir.
- WSDL, web hizmetlerinin belgelenmesi ve dokümantasyonunda kullanılır.