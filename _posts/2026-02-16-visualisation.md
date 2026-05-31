---
title: Visualisation Inspiration
tags: [recommendations, websites]
style: fill
color: danger
description: Websites with creative and interactive visualisations
---

{% include elements/figure.html image="/images/blog/blog_ant_illustration.png" caption="An illustration of various behaviours in marker-tagged ants. Image credit: Vasudha Kulkarni" %}

I am always in awe of creative people, especially those who are visually creative, those who effortlessly put together a good color palette, and those who make it engaging for the viewer. My sense of aesthetic (when it shows up) is rather mundane (look at my attempt to visualise places on [a map in Vienna](https://vasudha-kulkarni.github.io/blog/vienna-guide)), but I'm trying to work on it by curating websites that I find appealing and fun (several of these were shared by a friend, Bianca). I would curate paintings, murals, and other illustrations too, but their impact is reduced on screen, whereas websites are designed to be viewed on a screen!

First, here are some creators who have compiled several great interactive renditions, but I've only highlighted one of their creations in the cards below - 

* [_neal.fun_](https://neal.fun/) by Neal Agarwal has several fun, interactive games. My favourites are [_Absurd Trolley Problems_](https://neal.fun/absurd-trolley-problems/) and the [_Password Game_](https://neal.fun/password-game/).
* [_Visual Cinnamon_](https://www.visualcinnamon.com/) by Nadieh Bremer has several delightful illustrations. I really appreciate the color palette and design in [Intangible Cultural Heritage](https://ich.unesco.org/en/dive) for UNESCO
* [_Complexity Explorables_](https://www.complexity-explorables.org/) by Dirk Brockmann is a collection of interactive explorable explanations of complex systems in biology, physics and methamtics, such as the Vicsek model, opinion dynamics and pulse-coupled oscillators. They're a great resource for teaching when giving an intuition for these models.

<style>
  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 24px;
    padding: 10px 0;
  }
  .card {
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0,0,0,0.12);
    background: #fff;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }
  .card:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 30px rgba(0,0,0,0.18);
  }

  .placeholder {
    display: none; /* hidden by default, shown via JS */
    width: 100%;
    height: 100%;
    object-fit: cover;
    position: absolute;
    top: 0;
    left: 0;
  }
  .placeholder-fallback {
    display: none;
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    background: linear-gradient(135deg, #e8e8e8, #f5f5f5);
    align-items: center;
    justify-content: center;
    flex-direction: column;
    gap: 8px;
    color: #aaa;
    font-size: 13px;
  }
  .placeholder-fallback .icon { font-size: 32px; }

  .iframe-wrapper {
    position: relative;
    height: 220px;
    overflow: hidden;
  }
  .iframe-wrapper iframe {
    width: 200%;
    height: 200%;
    transform: scale(0.5);
    transform-origin: top left;
    border: none;
    pointer-events: none;
  }
  .iframe-overlay {
    position: absolute;
    inset: 0;
    z-index: 2;
    cursor: pointer;
    background: transparent;
    transition: background 0.2s ease;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 16px;
    font-weight: bold;
    text-decoration: none;
  }
  .iframe-wrapper:hover .iframe-overlay {
    background: rgba(0, 0, 0, 0.45);
  }
  .iframe-wrapper .iframe-overlay::after {
    content: '↗ Open Site';
    opacity: 0;
    transition: opacity 0.2s;
  }
  .iframe-wrapper:hover .iframe-overlay::after {
    opacity: 1;
  }
  .card-footer {
    padding: 10px 14px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-top: 1px solid #eee;
  }

  .card-desc  { font-size: 11px; color: #888; margin-top: 2px; }
  .open-btn {
    text-decoration: none;
    background: #222;
    color: white;
    padding: 5px 12px;
    border-radius: 20px;
    font-size: 12px;
    transition: background 0.2s;
  }
  .open-btn:hover { background: #555; }
</style>

<div class="grid" id="siteGrid"></div>

<script>
  // ✏️ Edit this array with your own sites
  const sites = [
    {
      title: "Fireflies",
      description: "By Nicky Case. An incredible interactive website to visualise the model describing how fireflies synchronise their flashing",
      url: "https://ncase.me/fireflies/"
    },
    {
      title: "Absurd Trolley Problems",
      description: "By Neal Agarwal. An absurd, interactive game to show how many people you'd kill by pulling the lever",
      url: "https://neal.fun/absurd-trolley-problems/",
      placeholder: "/images/blog/vis_trolley.png"
    },
    {
      title: "Of the Oak",
      description: "By Marshmallow Laser Feast. A digital, interactive journey created in collaboration by artists and scinetists celebrating oak trees as living monuments and networks connecting thousands of species that depend on them",
      url: "https://oftheoak.co.uk/oak-species"
    },
    {
      title: "The Vicsek Model",
      description: "By Dirk Brockmann. An interactive website to visualise how hordes of moving agents coordinate their collective motion",
      url: "https://www.complexity-explorables.org/explorables/horde-of-the-flies/"
    },
    {
      title: "The Collapse of Insects",
      description: "By Catherine Tai. A great visualisation of the immense biodiversity of insects and the silent insect apocalypse",
      url: "https://www.reuters.com/graphics/GLOBAL-ENVIRONMENT/INSECT-APOCALYPSE/egpbykdxjvq/",
      placeholder: "/images/blog/vis_insects.png"
    },
    {
      title: "Planets of Disparity",
      description: "By Liuhuaying Yang and Rainer Stütz. An interactive game that visualises how spontaneous preferences can unintentionally create inequalities",
      url: "https://vis.csh.ac.at/planets-of-disparity-two/"
    },
    {
      title: "Searching for Birds",
      description: "By Nadieh Bremer. An exploration of prominent birds in North America and how people search for them",
      url: "https://searchingforbirds.visualcinnamon.com/"
    },
    {
      title: "Book Covers",
      description: "By Melanie Richards. Creative illustration of covers of books that have stayed with Richards.",
      url: "https://highlights.melanie-richards.com/ "
    },
    {
      title: "Evolution of Fitness Landscapes",
      description: "By Bhaskar Kumawat. A visualisation of fitness landscape based on genotypes.",
      url: "https://maxjerdee.github.io/CSSS-arts/projects/fitness_landscapes.html"
    },
    {
      title: "Circular Distributions",
      description: "By Pedro M. Cruz. Cartogram of distributions of trips within cities in the U.S.",
      url: "https://pmcruz.com/works/circular-distributions.html"
    },
    {
      title: "Academic Networks",
      description: "By Ketika Garg. A visualisation of academic networks based on Bluesky starter packs.",
      url: "https://ketikagarg.github.io/blueSkyAcademicNetwork/network2.html"
    }
  ];

  const grid = document.getElementById('siteGrid');

  sites.forEach(site => {
    const preview = site.placeholder
      ? `<img src="${site.placeholder}" alt="${site.title} preview"
            style="width:100%; height:100%; object-fit:cover; display:block;" />`
      : `<iframe src="${site.url}" loading="lazy" scrolling="no"
            sandbox="allow-scripts allow-same-origin"
            style="width:200%; height:200%; transform:scale(0.5); transform-origin:top left; border:none; pointer-events:none;"
            title="${site.title}"></iframe>`;

    grid.innerHTML += `
      <div class="card">
        <div class="browser-bar">
          <div class="browser-dots">
            <div class="dot red"></div>
            <div class="dot yellow"></div>
            <div class="dot green"></div>
          </div>
        </div>
        <div class="iframe-wrapper">
          ${preview}
          <a class="iframe-overlay" href="${site.url}" target="_blank" rel="noopener"></a>
        </div>
        <div class="card-footer">
          <div>
            <div class="card-title">${site.title}</div>
            <div class="card-desc">${site.description}</div>
          </div>
          <a class="open-btn" href="${site.url}" target="_blank" rel="noopener">Open ↗</a>
        </div>
      </div>
    `;
  });
</script>



  
