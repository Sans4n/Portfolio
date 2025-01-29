<template>
    <div>
        <!-- Navbar with Scroll Effect -->
        <nav class="navbar navbar-expand-lg navbar-light sticky-top shadow-sm"
            :class="{ 'navbar-scrolled': isScrolled }">
            <div class="container">
                <a class="navbar-brand fw-bold" href="#">My Portfolio</a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
                    aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarNav">
                    <ul class="navbar-nav ms-auto">
                        <li class="nav-item">
                            <a class="nav-link" href="#about">About</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#projects">Projects</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#contact">Contact</a>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>

        <!-- Hero Section with Gradient Background -->
        <header class="text-bg-primary text-center py-5 position-relative">
            <h1 class="display-4 fw-bold animated fadeInUp">Welcome to My Portfolio</h1>
            <p class="lead animated fadeInUp">Showcasing my projects and skills</p>
        </header>

        <!-- Main Content -->
        <main class="container mb-5">
            <!-- About Section -->
            <section id="about" class="text-center mb-5">
                <h2 class="text-primary fw-bold mb-5 pt-5">About Me</h2>
                <div class="row">
                    <div class="col-md-4 text-center">
                        <img src="@/assets/img/Me.jpg" alt="Foto Kepala Sekolah" class="img-fluid rounded-4 mb-3">
                        <h3>Sansan nur azis</h3>
                        <p><em>Murid SMK Negeri 4 Tasikmalaya</em></p>
                    </div>
                    <div class="col-md-8 pt-4">
                        <p class="fs-5">Saya memiliki pengalaman sebagai junior web development selama 1,5 Tahun, dengan
                            fokus pada pengembangan aplikasi web menggunakan teknologi seperti HTML, CSS, JavaScript,
                            dan framework seperti Nuxt dan Vue.
                            Saya berhasil meningkatkan kinerja aplikasi web dan memperbaiki pengalaman pengguna melalui
                            desain antarmuka yang intuitif dan responsif.
                            Saya juga memiliki kemampuan dalam bekerja sama dengan tim dan berkomunikasi efektif dengan
                            klien untuk memenuhi kebutuhan mereka.</p>
                    </div>
                </div>
            </section>

            <!-- Projects Section -->
            <section id="projects" class="container text-bg-primary rounded-4 pb-5 mb-5">
                <h2 class="fw-bold mb-5 pt-5 text-center">Projects</h2>
                <div class="row justify-content-center">
                    <div class="col-md-4 mb-4" v-for="project in projects" :key="project.id">
                        <div class="card shadow-sm project-card">
                            <div class="card-img-wrapper">
                                <img :src="project.image" class="card-img-top" :alt="project.title" loading="lazy" />
                                <div class="card-overlay">
                                    <p class="card-text">{{ project.description }}</p>
                                    <a :href="project.link" class="btn btn-primary btn-sm">View Project</a>
                                </div>
                            </div>
                            <div class="card-body">
                                <h5 class="card-title fw-bold">{{ project.title }}</h5>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Contact Section -->
            <section id="contact" class="mb-5 pt-5 text-center">
                <h2 class="text-primary fw-bold mb-4">Contact</h2>
                <p class="fs-5">Feel free to reach out to me at <a href="mailto:sansannurazis@gmail.com"
                        class="text-decoration-none">sansannurazis@gmail.com</a></p>
                <div class="mt-4">
                    <a href="https://github.com/Sans4n" target="_blank" class="btn btn-outline-dark">
                        <i class="bi bi-github"></i> GitHub
                    </a>
                </div>

                <!-- Contact Form -->
                <form class="mt-5 w-50 mx-auto shadow-sm p-4 rounded" @submit.prevent="handleFormSubmit">
                    <div class="form-floating mb-3">
                        <input type="text" class="form-control" id="name" v-model="form.name"
                            placeholder="Enter your name" :class="{ 'is-invalid': formErrors.name }" required>
                        <label for="name">Name</label>
                        <div class="invalid-feedback">{{ formErrors.name }}</div>
                    </div>
                    <div class="form-floating mb-3">
                        <input type="email" class="form-control" id="email" v-model="form.email"
                            placeholder="Enter your email" :class="{ 'is-invalid': formErrors.email }" required>
                        <label for="email">Email</label>
                        <div class="invalid-feedback">{{ formErrors.email }}</div>
                    </div>
                    <div class="form-floating mb-3">
                        <textarea class="form-control" id="message" v-model="form.message" rows="4"
                            placeholder="Enter your message" :class="{ 'is-invalid': formErrors.message }"
                            required></textarea>
                        <label for="message">Message</label>
                        <div class="invalid-feedback">{{ formErrors.message }}</div>
                    </div>
                    <button type="submit" class="btn btn-primary w-100">Send Message</button>
                </form>
            </section>
        </main>

        <!-- Footer Section -->
        <footer class="bg-dark text-white text-center py-3">
            <div class="text-center">
                <p class="mb-0">&copy; 2025. My Portfolio. All rights reserved.</p>
                <p class="mb-0">Desain And Enginier by Sansan Nur Azis</p>
            </div>
            <a href="#"
                class="text-light bg-gradient text-decoration-none d-inline-flex align-items-center rounded-pill px-4 py-2 back-to-top shadow-lg">
                <i class="bi bi-arrow-up-circle-fill me-2"></i>
                Back to top
            </a>
        </footer>
    </div>
</template>

<script>
export default {
    data() {
        return {
            isScrolled: false,
            form: {
                name: '',
                email: '',
                message: ''
            },
            formErrors: {},
            projects: [
                { id: 1, title: 'Perpus Digital', description: 'A library management system for schools.', image: '/assets/Perpus-Digital.png', link: 'https://smkn4-web.netlify.app/' },
                { id: 2, title: 'Web Sekolah', description: 'An online platform for school administration.', image: '/assets/Sekolah.png', link: 'https://perpus-digital-zitech.vercel.app/' }
            ]
        };
    },
    mounted() {
        window.addEventListener('scroll', this.handleScroll);
    },
    methods: {
        handleScroll() {
            this.isScrolled = window.scrollY > 50;
        },
        validateForm() {
            const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            this.formErrors = {};
            if (!this.form.name) this.formErrors.name = 'Name is required';
            if (!this.form.email) this.formErrors.email = 'Email is required';
            else if (!emailPattern.test(this.form.email)) this.formErrors.email = 'Invalid email format';
            if (!this.form.message) this.formErrors.message = 'Message is required';
        },
        handleFormSubmit() {
            this.validateForm();
            if (!Object.keys(this.formErrors).length) {
                alert('Form submitted successfully!');
            }
        }
    }
};
</script>

<style scoped>
header {
    background: linear-gradient(45deg, #3a7bd5, #00d2ff);
    color: white;
    padding: 100px 0;
}

.navbar-scrolled {
    background-color: rgba(255, 255, 255, 0.9);
    transition: background-color 0.3s ease-in-out;
}

.pt-5 {
    margin-top: 5rem !important;
}

.pt-4 {
    margin-top: 10rem !important;
}

.project-card {
    transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out;
}

.project-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.card-img-wrapper {
    position: relative;
}

.card-overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.6);
    color: white;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    opacity: 0;
    transition: opacity 0.3s ease-in-out;
}

.card-img-wrapper:hover .card-overlay {
    opacity: 1;
}

.back-to-top {
    background: linear-gradient(45deg, #ff6a00, #ee0979);
    transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out;
    color: white !important;
    font-weight: bold;
}

.back-to-top:hover {
    transform: scale(1.1);
    box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.3);
    text-decoration: none;
}
</style>
