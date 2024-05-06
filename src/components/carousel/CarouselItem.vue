<template>
    <transition :name = "transitionEffect">
        <div class="carousel-item" v-show="currentSlide === index" @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave">
            <img v-if="slide.image" :src="slide.image" :alt="slide.alt" class="carousel-image"/>
            <div class="carousel-text" v-if="slide.title || slide.description" @mouseover="handleTextMouseEnter" @mouseleave="handleTextMouseLeave">
                <h3 v-if="slide.title">{{ slide.title }}</h3>
                <p v-if="slide.description">{{ slide.description }}</p>
            </div>
            <div v-if="index === 1" @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave"> 
                <p @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave" style="font-size: 30px; font-weight: bold; color: #bc0505; cursor: auto; user-select: none;">Escolha uma data</p>
            <div class="date-input">
                <input type="date" :value="selectedDate" class="date-input" :date-format="dateFormat" @change="updateSelectedDate($event.target.value)">
            </div>
            </div>
            <div v-if="index===2" @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave" class="flex-container">
                <div @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave" class="flex-content">
                    <p @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave" style="font-size: 40px; font-weight: bold;">Integration of Wind Farms into Electicity Grids</p>
                    <p @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave" style="font-size: 25px; font-weight: bold;">Workshop <br> by Vestas</p>
                    <p @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave" style="font-size: 20px;">This workshop will cover the representation of wind farms in simulation software, with an emphasis on wind turbine design and electrical performance for compliance with grid requirements.</p>   
                </div>
            </div>
        </div>
    </transition>
</template>

<script>
export default {
    emits: ['mouseenter', 'mouseleave', 'selectedDateChange'],
    props: ["slide", "currentSlide", "index", "direction", "selectedDate"],
    data() {
        return {
            isTextHovered: false,
            selectedDate: null,
            dateFormat: 'dd/MM/yyyy'
        };
    },
    computed: {
        transitionEffect () {
            return this.direction === "right" ? "slide-out" : "slide-in";
        }
    },
    methods: {
        handleMouseEnter() {
            if (!this.isTextHovered) {
                this.$emit('mouseenter');
            }
        },
        handleMouseLeave() {
            if (!this.isTextHovered) {
                this.$emit('mouseleave');
            }
        },
        handleTextMouseEnter() {
            this.isTextHovered = true;
            this.$emit('mouseenter');
        },
        handleTextMouseLeave() {
            this.isTextHovered = false;
            this.$emit('mouseleave');
        },
        updateSelectedDate(date) {
            this.selectedDate = date;
            this.$emit('selectedDateChange', date);
        }
    }
};
</script>

<style scoped>
.carousel-item {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background: #ffa8519d;
}
.carousel-image {
    width: 100%;   
}
.carousel-text {
    text-align: center;
    color: #bc0505;
    position: absolute;
    cursor: auto;
}
.carousel-text h3 {
    margin: 0;
    font-size: 50px;
    user-select: none;
}
.carousel-text p {
    margin: 0;
    font-size: 16px;
    user-select: none;
}
.slide-in-enter-active,
.slide-in-leave-active,
.slide-out-enter-active,
.slide-out-leave-active
{
    transition: all 1s ease-in-out;
}
.slide-in-enter-from {
    transform: translateX(-100%);
}
.slide-in-leave-to{
    transform: translateX(100%);
}
.slide-out-enter-from {
    transform: translateX(100%);
}
.slide-out-leave-to{
    transform: translateX(-100%);
}
.flex-container {
    display: flex;
    flex-direction: column;
    align-items: left;
    justify-content: space-around;
    height: 90%;
    width: 90%;
    max-width: 800px;
    max-height: 300px;
    color: #bc0505;
    background-color: #ff952b9d;
    border-radius: 20px;
}
.flex-content {
    padding: 0px;
    text-align: left;
    margin-left: 20px;
    margin-right: 20px;
    margin-top: -30px;
}
.date-input {
    justify-content: center;
    margin-top: -10px;
    display: flex;
}

</style>