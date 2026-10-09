---
description: Topics related operations
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# topics

{% hint style="info" %}
Topics management are available through API v2, which is currently in beta
{% endhint %}

{% openapi-operation spec="datagouv-api-v2" path="/topics/" method="get" %}
[OpenAPI datagouv-api-v2](https://www.data.gouv.fr/api/2/swagger.json)
{% endopenapi-operation %}

{% openapi-operation spec="datagouv-api-v2" path="/topics/" method="post" %}
[OpenAPI datagouv-api-v2](https://www.data.gouv.fr/api/2/swagger.json)
{% endopenapi-operation %}

{% openapi-operation spec="datagouv-api-v2" path="/topics/{topic}/" method="get" %}
[OpenAPI datagouv-api-v2](https://www.data.gouv.fr/api/2/swagger.json)
{% endopenapi-operation %}

{% openapi-operation spec="datagouv-api-v2" path="/topics/{topic}/" method="put" %}
[OpenAPI datagouv-api-v2](https://www.data.gouv.fr/api/2/swagger.json)
{% endopenapi-operation %}

{% openapi-operation spec="datagouv-api-v2" path="/topics/{topic}/" method="delete" %}
[OpenAPI datagouv-api-v2](https://www.data.gouv.fr/api/2/swagger.json)
{% endopenapi-operation %}

{% openapi-operation spec="datagouv-api-v2" path="/topics/{topic}/elements/" method="get" %}
[OpenAPI datagouv-api-v2](https://www.data.gouv.fr/api/2/swagger.json)
{% endopenapi-operation %}

{% openapi-operation spec="datagouv-api-v2" path="/topics/{topic}/elements/" method="post" %}
[OpenAPI datagouv-api-v2](https://www.data.gouv.fr/api/2/swagger.json)
{% endopenapi-operation %}

{% openapi-operation spec="datagouv-api-v2" path="/topics/{topic}/elements/{element_id}/" method="put" %}
[OpenAPI datagouv-api-v2](https://www.data.gouv.fr/api/2/swagger.json)
{% endopenapi-operation %}

{% openapi-operation spec="datagouv-api-v2" path="/topics/{topic}/elements/" method="delete" %}
[OpenAPI datagouv-api-v2](https://www.data.gouv.fr/api/2/swagger.json)
{% endopenapi-operation %}

{% openapi-operation spec="datagouv-api-v2" path="/topics/{topic}/elements/{element_id}/" method="delete" %}
[OpenAPI datagouv-api-v2](https://www.data.gouv.fr/api/2/swagger.json)
{% endopenapi-operation %}
