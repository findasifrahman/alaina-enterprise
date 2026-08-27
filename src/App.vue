<template>
  <div>
    <header class="topbar">
      <a class="brand" href="#home" aria-label="Alaina Enterprise home">
        <img src="/assets/brand/alaina-logo.jpeg" alt="Alaina Enterprise logo" />
        <span>Alaina Enterprise</span>
      </a>
      <nav class="desktop-nav" aria-label="Primary navigation">
        <a v-for="item in navItems" :key="item.href" :href="item.href">{{ item.label }}</a>
      </nav>
      <a class="phone-pill" href="tel:+8801819833911" aria-label="Call Alaina Enterprise">
        <span class="phone-icon">Tel</span>
        <span class="phone-number">+8801819833911</span>
      </a>
    </header>

    <main id="home">
      <section class="hero" aria-label="Company highlights">
        <div
          v-for="(slide, index) in heroSlides"
          :key="slide.title"
          class="hero-slide"
          :class="{ active: activeSlide === index }"
        >
          <img :src="slide.image" :alt="slide.alt" />
          <div class="hero-overlay"></div>
          <div class="hero-content">
            <p>{{ slide.kicker }}</p>
            <h1>{{ slide.title }}</h1>
            <span>{{ slide.copy }}</span>
            <div class="hero-actions">
              <a href="#services" class="primary-btn">Explore Services</a>
              <a href="#contact" class="secondary-btn">Contact Team</a>
            </div>
          </div>
        </div>
        <div class="hero-dots" aria-label="Carousel controls">
          <button
            v-for="(_, index) in heroSlides"
            :key="index"
            :class="{ active: activeSlide === index }"
            :aria-label="`Show slide ${index + 1}`"
            @click="activeSlide = index"
          ></button>
        </div>
      </section>

      <section class="section intro" id="about">
        <div class="section-title reveal">
          <p class="eyebrow">Who We Are</p>
          <h2>With a vision to serve Bangladesh's vertical infrastructure.</h2>
          <span>
            Alaina Enterprise provides <mark>one-stop engineering solutions</mark>
            for <mark>passenger elevators</mark>, rooftop solar, generators,
            sub-stations, electrical works and civil support.
          </span>
        </div>
        <div class="stat-grid reveal">
          <article v-for="stat in stats" :key="stat.label">
            <strong :class="{ 'counter-value': stat.counter }">
              {{ stat.counter ? `${counters[stat.counter]}${stat.suffix}` : stat.value }}
            </strong>
            <span>{{ stat.label }}</span>
          </article>
        </div>
      </section>

      <section class="mission-section" id="mission">
        <div class="section-title reveal">
          <p class="eyebrow">Mission & Vision</p>
          <h2>Purpose, quality and long-term client trust.</h2>
        </div>
        <div class="mission-grid">
          <article class="mission-panel reveal">
            <span>Vision</span>
            <h3>100% customer satisfaction through dependable delivery.</h3>
            <p>
              Our vision is to deliver quality products and services at an
              affordable cost while growing into a technology-based corporate
              solutions provider. We aim to respond confidently to client needs
              and keep improving the standard of every project we touch.
            </p>
          </article>
          <article class="mission-panel mission-dark reveal">
            <span>Mission</span>
            <h3>A high-standard, reliable solution and service provider.</h3>
            <p>
              Our mission is to build a reputation as a quality-driven,
              standards-focused and reliable provider of engineering solutions
              for companies, buildings, industries and government-sector
              clients across Bangladesh.
            </p>
          </article>
        </div>
      </section>

      <section class="section services" id="services">
        <div class="section-title reveal">
          <p class="eyebrow">Core Services</p>
          <h2>What we do</h2>
          <span>Designed, supplied, installed and maintained by one accountable team.</span>
        </div>
        <div class="service-showcase">
          <article v-for="service in services" :key="service.title" class="service-card reveal">
            <img :src="service.image" :alt="service.alt" />
            <div>
              <span>{{ service.number }}</span>
              <h3>{{ service.title }}</h3>
              <p>{{ service.copy }}</p>
            </div>
          </article>
        </div>
      </section>

      <section class="projects" id="projects">
        <div class="section-title reveal">
          <p class="eyebrow">Projects</p>
          <h2>Building references from Dhaka's residential growth corridor.</h2>
        </div>
        <article
          v-for="(project, index) in projects"
          :key="project.name"
          class="project-row reveal"
          :class="{ reverse: index % 2 === 1 }"
        >
          <div class="project-text">
            <p class="eyebrow">Project {{ String(index + 1).padStart(2, '0') }}</p>
            <h3>{{ project.name }}</h3>
            <ul>
              <li v-for="point in project.points" :key="point">{{ point }}</li>
            </ul>
          </div>
          <div class="project-image">
            <img :src="project.image" :alt="project.name" />
          </div>
        </article>
      </section>

      <section class="section team" id="team">
        <div class="section-title reveal">
          <p class="eyebrow">Leadership</p>
          <h2>Experienced professionals</h2>
        </div>
        <div class="team-grid">
          <article v-for="person in team" :key="person.name" class="team-card reveal">
            <img :src="person.image" :alt="person.name" />
            <div>
              <h3>{{ person.name }}</h3>
              <p>{{ person.role }}</p>
            </div>
          </article>
        </div>
      </section>

      <section class="section faq" id="faq">
        <div class="section-title reveal">
          <h2>FAQ.</h2>
        </div>
        <div class="faq-list">
          <details v-for="item in faqs" :key="item.question" class="reveal">
            <summary>{{ item.question }}</summary>
            <p>{{ item.answer }}</p>
          </details>
        </div>
      </section>

      <section class="contact-section" id="contact">
        <div class="section-title reveal">
          <p class="eyebrow">Get In Touch</p>
          <h2>Contact Alaina Enterprise</h2>
        </div>
        <div class="contact-grid">
          <div class="contact-card reveal">
            <h3>Office Address</h3>
            <p>House #508, 2nd Floor, Road 7, Avenue 7, Mirpur DOHS, Dhaka-1216, Bangladesh.</p>
            <h3>Phone</h3>
            <a href="tel:+8801819833911">01819833911</a>
            <a href="tel:+8801805032400">01805032400</a>
            <h3>Email</h3>
            <a href="mailto:info@alianaenterprise.com">info@alianaenterprise.com</a>
            <a href="mailto:mdlokeman@alainaenterprise.com">mdlokeman@alainaenterprise.com</a>
          </div>
          <div class="map-frame reveal">
            <iframe
              title="Alaina Enterprise office map"
              src="https://www.google.com/maps?q=Mirpur%20DOHS%20Dhaka%201216%20Bangladesh&output=embed"
              loading="lazy"
              referrerpolicy="no-referrer-when-downgrade"
            ></iframe>
          </div>
        </div>
      </section>

      <section class="section gallery" id="gallery">
        <div class="section-title reveal">
          <p class="eyebrow">Gallery</p>
          <h2>Service, project and partnership visuals.</h2>
        </div>
        <div class="gallery-grid">
          <button
            v-for="image in gallery"
            :key="image.src"
            class="gallery-item reveal"
            type="button"
            @click="selectedImage = image"
          >
            <img :src="image.src" :alt="image.alt" />
            <span>{{ image.caption }}</span>
          </button>
        </div>
      </section>
    </main>

    <footer class="footer">
      <div class="footer-brand">
        <img src="/assets/brand/alaina-logo.jpeg" alt="Alaina Enterprise logo" />
        <h2>Alaina Enterprise</h2>
        <p>Elevator, generator, rooftop solar, sub-station and electrical solutions across Bangladesh.</p>
      </div>
      <div>
        <h3>Quick Links</h3>
        <a v-for="item in navItems" :key="item.href" :href="item.href">{{ item.label }}</a>
      </div>
      <div>
        <h3>Address</h3>
        <p>House #508, 2nd Floor, Road 7, Avenue 7, Mirpur DOHS, Dhaka-1216, Bangladesh.</p>
        <a href="mailto:info@alianaenterprise.com">info@alianaenterprise.com</a>
        <a href="mailto:mdlokeman@alainaenterprise.com">mdlokeman@alainaenterprise.com</a>
      </div>
      <div>
        <h3>Social</h3>
        <div class="socials">
          <a href="https://www.facebook.com/" aria-label="Facebook">f</a>
          <a href="https://www.linkedin.com/" aria-label="LinkedIn">in</a>
          <a href="https://www.youtube.com/" aria-label="YouTube">yt</a>
        </div>
        <a class="footer-phone" href="tel:+8801819833911">+8801819833911</a>
        <a class="footer-phone" href="tel:+8801817291846">+8801817291846</a>
      </div>
    </footer>

    <div v-if="selectedImage" class="lightbox" role="dialog" aria-modal="true" @click.self="selectedImage = null">
      <button type="button" class="lightbox-close" aria-label="Close gallery image" @click="selectedImage = null">Close</button>
      <figure>
        <img :src="selectedImage.src" :alt="selectedImage.alt" />
        <figcaption>{{ selectedImage.caption }}</figcaption>
      </figure>
    </div>

    <a class="whatsapp" href="https://wa.me/8801819833911" target="_blank" rel="noreferrer" aria-label="Chat on WhatsApp">
      <svg viewBox="0 0 32 32" aria-hidden="true">
        <path d="M16 3.2A12.6 12.6 0 0 0 5.2 22.3L3.7 28.8l6.6-1.7A12.6 12.6 0 1 0 16 3.2Zm0 2.3a10.3 10.3 0 0 1 8.9 15.5 10.3 10.3 0 0 1-13.9 4l-.5-.3-3.7 1 1-3.6-.3-.6A10.3 10.3 0 0 1 16 5.5Zm-4.3 5.3c-.2 0-.6.1-.9.5-.3.4-1.1 1.1-1.1 2.7s1.2 3.1 1.3 3.3c.2.2 2.3 3.6 5.7 4.9 2.8 1.1 3.4.9 4 .8.6-.1 2-.8 2.2-1.6.3-.8.3-1.5.2-1.6-.1-.2-.3-.2-.7-.4l-2.2-1c-.3-.1-.6-.2-.8.2-.2.3-.9 1.1-1.1 1.3-.2.2-.4.2-.7.1-.4-.2-1.5-.6-2.8-1.7-1-1-1.7-2.1-1.9-2.5-.2-.3 0-.5.1-.7l.5-.6c.2-.2.2-.3.3-.6.1-.2.1-.4 0-.6l-1-2.4c-.2-.6-.5-.6-.8-.6h-.3Z" />
      </svg>
    </a>

    <nav class="mobile-tabs" aria-label="Mobile quick navigation">
      <a v-for="item in mobileItems" :key="item.href" :href="item.href">
        <component :is="item.icon" :size="21" stroke-width="2.4" aria-hidden="true" />
        {{ item.label }}
      </a>
    </nav>
  </div>
