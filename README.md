# Get _fbc or create it
_fbc cookie tells the Facebook that the person 'Mário' came from this specific Ad, and when he've clicked on it.

**The purpose of this implementation is basically:**<br>
Check if _fbc exists. If it doesn't, create fbc using URL parameters.

## What is the main purpose of _fbc cookie?
When someone clicks on a Facebook Ad, the link URL may include a parameter: 'fbclid'.
Based on this, Facebook Pixel automatically creates the _fbc cookie for this lead.

**But... Therein lies the problem!**
If Facebook Pixel isn't properly installed or simply doesn't create it, you'll lose important data information for your data driven decisions, on your Facebook campaigns.

### Data is certainly the most important asset for making decisions!
In order to track 100% right your metrics, all you have to do is load this code on your **Sales pages.**
And that's it, you _fbc parameter to send to Facebook.

On your sales page, copy and paste this script:
```
 document.querySelectorAll('a').forEach((e) => {

            let fbp = document.cookie.split(';').filter(c => c.includes('_fbp=')).map(c => c.split('_fbp=')[1]);
            let fbc = document.cookie.split(';').filter(c => c.includes('_fbc=')).map(c => c.split('_fbc=')[1]);
            fbp = (fbp.length && fbp[0]) || null;
            fbc = (fbc.length && fbc[0]) || null;


            var link = e.getAttribute('href');

            // Se o href contiver 'checkout':
            if (link.indexOf('/checkout/') > 0) {

                // Cria o fbc se ele não existir:
                if (!fbc && window.location.search.includes('fbclid=')) {

                    // Pega o 'fbclid' da url:
                    var fbclid = window.location.search.split('fbclid=')[1];
                    fbclid = 'fbclid=' + fbclid;

                    // Passando o parametro para o link de checkout:
                    link = link + "&" + fbclid;
                    e.setAttribute('href', link);

                    // Criando o fbc (no caso dele não existir):
                    fbc = 'fb.1.' + (+new Date()) + '.' + window.location.search.split('fbclid=')[1];

                }
            }
        });
```
