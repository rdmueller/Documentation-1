---
title: "Installation Process"
slug: "installation-process"
hidden: false
---

# Install Voice Gateway

## Install Helm Charts

To install Voice Gateway please perform following steps:

<!---
TODO: Update the Voice Gateway Helm Chart links (main page and readme) with the public GitHub Helm Chart repository once we have it.
TODO: Voice Gateway Helm Chart is being refactored and only when is done the above comment will be fulfilled.
-->

1. Install Voice Gateway with [Voice Gateway Helm Chart](https://cognigy.visualstudio.com/VoiceGateway/_git/voicegateway-app). For up-to-date installation instructions refer to [README.md](https://cognigy.visualstudio.com/VoiceGateway/_git/voicegateway-app?path=/README.md)

Once Helm releases is successfully installed, you can open a web-browser and visit the URL which you have set in `webapp.host` parameter Voice Gateway Helm release. You should be able to see the login screen of Voice Gateway WebApp:

<figure>
  <img class="image-center" src="{{config.site_url}}voicegateway/images/VG-login.png" width="90%" />
  <figcaption>Login screen of Voice Gateway WebApp</figcaption>
</figure>

## Initial Login Credentials

Once you are able to see the Voice Gateway login screen you can be use to log in, the default `admin` user with initial password `admin` as well. You will be asked to change the password after the first login, please do that and choose a strong new password.