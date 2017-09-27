

#//10
#Advanced Selector:不仅方便选择，而且能够扩充效果
##:target 伪类:当元素满足于某一种状态的时候
- 表示元素被hash匹配时的状态
- 比如URL是/post/a#heading时，name为heading的元素处于被target的状态

<nav>
  <a href="#p1">History</a>
  <a href="#p2">Geography</a>
  <a href="#p3">Plants</a>
</nav>
<p id="p1">Native Americans have inhabited the area since long before white settlers first saw Lassen.</p>
<p id="p2">The park is locate near the northern end of the Sacramento Velley.</p>
<p id="p3">Lying at the northern end of the Sierra Nevada forests ecoregion, Lassen Volcanic National Park preserves a landscape nearly as it existed before Euro-American settlement</p>
<style>
  p:target {
    color: red;
  }
</style>

<nav>
  <a href="#p1">History</a>
  <a href="#p2">Geography</a>
  <a href="#p3">Plants</a>
</nav>
<p id="p1">Native Americans have inhabited the area since long before white settlers first saw Lassen.</p>
<p id="p2">The park is locate near the northern end of the Sacramento Velley.</p>
<p id="p3">Lying at the northern end of the Sierra Nevada forests ecoregion, Lassen Volcanic National Park preserves a landscape nearly as it existed before Euro-American settlement</p>
<style>
  p {
    display: none;
  }
  p:target {
    display: block;
  }
</style>

##:lang伪类
- 元素匹配上指定语言时的状态
- 浏览器通过lang属性获得语言信息

<section>
  <p><q>C'est la vie</q>, il parlait.</p>
</section>
<style>
:lang(fr) q:before {
  content: "《"
}
:lang(fr) q:after {
  content: "》";
}
</style>

##:nth-child
- 通过：nth-child(an+b)选中某些子元素
- 例如：nth-child(3n)选中第3、6、9……个子元素
- a可以为负数
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
  <li>Item 4</li>
  <li>Item 5</li>
  <li>Item 6</li>
  <li>Item 7</li>
</ul>
<style>
  li:nth-child(3n+1) {
    color: red;
  }
</style>


<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
  <li>Item 4</li>
  <li>Item 5</li>
  <li>Item 6</li>
  <li>Item 7</li>
</ul>
<style>
  li:nth-child(odd) {
    color: red;
  }
  li:nth-child(even) {
    color: green;
  }
</style>

##:nth-of-type: 第n个同类型的元素
<article>
  <h1>This is a test</h1>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
  <p>Paragraph 3</p>
  <p>Paragraph 4</p>
</article>
<style>
article :nth-child(3n+1) {//1,4
  color: red;
}
article :nth-of-type(3n+1) {//1,2,4
  text-decoration: underline;
}
</style>

http://nthmaster.com/

##:first-child
<p>
text 1
<button>Button 1</button>
<button>Button 2</button>
<button>Button 3</button>
<button>Button 4</button>
text 2
</p>
<style>
button {
  margin-left: 2em;
}
button:first-child {
  margin-left: 0;
}
</style>

<p>
text 1
<button>Button 1</button>
<button>Button 2</button>
<button>Button 3</button>
<button>Button 4</button>
text 2
</p>
<style>
button {
  margin-right: 2em;
}
button:last-child {
  margin-right: 0;
}
</style>

##:not()  括号里面的selector都排队掉
- 排队匹配的元素
- 比如 img:not([alt])  选择没有写alt属性的图片

<p>
text 1
<button>Button 1</button>
<button>Button 2</button>
<button>Button 3</button>
<button>Button 4</button>
text 2
</p>
<style>
button:not(:last-child) {
  margin-right: 2em;
}
</style>

##其它选择器
- :nth-last-child()
- :nth-last-of-type()
- :first-of-type
- :last-of-type
- :only-child   
- :only-of-type

##:empty
<ul>
  <li>Item 1</li>
  <li></li>
  <li><Item 2</li>
</ul>
<style>
li:empty {
  display: none;
}
</style>

##::first-line 跟文字相关的伪元素，这个就不是伪类了，伪类是真实存在的元素，伪元素是在HTML里面压根就没有这个元素，在CSS里面虚拟出来的元素
<p>Species that area typically found in these forested areas are black bear, fox, mule deer, marten, cougar, brown creeper, a variety of chipmunk species, raccoon, mountain chickadee, a variety of squirrel species, white-headed woodpecker, coyote, bobcat, weasel, a variety of muse species, long-toed salamander, skunk, and a wide variety of bat species.</p>
<style>
p::first-line {
  color: red;
}
</style>


<p>Species that area typically found in these forested areas are black bear, fox, mule deer, marten, cougar, brown creeper, a variety of chipmunk species, raccoon, mountain chickadee, a variety of squirrel species, white-headed woodpecker, coyote, bobcat, weasel, a variety of muse species, long-toed salamander, skunk, and a wide variety of bat species.</p>
<style>
p {
  font-family: Helvetica, sans-serif;
}
p::first-letter {
  font-size: 2em;
  float: left;
  color: red;
}
</style>

##兄弟选择器
- 相邻兄弟选择器 E + F
- 通用兄弟选择器 E ~ F

<section>
  <p>There area active hot sprints and mud pots in the Lassen area.</p>
  <h2>Volcanoes rise</h2>
  <p>Pyroclastic eruptions then started to pile tephra into cones in the northern area of the park.</p>
  <p>Mount Tehama(also known as Brokeoff Volcano) rose as a stratovolcano in the southwestern corner of the park during the Pleistocene.</p>
</section>
<style>
  h2 + p {
    color: red;
  }
  h2 ~ p {
    text-decoration: underline;
  }
</style>

##:checked ~ F
<div class="toggle">
  <input type="checkbox" checked id="t">
  <label for="t"></label>
</div>
<style>
.toggle {
  width: 80px;
  height: 26px;
  background: #333;
  margin: 20px auto;
  position: relative;
  border-radius: 50px;
  box-shadow: inset 0px 1px 1px rgba(0,0,0,0.5),0px 1px 0px rgba(255,255,255,0.2);
}
.toggle:after {
  content: 'OFF',
  color: #fff;
  position: absolute;
  right: 10px;
  z-index: 0;
  font: 12px/26px Arial, sans-serif;
  font-weight: bold;
  text-shadow: 1px 1px 0px rgba(255,255,255,.15);
}
.toggle:before {
  content: 'ON';
  color: #f66;
  position: absolute;
  left: 10px;
  z-index: 0;
  font: 12px/26px Arial, sans-serif;
  font-weight: bold;
}
.toggle label {
  display: block;
  width: 34px;
  height: 20px;
  cursor: pointer;
  position: absolute;
  top: 3px;
  left: 3px;
  z-idnex: 1;
  background: #fcfff4;
  background: linear-gradient(top, #fcfff4 0%, #dfe5d7 40% #b3bead 100%);
  border-radius: 50px;
  transition: all 0.4s ease;
  box-shadow: 0px 2px 5px 0px rgbba(0,0,0,0.3);
}
.toggle input[type=checkbox] {
  visibility: hidden;
}
.toggle input:check + label {
  left: 43px;
}
</style>
