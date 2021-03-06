# vue2-timeago 
[![vue2](https://img.shields.io/badge/vue-2.x-brightgreen.svg)](https://vuejs.org/) [![npm](https://img.shields.io/npm/v/vue2-timeago.svg)](https://www.npmjs.com/package/vue2-timeago) [![npm](https://img.shields.io/npm/l/vue2-timeago.svg)](https://github.com/runkids/vue2-timeago/blob/master/LICENSE)

- Localization supported
- Show tooltip 
- Auto refresh time
- When time refresh call a customizable function 
- Formats a date/timestamp to:
  -  just now
  -  5m
  -  3h
  -  2 days ago
  -  2017-08-03
- Rules:
  -  less than 1 minute , show `just now`
  -  1 minute ~ 1 hour , show `** minutes ago`
  -  1 hour ~ 1 day , show `** hours ago`
  -  1 day ~ 1 month( 31 days ) , show `** days ago`
  -  more than 1 month( 31 days ) , show `yyyy-mm-dd hh:mm`

## Live Demo
[![Edit vue2_timeago_demo](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/embed/myomwvkojj)

## Installation 
Get from npm / yarn:
```js
npm i vue2-timeago
```
```js
yarn add vue2-timeago
```
or just include [vue2-timeago.js](https://github.com/runkids/vue2-timeago/blob/master/dist/vue2-timeago.js) to your view like 

```js
<script src='./vue2-timeago.js'></script>
```

## Usage
Use this inside your app:
``` js
import TimeAgo from 'vue2-timeago'

export default {
  name: 'app',
  components: {
    TimeAgo,
  }
}
```

##### With Default CSS 
```js
import 'vue2-timeago/dist/vue2-timeago.css'
```
or just include [vue2-timeago.css](https://github.com/runkids/vue2-timeago/blob/master/dist/vue2-timeago.css)


##### HTML
```html
<time-ago :refresh="60" :datetime="new Date(2018, 7, 4, 0, 24, 0)" locale="zh_TW" tooltip></time-ago>
```
## Examples

#####  1. locale
Default locale is en, and the library supports en and zh_TW.
```html
<time-ago locale="en"></time-ago> 
<time-ago :locale="locale"></time-ago> use v-bind
```
```js
export default {
  ...
  data(){
    return{
      locale:"zh_TW",
    }
  },
  ...
```
#####  2. datetime
```html
<time-ago datetime="2018-08-03 15:47:00"></time-ago> 
<time-ago :datetime="new Date(2018, 7, 4, 0, 24, 0)"></time-ago> use v-bind
<time-ago :datetime="1533286641826"></time-ago> timestamp
```
  - Note. Don't bind with `new Date()` when you use refresh property.
  Because every time refresh will get a new date value.

    ```html
    <time-ago :datetime="new Date(2018, 7, 4, 0, 24, 0)"></time-ago>  --> OK
    <time-ago refresh :datetime="new Date()"></time-ago> --> not OK
    ```

    If you want use new Date() , just remove datetime property.

    ```html
    <time-ago refresh></time-ago>
    ```

#####  3.  refresh
```html
<time-ago refresh></time-ago> Boolean , default refresh time 60/s
<time-ago :refresh="3600"></time-ago> bind value with a number
```

#####  4. tooltip
<img src="https://i.imgur.com/mRMt7Ps.png"/>

```html
<time-ago tooltip></time-ago> Show tooltip 
```

#####  5. long
```html
<time-ago :datetime="datetime"></time-ago> show : 2d
<time-ago :datetime="datetime" long></time-ago> show : 2 days ago
```

#####  6. todo
You can do something when time refresh every time
<img src="https://i.imgur.com/V1K6Xa2.gif"/>

```html
<time-ago :refresh="1" :locale="locale" :todo="()=> count+=1"></time-ago>
```
#####  7. native event
```html
<time-ago @click.native="todo"></>
```
## Props

| Property  |  Type |  Default |  Description |
| ------------ | ------------ | ------------ | ------------ |
| datetime  |  Date, String, Number  |  new Date()  | The datetime to be formatted.|
| locale  |  String  |  en    | message language |
| refresh  |  Boolean, Number  |  false    | The period to update the component, in seconds. When true it will be 60s. Also you can bind a number.|
| long  |  Boolean  |  false    | Show long string with time message . ex. 3h -> 3 hours age|
| tooltip  |  Boolean  |  false    | Show tooltip.|
| todo  |  Function  |  false    | You can call a function when time refresh every time.|

## Contributions
locale translations: The component needs more locale translations. You can `Open an issue to write the locale translations, or submit a pull request`. 
See example [here](https://github.com/runkids/vue2-timeago/blob/master/src/lib/lang).

locale support list : 
- English ( en )  
- 繁體中文 ( zh_TW ) 
- 简体中文 ( zh_CN )
- 日本語 ( jp )
