# Les métas données

## Annotation des images

Les json+ld sont enfin un peu partout! [La documentation sur W3](https://www.w3.org/TR/annotation-model/)

Exemple :
```json
/*Example 2: External Web Resources*/
{
  "@context": "http://www.w3.org/ns/anno.jsonld",
  "id": "http://example.org/anno2",
  "type": "Annotation",
  "body": {
    "id": "http://example.org/analysis1.mp3",
    "format": "audio/mpeg",
    "language": "fr"
  },
  "target": {
    "id": "http://example.gov/patent1.pdf",
    "format": "application/pdf",
    "language": ["en", "ar"],
    "textDirection": "ltr",
    "processingLanguage": "en"
  }
}
```

Il faut qu'un serveur envoie les données JSON+LD avec les bonnes entêtes [Sources / documentation](https://www.w3.org/TR/annotation-protocol/)
```http
HTTP/1.1 200 OK
Content-Type: application/ld+json; profile="http://www.w3.org/ns/anno.jsonld"
Link: <http://www.w3.org/ns/ldp#Resource>; rel="type"
ETag: "_87e52ce126126"
Allow: PUT,GET,OPTIONS,HEAD,DELETE,PATCH
Vary: Accept
Content-Length: 287
```
```JSON
{
  "@context": "http://www.w3.org/ns/anno.jsonld",
  "id": "http://example.org/annotations/anno1",
  "type": "Annotation",
  "created": "2015-01-31T12:03:45Z",
  "body": {
    "type": "TextualBody",
    "value": "I like this page!"
  },
  "target": "http://www.example.com/index.html"
}
```
