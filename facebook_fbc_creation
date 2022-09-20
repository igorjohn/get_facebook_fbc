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
