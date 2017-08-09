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
```javascript
import Ember from 'ember';

export default Ember.Route.extend({
  model() {
    return ['Marie Curie', 'Mae Jemison', 'Albert Hofmann'];
  }
});
```

<br/>

- app/templates/scientists.hbs

```html
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

```hbs
import Ember from 'ember';

export default Ember.Route.extend({
  beforeModel() {
    this.replaceWith('scientists');
  }
});

```

<br/>
<br/>

### Installing Addons Edit Page


The vendor directory in Ember is a special directory where you can include content that gets compiled into your application. When Ember CLI builds our app from our source code, it copies ember-tutorial.css into a file called vendor.css.

```
ember install ember-cli-tutorial-style
```



<br/>
<br/>

## 예제

```
ember new test-app
cd test-app
ember server
```
서버 실행 후 확인
`http://localhost:4200`

`app/templates/application.hbs`

```hbs
{{outlet}}
```

<br/>

### about page 생성

```
ember generate route about
```
or
```
ember g route about
```

<br/>

`app/templates/about.hbs` 수정

```html
<div class="jumbo">
  <div class="right tomster"></div>
  <h2>타이틀</h2>
  <p>
    설명글을 써봅니다.
  </p>
</div>
```

`http://localhost:4200/about` 확인



### Contact 페이지 생성

```
ember generate route contact
```

`app/templates/contact.hbs` 수정

```html
<div class="jumbo">
  <div class="right tomster"></div>
  <h2>Contact Us</h2>
  <p>연락처하지마세영</p>
  <p>
    하하하하하하하하하
    <address>
      마포구 동교동 197-42
    </address>
    <a href="tel:02.333.1714">(02) 333-1714</a><br>
    <a href="mailto:dev@cizion.com">dev@cizion.com</a>
  </p>
</div>
```

### link-to

`app/templates/about.hbs` 수정
```html
<div class="jumbo">
  <div class="right tomster"></div>
  <h2>타이틀</h2>
  <p>
    설명글을 써봅니다.
  </p>
  {{#link-to 'contact' class="button"}}
    Contact Us
  {{/link-to}}
</div>
```


`app/templates/contact.hbs` 수정

```html
<div class="jumbo">
  <div class="right tomster"></div>
  <h2>Contact Us</h2>
  <p>연락처하지마세영</p>
  <p>
    하하하하하하하하하
    <address>
      마포구 동교동 197-42
    </address>
    <a href="tel:02.333.1714">(02) 333-1714</a><br>
    <a href="mailto:dev@cizion.com">dev@cizion.com</a>
  </p>
  {{#link-to 'about' class="button"}}
    About
  {{/link-to}}
</div>
```

### main 생성

```
ember g route main
```


### index 생성

```
ember g route index
```

`app/routes/index.js` 수정

```javascript
import Ember from 'ember';

export default Ember.Route.extend({
  beforeModel() {
    this.replaceWith('main');
  }
});
```
index에 main 페이지를 연결 시킴 

### navigation menu만들기 

`app/templates/application.hbs`
```html
<div class="container">
  <div class="menu">
    {{#link-to 'index'}}
      <h1>
        <em>메인</em>
      </h1>
    {{/link-to}}
    <div class="links">
      {{#link-to 'about'}}
        About
      {{/link-to}}
      {{#link-to 'contact'}}
        연락처
      {{/link-to}}
    </div>
  </div>
  <div class="body">
    {{outlet}}
  </div>
</div>
```

### model hook

main.js에서 작성된 데이터를 main.hbs에서 사용
`model()` 는 `model: function()`과 같음. 정의된 메소드.

`app/routes/main.js`
```
import Ember from 'ember';

export default Ember.Route.extend({
  model() {
    return [
      {id: '1',
      title: 'title1',
      writer: 'kero',
      propertyType: 'comment',
      image: 'https://upload.wikimedia.org/wikipedia/commons/c/cb/Crane_estate_(5).jpg',
      content: '하하하핳',
      description: '설명1'},
      {id: '2',
      title: 'title2',
      writer: 'kero2',
      propertyType: 'reply',
      image: 'https://upload.wikimedia.org/wikipedia/commons/0/0e/Alfonso_13_Highrise_Tegucigalpa.jpg',
      content: '뭐야이이이이',
      description: '설명2'}
    ]
  }
});
```


`app/templates/main.hbs`
```
<div class="jumbo">
  <div class="right tomster"></div>
  <h2>Welcome!</h2>
  <p>Hello World</p>
  {{#link-to 'about' class="button"}}
    About
  {{/link-to}}
</div>
  {{#each model as |item|}}
    <article class="listing">
    <h3>{{item.title}}</h3>
    <div class="detail owner">
      <span>writer:</span> {{item.writer}}
    </div>
    <div class="detail type">
      <span>Type:</span> {{item.propertyType}}
    </div>
    <div class="detail location">
      <span>content:</span> {{item.content}}
    </div>
    <div class="detail bedrooms">
      <span>description</span> {{item.description}}
    </div>
  </article>
  {{/each}}
```

### addon 사용

`https://emberobserver.com/`에서 다른 addon을 찾을 수 있음.
ember-cli-tutorial-style 을 사용할꺼임.

```
ember install ember-cli-tutorial-style
ember s
```
스타일 적용이 뙇
변경하고자 하면 `vendor/ember-tutorial.css`에서 변경 가능


### component 추가

```
ember g component listing
```

`app/templates/components/rental-listing.hbs`
```
<article class="listing">
    <img src="{{item.image}}" alt="">
    <h3>{{item.title}}</h3>
    <div class="detail owner">
      <span>writer:</span> {{item.writer}}
    </div>
    <div class="detail type">
      <span>Type:</span> {{item.propertyType}}
    </div>
    <div class="detail location">
      <span>content:</span> {{item.content}}
    </div>
    <div class="detail bedrooms">
      <span>description</span> {{item.description}}
    </div>
  </article>
  ```
  
  
`app/templates/main.hbs`
```
<div class="jumbo">
  <div class="right tomster"></div>
  <h2>Welcome!</h2>
  <p>Hello World</p>
  {{#link-to 'about' class="button"}}
    About
  {{/link-to}}

  {{#each model as |items|}}
  {{rental-listing items=items}}
  {{/each}}
</div>
```


### image show hide action

`app/templates/components/listing.hbs`

```
<article class="listing">
 <!-- 수정 -->
 <a {{action 'toggleImageSize'}} class="image {{if isWide "wide"}}">
    <img src="{{item.image}}" alt="">
    <small>View Larger</small>
  </a>
 <!-- 수정 -->
  <h3>{{item.title}}</h3>
  <div class="detail owner">
    <span>writer:</span> {{item.writer}}
  </div>
  <div class="detail type">
    <span>Type:</span> {{item.propertyType}}
  </div>
  <div class="detail location">
    <span>content:</span> {{item.content}}
  </div>
  <div class="detail bedrooms">
    <span>description</span> {{item.description}}
  </div>
</article>
```


`app/components/listing.js`
```
import Ember from 'ember';

export default Ember.Component.extend({
  isWide: false,
  actions: {
    toggleImageSize() {
      this.toggleProperty('isWide');
    }
  }
});
```
