<template>
  <header>
    <nav class="navbar">
      <div class="logo">
        <a href="/">
          <p>logo</p>
        </a>
      </div>
      <div class="hamburger-menu">
        <span class="line"></span>
        <span class="line"></span>
        <span class="line"></span>
      </div>
      <div class="nav-menu hide">
        <!-- Use buttons instead of anchor tags -->
        <button @click="smoothScroll($refs.start)">Categories</button>
        <button @click="smoothScroll(tutorials)">Helpful Tutorials</button>
        <button @click="smoothScroll(allBooks)">All Books</button>
      </div>
    </nav>

    <h1 id="headline"></h1>
    <div class="header-container">
      <div id="typed-strings" style="display: none">
        <p>Start Your Coding Journey Today.</p>
        <p>Here are books you'll probably</p>
        <p>Here are books you'll definitely need!</p>
      </div>
      <div id="searchInput" class="search glass-effect">
        <i class="fa fa-search"></i>
        <input
          id="searchbar"
          class="searchbar"
          type="text"
          placeholder="Looking for a book?"
          onfocus="this.placeholder = ''"
        />
      </div>
      <a href="#" @click.prevent="smoothScroll($refs.start)" class="arrow-down">
        <i class="fa-solid fa-chevron-down"></i
      ></a>
    </div>
  </header>
</template>

<script>
export default {
  mounted() {
    this.typeWriter()
  },

  methods: {
    smoothScroll(targetElement) {
      if (targetElement) {
        targetElement.scrollIntoView({
          behavior: 'smooth'
        })
      }
    },
    typeWriter() {
      // Initialize Typed.js
      new Typed('#headline', {
        stringsElement: '#typed-strings',
        backSpeed: 35,
        typeSpeed: 80,
        backDelay: 1000,
        loop: true,
        loopCount: 1,
        showCursor: false
      })
    }
  }
}
</script>

<style scoped>
header {
  display: grid;
  place-items: center; /* Center items vertically and horizontally */
  background: linear-gradient(
    144deg,
    rgba(39, 101, 112, 1) 0%,
    rgba(37, 63, 85, 1) 27%,
    rgba(27, 32, 46, 1) 100%
  );
  padding: 1rem 0 12rem 0;
  text-align: center;
  box-shadow: 0 2rem 4rem rgba(0, 0, 0, 0.127);
}

.header-container {
  display: grid;
  place-items: center;
  gap: 3.5rem;
  grid-template-rows: auto auto;
  min-width: 70%;
}

/* navbar styling */
.navbar {
  display: flex;
  height: 5rem;
  justify-content: space-between;
  align-items: center;
  padding-top: 1rem;
  margin-bottom: 10rem;
}

/* logo style  */
.logo img {
  width: 4rem;
  height: 4rem;
  margin-left: 1rem;
}

.hamburger-menu {
  padding-right: 1.5rem;
  cursor: pointer;
}

.hamburger-menu .line {
  display: block;
  width: 2.5rem;
  height: 2px;
  margin-bottom: 10px;
  background-color: black;
  cursor: pointer;
}

.nav-menu button {
  padding: 15px 20px;
  background-color: transparent;
  border: none;
  font-size: 1rem;
  font-weight: 500;
  color: var(--color);
  text-transform: uppercase;
  letter-spacing: 0.3rem;
  transition: 0.2s ease-out;
}

.nav-menu button:hover {
  background-color: var(--dark-blue);
  border-radius: 0.3rem;
  text-align: center;
}

.hide {
  display: none;
}

.section-content {
  margin-bottom: 3.5rem;
}

.search,
.arrow-down {
  margin-top: auto;
}

.search {
  display: flex;
  gap: 1rem;
  align-items: center;
  width: 70%;
  height: 4rem;
  background-color: #ffffff78;
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
  color: var(--color);
  margin-bottom: 1.5rem;
  transition: 0.6s;
}

.search:hover {
  padding: 0.7rem 1.2rem;
}

.searchbar {
  background: rgba(255, 255, 255, 0);
  border: none;
  width: 80%;
  height: 2rem;
  font-weight: 500;
}

.searchbar:focus {
  outline: none;
  color: var(--color);
}

.search ::placeholder {
  color: var(--color);
  font-size: 1.2rem;
}

.arrow-down {
  font-size: 3rem;
  color: var(--color);
}

@media screen and (min-width: 600px) {
  .navbar {
    justify-content: space-between;
    padding: 2rem 3rem 5rem 3rem;
    min-width: 100%;
  }
  .nav-menu {
    display: block;
    position: static;
    width: auto;
    margin-right: 20px;
    background: none;
  }
  .nav-menu a {
    display: inline-block;
    padding: 15px 20px;
    text-decoration: none;
    color: var(--color);
    text-transform: uppercase;
    letter-spacing: 0.3rem;
  }
  .nav-menu a:hover {
    background-color: var(--dark-blue);
    border-radius: 5px;
  }
  .hamburger-menu {
    display: none;
  }
}
</style>
