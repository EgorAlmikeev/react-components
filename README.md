# react-components

[Kodaktor](https://kodaktor.ru/?!=compo2_15162)

```javascript
<!DOCTYPE html>
<html>
 <head>
  <title>Кастомные элементы</title><meta charset="utf-8">
 </head>
 <body>
  <article>
    <h1>Кастомные элементы</h1>
    <h4 id="EgorA" title="GossJS"> EgorA </h4>
	<x-cntr val="100"></x-cntr>
	<br>
	<x-cntr val="16"></x-cntr>
  </article><script>{

  class Counter extends HTMLElement { 
    constructor() {
		super();
      const shadow = this.attachShadow({mode: 'open'});
      this.style.cursor = 'pointer';
      
      this.val = this.getAttribute('val');
      const spanArrow = document.createElement('span');
      this.spanVal = document.createElement('span');
      
      
      spanArrow.appendChild(document.createTextNode('☝︎☝︎'));
      this.spanVal.appendChild(document.createTextNode(this.val));
      shadow.appendChild(spanArrow);
      shadow.appendChild(this.spanVal);
      
      this.addEventListener('click', e => {
        this.val++;
        this.setAttribute('val', this.val);
      });
    }
    static get observedAttributes(){
      return ['val'];
    }
    attributeChangedCallback(name, oldValue, newValue) {
      this.spanVal.textContent = newValue;
    }
  }
  customElements.define('x-cntr', Counter);
  
}</script>
 </body>
</html>
```
