---
layout: myLayout
show_header: true
title: Your Dota2 doll is
---

<script>
    const url = new URL(window.location.href);
    let openidParam = url.searchParams.get("openid.claimed_id")
    let steamID64 = null

    if (openidParam) {
        steamID64 = openidParam.replace('https://steamcommunity.com/openid/id/','');
    } else {
        steamID64 = url.searchParams.get('id')
    }
    
    const steamID32 = SteamIDConverter.toSteamID3(steamID64).split(':')[2].slice(0, -1)
</script>


{% include components/the-doll.html %}
