<template>
    <footer>
        <a target="__blank" class="socialLink" v-for="(socialLink, index) in socialLinks" :key="index" :href="socialLink.link">
            <img :alt="socialLink.label" :title="socialLink.title" :src="socialLink.icon">
        </a>
    </footer>
</template>


<script>
import api from '@/services/api.js';

export default {
    name: 'Footer',
    data() {
        return {
            socialLinks:[]
        }
    },
    mounted(){
        api.get('/social-links.json').then(response => {
            // console.log(response.data);
            this.socialLinks = response.data;
        });
    }
}
</script>

<style scoped>
footer {
    width: 100%;
    height: 60px;
    background-color: var(--color-background-nav);
    display: flex;
    justify-content: center;
    align-items: center;
}

.socialLink {
    border: 2px solid var(--color-text-light);
    align-items: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    margin: 0 5px;

}

.socialLink img{
    width: 20px;
}

</style>