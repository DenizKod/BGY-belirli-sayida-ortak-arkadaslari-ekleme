# BGY-belirli-sayida-ortak-arkadaslari-ekleme

### ADIM 1

<p>- Facebook dilini Türkçe yap</p>
<p>- Tampermonkey eklentisi tarayıcınıza ekleyin</p>
<p>- Yeni Betik oluştura tıklayın</p>

![image](https://github.com/DenizKod/ARK-ISTEGI-IPTAL-ETME/assets/168285638/7e1b2696-803e-447a-ae3f-f7844a44d28f)

#### Aşağıdaki kodu betik oluşturma sayfasına yapıştırıp betiği kaydedin

```
// ==UserScript==
// @name         BGY belirli ortak sayıda kişilere istek atma
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  BGY belirli ortak sayıda kişilere istek atma
// @author       Deniz Kod
// @match        https://www.facebook.com/*
// @grant        none
// ==/UserScript==
(function() {
    'use strict';
    document.addEventListener('keydown', function(e) {
        // Check if the Pause key is pressed
        if (e.keyCode === 19) {
            // Query all the items that might contain friend buttons and mutual friend info
            const items = document.querySelectorAll('div[data-visualcompletion="ignore-dynamic"][role="listitem"]');
            items.forEach((item) => {
                // Assuming mutual friend count is in the following format: "xxx ortak arkadaş"
                const mutualFriendsText = item.innerText.match(/(\d+)\s+ortak arkadaş/);
                if (mutualFriendsText && mutualFriendsText[1] && parseInt(mutualFriendsText[1]) >= 200) {
                    // Find the "Arkadaş Ekle" button within this list item
                    const friendRequestButton = item.querySelector('[aria-label="Arkadaş Ekle"]');
                    if (friendRequestButton) {
                        friendRequestButton.click();
                    }
                }
            });
        }
    });
})();
```

![image](https://github.com/DenizKod/BGY-belirli-sayida-ortak-arkadaslari-ekleme/assets/168285638/09458b84-cc9c-4fd6-a522-60f0cff31a83)


<p>- BU SAYFAYA GİT : https://www.facebook.com/groups/bgyagain3/members/things_in_common </p>

### Klavye de PAUSE tuşuna bastıkça belirlediğiniz sayının üstündeki ortak arkadaşa sahip olan kişilere istek atacak.
