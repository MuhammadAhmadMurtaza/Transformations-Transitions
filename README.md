<div align="center">

# 🎨 CSS Fundamentals: Transform, Transitions & a Responsive Download Page

**Three projects on moving elements, animating changes between states, and building a responsive multilingual card grid**

</div>

---

## 📖 About This Repository

This repository contains mini-projects I built while learning CSS. Each folder holds a single `index.html` file, so every concept is easy to see, edit, and experiment with.

No frameworks, no build tools. Just HTML and CSS.

---

## 📑 Table of Contents

1. [Project Structure](#-project-structure)
2. [Project 1: Responsive Download Page](#-project-1-responsive-download-page)
3. [Experiment 2: CSS Transform](#-experiment-2-css-transform)
4. [Experiment 3: CSS Transitions](#-experiment-3-css-transitions)
5. [How Transform and Transition Work Together](#-how-transform-and-transition-work-together)
6. [How to Run](#-how-to-run)
7. [Key Takeaways](#-key-takeaways)
8. [Roadmap](#-roadmap)

---

## 📂 Project Structure

```
css-fundamentals/
│
├── 18-download-page/
│   └── index.html
│
├── 19-css-transform/
│   └── index.html
│
├── 20-css-transitions/
│   └── index.html
│
└── README.md
```

> 💡 Rename the folders to match your own layout. Each `index.html` is fully standalone.

---

## 📥 Project 1: Responsive Download Page

📁 `18-download-page/index.html`

### 🎯 Goal
Build a clean, responsive page of **language cards**, each with its own download button, using CSS Grid and a media query.

### 🧱 Page Structure

<table>
  <tr>
    <th>Part</th>
    <th>Contents</th>
    <th>Key technique</th>
  </tr>
  <tr>
    <td><b>Container</b></td>
    <td>Centered wrapper at 80% width</td>
    <td><code>width: 80%; margin: 50px auto;</code></td>
  </tr>
  <tr>
    <td><b>Heading</b></td>
    <td>"Download UltraEdit for Windows"</td>
    <td><code>text-align: center</code>, light <code>font-weight: 400</code></td>
  </tr>
  <tr>
    <td><b>Grid</b></td>
    <td>Nine language cards (English, Deutsch, Italiano, Español, Français, Português, 日本語, 한국어, 中国)</td>
    <td><code>grid-template-columns: repeat(3, 1fr)</code></td>
  </tr>
  <tr>
    <td><b>Card</b></td>
    <td>Language name, English label, download button</td>
    <td>Padding, rounded corners, centered text</td>
  </tr>
</table>

### 🔑 Concepts Covered

<table>
  <tr>
    <th>Concept</th>
    <th>Where it's used</th>
    <th>Why it matters</th>
  </tr>
  <tr>
    <td>Equal-width columns</td>
    <td><code>repeat(3, 1fr)</code></td>
    <td>Three columns that share the available space equally.</td>
  </tr>
  <tr>
    <td>Responsive collapse</td>
    <td><code>@media (max-width: 768px)</code></td>
    <td>Switches to <code>1fr</code> (a single column) on tablets and phones.</td>
  </tr>
  <tr>
    <td>Grid <code>gap</code></td>
    <td><code>.grid</code></td>
    <td>Even spacing between cards in both directions.</td>
  </tr>
  <tr>
    <td>Universal reset + <code>border-box</code></td>
    <td><code>*</code></td>
    <td>Predictable sizing: padding and borders stay inside the declared width.</td>
  </tr>
  <tr>
    <td>Button states</td>
    <td><code>.card button:hover</code></td>
    <td>A darker green on hover gives clear feedback.</td>
  </tr>
  <tr>
    <td>Non-breaking space</td>
    <td><code>&lt;p&gt;&amp;nbsp;&lt;/p&gt;</code></td>
    <td>The English card has no subtitle, so a blank character keeps its height and button aligned with the others.</td>
  </tr>
  <tr>
    <td>Multilingual text</td>
    <td>Japanese, Korean, Chinese</td>
    <td>Layouts must handle different scripts and character widths, not just English.</td>
  </tr>
</table>

### 🧪 Code Highlight

```css
.container {
  width: 80%;
  margin: 50px auto;
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 25px;
}

.card {
  background-color: #f9f9f9;
  text-align: center;
  padding: 25px;
  border-radius: 6px;
}

.card button {
  background-color: #5cb85c;
  color: white;
  border: none;
  padding: 12px 18px;
  border-radius: 6px;
  cursor: pointer;
  font-weight: bold;
}

.card button:hover {
  background-color: #4cae4c;
}

/* One column on small screens */
@media (max-width: 768px) {
  .grid {
    grid-template-columns: 1fr;
  }
}
```

### 🎨 Color Palette

<table>
  <tr>
    <th>Use</th>
    <th>Value</th>
  </tr>
  <tr>
    <td>Page background</td>
    <td><code>white</code></td>
  </tr>
  <tr>
    <td>Card background</td>
    <td><code>#f9f9f9</code></td>
  </tr>
  <tr>
    <td>Subtitle text</td>
    <td><code>gray</code></td>
  </tr>
  <tr>
    <td>Button</td>
    <td><code>#5cb85c</code></td>
  </tr>
  <tr>
    <td>Button hover</td>
    <td><code>#4cae4c</code></td>
  </tr>
</table>

### 🐛 Common Pitfalls

<table>
  <tr>
    <td>⚠️</td>
    <td><b>Wrong label:</b> <code>中国</code> means "China" (the country). For the language, the usual label is <code>中文</code>, or <code>简体中文</code> / <code>繁體中文</code> for Simplified and Traditional.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>Missing <code>lang</code> attributes:</b> add <code>lang="ja"</code>, <code>lang="ko"</code>, <code>lang="zh"</code>, etc. on those elements so browsers pick the right fonts and screen readers pronounce them correctly.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>The <code>&amp;nbsp;</code> trick:</b> it works, but a cleaner option is to give every <code>&lt;p&gt;</code> a <code>min-height</code> in CSS.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>Buttons without links:</b> real download buttons would be <code>&lt;a href="..."&gt;</code> elements styled like buttons, so they actually download something.</td>
  </tr>
</table>

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Resize the window below 768px and watch the three columns collapse into one.
2. Add a second breakpoint for tablets, for example `@media (max-width: 1024px) { .grid { grid-template-columns: repeat(2, 1fr); } }`.
3. Replace `repeat(3, 1fr)` with `repeat(auto-fit, minmax(250px, 1fr))` and delete the media query. The grid now adapts by itself.
4. Remove the `&nbsp;` from the English card and see the button move out of line with its neighbors.
5. Add `transition: transform 0.2s;` and `.card:hover { transform: translateY(-5px); }` to lift each card on hover.
6. Add `lang="ja"` to the Japanese card and compare the font rendering.

</details>

---

## 🔄 Experiment 2: CSS Transform

📁 `19-css-transform/index.html`

### 🎯 Goal
Rotate, skew, move, and scale an element **without affecting the layout around it**.

### 🔑 Concepts Covered

<table>
  <tr>
    <th>Function</th>
    <th>Example</th>
    <th>What it does</th>
  </tr>
  <tr>
    <td><code>rotate()</code></td>
    <td><code>rotate(.125turn)</code></td>
    <td>Rotates the element. <code>.125turn</code> is the same as <code>45deg</code>.</td>
  </tr>
  <tr>
    <td><code>rotateZ()</code></td>
    <td><code>rotateZ(9deg)</code></td>
    <td>Rotates around the Z axis. In 2D it behaves like <code>rotate()</code>.</td>
  </tr>
  <tr>
    <td><code>skew()</code></td>
    <td><code>skew(34deg)</code></td>
    <td>Slants the element. A single value skews along the X axis only.</td>
  </tr>
  <tr>
    <td><code>skewX()</code> / <code>skewY()</code></td>
    <td><code>skewX(40deg)</code></td>
    <td>Slants along one specific axis.</td>
  </tr>
  <tr>
    <td><code>translateX()</code> / <code>translateY()</code></td>
    <td><code>translateY(100%)</code></td>
    <td>Moves the element. Percentages are relative to the <b>element's own size</b>.</td>
  </tr>
  <tr>
    <td>Chaining</td>
    <td><code>translateY(100%) skewX(40deg) translateX(45%)</code></td>
    <td>Multiple functions in one <code>transform</code> declaration. <b>Order matters.</b></td>
  </tr>
</table>

### 🧪 Code Highlight

```css
.box {
  height: 50px;
  width: 50px;
  background-color: beige;
  border: 2px solid black;
  transform: rotate(.125turn);   /* 45 degrees */
  /* transform: rotateZ(9deg); */
  /* transform: skew(34deg); */
  /* transform: translateY(100%) skewX(40deg) translateX(45%); */
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  height: 80vh;
  border: 2px solid purple;
}
```

### 📐 Angle Units

<table>
  <tr>
    <th>Unit</th>
    <th>Full circle</th>
    <th>Example of a 45° turn</th>
  </tr>
  <tr>
    <td><code>deg</code></td>
    <td>360deg</td>
    <td><code>45deg</code></td>
  </tr>
  <tr>
    <td><code>turn</code></td>
    <td>1turn</td>
    <td><code>.125turn</code></td>
  </tr>
  <tr>
    <td><code>rad</code></td>
    <td>2π rad</td>
    <td><code>0.785rad</code></td>
  </tr>
  <tr>
    <td><code>grad</code></td>
    <td>400grad</td>
    <td><code>50grad</code></td>
  </tr>
</table>

### 🧠 What Happens Here

<table>
  <tr>
    <td>1️⃣</td>
    <td>The box is rotated 45° around its <b>center</b>, which is the default <code>transform-origin</code>.</td>
  </tr>
  <tr>
    <td>2️⃣</td>
    <td>Transforms are <b>visual only</b>. The box still takes up its original 54px × 54px (50px plus a 2px border on each side) in the layout, so nothing around it moves.</td>
  </tr>
  <tr>
    <td>3️⃣</td>
    <td>The container has two <code>height</code> declarations in the original code. The second one (<code>80vh</code>) overrides the first, so only one is needed.</td>
  </tr>
</table>

### ⚠️ Order Matters

Each function in a chain works in the coordinate system left behind by the one before it.

<table>
  <tr>
    <th>Code</th>
    <th>Result</th>
  </tr>
  <tr>
    <td><code>translateX(100px) rotate(45deg)</code></td>
    <td>The box moves 100px to the right, then rotates in place.</td>
  </tr>
  <tr>
    <td><code>rotate(45deg) translateX(100px)</code></td>
    <td>The box rotates first, so "right" now points diagonally. It ends up somewhere else entirely.</td>
  </tr>
</table>

### 📝 Good to Know

<table>
  <tr>
    <td>💡</td>
    <td><code>transform-origin</code> changes the point an element rotates or scales around. For example, <code>transform-origin: top left;</code>.</td>
  </tr>
  <tr>
    <td>💡</td>
    <td>Transforms do not apply to plain inline elements (like <code>&lt;span&gt;</code>). Make them <code>inline-block</code> or <code>block</code> first.</td>
  </tr>
  <tr>
    <td>💡</td>
    <td>An element with a <code>transform</code> becomes the reference point for its <code>absolute</code> and <code>fixed</code> children, just like a positioned parent.</td>
  </tr>
  <tr>
    <td>💡</td>
    <td>Transforms are cheap for the browser to animate because they usually don't force a re-layout.</td>
  </tr>
</table>

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Change `rotate(.125turn)` to `rotate(45deg)` and confirm they look identical.
2. Uncomment each commented `transform` line one at a time and compare.
3. Swap the order of `translateX()` and `rotate()` in a chain and see the box land in different places.
4. Add `transform-origin: top left;` and watch the rotation pivot from the corner.
5. Add `transform: scale(2);` and notice that the layout around the box doesn't change.
6. Try a negative angle, such as `rotate(-.125turn)`, to rotate the other way.
7. Add `rotateX(45deg)` with `perspective: 400px` on the container for a first look at 3D.

</details>

### 📚 Transform Cheat Sheet

| Goal | Use |
|---|---|
| Rotate | `rotate(45deg)` |
| Move | `translate(x, y)` |
| Resize | `scale(1.5)` |
| Slant | `skew(20deg)` |
| Center an absolute element | `top: 50%; left: 50%; transform: translate(-50%, -50%);` |
| Change the pivot point | `transform-origin: ...;` |

---

## ⏱️ Experiment 3: CSS Transitions

📁 `20-css-transitions/index.html`

### 🎯 Goal
Animate **smoothly between two states** of an element instead of snapping from one to the other.

### 🔑 Concepts Covered

<table>
  <tr>
    <th>Property</th>
    <th>Example</th>
    <th>What it controls</th>
  </tr>
  <tr>
    <td><code>transition-property</code></td>
    <td><code>background-color, transform</code></td>
    <td>Which properties animate. <code>all</code> animates every animatable property.</td>
  </tr>
  <tr>
    <td><code>transition-duration</code></td>
    <td><code>3s</code></td>
    <td>How long the animation takes.</td>
  </tr>
  <tr>
    <td><code>transition-timing-function</code></td>
    <td><code>cubic-bezier(0.22, 0.52, 0.01, 1)</code></td>
    <td>The speed curve: how the motion accelerates and slows.</td>
  </tr>
  <tr>
    <td><code>transition-delay</code></td>
    <td><code>1s</code></td>
    <td>How long to wait before starting.</td>
  </tr>
  <tr>
    <td><code>transition</code> (shorthand)</td>
    <td><code>all 3s cubic-bezier(...) 1s</code></td>
    <td>All four in one line.</td>
  </tr>
</table>

### 🧪 Code Highlight

```css
.box {
  background-color: aquamarine;
  width: 5vw;
  height: 4vh;
  /* shorthand: property | duration | timing-function | delay */
  transition: all 3s cubic-bezier(0.22, 0.52, 0.01, 1) 1s;
}

.translate {
  transform: translateX(10vw) translateY(10vh) scale(2);
  background-color: blue;
}
```

### 🧩 Reading the Shorthand

<table>
  <tr>
    <th><code>all</code></th>
    <th><code>3s</code></th>
    <th><code>cubic-bezier(0.22, 0.52, 0.01, 1)</code></th>
    <th><code>1s</code></th>
  </tr>
  <tr align="center">
    <td>property</td>
    <td>duration</td>
    <td>timing function</td>
    <td>delay</td>
  </tr>
</table>

> ℹ️ When there are two time values, the **first is always the duration** and the **second is the delay**.

### 🎚️ Timing Functions

<table>
  <tr>
    <th>Value</th>
    <th>Feel</th>
  </tr>
  <tr>
    <td><code>linear</code></td>
    <td>Constant speed</td>
  </tr>
  <tr>
    <td><code>ease</code> (default)</td>
    <td>Slow start, fast middle, slow end</td>
  </tr>
  <tr>
    <td><code>ease-in</code></td>
    <td>Starts slow, ends fast</td>
  </tr>
  <tr>
    <td><code>ease-out</code></td>
    <td>Starts fast, ends slow</td>
  </tr>
  <tr>
    <td><code>ease-in-out</code></td>
    <td>Slow at both ends</td>
  </tr>
  <tr>
    <td><code>cubic-bezier(x1, y1, x2, y2)</code></td>
    <td>A custom curve. The two x values must be between 0 and 1. <code>(0.22, 0.52, 0.01, 1)</code> starts fast and eases to a long, gentle stop.</td>
  </tr>
  <tr>
    <td><code>steps(n)</code></td>
    <td>Jumps in discrete steps instead of moving smoothly</td>
  </tr>
</table>

### 🐛 Important: Why the Original Demo Doesn't Animate

<table>
  <tr>
    <td>⚠️</td>
    <td>The HTML is <code>&lt;div class="box translate"&gt;</code>, so the box <b>already has the final state when the page loads</b>. A transition needs a <b>change</b> to animate, and nothing changes. The box just appears moved, scaled, and blue.</td>
  </tr>
</table>

**Fix 1: trigger it on hover** (the most common approach)

```css
.box {
  background-color: aquamarine;
  width: 5vw;
  height: 4vh;
  transition: all 3s cubic-bezier(0.22, 0.52, 0.01, 1) 1s;
}

.box:hover {
  transform: translateX(10vw) translateY(10vh) scale(2);
  background-color: blue;
}
```

**Fix 2: toggle the class with JavaScript**

```html
<div class="box" onclick="this.classList.toggle('translate')"></div>
```

Now each click adds or removes `.translate`, and the box animates both ways.

### 📝 Good to Know

<table>
  <tr>
    <td>💡</td>
    <td>Put the <code>transition</code> on the <b>base</b> rule (<code>.box</code>), not only on the end state. That way it animates <b>both</b> into the new state and back out.</td>
  </tr>
  <tr>
    <td>💡</td>
    <td><code>transition: all</code> is convenient while learning, but listing exact properties (<code>transform, background-color</code>) is safer and often faster.</td>
  </tr>
  <tr>
    <td>💡</td>
    <td>Not every property can animate. Numbers, lengths, and colors can. <code>display</code> cannot.</td>
  </tr>
  <tr>
    <td>💡</td>
    <td>Touch screens have no true hover. For important interactions, also support <code>:focus</code> or a click.</td>
  </tr>
</table>

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Apply **Fix 1** above and hover over the box to see the transition play.
2. Change the duration from `3s` to `0.3s` for a snappier, more realistic UI feel.
3. Remove the `1s` delay and see the animation start immediately.
4. Replace the custom curve with `linear`, `ease-in`, and `ease-out` and compare how each feels.
5. Switch to the longhand properties (`transition-property: background-color, transform;` and so on).
6. Give the color and the transform **different durations**: `transition: background-color 1s, transform 3s;`.
7. Try [cubic-bezier.com](https://cubic-bezier.com) to design your own timing curve.

</details>

---

## 🤝 How Transform and Transition Work Together

<table>
  <tr>
    <th>Feature</th>
    <th>Role</th>
    <th>Analogy</th>
  </tr>
  <tr>
    <td><code>transform</code></td>
    <td>Defines <b>what</b> the new look is (rotated, moved, scaled).</td>
    <td>The destination</td>
  </tr>
  <tr>
    <td><code>transition</code></td>
    <td>Defines <b>how</b> the element gets there (time, curve, delay).</td>
    <td>The journey</td>
  </tr>
  <tr>
    <td><code>:hover</code> / class toggle</td>
    <td>Defines <b>when</b> the change happens.</td>
    <td>The trigger</td>
  </tr>
</table>

A typical hover card needs all three:

```css
.card {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-8px);
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
}
```

---

## 🚀 How to Run

No installation needed.

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/<your-repo-name>.git

# 2. Move into the project
cd <your-repo-name>

# 3. Open any experiment in your browser
open 18-download-page/index.html      # macOS
start 18-download-page/index.html     # Windows
xdg-open 18-download-page/index.html  # Linux
```

💡 **Tip:** Use the VS Code **Live Server** extension to see changes instantly as you edit.

---

## 🎓 Key Takeaways

<table>
  <tr>
    <td>✅</td>
    <td><code>repeat(3, 1fr)</code> plus a single media query gives a clean responsive card grid.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Layouts should be tested with different scripts, not only English, and labels should be checked for accuracy.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td><code>transform</code> changes how an element looks without changing the layout around it.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Order matters when chaining transform functions.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>A <code>turn</code> is a readable angle unit: <code>.125turn</code> equals <code>45deg</code>.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>A transition needs a <b>state change</b> to animate. An element that starts in its final state won't animate.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>The <code>transition</code> shorthand order is property, duration, timing function, delay.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Put transitions on the base rule so the animation plays in both directions.</td>
  </tr>
</table>

---

## 🗺️ Roadmap

- [x] `display` property
- [x] Viewport units and box model
- [x] CSS specificity
- [x] `overflow`
- [x] Lists and `list-style`
- [x] `box-shadow` and `text-shadow`
- [x] Positioning (`relative`, `absolute`, `fixed`, `sticky`)
- [x] Card component
- [x] Media queries
- [x] CSS variables
- [x] Landing page project
- [x] Float and clear
- [x] Pseudo-elements and advanced selectors
- [x] Full page layout with sticky navbar
- [x] Flexbox fundamentals
- [x] CSS Grid fundamentals and template areas
- [x] Responsive grid download page
- [x] CSS transforms
- [x] CSS transitions
- [ ] Keyframe animations (`@keyframes`, `animation`)
- [ ] Responsive project combining Flexbox, Grid, and media queries
- [ ] Grid auto-placement (`grid-auto-flow`, `grid-auto-rows`)
- [ ] Mobile-first workflow

---

<div align="center">

### ⭐ If you found this helpful, consider giving the repo a star!

Made with ❤️ while learning CSS

</div>
