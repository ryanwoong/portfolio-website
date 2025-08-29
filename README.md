# Portfolio Website

A modern, responsive portfolio website built with Vue 3, TypeScript, and Tailwind CSS. This website showcases my projects, work experience, skills, and provides easy access to my resume and contact information.

## 🚀 Live Demo

[View Portfolio Website](https://ryanwong.ca)

## ✨ Features

- **Responsive Design**: Optimized for all device sizes and screen resolutions
- **Modern UI**: Clean, professional design using Tailwind CSS
- **Project Showcase**: Detailed project cards with descriptions, technologies used, and live links
- **Experience Timeline**: Professional work experience with descriptions and skills
- **Skills Display**: Visual representation of technical skills and expertise
- **Resume Access**: Direct download link for PDF resume
- **Contact Links**: Easy access to professional social media profiles
- **Fast Performance**: Built with Vite for optimal loading speeds
- **Type Safety**: Full TypeScript support for better development experience

## 🛠️ Tech Stack

- **Frontend Framework**: Vue 3 (Composition API)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **Icons**: PrimeIcons
- **Routing**: Vue Router 4
- **Build Tool**: Vite
- **Package Manager**: Bun/npm

## 📁 Project Structure

```
src/
├── components/          # Reusable Vue components
│   ├── Experience.vue   # Individual experience item
│   ├── Experiences.vue  # Experience section
│   ├── Navbar.vue      # Navigation component
│   ├── Project.vue     # Individual project card
│   ├── Projects.vue    # Projects section
│   ├── Skill.vue       # Individual skill item
│   └── Skills.vue      # Skills section
├── views/              # Page components
│   ├── HomeView.vue    # Main landing page
│   ├── LinksView.vue   # Social links page
│   ├── NotFoundView.vue # 404 error page
│   └── ResumeView.vue  # Resume display page
├── router/             # Vue Router configuration
├── assets/             # Static assets (images, resume, etc.)
├── data.json          # Portfolio content data
└── main.ts            # Application entry point
```
