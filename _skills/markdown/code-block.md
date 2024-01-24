---
layout: skill
title: Markdown - Code Block 작성하기
date: 2023-04-09
---




- code block은 2가지 방법으로 작성할 수 있습니다.




---




## 방법 1. Code Tag로 감싸기

- `<pre><code> </code></pre>`를 사용합니다.


### 문법

```txt
<pre>
<code>
main( ) {
    puts("Hello, world!");
    return 0;
}
</code>
</pre>
```


### 결과

<pre><code>main( ) {
    puts("Hello, world!");
    return 0;
}</code></pre>




---




## 방법 2. Code Block Code로 감싸기

- \`\`\` \`\`\`를 사용합니다.


### 문법

<pre><code class='language-plaintext'>```
main( ) {
    puts("Hello, world!");
    return 0;
}
```</code></pre>


### 결과

```
main( ) {
    puts("Hello, world!");
    return 0;
}
```