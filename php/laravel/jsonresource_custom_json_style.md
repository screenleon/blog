# JsonResource custom json style
================================

**Author**: Lien Chen  **Date**: 2021-06-11

* When I use JsonResource, it return link with `{"data": {"href": "http:\/\/localhost"}`
* Seems link need to be `http://localhost`

* Try to add below code to unescaped slashes

```php
class SampleResource extends JsonResource
{
    public function toResponse($request)
    {
        return parent::toResponse($request)->setEncodingOptions(JSON_FLAGS);
    }
}
```

---

[Laravel China](https://learnku.com/articles/28054?order_by=vote_count&)
