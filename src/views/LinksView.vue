<template>
  <div class="links-container">
    <div class="profile-section">
      <img src="../assets/rjw.svg" alt="Profile Image" class="profile-image" />
      <h1 class="profile-name">Ryan Wong</h1>
      <p class="profile-description">Connect with me!</p>
    </div>
    
    <!-- New Recent Releases Section -->
    <div class="section-title">
      <h2>Recent Releases</h2>
    </div>
    
    <div class="recent-releases-section">
      <a href="https://www.youtube.com/watch?v=euQlo9ny4Ec" target="_blank" rel="noopener noreferrer" class="release-card youtube-release">
        <div class="release-content">
          <div class="release-badge">NEW</div>
          <i class="fab fa-youtube"></i>
          <span class="release-title">shinjuku got expensive... BUT SO WORTH IT | Japan Part 2</span>
          <span class="release-date">March 28, 2025</span>
        </div>
      </a>
      
      <a href="https://www.blog.ryanwong.ca/blog/diy-nas" target="_blank" rel="noopener noreferrer" class="release-card blog-release">
        <div class="release-content">
          <div class="release-badge">NEW</div>
          <i class="fas fa-rss"></i>
          <span class="release-title">DIY NAS</span>
          <span class="release-date">March 17, 2025</span>
        </div>
      </a>
      
      <!-- Add more recent releases here as needed -->
    </div>
    
    <div class="section-title">
      <h2>Links</h2>
    </div>
    
    <div class="links-section">
      <a href="/" class="link-button portfolio">
        <i class="fas fa-home"></i> Portfolio Website
      </a>

      <a href="/blog" class="link-button blog">
        <i class="fas fa-rss"></i> Blog
      </a>
            
      <!-- Social Media Links with Icons -->
      <a href="https://www.youtube.com/@ryanwoong" target="_blank" rel="noopener noreferrer" class="link-button youtube">
        <i class="fab fa-youtube"></i> YouTube Channel
      </a>
            <a href="https://vsco.co/ryanwoong" target="_blank" rel="noopener noreferrer" class="link-button vsco">
        <i class="fas fa-camera"></i> VSCO
      </a>
      <a href="https://www.instagram.com/ryxn.wxng/" target="_blank" rel="noopener noreferrer" class="link-button instagram">
        <i class="fab fa-instagram"></i> @ryxn.wxng
      </a>
      <a href="https://www.instagram.com/shotbywong/" target="_blank" rel="noopener noreferrer" class="link-button instagram">
        <i class="fab fa-instagram"></i> @shotbywong
      </a>
      <a href="https://x.com/ryxnwxng" target="_blank" rel="noopener noreferrer" class="link-button twitter">
        <i class="fab fa-x-twitter"></i> @ryxnwxng
      </a>
      <a href="https://www.linkedin.com/in/ryanwongyyc/" target="_blank" rel="noopener noreferrer" class="link-button linkedin">
        <i class="fab fa-linkedin"></i> LinkedIn
      </a>
      <a href="https://github.com/ryanwoong" target="_blank" rel="noopener noreferrer" class="link-button github">
        <i class="fab fa-github"></i> GitHub
      </a>

    </div>
  </div>
</template>

<style scoped>
.links-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
}

/* Add a parent wrapper with a background gradient that covers the entire view */
:deep(body) {
  margin: 0;
  padding: 0;
}

/* Using :deep to target the parent #app element */
:deep(#app) {
  min-height: 100vh;
  background: linear-gradient(135deg, #f5f7fa, #e4e9f0);
  padding: 2rem 0;
}

.profile-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 2rem;
}

.profile-image {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 1rem;
}

.profile-name {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.profile-description {
  font-size: 1rem;
  color: #666;
  margin-bottom: 1.5rem;
}

.links-section {
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: 1rem;
}

.link-button {
  padding: 1rem;
  border-radius: 0.5rem;
  text-align: center;
  text-decoration: none;
  color: white;
  font-weight: 500;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  position: relative;
  overflow: hidden;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.link-button i {
  font-size: 1.2rem;
}

.link-button:hover {
  transform: translateY(-3px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.15);
}

/* New Styles for Recent Releases Section */
.section-title {
  width: 100%;
  margin: 1rem 0;
  text-align: left;
}

.section-title h2 {
  font-size: 1.3rem;
  font-weight: 600;
  color: #333;
  margin-bottom: 0.5rem;
}

.recent-releases-section {
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.release-card {
  padding: 1rem;
  border-radius: 0.5rem;
  text-decoration: none;
  color: white;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

/* Release card styles */
.youtube-release {
  background: linear-gradient(135deg, #FF0000, #CC0000);
}

.blog-release {
  background: linear-gradient(135deg, #32746d, #1d4540);
}

.release-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  position: relative;
  z-index: 1;
}

.release-badge {
  position: absolute;
  top: -8px;
  right: -8px;
  background-color: #ffcc00;
  color: #333;
  font-size: 0.7rem;
  font-weight: bold;
  padding: 3px 8px;
  border-radius: 10px;
  transform: rotate(15deg);
}

.release-title {
  font-weight: bold;
  font-size: 1.1rem;
  text-align: center;
}

.release-date {
  font-size: 0.8rem;
  opacity: 0.8;
}

.release-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

/* Social Media Brand Colors with Gradients */
.portfolio {
  background: linear-gradient(135deg, #32746d, #1d4540);
  color: white;
}

.portfolio:hover {
  background: linear-gradient(135deg, #3b8a81, #285f58);
}

.youtube {
  background: linear-gradient(135deg, #FF0000, #CC0000);
}

.youtube:hover {
  background: linear-gradient(135deg, #FF1a1a, #b30000);
}

.instagram {
  background: linear-gradient(45deg, #f09433, #e6683c, #dc2743, #cc2366, #bc1888);
}

.instagram:hover {
  background: linear-gradient(45deg, #f1a243, #e87a4c, #dd3853, #cd3476, #bd2998);
}

.vsco {
  background: linear-gradient(135deg, #000000, #333333);
}

.vsco:hover {
  background: linear-gradient(135deg, #1a1a1a, #4d4d4d);
}

.linkedin {
  background: linear-gradient(135deg, #0077B5, #00497e);
}

.linkedin:hover {
  background: linear-gradient(135deg, #0088cc, #005c99);
}

.github {
  background: linear-gradient(135deg, #333333, #111111);
}

.github:hover {
  background: linear-gradient(135deg, #444444, #222222);
}

.blog {
  background: linear-gradient(135deg, #32746d, #1d4540);
}

.blog:hover {
  background: linear-gradient(135deg, #3b8a81, #285f58);
}

.twitter {
  background: linear-gradient(135deg, #000000, #14171A);
}

.twitter:hover {
  background: linear-gradient(135deg, #1a1a1a, #2e3236);
}

/* Default button gradient for non-branded buttons */
.link-button:not([class*=" "]) {
  background: linear-gradient(135deg, #f0f0f0, #d0d0d0);
  color: #333;
}

.link-button:not([class*=" "]):hover {
  background: linear-gradient(135deg, #f5f5f5, #e0e0e0);
}
</style>