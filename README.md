# Want to contribute to the website? Please read this!

- [a. Want to add art](#a-want-to-add-arts)
- [b. Want to add event photos and notes](#b-want-to-add-event-photos-and-notes)
- [c. Want to add content for updates (sidebar)](#c-want-to-add-content-for-updates-sidebar)
- [d. Want to change the style](#d-want-to-change-the-style)
- [e. Want to change the cursor](#e-want-to-change-the-cursor)

## a. Want to add art

### How to add art in main page

1. Make your file's name as {author}_{name}.png or {author}_{name}.jpg
2. Put the file under the `imgs/`
3. Copy and paste the name({author}_{name}.{format}) to the `imgs.csv`, it will automatically extract the name and show on the main page

### How to add art in art page

1. Make your file's name as {author}_{name}.png or {author}_{name}.jpg
2. Put the file under the `imgs/`
3. Add the code in `pages/faa.html`, put the code within `<div class="gallery-grid">`, keep the code as the following format(alt can be blank):
```
<div class="gallery-item">
    <img src="../imgs/{author}_{name}.{format}" alt="{name} by {author}" onclick="openLightbox(this.src)">
    <span class="art-author">© {name}</span>
</div>
```

## b. Want to add event photos and notes

### How to add event photos and notes

1. Put the file under the `event_imgs/{meeting_number}/`
2. Add the code in `pages/events.html`, put the code under `<p class="hero-title">Events History</p>`, keep the code as the following format, just need to use the lateast context replace {context}:
```
<div class="event-entry">
    <div class="event-meta">
        <div class="event-meta-date">{date}</div>
        <div class="event-meta-month">{month}</div>
        <div class="event-meta-year">{year}</div>
    </div>
    <div class="event-divider"></div>
    <div class="event-body">
        <h3>{Number} Meeting</h3>
        <p>{Context}</p>
        <div class="event-gallery">
        <img src="..\event_imgs\{meeting_number}\{name}.{format}" onclick="openLightbox(this.src)">
        </div>
    </div>
    </div>
```

## c. Want to add content for updates (sidebar)

### How to update the sidebar

1. Add the code in `updates.js`, put the code within `<ul class="update-list">`, keep the code as the following format, just need to use the lateast context replace {context}:
```
<li><span class="update-date">{month} {date}, {year}</span> {context}</li>
```

## d. Want to change the style

### How to change the style

1. Replace / Add the code in `theme.js`


## e. Want to change the cursor

### How to change the cursor

1. Put the file under the `cursor/{character}`
2. Replace the code in `style.css`, based on your cursor style, there are **3** things can be changed:

a. For regular cursor:
```
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  cursor: url('/cursor/{character}/{character}.png') 0 0, auto !important;
}
```

b. For I-beam:
```
p, h1, h2, h3, h4, h5, h6, span, li {
  cursor: url('/cursor/{character}/{character}_select.png') 0 0, text !important;
}
```

c. For pointer:
```
a, button, [onclick], img, .theme-dot, .footer-icon, .footer-icon *, .cal-nav-btn, .cal-cell.has-event, .cal-cell.has-event span {
  cursor: url('/cursor/{character}/{character}_pointer.png') 0 0, pointer !important;
}
```

3. If your images are too big, put your imgs under `cursor/`, and run the following code:
```
python -c "from PIL import Image; import os; [Image.open(f'cursor/{f}').convert('RGBA').resize((32,32),Image.LANCZOS).save(f'cursor/{f}') for f in os.listdir('cursor') if f.lower().endswith(('.png','.jpg','.jpeg'))]"
```

4. Remember to delete your old images!
