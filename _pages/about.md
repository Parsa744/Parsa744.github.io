---
permalink: /
title: "This is Parsa Hariri."
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

Hello! My name is Parsa, and I work as a computational biologist and bioinformatician at the University of Göttingen. I specialize in modeling biological networks, such as those found in the brain and embryos. If you're interested in a scientific discussion, want to know more about my educational journey, or have any other questions, please don't hesitate to reach out. I also organize some talks about bioinformatics, you can learn more about it [here](https://parsa744.github.io/talks/2024-03-01-talk-1)
![my presentation in Goettingen Uni](images/27811002-0b3e-4b66-99db-7643729f2c6f.jpeg)

<section>
  <h2>Latest Projects</h2>
  <div class="projects-list">
    {% for post in site.projects limit: 3 %}
      <article class="project-item">
        <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
        <p>{{ post.excerpt }}</p>
        <p><a href="{{ post.url }}">Read more</a></p>
      </article>
    {% endfor %}
  </div>
</section>

<section>
  <h2>Latest Posts</h2>
  <div class="posts-list">
    {% for post in site.posts limit: 3 %}
      <article class="project-item">
        <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
        <p>{{ post.excerpt }}</p>
        <p><a href="{{ post.url }}">Read more</a></p>
      </article>
    {% endfor %}
  </div>
</section>
