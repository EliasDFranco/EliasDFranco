<h1 align="center">¡Hola! Soy Elias Franco Duarte.</h1>

###

<h4 align="center">Soy un apasionado desarrollador de software con especial interés en Python y el desarrollo de Apps móviles. Siempre estoy buscando nuevas formas de aprender y mejorar mis habilidades, creando proyectos que resuelvan problemas o simplifiquen tareas cotidianas.</h4>

###

<br clear="both">

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=EliasDFranco&hide_title=false&hide_rank=false&show_icons=true&include_all_commits=true&count_private=true&disable_animations=false&theme=gotham&locale=es&hide_border=false" height="150" alt="stats graph"  />
  <img src="https://github-readme-stats.vercel.app/api/top-langs?username=EliasDFranco&locale=es&hide_title=false&layout=compact&card_width=320&langs_count=5&theme=gotham&hide_border=false" height="150" alt="languages graph"  />
</div>

###

<img align="right" height="150" src="https://avatars.githubusercontent.com/u/178526288?s=400&u=1e347b9cdd3bf5529dea1c6e423caeee247d86de&v=4"  />

###

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" height="30" alt="python logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" height="30" alt="linux logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" height="30" alt="html5 logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" height="30" alt="css3 logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg" height="30" alt="mysql logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/cplusplus/cplusplus-original.svg" height="30" alt="cplusplus logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/django/django-plain.svg" height="30" alt="django logo"  />
</div>

###

<div align="left">
  <a href="https://www.linkedin.com/in/elias-franco-duarte-015b24212" target="_blank">
    <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="linkedin logo"  />
  </a>
  <a href="https://www.instagram.com/eliasdfranco/" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Instagram&logo=instagram&label=&color=E4405F&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="instagram logo"  />
  </a>
  <a href="eliasdfranco@hotmail.com" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Gmail&logo=gmail&label=&color=D14836&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="gmail logo"  />
  </a>
</div>

###

<br clear="both">

<img src="https://raw.githubusercontent.com/EliasDFranco/EliasDFranco/output/snake.svg" alt="Snake animation" />

###

<div align="center">
  <img src="https://profile-counter.glitch.me/EliasDFranco/count.svg?"  />
</div>

###


name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - master

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
