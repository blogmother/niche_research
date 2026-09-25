# Embedding the calculator (unbranded)

`embed.html` is the calculator without the OurHappyValleyHome.com header, agent contact block, eXp logo or Equal Housing Opportunity logo, so it sits inside a page that already carries that branding. It stays in light mode (add `?theme=dark` to the URL for dark) and has a white background.

BoldTrail's custom HTML widgets don't run JavaScript, so the calculator can't be pasted in directly. Host `embed.html` at a public URL and show it in an iframe.

## Embed code

Replace the `src` URL if the file is hosted somewhere other than GitHub Pages.

```html
<style>
  .bmc-frame { width: 100%; height: 3050px; border: 0; display: block; }
  @media (max-width: 900px) { .bmc-frame { height: 4550px; } }
  @media (max-width: 560px) { .bmc-frame { height: 6450px; } }
</style>
<iframe class="bmc-frame"
        src="https://blogmother.github.io/niche_research/blended-mortgage-calculator/embed.html"
        title="Blended Mortgage Calculator"
        loading="lazy"
        style="width:100%; height:3050px; border:0;"></iframe>
```

If the editor strips the `<style>` block, the inline `style` still gives a 3,050px desktop height. On phones the calculator then scrolls inside its frame.

## Prefilled scenario for a listing

Add query parameters to the `src` URL:

```
embed.html?price=425000&balance=268000&rate=3.25&years=26&months=6&pi=1258&type=FHA&down=40000
```

Supported keys: `price`, `down`, `type`, `rate`, `balance`, `pi`, `years`, `months`, `mip`, `feeUpfront`, `feeCtc`, `rate2`, `term2`, `market`, `taxes`, `ins`, `hoa`, `theme=dark`.

## Auto-height (optional, only where the host page allows JavaScript)

The embed posts its height to the parent page. On a site that runs scripts, this removes the fixed height:

```html
<script>
  window.addEventListener("message", function (e) {
    if (e.data && e.data.type === "bmc-height") {
      document.querySelectorAll(".bmc-frame").forEach(function (f) { f.style.height = e.data.height + "px"; });
    }
  });
</script>
```
