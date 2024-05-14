<template>
  <section ref="start" class="section">
    <h2>Get started</h2>
    <div id="categories" class="section-content">
      <div class="category-container">
        <a id="java" class="category glass-effect"><i class="fa-brands fa-java"></i></a>
        <h3>Java</h3>
      </div>
      <div class="category-container">
        <a id="javascript" class="category glass-effect"><i class="fa-brands fa-js"></i></a>
        <h3>JavaScript</h3>
      </div>
      <div class="category-container">
        <a id="python" class="category glass-effect"><i class="fa-brands fa-python"></i></a>
        <h3>Python</h3>
      </div>
      <div class="category-container">
        <a id="html" class="category glass-effect"><i class="fa-brands fa-html5"></i></a>
        <h3>HTML5</h3>
      </div>
      <div class="category-container">
        <a id="css" class="category glass-effect"><i class="fa-regular fa-file-code"></i> </a>
        <h3>CSS</h3>
      </div>
    </div>
  </section>
</template>

<style scoped>
#categories {
  display: flex;
  justify-content: space-between;
}

.category {
  display: flex;
  place-items: center;
  justify-content: center;
  font-size: 5rem;
  height: 10rem;
  width: 10rem;
  border-radius: 3rem;
  background-color: var(--glass-background);
  margin-bottom: 2rem;
}

.category:hover {
  scale: 105%;
}
</style>
