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
ember new super-rentals
cd super-rentals
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
  <h2>About Super Rentals</h2>
  <p>
    The Super Rentals website is a delightful project created to explore Ember.
    By building a property rental site, we can simultaneously imagine traveling
    AND building Ember applications.
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
  <p>Super Rentals Representatives would love to help you<br>choose a destination or answer
    any questions you may have.</p>
  <p>
    Super Rentals HQ
    <address>
      1212 Test Address Avenue<br>
      Testington, OR 97233
    </address>
    <a href="tel:503.555.1212">+1 (503) 555-1212</a><br>
    <a href="mailto:superrentalsrep@emberjs.com">superrentalsrep@emberjs.com</a>
  </p>
</div>
```

### link-to

`app/templates/about.hbs` 수정
```html
<div class="jumbo">
  <div class="right tomster"></div>
  <h2>About Super Rentals</h2>
  <p>
    The Super Rentals website is a delightful project created to explore Ember.
    By building a property rental site, we can simultaneously imagine traveling
    AND building Ember applications.
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
  <p>Super Rentals Representatives would love to help you<br>choose a destination or answer
    any questions you may have.</p>
  <p>
    Super Rentals HQ
    <address>
      1212 Test Address Avenue<br>
      Testington, OR 97233
    </address>
    <a href="tel:503.555.1212">+1 (503) 555-1212</a><br>
    <a href="mailto:superrentalsrep@emberjs.com">superrentalsrep@emberjs.com</a>
  </p>
  {{#link-to 'about' class="button"}}
    About
  {{/link-to}}
</div>
```