</template>

<script setup>
import { onMounted, onUnmounted, ref } from 'vue'
import { Home, Images, Phone, Wrench } from '@lucide/vue'

const navItems = [
  { label: 'About', href: '#about' },
  { label: 'Mission', href: '#mission' },
  { label: 'Services', href: '#services' },
  { label: 'Projects', href: '#projects' },
  { label: 'Gallery', href: '#gallery' },
  { label: 'Contact', href: '#contact' }
]

const mobileItems = [
  { label: 'Home', href: '#home', icon: Home },
  { label: 'Services', href: '#services', icon: Wrench },
  { label: 'Gallery', href: '#gallery', icon: Images },
  { label: 'Call', href: 'tel:+8801819833911', icon: Phone }
]

const heroSlides = [
  {
    image: '/assets/gallery/ai-lift-servicing-hero.png',
    alt: 'Elevator technicians servicing a passenger lift in a modern building lobby',
    kicker: 'Lift | Service',
    title: 'Passenger lift service built for daily reliability.',
    copy: 'Lift sales, installation, repair and maintenance support for safe vertical movement.'
  },
  {
    image: '/assets/projects/dream-korobi.png',
    alt: 'Dream Korobi residential building project',
    kicker: 'Quality | Standard',
    title: 'We construct service confidence.',
    copy: 'Passenger lift and electrical support shaped for Bangladesh building conditions.'
  },
  {
    image: '/assets/gallery/ai-substation-bangladesh.png',
    alt: 'Bangladeshi electrical technicians inspecting a sub-station',
    kicker: 'Power | Safety',
    title: 'Sub-station service',
    copy: 'Testing, commissioning and maintenance capability for commercial and industrial sites.'
  }
]

