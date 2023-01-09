---
id: f9h7q
name: A flow in the code
file_version: 1.1.0
app_version: 1.0.6
file_blobs:
  src/script.js: 22fbbdf7f1423041805c72b4216009994febbff9
---

## Introduction

This doc describes o setup de uma cena dentro do projeto.

<br/>

## Following the flow

Para iniciar, precisa importar duas libraries dentro do script.js:

*   style.css — arquivo de estilização
    
*   THREE — depois de importar three com **npm i three**

<br/>

Inicialização do documento
<!-- NOTE-swimm-snippet: the lines below link your snippet to Swimm -->
### 📄 src/script.js
```javascript
🟩 1      import './style.css'
🟩 2      import * as THREE from 'three'
```

<br/>

——

<br/>

——

Quando se renderiza a cena, você tira uma "foto" daquele momento. Tudo que é escrito depois da renderização não aparece diretamente na cena, pois é como se acontecesse depois da captura da foto.

<br/>

Renderização de cenas
<!-- NOTE-swimm-snippet: the lines below link your snippet to Swimm -->
### 📄 src/script.js
```javascript
🟩 50     // Renderer
🟩 51     const renderer = new THREE.WebGLRenderer({
🟩 52         canvas: canvas
🟩 53     })
🟩 54     renderer.setSize(sizes.width, sizes.height)
```

<br/>

<div align="center"><img src="https://media4.giphy.com/media/j5E9vHJSjBcDTXe4E4/giphy.gif?cid=d56c4a8bl40tb20urwjd4s1ezk0sprd9wwnwkm2w07a2pyd2&rid=giphy.gif&ct=g" style="width:'50%'"/></div>

<br/>

## Things to note

{{Who uses this flow and when?}}

<br/>

This file was generated by Swimm. [Click here to view it in the app](https://app.swimm.io/repos/Z2l0aHViJTNBJTNBVGhyZWVKU19Qcm9qZWN0JTNBJTNBZGFuaWVsYXBhc3Nvcw==/docs/f9h7q).