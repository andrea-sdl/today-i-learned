# A simple pure CSS Radial Chart with 10% increments

I wanted a css radial that had 10% increments, this is a base example (could be easily generalized into a scss mixin)
Inspired by http://codepen.io/lumi/pen/pvuyA/
```html
<div class="pie-wrapper progress-30">
  <span class="label">30<span class="smaller">%</span></span>
  <div class="pie">
    <div class="left-side half-circle"></div>
    <div class="right-side half-circle"></div>
  </div>
</div>
```


```css
.pie-wrapper *,
.pie-wrapper *:before,
.pie-wrapper *:after {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}
.pie-wrapper {
  display: inline-block;
  height: 200px;
  margin: 10px;
  position: relative;
  width: 200px;
}
.pie-wrapper .pie {
  clip: rect(0, 200px, 200px, 100px);
  height: 200px;
  position: absolute;
  width: 200px;
}
.pie-wrapper .pie .half-circle {
  border: 15px solid #3498db;
  border-radius: 50%;
  clip: rect(0, 100px, 200px, 0);
  height: 200px;
  position: absolute;
  width: 200px;
}
.pie-wrapper .label {
  background: #34495e;
  border-radius: 50%;
  cursor: default;
  display: block;
  font-size: 3em;
  height: 200px;
  line-height: 3em;
  position: absolute;
  text-align: center;
  width: 200px;
  color:black
}
.pie-wrapper .label .smaller {
  font-size: .45em;
  padding-bottom: 20px;
  vertical-align: super;
}
.pie-wrapper.style-2 .shadow {
  border: 15px solid #bdc3c7;
  border-radius: 50%;
  height: 100%;
  width: 100%;
}
.pie-wrapper.style-2 .label {
  background: none;
}

.pie-wrapper .pie .half-circle {
  border-color: #70b300;
}
.pie-wrapper.progress-100 .shadow {
    border-color: #70b300;
}
.pie-wrapper.progress-10 .pie .right-side,
.pie-wrapper.progress-20 .pie .right-side,
.pie-wrapper.progress-30 .pie .right-side,
.pie-wrapper.progress-40 .pie .right-side,
.pie-wrapper.progress-50 .pie .right-side{
  display: none;
}
.pie-wrapper.progress-10 .pie .left-side {
  -webkit-transform: rotate(36deg);
  -moz-transform: rotate(36deg);
  -ms-transform: rotate(36deg);
  -o-transform: rotate(36deg);
  transform: rotate(36deg);
}
.pie-wrapper.progress-20 .pie .left-side {
  -webkit-transform: rotate(72deg);
  -moz-transform: rotate(72deg);
  -ms-transform: rotate(72deg);
  -o-transform: rotate(72deg);
  transform: rotate(72deg);
}

.pie-wrapper.progress-30 .pie .left-side {
  -webkit-transform: rotate(108deg);
  -moz-transform: rotate(108deg);
  -ms-transform: rotate(108deg);
  -o-transform: rotate(108deg);
  transform: rotate(108deg);
}

.pie-wrapper.progress-40 .pie .left-side {
  -webkit-transform: rotate(144deg);
  -moz-transform: rotate(144deg);
  -ms-transform: rotate(144deg);
  -o-transform: rotate(144deg);
  transform: rotate(144deg);
}

.pie-wrapper.progress-50 .pie .left-side {
  -webkit-transform: rotate(180deg);
  -moz-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  -o-transform: rotate(180deg);
  transform: rotate(180deg);
}

.pie-wrapper.progress-60 .pie,
.pie-wrapper.progress-70 .pie,
.pie-wrapper.progress-80 .pie,
.pie-wrapper.progress-90 .pie 
{
  clip: rect(auto, auto, auto, auto);
}
.pie-wrapper.progress-60 .pie .right-side,
.pie-wrapper.progress-70 .pie .right-side,
.pie-wrapper.progress-80 .pie .right-side,
.pie-wrapper.progress-90 .pie .right-side{
  -webkit-transform: rotate(180deg);
  -moz-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  -o-transform: rotate(180deg);
  transform: rotate(180deg);
}
.pie-wrapper.progress-60 .pie .left-side {
  -webkit-transform: rotate(216deg);
  -moz-transform: rotate(216deg);
  -ms-transform: rotate(216deg);
  -o-transform: rotate(216deg);
  transform: rotate(216deg);
}

.pie-wrapper.progress-70 .pie .left-side {
  -webkit-transform: rotate(252deg);
  -moz-transform: rotate(252deg);
  -ms-transform: rotate(252deg);
  -o-transform: rotate(252deg);
  transform: rotate(252deg);
}

.pie-wrapper.progress-80 .pie .left-side {
  -webkit-transform: rotate(288deg);
  -moz-transform: rotate(288deg);
  -ms-transform: rotate(288deg);
  -o-transform: rotate(288deg);
  transform: rotate(288deg);
}

.pie-wrapper.progress-90 .pie .left-side {
  -webkit-transform: rotate(324deg);
  -moz-transform: rotate(324deg);
  -ms-transform: rotate(324deg);
  -o-transform: rotate(324deg);
  transform: rotate(324deg);
}

```