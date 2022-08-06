---
layout: page
title: "CSS Samples"
permalink: ebook/
---

{% include menu2.md %}

## Base CSS
### Lists

```
/*sidebar*/

ol li p {
font-family:"Graphik", sans-serif;
font-weight: normal;
font-size: 95%;
color: black;
}

ol li {
font-family:"Graphik", sans-serif;
font-weight: bold;
color: #666;
}

.InlineHeadSidebar{
font-weight:bold;
}

ul li{
color: #aaa;
}

ul li p {
color: black;
}

```

```
@font-face {
	font-family:"Graphik";
	font-style:normal;
	font-weight:900;
	src : url("../font/Graphik-Black.otf");
}
@font-face {
	font-family:"Graphik";
	font-style:normal;
	font-weight:bold;
	src : url("../font/Graphik-Bold.otf");
}
@font-face {
	font-family:"Graphik";
	font-style:normal;
	font-weight:500;
	src : url("../font/Graphik-Medium.otf");
}
@font-face {
	font-family:"Graphik";
	font-style:normal;
	font-weight:normal;
	src : url("../font/Graphik-Regular.otf");
}
@font-face {
	font-family:"Graphik";
	font-style:normal;
	font-weight:600;
	src : url("../font/Graphik-Semibold.otf");
}
```