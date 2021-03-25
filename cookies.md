---
layout: post
title: Cookie Policy
show_tile: false
---
<style>
    #cookie-notice a {display: inline-block; cursor: pointer; margin-left: 0.5rem;}
    @media (max-width: 767px) {
        #cookie-notice span {display: block; padding-top: 3px; margin-bottom: 1rem;}
        #cookie-notice a {position: relative; bottom: 4px;}
    }
</style>
<div id="cookie-notice"><span>We use cookies to improve user experience, and analyze website traffic. For these reasons, we may share your site usage data with our analytics partners. By clicking “Accept” you consent to store on your device all the technologies described in our<a href="/cookies">Cookie Policy</a>.</span><div><a id="cookie-notice-accept" class="button">Accept</a><a id="cookie-notice-decline" class="button">Decline</a></div></div>
<script>
    function readCookie(name) {
        var nameEQ = name + "=";
        var ca = document.cookie.split(';');
        for(var i=0;i < ca.length;i++) {
            var c = ca[i];
            while (c.charAt(0)==' ') c = c.substring(1,c.length);
            if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length,c.length);
        }
        return null;
    }

    function createCookie(name,value,days) {
        var expires = "";
        if (days) {
            var date = new Date();
            date.setTime(date.getTime() + (days*24*60*60*1000));
            expires = "; expires=" + date.toUTCString();
        }
        document.cookie = name + "=" + value + expires + "; path=/";
    }

    function eraseCookie(name) {
        createCookie(name,"",-1);
    }

    if(readCookie('cookie-notice-dismissed')=='true') {
        console.log('cookies approved');
    } else {
        document.getElementById('cookie-notice').style.display = 'block';
    }
    document.getElementById('cookie-notice-accept').addEventListener("click",function() {
        createCookie('cookie-notice-dismissed','true',31);
        document.getElementById('cookie-notice').style.display = 'none';
        location.reload();
    });
    document.getElementById('cookie-notice-decline').addEventListener("click",function() {
        console.log('cookies declined');
        eraseCookie('cookie-notice-dismissed', '', -1);
    });

</script>