# FabUnit 🪄

FabUnit is a sass function that helps you to define a perfectly responsive value without any effort. It takes a minimum and an optimum value, spits out a calculation to your css property, considering the screen width, aspect ratio and the specified anchor points. No media queries, no break points, no design jumps. A formula that controls and synchronises your whole project.

```scss
fab-unit(12, 16); 🪄
```
 

[↓ Features](#-features)   
[↓ Install](#-install)  
[↓ Use](#-use)  
[↓ Options](#-options)  
[↓ Links](#-links)  
 
&nbsp;

## 💚 Features

- takes min and opt value
- 4 customisable anchor points
- improved tablet view (stretch opt screen)
- auto max size, depending on the last anchor point (wrapper)
- considers aspect ratio


```
size
|                                     ○ • • •
|                               •     |
|                 ○ • • • ◉           |
|           •     |       |           |
| • • ◉           |       |           |
|     |           |       |           |
|     |     ≈     |       |     ≈     |
■---min---fluid---opt---opt---fluid---max----- screen
          m=auto               m=1
      |            |      |           |
      Mobile              Desktop     Wrapper
      Design              Design      (optional)
```
[→ FabUnit Visualiser](https://codepen.io/Faboolea/live/yLvGMqZ/ed43660a7931e55b2fb2ec35d18e7f8c) 

&nbsp;

## 📀 Install

```bash
npm i fab-unit
```

```scss
@import "fab-unit";

html {
  font-size: calc(100% * (#{strip-units($fab-rem-base)} / 16)); // px to rem
}
```
  
&nbsp;

## 🚀 Use 


```scss
body {
    font-size: fab-unit(16, 22); // min, opt
}
```
[→ Example CodeSandbox](https://codesandbox.io/s/fabunit-ow8wjr)
  
&nbsp;

## 🍬 Options 
| Variable | Description | Default |
| -------- | ----------- | ------- |
| <sub>`$fab-screen-min`</sub> | <sub>anchor point mobile</sub>  | <sub>`375`</sub>
| <sub>`$fab-screen-opt-start`</sub> | <sub>anchor point desktop (from …)</sub> | <sub>`1024`</sub>
| <sub>`$fab-screen-opt-end`</sub> | <sub>anchor point desktop (… to)</sub> | <sub>`1440`</sub>
| <sub>`$fab-screen-max`</sub> | <sub>anchor point max layout wrapper</sub>  | <sub>`1800`*</sub>
| <sub>`$fab-aspect-ratio`</sub> | <sub>aspect ratio factor (improvement for wider screens)</sub> | <sub>`math.div(16, 9)`</sub>

*<sub>\* set to `false` if no max wrapper is needed (elastic upwards)</sub>*

[→ FabUnit Visualiser](https://codepen.io/Faboolea/live/yLvGMqZ/ed43660a7931e55b2fb2ec35d18e7f8c)  

&nbsp;

### Overwrite default values globally
```scss
$fab-screen-min: 300;
$fab-screen-opt-start: 768;
$fab-screen-opt-end: 1024;
$fab-screen-max: 2000;
$fab-aspect-ratio: math.div(3, 2);

body {
    font-size: fab-unit(16, 22); // min, opt
}

h1 {
  font-size: fab-unit(36, 60);
  margin-block: fab-unit(10, 16);
}

.wrapper {
  max-width: rem($fab-screen-max);
  margin-inline: auto;
}
```
[→ Example CodeSandbox](https://codesandbox.io/s/fabunit-ow8wjr)
  
&nbsp;

### Set custom arguments locally (exceptionally)

```scss
.thing {
    /* min, opt, custom anchor points, aspect ratio 🪄 */
    height: fab-unit(16, 22, 300, 768, 1024, 2000, math.div(4, 3));
}
```
  
&nbsp;

## 🔥 Links
[→ FabUnit Visualiser](https://codepen.io/Faboolea/live/yLvGMqZ/ed43660a7931e55b2fb2ec35d18e7f8c)  
[→ Example CodeSandbox](https://codesandbox.io/s/fabunit-ow8wjr)  
[→ Article Smashing Magazine*](#)