const stats = [
  { value: '24/7', label: 'Customer service support' },
  { label: 'Years leadership experience', counter: 'leadership', suffix: '+' },
  { label: 'Projects completed', counter: 'projects', suffix: '+' },
  { value: '100%', label: 'Customer satisfaction vision' }
]

const services = [
  {
    number: '01',
    title: 'Passenger Lift Sales & Maintenance',
    copy: 'Lift supply, installation, modernization and technical maintenance for multistoried residential and commercial buildings.',
    image: '/assets/gallery/ai-elevator-maintenance.png',
    alt: 'AI generated elevator technicians inspecting a passenger lift'
  },
  {
    number: '02',
    title: 'Rooftop Solar Sales & Maintenance',
    copy: 'Solar design, supply, installation, commissioning and support for reliable rooftop energy performance.',
    image: '/assets/gallery/ai-rooftop-solar-bangladesh.png',
    alt: 'Bangladeshi technicians inspecting rooftop solar panels'
  },
  {
    number: '03',
    title: 'Sub-Station Solutions',
    copy: 'Sub-station supply, installation, testing, commissioning, repair and maintenance for commercial and industrial sites.',
    image: '/assets/gallery/ai-substation-bangladesh.png',
    alt: 'Bangladeshi electrical technicians inspecting a sub-station control panel'
  }
]

