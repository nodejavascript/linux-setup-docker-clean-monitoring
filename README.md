<div id="top"></div>

<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->

<br />
<div align="center">

  [![Reddit][forks-shield]][forks-url]

  [![Forks][forks-shield]][forks-url]
  [![Stargazers][stars-shield]][stars-url]
  [![Issues][issues-shield]][issues-url]
  [![Contributors][contributors-shield]][contributors-url]
  [![LinkedIn][linkedin-shield]][linkedin-url]

  <a href="https://nodejavascript.com?ref=githubLogo">
    <img src="https://avatars.githubusercontent.com/u/105805523?v=4" alt="Logo" width="80" height="80">
    <br />
    nodejavascript.com
  </a>

<!-- line feeds break list of a tags below -->
<h3 align="center">linux-setup-docker-clean-monitoring</h3>
  <p align="center">
    <br />
    <a href="https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/issues">Report Issue</a>
    ·
    <a href="https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/issues">Request Feature</a>
  </p>
</div>

<!-- ABOUT THE PROJECT -->
## For my Ubuntu fresh installs
This assumes your new linux install just spun up and you can terminal into it.

Copy & paste at <img src="https://upload.wikimedia.org/wikipedia/en/2/20/WilRiker.jpg" alt="Will" title="Will" width="50"> and at your own risk. I said it.

# SSH into server from terminal.
use if you want shortcut in `.bash_profile` on `local`
```
# use once ssh-copy-id username@host
alias mynewserver='ssh username@host'
```

# use after `server` is created
(may or may not need `sudo`)
```sudo apt-get update && sudo apt-get upgrade -y
sudo apt install nmon -y
sudo bash <(curl -Ss https://my-netdata.io/kickstart.sh) -y
sudo reboot
```

# then use to install docker.io on `server`
(may or may not need `sudo`)
```sudo apt-get update && sudo apt-get upgrade -y
sudo apt install docker.io
sudo systemctl start docker
sudo systemctl enable docker
docker network create web
sudo apt install docker-compose -y
sudo reboot
```

# use if you want to build with `nodejs` on `server`
(may or may not need `sudo`)
```sudo apt install npm
sudo npm install -g n
n 14.19.2
n 17.8.0
sudo reboot
```

# use if you want to clone any `private` repos on `server`
```ssh-keygen -t rsa -y
cat ~/.ssh# cat ~/.ssh/id_rsa.pub
```
- *After using the above command*, `copy` the whole public key the command displayed.
- Then, paste this `SSH key` in your github, gitlab Profile settings.

# `clone` this repo
(may or may not need `sudo`)
```cd /opt
sudo mkdir github && cd github
git clone git@github.com:nodejavascript/linux-setup-docker-clean-monitoring.git
cd linux-setup-docker-clean-monitoring/
```

#before running `docker-compose up -d`:
```copy .env.example .env

# add environment variables
sudo nano .env

# add prometheus variables
sudo nano prometheus.yml

# add ghost variables
sudo nano ghost_byblog_config.json

# add traefik variables
sudo nano traefik.toml
```

# adjust open ports on your host firewall
Maybe map these ports to your home IP:
```
19999, 9000, 9999, 3050, 9090, 9100, 9001, 8080, 3001, 3306, 8183, 6379, 8081, 27017
```

Maybe open ports `80`, `443` to All for `trekfik`

- 19999 : netdata
- 9000 : portainer
- 9999 : dozzle
- 3050 : grafana
- 9090 : prometheus
- 9100 : node-exporter
- 9001 : mqtt-exporter
- 8080 : cadvisor
- 3001 : uptime-kuma
- 80 : traefik
- 443 : traefik
- 3306 : mysql
- 8183 : phpmyadmin
- 6379 : redis
- 8081 : rediscommander
- 27017 : mongodb

# run docker!
`docker-compose up -d`

# traefik will create `acme.json`
Run this permission on the file:
`chmod 600 acme.json`

# finishing:
## `sudo reboot`
There are side effects with DNS, so reboot and be patient wth DNS...

# setup grafana
Add new dashboards with these templateIds:
- Note Exporter: 1860
- Dashboard cadvisor: 14282
- Dozzle can help you troubleshot what's wrong with containers that won't start
- traefik is kinda setup with ghost and mysql (you need to edit enviroment variables, config.json, mysql user). I think you have enough to get it running, and I'll update this report next time I document a full run-through of this procedure myself.

# other links
You should access to all containers.

Example: `http://serverip:9000` would be for portainer.


## Tips
- `nmon` is great if server becomes somewhat unresponsive.
- `http://serverip:19999` is great for watching `docker-compose up -d` and deciding if you need more resources.





<!-- CONTRIBUTING -->
## Contributing

Contributions should support [/r/selfhosted](https://www.reddit.com/r/selfhosted/)

<img src="https://img.shields.io/reddit/subreddit-subscribers/selfhosted?style=for-the-badge" alt="subreddit-subscribers/selfhosted">

<!-- LICENSE -->
## License

MIT

<!-- CONTACT -->
## Contact
* Home - [nodejavascript.com](https://nodejavascript.com?ref=githubContact)
* YouTube - [nodejavascript](https://www.youtube.com/channel/UCZFJHjd0c79xyj2SpB8UbJg)
* Twitter - [@nodejavascript](https://twitter.com/nodejavascript)
* LinkedIn - [@nodejavascript](https://linkedin.com/in/georgefielder)
* Email - [github@nodejavascript.com](mailto:github@nodejavascript.com)

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments
* [Best-README-Template](https://github.com/othneildrew/Best-README-Template)


<p align="right">(<a href="#top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/nodejavascript/linux-setup-docker-clean-monitoring.svg?style=plastic
[contributors-url]: https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/nodejavascript/linux-setup-docker-clean-monitoring.svg?style=plastic
[forks-url]: https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/network/members
[stars-shield]: https://img.shields.io/github/stars/nodejavascript/linux-setup-docker-clean-monitoring.svg?style=plastic
[stars-url]: https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/stargazers
[issues-shield]: https://img.shields.io/github/issues/nodejavascript/linux-setup-docker-clean-monitoring.svg?style=plastic
[issues-url]: https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/issues
[license-shield]: https://img.shields.io/github/license/nodejavascript/linux-setup-docker-clean-monitoring.svg?style=plastic
[license-url]: https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg??style=social&logo=appveyor
[linkedin-url]: https://linkedin.com/in/georgefielder
