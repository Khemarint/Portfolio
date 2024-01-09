<template>
    <div class="container">
        <svg x="0px" y="0px" viewBox="0 0 1080 1080" style="enable-background:new 0 0 1080 1080;" xml:space="preserve">
                <g id="logo">
                    <rect class="st0" width="1080" height="1080"/>
                    <g>
                        <g>
                            <path class="st1" d="M539.76,170.63c-71.88,41.22-143.75,82.44-215.63,123.65c0,83.97,0,167.94,0,251.91     c22.14,12.6,44.28,25.2,66.43,37.81c0-35.77,0-71.53,0-107.3c18.97-10.99,37.95-21.98,56.92-32.97c0,58.21,0,116.42,0,174.63     c21.74,12.29,43.47,24.58,65.21,36.87c0-83.2,0-166.4,0-249.6c72.13-41.52,144.26-83.04,216.39-124.55     C665.97,244.26,602.87,207.44,539.76,170.63z M390.64,399.12c-0.11-22.17-0.22-44.35-0.32-66.52     c49.87-28.23,99.73-56.46,149.6-84.7c17.85,10.6,35.7,21.2,53.54,31.8C525.85,319.51,458.25,359.32,390.64,399.12z"/>
                            <path class="st1" d="M568.37,437.96v310.38l67.14-35.47v-98.39l120.35-68.83V329.43L568.37,437.96z M688.58,506.94l-51.35,29.65     v-60.58l51.35-30.51C688.58,446.14,688.58,506.94,688.58,506.94z"/>
                        </g>
                    </g>
                </g>
                </svg>
    </div>
</template>

<script>
import { gsap } from "gsap";

export default {
  name: "AnimatedSVG",
  mounted() {
    gsap.timeline({defaults: {ease: 'power4.out', duration: .7 }})

    let paths = this.$el.querySelectorAll('path');
    paths.forEach(path => {
        path.addEventListener('animationend', () => {
            // Animation has ended, navigate to the home page
            setTimeout(this.revealNewPage, 4000); // Increase delay to 4 seconds
        });
    });
  },
  methods: {
    revealNewPage() {
        // Navigate to the home page
        this.$router.push('/');
    }
  }
}
</script>

    
<style scoped>


.st0{display:none;fill:#0C1421;}
.st1{fill:#FFDB70;}

.container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

/* g {
    overflow: hidden;
    visibility: hidden;
} */
svg{
    width: 50vw;
    overflow: visible;
}
@keyframes fadeInFromTop {
    0% {
        opacity: 0;
        transform: translateY(-20px);
    }
    100% {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes fadeInFromBottom {
    0% {
        opacity: 0;
        transform: translateY(20px);
    }
    100% {
        opacity: 1;
        transform: translateY(0);
    }
}
@keyframes shine {
    0% {
        background-position: -100%;
    }
    50%, 100% {
        background-position: 200%;
    }
}

.shine {
    background: linear-gradient(90deg, rgba(255,255,255,0) 0%, rgba(255,255,255,0.5) 50%, rgba(255,255,255,0) 100%);
    background-size: 200% auto;
    animation: shine 4s linear 2s infinite; /* Add 2s delay */
}

@keyframes fadeOut {
    0% {
        opacity: 1;
    }
    80% { /* Stop shine effect at 80% of the fade-out animation */
        background-position: 200%;
    }
    100% {
        opacity: 0;
    }
}

path {
    animation: fadeOut 6s ease-in-out forwards; /* Increase duration to 6s */
}


path:first-child {
    animation: fadeInFromTop 4s ease-in-out;
}

path:last-child {
    animation: fadeInFromBottom 4s ease-in-out;
}

/* Media query for mobile screens */
@media (max-width: 600px) {
    svg {
        width: 80vw; /* Increase the size of the SVG on mobile screens */
    }
}
</style>