const projects = [
  {
    name: 'Dream Korobi',
    image: '/assets/projects/dream-korobi.png',
    points: [
      'Residential tower support focused on safe passenger lift movement for daily family use.',
      'Electrical coordination suitable for Dhaka apartment load patterns and backup power planning.',
      'Service access considered for routine maintenance without disrupting occupants.',
      'Finish-sensitive installation approach for lobby, shaft and landing areas.'
    ]
  },
  {
    name: 'Sopno Bilash',
    image: '/assets/projects/sopno-bilash.png',
    points: [
      'Apartment-building service planning for reliable vertical circulation during peak resident hours.',
      'Lift and electrical checks aligned with Bangladesh building safety expectations.',
      'Maintenance-ready system layout for quick response from technical support teams.',
      'Practical coordination with civil finishing, wiring routes and common-area usage.'
    ]
  },
  {
    name: 'Kholifa Tower',
    image: '/assets/projects/kholifa-tower.png',
    points: [
      'Multistoried building support shaped around durable lift operation and controlled power supply.',
      'Sub-station and generator-readiness considered for stable service during voltage fluctuation.',
      'Installation planning suitable for tight urban construction sites in Dhaka.',
      'Safety-first inspection points for landing doors, machine-room access and emergency service.'
    ]
  },
  {
    name: 'Ongoing Project',
    image: '/assets/projects/ongoing-project.png',
    points: [
      'Active building coordination for lift, electrical and service access before final handover.',
      'Site-stage planning that respects concrete curing, shaft alignment and finishing sequence.',
      'Rooftop and power-service options prepared for future energy and backup requirements.',
      'Technical support path designed for commissioning, testing and post-installation maintenance.'
    ]
  }
]

