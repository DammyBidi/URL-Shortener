<!-- Shortener.vue -->

<template>
  <div>
    <nav>
      <div class="links">
        <h3>Shortly</h3>
        <a href="">features</a>
        <a href="">Pricing</a>
        <a href="">Resources</a>
      </div>
      <div class="login">
        <a href="">Login</a>
        <button>Sign Up</button>
      </div>
      <div class="mobile-nav-toggle" @click="toggleMobileNav">
        <ion-icon name="menu-outline"></ion-icon>
      </div>
    </nav>
    <header>
      <!-- Mobile navigation -->
      <div class="mobile-nav" v-if="showMobileNav">
        <div class="mobile-links">
          <a href="">Features</a>
          <a href="">Pricing</a>
          <a href="">Resources</a>
        </div>
        <hr>
        <div class="mobile-login">
          <a href="">Login</a>
          <button>Sign Up</button>
        </div>
      </div>
      <div class="hero">
        <div class="text">
          <h1>More than just shorter links</h1>
          <p>
            Build your brand's recognition and get detailed insights on how your
            links are performing.
          </p>
          <button>Get Started</button>
        </div>
        <div class="image">
          <img
            src="/src/assets/illustration-working.svg"
            alt="illustration of a person working on a computer"
          />
        </div>
      </div>
      <div class="form">
        <form crossorigin="anonymous" action="" @submit.prevent="shortenUrl">
          <div class="input-container">
            <input
              type="url"
              name="url-input"
              v-model="originalUrl"
              placeholder="Shorten a link here..."
              :class="{ 'error-input': errorMessage }"
              :style="{
                borderColor: errorMessage ? 'hsl(0, 87%, 67%)' : '',
                color: errorMessage ? 'hsl(0, 87%, 67%)' : '',
              }"
            />
            <label v-if="errorMessage" class="error-message" for="url-input">
              <i> {{ errorMessage }} </i>
            </label>
          </div>
          <button type="submit">Shorten It!</button>
        </form>
      </div>
    </header>

    <div class="grey-bg">
      <div class="link-section">
        <div v-if="shortenedLinks.length > 0">
          <div v-for="(link, index) in shortenedLinks" :key="index">
            <div class="link-container">
              <div class="original-link">{{ link.originalUrl }}</div>
              <div class="short-link">
                <span>{{ link.shortened_url }}</span>
                <button
                  @click="copyToClipboard(link.shortened_url, index)"
                  :class="{ 'violet-button': link.copied }"
                >
                  {{ link.copied ? "Copied!" : "Copy" }}
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="statistics">
        <div class="statistics-title">
          <h2>Advanced Statistics</h2>
          <p>
            Track how your links are performing across the web with our advanced
            statistics dashboard.
          </p>
        </div>
        <div class="cards">
          <div class="card c1">
            <div class="card-icon">
              <img
                src="/src/assets/icon-brand-recognition.svg"
                alt="brand recognition icon"
              />
            </div>
            <h3>Brand Recognition</h3>
            <p>
              Boost your brand recognition with <br />
              each click. Generic links don't mean a thing. Branded links help
              instil confidence in your content.
            </p>
          </div>
          <div class="card c2">
            <div class="card-icon">
              <img
                src="/src/assets/icon-detailed-records.svg"
                alt="detailed records icon"
              />
            </div>
            <h3>Detailed Records</h3>
            <p>
              Gain insights into who is clicking your links. Knowing when and
              where people engage with your content helps inform better
              decisions.
            </p>
          </div>
          <div class="card c3">
            <div class="card-icon">
              <img
                src="/src/assets/icon-fully-customizable.svg"
                alt="fully customizable icon"
              />
            </div>
            <h3>Fully Customizable</h3>
            <p>
              Improve brand awareness and <br />
              content discoverability through <br />
              customizable links, supercharging audience engagement.
            </p>
          </div>
          <div class="connect-line"></div>
        </div>
      </div>
    </div>

    <div class="boost">
      <h2>Boost your links today</h2>
      <button>Get Started</button>
    </div>

    <div class="footer-bg">
      <footer>
        <div class="footer-logo">
          <h3>Shortly</h3>
        </div>
        <div class="footer-links">
          <div class="footer-links-section">
            <h3>Features</h3>
            <a href="">Link Shortening</a>
            <a href="">Branded Links</a>
            <a href="">Analytics</a>
          </div>
          <div class="footer-links-section">
            <h3>Resources</h3>
            <a href="">Blog</a>
            <a href="">Developers</a>
            <a href="">Support</a>
          </div>
          <div class="footer-links-section">
            <h3>Company</h3>
            <a href="">About</a>
            <a href="">Our Team</a>
            <a href="">Careers</a>
            <a href="">Contact</a>
          </div>
          <div class="footer-social">
            <img src="/src/assets/icon-facebook.svg" alt="facebook icon" />
            <img src="/src/assets/icon-twitter.svg" alt="twitter icon" />
            <img src="/src/assets/icon-pinterest.svg" alt="pinterest icon" />
            <img src="/src/assets/icon-instagram.svg" alt="instagram icon" />
          </div>
        </div>
      </footer>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      originalUrl: "",
      shortenedLinks: JSON.parse(localStorage.getItem("shortenedLinks")) || [],
      errorMessage: "",
      showMobileNav: false,
    };
  },
  methods: {
    shortenUrl() {
      this.errorMessage = "";

      if (!this.originalUrl) {
        this.errorMessage = "Please enter a valid URL";
        return;
      }

      axios
        .get(
          `https://tinyurl.com/api-create.php?url=${encodeURIComponent(
            this.originalUrl
          )}`
        )
        .then((response) => {
          this.shortenedLinks.unshift({
            originalUrl: this.originalUrl,
            shortened_url: response.data,
            copied: false,
          });
          this.saveToLocalStorage();
          this.originalUrl = "";
        })
        .catch((error) => {
          console.error("Error shortening URL:", error);
          alert("Error shortening URL. Please try again.");
        });
    },
    copyToClipboard(text, index) {
      navigator.clipboard.writeText(text).then(() => {
        this.shortenedLinks[index].copied = true;
        this.saveToLocalStorage();
        setTimeout(() => {
          this.shortenedLinks[index].copied = false;
        }, 3000);
      });
    },
    saveToLocalStorage() {
      localStorage.setItem(
        "shortenedLinks",
        JSON.stringify(this.shortenedLinks)
      );
    },
    toggleMobileNav() {
      this.showMobileNav = !this.showMobileNav;
    },
  },
};
</script>

<style scoped>
@import "./Shortener.css";
</style>
