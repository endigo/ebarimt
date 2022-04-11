# ebarimt as a HTTP service

## Docker image

```
docker pull registry.gitlab.com/endigo/ebarimt:latest
```

## License үүсгэх

[https://posapi.vercel.app](https://posapi.vercel.app)

## Жишээ ажиллуулах

1. `git clone git@github.com:endigo/ebarimt.git`
2. `cd ebarimt/examples`
3. `docker-compose up`
4. `curl -XGET http://localhost:8080/getInformation`
5. `curl -XGET http://localhost:8080/checkApi`
6. `curl -XPOST http://localhost:8080/sendData`
7. [http://localhost:8080/docs](http://localhost:8080/docs) эсвэл
8. [http://localhost:8080/redoc](http://localhost:8080/redoc) хандаж API document унших

# ⚠️ Энд байгаа `libPosAPI.so` файл нь тестийн зориулалттай файл болно.

# Changes

- `FastAPI` руу шилжүүлсэн.
- `Ubuntu 14.04` -с `Ubuntu 20.04` руу шилжүүлсэн.
- `/batch-put` нэмэгдсэн. Нэг дор олон баримт үүсгэх боломжтой болсон.
- `/api/*` alias нэмэгдсэн.
- `API_KEY` нэмсэн. Public domain тохируулах бол ашиглах
- Олон `libPosAPI.so` ашиглах боломжтой болсон.
  QueryParam болон Header ашиглаж хооронд нь сольж болно.

```
curl --request GET \
  --url http://localhost:8080/checkApi?lib=0000038
```

```
curl --request GET \
  --url http://localhost:8080/checkApi \
  --header 'x-lib: 0000038'
```

- Дээрхийн аль 1г дамжуулаагүй тохиолдолд `libPosAPI.so` файлыг default-р ашиглана.
- `libPosAPI.so` олдохгүй тохиолдолд алдаа шиднэ.

- Байгууллагын регистрийн дугаараар шалгах боломжтой болсон.

```
curl --request GET \
  --url http://localhost:8080/organization/1234567
```

- Хувь хүний регистрийг хөрвүүлэх боломжтой болсон

```
curl --request POST \
  --url http://localhost:8080/citizen \
  --header 'content-type: application/json' \
  --data '{"registerNo": "АБ11223344"}'
```

- `LICENSE_KEY` нэмэгдсэн.
