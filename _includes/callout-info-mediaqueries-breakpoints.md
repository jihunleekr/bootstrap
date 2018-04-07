{% capture callout %}
브라우저는 현재 [범위 기반 쿼리](https://www.w3.org/TR/mediaqueries-4/#range-context) 를 지원하지 않으므로 우리는 분수형 너비 (예: 고해상도 장치의 특정 조건에서 발생할 수 있음) 의 [접두어 `min-` 과 `max-` ](https://www.w3.org/TR/mediaqueries-4/#mq-min-max) 와 뷰포트 제한사항을 더 정밀한 값을 사용함으로써 극복하고 있습니다.
{% endcapture %}
{% include callout.html content=callout type="info" %}
