### Opa! Sou o RC👋

- 🌱 Estudando: front-end
- 😄 Pronouns: ele/dele

![RC GitHub stats](https://github-readme-stats.vercel.app/api?username=Digoaranha&show_icons=true&theme=dark)
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=Digoaranha&theme=dark&hide_border=false&&layout=compact)

<!-- LINGUAGENS DE PROGRAMAÇÃO (ATT) ICONs: https://devicon.dev/
<div style="display: inline_block"><br>
  <img align="center" alt="Rafa-Js" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-plain.svg">
  <img align="center" alt="Rafa-Ts" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-plain.svg">
  <img align="center" alt="Rafa-React" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original.svg">
  <img align="center" alt="Rafa-HTML" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original.svg">
  <img align="center" alt="Rafa-CSS" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original.svg">
  <img align="center" alt="Rafa-Python" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg">
  <img align="center" alt="Rafa-Csharp" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/csharp/csharp-original.svg">
</div>
-->
##

<!-- REDES SOCIAIS (ATT QUANDO CRIAR) https://dev.to/envoy_/150-badges-for-github-pnk
<div> 
  <a href="https://www.youtube.com" target="_blank"><img src="https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white" target="_blank"></a>
  <a href="https://instagram.com" target="_blank"><img src="https://img.shields.io/badge/-Instagram-%23E4405F?style=for-the-badge&logo=instagram&logoColor=white" target="_blank"></a>
 	<a href="https://www.twitch.tv" target="_blank"><img src="https://img.shields.io/badge/Twitch-9146FF?style=for-the-badge&logo=twitch&logoColor=white" target="_blank"></a>
 <a href="https://discord.gg/" target="_blank"><img src="https://img.shields.io/badge/Discord-7289DA?style=for-the-badge&logo=discord&logoColor=white" target="_blank"></a> 
  <a href = "mailto:@gmail.com"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>
  <a href="https://www.linkedin.com" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a> 
</div
>-->

![Snake animation](https://github.com/rafaballerini/rafaballerini2/blod/output/github-contribution-grid-snake.svg)
  

# GitHub Action for generating a contribution graph with a snake eating your contributions.

name: Generate Snake

# Controls when the action will run. This action runs every 6 hours.

on:
  schedule:
      # every 6 hours
    - cron: "0 */6 * * *"

# This command allows us to run the Action automatically from the Actions tab.
  workflow_dispatch:

# The sequence of runs in this workflow:
jobs:
  # This workflow contains a single job called "build"
  build:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:

    # Checks repo under $GITHUB_WORKSHOP, so your job can access it
      - uses: actions/checkout@v2

    # Generates the snake  
      - uses: Platane/snk@master
        id: snake-gif
        with:
          github_user_name: mishmanners
          # these next 2 lines generate the files on a branch called "output". This keeps the main branch from cluttering up.
          gif_out_path: dist/github-contribution-grid-snake.gif
          svg_out_path: dist/github-contribution-grid-snake.svg

     # show the status of the build. Makes it easier for debugging (if there's any issues).
      - run: git status

      # Push the changes
      - name: Push changes
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: master
          force: true

      - uses: crazy-max/ghaction-github-pages@v2.1.3
        with:
          # the output branch we mentioned above
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
