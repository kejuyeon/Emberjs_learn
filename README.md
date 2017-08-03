# Emberjs_learn

## Ember?

Ember는 대규모에 복잡한 유저 상호작용을 사용하는 웹사이트를 구축하는데 도움을 줄 수 있도록 디자인 된 자바스크립트 프론트엔드 프레임워크입니다. 이는 현대적인 웹앱의 복잡성을 관리하는데 필요한 많은 기능과 빠른 반복 작업을 가능하게 하는 통합 개발 툴킷을 제공하기에 가능합니다.

<br/>

## Quick Start
1. Installing Ember.
2. Creating a new application.
3. Defining a route.
4. Writing a UI component.
5. Building your app to be deployed to production.


### Install Ember

```
npm install -g ember-cli@2.14
```


### Create a New Application

```
ember new ember-quickstart
```

```
cd ember-quickstart
ember server
```

```
Livereload server on http://localhost:49152
Serving on http://localhost:4200/
```

(To stop the server at any time, type Ctrl-C in your terminal.)

브라우저에서 열기 `http://localhost:4200/`


### Define a Route

```
ember generate route scientists
```
<br/>

- app/templates/scientists.hbs
```html
<h2>List of Scientists</h2>
```

브라우저에서 열기 `http://localhost:4200/scientists`

<br/>

- app/routes/scientists.js
``` javascript
import Ember from 'ember';

export default Ember.Route.extend({
  model() {
    return ['Marie Curie', 'Mae Jemison', 'Albert Hofmann'];
  }
});
```

<br/>

- app/templates/scientists.hbs

``` html
<h2>List of Scientists</h2>

<ul>
  {{#each model as |scientist|}}
    <li>{{scientist}}</li>
  {{/each}}
</ul>
```

<br/>

변경사항 확인

<br/>

index 설정

```
import Ember from 'ember';

export default Ember.Route.extend({
  beforeModel() {
    this.replaceWith('rentals');
  }
});

```