const gallery = [
  { src: '/assets/projects/dream-korobi.png', alt: 'Dream Korobi building', caption: 'Dream Korobi' },
  { src: '/assets/projects/sopno-bilash.png', alt: 'Sopno Bilash building', caption: 'Sopno Bilash' },
  { src: '/assets/projects/kholifa-tower.png', alt: 'Kholifa Tower building', caption: 'Kholifa Tower' },
  { src: '/assets/gallery/ai-elevator-maintenance.png', alt: 'Elevator maintenance technicians', caption: 'Passenger lift service' },
  { src: '/assets/gallery/ai-rooftop-solar-bangladesh.png', alt: 'Bangladeshi technicians installing rooftop solar panels', caption: 'Rooftop solar' },
  { src: '/assets/gallery/ai-substation-bangladesh.png', alt: 'Bangladeshi electrical technicians inspecting a sub-station', caption: 'Sub-station solutions' },
  { src: '/assets/gallery/partnership-handshake.png', alt: 'Business partnership handshake', caption: 'Trusted partnerships' },
  { src: '/assets/projects/ongoing-project.png', alt: 'Ongoing project building', caption: 'Ongoing project' }
]

const team = [
  { name: 'MD. Mainul Haque Moin', role: 'Chairman', image: '/assets/team/mainul-haque-moin-chairman.png' },
  { name: 'MD. Lokman', role: 'Managing Director', image: '/assets/team/md-lokman-managing-director.png' },
  { name: 'Md. Morshed Alom', role: 'Director Marketing & Sales', image: '/assets/team/md-morshed-alom-director-marketing-sales.png' },
  { name: 'Mehedi Hasan Mohin', role: 'Director Marketing & Admin', image: '/assets/team/mehedi-hasan-mohin-director-marketing-admin.png' }
]

const faqs = [
  {
    question: 'Is Alaina Enterprise a Bangladesh lift company?',
    answer: 'Yes. Alaina Enterprise works as a Bangladesh lift company providing passenger lift sales, installation, modernization, maintenance and technical support for residential and commercial buildings.'
  },
  {
    question: 'Do you supply lift spare parts in Bangladesh?',
    answer: 'Alaina Enterprise supports lift spare parts supply, repair and maintenance requirements for passenger lifts, helping building owners keep elevator systems reliable and service-ready.'
  },
  {
    question: 'Is this also a construction and engineering support company?',
    answer: 'Yes. Alaina Enterprise supports construction company requirements with lift, electrical, generator, sub-station and related civil coordination for multistoried building projects in Bangladesh.'
  },
  {
    question: 'Does Alaina Enterprise provide rooftop solar solutions?',
    answer: 'Yes. Alaina Enterprise works as a rooftop solar company in Bangladesh, offering solar design, supply, installation, commissioning, maintenance and technical support.'
  },
  {
    question: 'What is the official website link for Alaina Enterprise?',
    answer: 'The website link is https://alainaenterprise.com. You can also use the contact section on this page for phone, email, address and map information.'
  }
]

const activeSlide = ref(0)
const selectedImage = ref(null)
const counters = ref({ leadership: 0, projects: 0 })
let timer
let observer
let countersStarted = false

const animateCounter = (key, target) => {
  const duration = 1300
  const start = performance.now()

  const tick = now => {
    const progress = Math.min((now - start) / duration, 1)
    counters.value[key] = Math.round(target * (1 - Math.pow(1 - progress, 3)))
    if (progress < 1) requestAnimationFrame(tick)
  }

  requestAnimationFrame(tick)
}

const startCounters = () => {
  if (countersStarted) return
  countersStarted = true
  animateCounter('leadership', 23)
  animateCounter('projects', 14)
}

onMounted(() => {
  timer = window.setInterval(() => {
    activeSlide.value = (activeSlide.value + 1) % heroSlides.length
  }, 5200)

  observer = new IntersectionObserver(
    entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible')
          if (entry.target.classList.contains('stat-grid')) startCounters()
        }
      })
    },
    { threshold: 0.16 }
  )

  document.querySelectorAll('.reveal').forEach((element, index) => {
    element.style.transitionDelay = `${Math.min(index * 55, 360)}ms`
    observer.observe(element)
  })
})

onUnmounted(() => {
  window.clearInterval(timer)
  if (observer) observer.disconnect()
})
</script>
