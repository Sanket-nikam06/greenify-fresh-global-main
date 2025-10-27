# Greenify Fresh Global - Complete Project Guide

## 📋 Table of Contents
1. [Project Overview](#project-overview)
2. [Project Structure](#project-structure)
3. [How to Add/Remove Products](#how-to-addremove-products)
4. [How to Edit Product Details](#how-to-edit-product-details)
5. [How to Change Images](#how-to-change-images)
6. [How to Edit Text Content](#how-to-edit-text-content)
7. [How to Add New Sections](#how-to-add-new-sections)
8. [How to Change Colors and Styling](#how-to-change-colors-and-styling)
9. [How to Add New Languages](#how-to-add-new-languages)
10. [How to Deploy](#how-to-deploy)

--- 

## 🚀 Project Overview

This is a modern React website for Greenify Fresh Global, a fruit and vegetable export company. The website features:

- **Responsive Design** - Works on desktop, tablet, and mobile
- **Multi-language Support** - English and other languages
- **Interactive Product Showcase** - Beautiful product cards with details
- **Modern UI Components** - Built with Tailwind CSS and Shadcn/ui
- **Smooth Animations** - Fade-in effects and hover animations
- **Contact Forms** - Easy way for customers to get in touch

---

## 📁 Project Structure

```
src/
├── components/           # Reusable UI components
│   ├── Navigation.tsx    # Top navigation bar
│   ├── HeroSection.tsx   # Main banner section
│   ├── ServicesSection.tsx # Services carousel
│   ├── WhyChooseUsSection.tsx # Company advantages
│   ├── CertificationsSection.tsx # Certifications display
│   ├── ProductsSection.tsx # Products grid
│   ├── AboutSection.tsx  # About company
│   ├── ContactSection.tsx # Contact form
│   ├── Footer.tsx        # Footer with links
│   └── FloatingContactButton.tsx # Floating contact button
├── pages/               # Main pages
│   ├── Index.tsx        # Home page
│   ├── ProductDetail.tsx # Individual product page
│   └── NotFound.tsx     # 404 error page
├── contexts/            # Global state management
│   └── TranslationContext.tsx # Multi-language system
├── assets/              # Images and media
│   ├── service-fruits.jpg
│   ├── service-vegetables.jpg
│   ├── service-packaging.jpg
│   └── service-logistics.jpg
└── App.tsx              # Main app component
```

---

## 🛍️ How to Add/Remove Products

### Adding a New Product

**Step 1: Add Product to ProductsSection.tsx**
```typescript
// In src/components/ProductsSection.tsx
const products = [
  {
    id: "grapes",           // Unique ID for the product
    image: grapeImg,        // Image to display
  },
  {
    id: "pomegranate",      // Another product
    image: grapeImg,
  },
  // ADD YOUR NEW PRODUCT HERE
  {
    id: "bananas",          // New product ID
    image: grapeImg,        // Choose appropriate image
  },
];
```

**Step 2: Add Product Details to TranslationContext.tsx**
```typescript
// In src/contexts/TranslationContext.tsx
// Find the productDetails section and add your product:

productDetails: {
  // ... existing products ...
  bananas: {
    name: "Fresh Bananas",
    tagline: "Premium quality bananas",
    description: "Our bananas are carefully selected and packed to maintain freshness...",
    regions: "South America, Central America",
    packaging: "Cardboard boxes, 18kg per box",
    certifications: "Organic Certified, Fair Trade"
  }
}
```

**Step 3: Add Product Image Mapping to ProductDetail.tsx**
```typescript
// In src/pages/ProductDetail.tsx
const productImages: { [key: string]: string } = {
  grapes: grapeImg,
  pomegranate: grapeImg,
  onions: vegetableImg,
  tomatoes: vegetableImg,
  mangoes: grapeImg,
  spices: vegetableImg,
  bananas: grapeImg,  // Add your new product here
};
```

### Removing a Product

1. **Remove from ProductsSection.tsx** - Delete the product object from the `products` array
2. **Remove from TranslationContext.tsx** - Delete the product details from `productDetails`
3. **Remove from ProductDetail.tsx** - Delete the product from `productImages` object

---

## ✏️ How to Edit Product Details

### Changing Product Information

**Edit in TranslationContext.tsx:**
```typescript
// Find your product in the productDetails section
productDetails: {
  grapes: {
    name: "Premium Grapes",           // Change product name
    tagline: "Sweet and juicy",       // Change tagline
    description: "Our grapes are...", // Change description
    regions: "California, Italy",     // Change export regions
    packaging: "Plastic crates",      // Change packaging info
    certifications: "Organic, HACCP"  // Change certifications
  }
}
```

### Changing Product Images

**Option 1: Use Existing Images**
```typescript
// In ProductsSection.tsx, change the image:
{
  id: "grapes",
  image: vegetableImg,  // Changed from grapeImg to vegetableImg
}
```

**Option 2: Add New Images**
1. Add your image to `src/assets/` folder
2. Import it in ProductsSection.tsx:
```typescript
import newImage from "@/assets/your-new-image.jpg";
```
3. Use it in your product:
```typescript
{
  id: "grapes",
  image: newImage,
}
```

---

## 🖼️ How to Change Images

### Changing Service Images

**In ServicesSection.tsx:**
```typescript
// Import your new image
import newServiceImage from "@/assets/your-service-image.jpg";

// Use it in the services array
const services = [
  {
    image: newServiceImage,  // Your new image
    title: t.services.freshFruit.title,
    description: t.services.freshFruit.description
  }
];
```

### Changing Hero Video

**In HeroSection.tsx:**
```html
<video 
  autoPlay
  muted
  loop
  playsInline
  className="w-full h-full object-cover"
>
  <source src="/videos/your-new-video.mp4" type="video/mp4" />
  Your browser does not support the video tag.
</video>
```

### Changing Company Logo

**In Navigation.tsx:**
```typescript
// Replace the Leaf icon with your logo
<div className="w-10 h-10 bg-gradient-primary rounded-lg flex items-center justify-center">
  <img src="/your-logo.png" alt="Logo" className="w-6 h-6" />
</div>
```

---

## 📝 How to Edit Text Content

### Changing Section Titles and Descriptions

**Edit in TranslationContext.tsx:**
```typescript
// Example: Change the products section title
productsPage: {
  title: "Our Premium Products",  // Change this
  subtitle: "Fresh from farm to your table",  // Change this
  viewDetails: "Learn More",  // Change this
  // ... other text
}
```

### Changing Company Information

**Edit in TranslationContext.tsx:**
```typescript
// Change company name
nav: {
  logo: "Your Company Name",  // Change this
  home: "Home",
  // ... other navigation items
}

// Change hero section
hero: {
  title: "Your Company Name",  // Change this
  subtitle: "Your tagline here",  // Change this
  exploreServices: "Our Services",  // Change this
  contactUs: "Contact Us"  // Change this
}
```

### Changing Contact Information

**Edit in ContactSection.tsx:**
```typescript
// Find and change contact details
const contactInfo = {
  phone: "+1 234 567 8900",  // Change phone
  email: "info@yourcompany.com",  // Change email
  address: "Your Address Here"  // Change address
};
```

---

## ➕ How to Add New Sections

### Adding a New Section to Home Page

**Step 1: Create the Component**
```typescript
// Create src/components/NewSection.tsx
import React from 'react';

const NewSection = () => {
  return (
    <section id="new-section" className="py-20 bg-background">
      <div className="container mx-auto px-6">
        <h2 className="text-4xl font-bold text-center mb-8">
          Your New Section
        </h2>
        <p className="text-center text-muted-foreground">
          Your section content here
        </p>
      </div>
    </section>
  );
};

export default NewSection;
```

**Step 2: Add to Home Page**
```typescript
// In src/pages/Index.tsx
import NewSection from "@/components/NewSection";

const Index = () => {
  return (
    <div className="min-h-screen">
      <Navigation />
      <HeroSection />
      <ServicesSection />
      <NewSection />  {/* Add your new section here */}
      <WhyChooseUsSection />
      {/* ... other sections */}
    </div>
  );
};
```

**Step 3: Add Navigation Link**
```typescript
// In src/components/Navigation.tsx
// Add to desktop menu
<button 
  onClick={() => scrollToSection('new-section')}
  className="text-foreground hover:text-primary transition-colors font-medium"
>
  New Section
</button>

// Add to mobile menu
<button 
  onClick={() => scrollToSection('new-section')}
  className="block w-full text-left px-4 py-2 text-foreground hover:text-primary transition-colors font-medium"
>
  New Section
</button>
```

---

## 🎨 How to Change Colors and Styling

### Changing Theme Colors

**Edit tailwind.config.js:**
```javascript
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: {
          DEFAULT: '#your-primary-color',  // Change primary color
          dark: '#your-primary-dark',      // Change primary dark
        },
        secondary: {
          DEFAULT: '#your-secondary-color', // Change secondary color
        },
        // ... other colors
      }
    }
  }
}
```

### Changing Background Colors

**In any component:**
```typescript
// Change section background
<section className="py-20 bg-your-color">  // Change bg-accent to bg-your-color
```

### Changing Text Colors

```typescript
// Change text color
<h2 className="text-4xl font-bold text-your-color">  // Change text-primary to text-your-color
```

---

## 🌍 How to Add New Languages

### Adding a New Language

**Step 1: Add Language to TranslationContext.tsx**
```typescript
// In src/contexts/TranslationContext.tsx
const translations = {
  en: {
    // ... existing English translations
  },
  es: {  // Add Spanish
    nav: {
      logo: "Greenify Export",
      home: "Inicio",
      services: "Servicios",
      // ... translate all text
    },
    // ... translate all other sections
  }
};
```

**Step 2: Add Language Option to LanguageSelector.tsx**
```typescript
// In src/components/LanguageSelector.tsx
const languages = [
  { code: 'en', name: 'English' },
  { code: 'es', name: 'Español' },  // Add your new language
];
```

---

## 🚀 How to Deploy

### Build the Project
```bash
npm run build
```

### Deploy to Vercel (Recommended)
1. Push your code to GitHub
2. Connect your GitHub repo to Vercel
3. Vercel will automatically deploy your site

### Deploy to Netlify
1. Build your project: `npm run build`
2. Upload the `dist` folder to Netlify
3. Your site will be live!

### Deploy to Any Hosting Service
1. Run `npm run build`
2. Upload the contents of the `dist` folder to your hosting service
3. Make sure your hosting service supports React SPA routing

---

## 🛠️ Common Tasks

### How to Change the Company Name
1. Edit `src/contexts/TranslationContext.tsx` - Change all instances of "Greenify Export"
2. Edit `src/components/Navigation.tsx` - Change the hardcoded company name

### How to Change the Contact Email
1. Edit `src/components/ContactSection.tsx` - Find the email field and change it
2. Update your contact form handler to use the new email

### How to Add Social Media Links
1. Edit `src/components/Footer.tsx` - Add social media icons and links
2. Import the icons from `lucide-react`

### How to Change the Video Background
1. Replace the video file in `public/videos/`
2. Update the video source in `src/components/HeroSection.tsx`

---

## 📞 Support

If you need help making changes to your website:

1. **Check this README first** - Most common tasks are covered here
2. **Look at the code** - The code is well-structured and easy to understand
3. **Test changes locally** - Always test your changes before deploying
4. **Make backups** - Keep a backup of your working code

---

## 🎯 Quick Reference

| What to Change | File to Edit | What to Look For |
|----------------|--------------|------------------|
| Product names/descriptions | `TranslationContext.tsx` | `productDetails` |
| Add/remove products | `ProductsSection.tsx` | `products` array |
| Change images | `assets/` folder | Import statements |
| Change colors | `tailwind.config.js` | `colors` section |
| Change text content | `TranslationContext.tsx` | Any text object |
| Add new sections | Create new component | Import in `Index.tsx` |
| Change company info | `TranslationContext.tsx` | `nav` and `hero` sections |

---

**Happy coding! 🚀**

