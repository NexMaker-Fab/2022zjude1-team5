# HTML

```html
<script>
  window.$docsify = {
    name: "Your Name",
    repo: "",
    loadSidebar: true, //prepare for sidebar
    loadNavbar: true, //prepare for navbar
    alias: {
      "/.*/_sidebar.md": "/_sidebar.md",
    },
    sidebarDisplayLevel: 1,
  };
</script>

<!-- Docsify v4 -->
<script src="//cdn.jsdelivr.net/npm/docsify@4"></script>

<!-- plugins -->
<script src="//cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/docsify-sidebar-collapse.min.js"></script>
```

# css

```css
body {
  /* background: linear-gradient(
    to right top,
    #a8eb12
  ); */
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  background-attachment: fixed;
}

.sidebar {
  background-color: transparent;
}

.sidebar > h1 {
  font-weight: 700;
}
```

# Arduino

```c
const int buttonPin = 2;     // the number of the pushbutton pin
const int ledPin =  13;      // the number of the LED pin

// variables will change:
int buttonState = 0;         // variable for reading the pushbutton status

void setup() {
  // initialize the LED pin as an output:
  pinMode(ledPin, OUTPUT);
  // initialize the pushbutton pin as an input:
  pinMode(buttonPin, INPUT);
}

```

# Processing

```java
//height是眼睛的高度
float height = 120;

//b是火花描边的颜色
int b = 0;

void setup() {
  size(600, 600);
  noStroke();
  loop();
}

void draw() {
  background(0);

  //火花形状
  stroke(b);
  line(mouseX-8, mouseY, mouseX-16, mouseY);
  line(mouseX+8, mouseY, mouseX+16, mouseY);
  line(mouseX+5, mouseY+8, mouseX+8,mouseY+13);

  //眨眼后睁眼，火花熄灭
  if (millis()>1000) {
    height = 120;
    b = 0;
  }
}
```
