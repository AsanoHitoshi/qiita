---
title: 【入門】Laravel×Vue.js②〜実装編〜
tags:
  - PHP
  - JavaScript
  - Laravel
  - Vue.js
private: false
updated_at: '2019-12-22T14:47:07+09:00'
id: cddd90cad30e8a4e4b22
organization_url_name: null
slide: false
ignorePublish: false
---
#はじめに
**PHPのフレームワークであるLaravel**で作成したアプリケーションに
**JavaScriptのフレームワークであるVue.js**を連携させる方法について説明します。
簡単な機能を実装します。自分のコンポーネントを登録する方法について説明します
**実装する機能
　　メッセージを表示して、ボタンを押すと、メッセージを反転する**

#コンポーネントの作成
まず、`resources/js/components/`内に`HelloComponent.vue`を作成してください
そして、内容を以下のようにしてください

```html:resources/js/components/HelloComponent.vue
<template>
	<div id="app">
	  <p>{{ message }}</p>
	  <button v-on:click="reverseMessage">Reverse Message</button>
	</div>
</template>
<script>
export default {
	  data:function(){
		  return {
		    message: 'Hello Vue!',
		  };
	  },
	  methods: {
	    reverseMessage: function () {
	      this.message = this.message.split('').reverse().join('')
	    }
	  }
}
</script>
```


#コンポーネントの登録
上で作成したコンポーネントを登録しましょう

```javascript:resource/js/app.js
require('./bootstrap');

window.Vue = require('vue');

Vue.component('example-component', require('./components/ExampleComponent.vue').default);
Vue.component('hello-component', require('./components/HelloComponent.vue').default);


```

#ビューファイルへの組み込み
ビューファイルの追加したい時に下記を記述してください

```html:hello/index.blade.php
<div id="app">
  <hello-component></hello-component>
</div>
```

以上で実装完了です。

**疑問、気になるところがございましたら、質問、コメントよろしくお願いします！！！**
