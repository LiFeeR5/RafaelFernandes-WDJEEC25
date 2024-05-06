<template>
    <div>
        <div class="carousel-arrow left" @click="$emit('prev')">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
                <path fill="#FFFFFF" d="M14.41 7.41L13 6l-6 6 6 6 1.41-1.41L10.83 12l3.58-3.59z" />
                <path d="M0 0h24v24H0z" fill="none"/>
            </svg>
        </div>
        <div class="carousel-arrow right" @click="$emit('next')">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
                <path fill="#FFFFFF" d="M10 6L8.59 7.41 13.17 12l-4.58 4.59L10 18l6-6z"/>
                <path d="M0 0h24v24H0z" fill="none"/>
            </svg>
        </div>
    </div>
</template>

<script>
export default {
    emits: ['prev', 'next']
}
</script>

<style scoped>
.carousel-arrow {
    position: absolute;
    top: calc(50% - 12px);
    width: 24px;
    height: 24px;
    background-color: #008adf83;
    border-radius: 50%;
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: background-color 0.3s;
}
.carousel-arrow:hover {
    background-color: #008ADF;
}
.left {
    left: 10px;
}
.right {
    right: 10px;
}
svg {
    fill: white;
}
</style>
