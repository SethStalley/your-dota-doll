---
layout: myLayout
---


<script>
    var clientInfo = {
        client_id : '(your-client-id)',
        redirect_uri : './login-callback.html'
    };
    var providerInfo = OIDC.discover('https://steamcommunity.com/openid');
    OIDC.setClientInfo( clientInfo );
    OIDC.setProviderInfo( providerInfo );
    OIDC.storeInfo(providerInfo, clientInfo);
    // Remove State and Nonce from previous session
    sessionStorage.removeItem('state');
    sessionStorage.removeItem('nonce');
    loginRequest = OIDC.generateLoginRequest({scope : 'openid profile email',
    response_type : 'token id_token'});
</script>

<div class="container" style="margin-bottom: 50px;">
    <h1>Implicit Flow Test Login Page</h1>
    <br>
    <b>clientInfo</b>
    <div id="clientInfo">
        clientInfo not found
    </div>
    <script type="text/javascript">
    document.getElementById('clientInfo').innerHTML = JSONObjToHTMLTable(clientInfo);
    </script>
    <b>loginRequest</b>
    <div id="loginRequest">
        loginRequest not generated yet
    </div>
    <script type="text/javascript">
    document.getElementById('loginRequest').innerHTML = JSONObjToHTMLTable(loginRequest);
    </script>
    <br>
    <div class="buttons">
        <button onClick="OIDC.login( {scope : 'openid profile email',
        response_type : 'token id_token'} );"
        type="button" class="btn btn-success" >Authenticate</button>
    </div>
</div>

{% include components/the-doll.html %}
                