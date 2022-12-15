# redireccion-web

Copiar y pegar el siguiente código. Cambiar el url

```
<script>
    let url = "https://www.youtube.com";

    function getCookieValue(name) {
        if (document.cookie.includes(name)) {
            return document.cookie.match('(^|;)\\s*' + name + '\\s*=\\s*([^;]+)')?.pop() || ''
        } else {
            return false;
        }
    }

    let redirect = (getCookieValue('redirect') === "true");

    if (redirect) {
        window.location.replace(url);
    }

    if (!document.cookie.includes("redirect")) {
        getCountryFromIP();
    }

    function setCountry(country) {
        if (country === "Venezuela" || country === "Nicaragua") {
            document.cookie = "redirect=true";
            window.location.replace(url);
        } else {
            document.cookie = "redirect=false";
        }
    }

    function getCountryFromIP() {
        fetch('https://ipgeolocation.abstractapi.com/v1/?api_key=6796c02a738748e2bcca7392f4617762')
            .then((response) => response.json())
            .then((data) => setCountry(data["country"]));
    }

</script>
```
