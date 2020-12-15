# Flag google trasnalte demo without google bar and logo

## Screenshot
![ScreenShot](/screenshots/screenshot.png)

## How to use this

### 1. Create a country checklist containing languages from which you’ll select to translate your webpage.
```javascript
<!-- jQuery Is Required -->
<script src="/path/to/cdn/jquery.slim.min.js"></script>

<!-- Bootstrap -->
<link rel="stylesheet" href="/path/to/cdn/bootstrap.min.css" />
<script src="/path/to/cdn/bootstrap.min.js"></script>

<!-- Bootstrap Select -->
<link rel="stylesheet" href="/path/to/cdn/bootstrap-select.min.css" />
<script src="/path/to/cdn/bootstrap-select.min.js"></script>

<!-- Flag Icon -->
<link rel="stylesheet" href="/path/to/cdn/flag-icon.min.css" />
```

```javascript
<select class="selectpicker" data-width="fit" onchange="translateLanguage(this.value);">
  <option data-content='<span class="flag-icon flag-icon-af"></span> Afrikaans' value="Afrikaans">Afrikaans</option>
  <option  data-content='<span class="flag-icon flag-icon-al"></span> Albanian' value="Albanian">Albanian</option>
  <option  data-content='<span class="flag-icon flag-icon-ar"></span> Arabic' value="Arabic">Arabic</option>
  <option  data-content='<span class="flag-icon flag-icon-am"></span> Armenian' value="Armenian">Armenian</option>
  <option  data-content='<span class="flag-icon flag-icon-az"></span> Azerbaijani' value="Azerbaijani">Azerbaijani</option>
  ...
</select>
```

### 2. Load the needed Google Translate API.
```javascript
<script src="https://translate.google.com/translate_a/element.js?cb=googleTranslateElementInit" type="text/javascript"></script>
```

### 3. Add the Google Translator Widget to the web page.
```html
<div id="google_translate_element"></div>
```

### 4. The important script to allow the Google Translator on your webpage.
```javascript
function googleTranslateElementInit() {
  new google.translate.TranslateElement({ pageLanguage: 'en', layout: google.translate.TranslateElement.InlineLayout.SIMPLE, autoDisplay: false }, 'google_translate_element');
}

function translateLanguage(lang) {
  googleTranslateElementInit();
  var $frame = $('.goog-te-menu-frame:first');
  if (!$frame.size()) {
    alert("Error: Could not find Google translate frame.");
    return false;
  }
  $frame.contents().find('.goog-te-menu2-item span.text:contains(' + lang + ')').get(0).click();
  return false;
}

$(function(){
  $('.selectpicker').selectpicker();
});
```
