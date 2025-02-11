<template>
    <div class="min-h-screen flex flex-col items-center justify-center bg-gray-900 text-white">
        <!-- Hero Section -->
        <div class="text-center">
            <h1 class="text-5xl font-extrabold mb-4 animate-slide-left">
                Welcome to <span class="text-blue-400">My Vue Page</span>
            </h1>
            <p class="text-lg text-gray-300 max-w-xl mx-auto">
                This is a beautiful Vue.js page with smooth animations and a modern design.
            </p>
        </div>

        <!-- Call to Action Button -->
        <div class="mt-8">
            <button 
                class="px-6 py-3 bg-blue-500 hover:bg-blue-600 text-white font-semibold text-lg rounded-lg shadow-lg transition-transform transform hover:scale-105 animate-bounce">
                Get Started
            </button>
        </div>

        <!-- Features Section -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mt-16 max-w-4xl">
            <div 
                v-for="(feature, index) in features" 
                :key="index" 
                class="p-6 bg-gray-800 rounded-xl shadow-lg transition-transform transform hover:scale-105"
                :style="{ color: feature.color }"
            >
                <h2 class="text-2xl font-semibold">{{ feature.title }}</h2>
                <p class="text-gray-300 mt-2">{{ feature.description }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "ExampleComponent",
    data() {
        return {
            features: [
                { title: "Fast & Responsive", description: "Optimized for speed and smooth interactions.", color: "#3b82f6" },
                { title: "Beautiful UI", description: "A clean and modern interface built with Tailwind.", color: "#10b981" },
                { title: "Smooth Animations", description: "Subtle effects that enhance the user experience.", color: "#facc15" }
            ],
            colors: ["#3b82f6", "#10b981", "#facc15", "#ef4444", "#a855f7"] // Different colors
        };
    },
    mounted() {
        this.startColorChange();
    },
    methods: {
        startColorChange() {
            setInterval(() => {
                this.features.forEach((feature) => {
                    feature.color = this.colors[Math.floor(Math.random() * this.colors.length)];
                });
            }, 5000); // Change color every 5 seconds
        }
    }
};
</script>

<style>
/* Slide-in from Left Animation */
@keyframes slideLeft {
    from {
        transform: translateX(-50px);
        opacity: 0;
    }
    to {
        transform: translateX(0);
        opacity: 1;
    }
}

.animate-slide-left {
    animation: slideLeft 1.5s ease-out;
}

/* Bounce Button Animation */
@keyframes bounce {
    0%, 100% {
        transform: translateY(0);
    }
    50% {
        transform: translateY(-8px);
    }
}

.animate-bounce {
    animation: bounce 1s infinite;
}
</style>
