<template>
    <div class="header" :class="isScrolled ? 'headercolor':''">
        <div class="sub-header">
            <h1 class="logo">
                <v-icon>mdi-alpha-h-circle</v-icon>
                <span>Humberto</span>
                <span class="animate" style="--i:1"></span>
            </h1>
            <nav class="navbar">
                <ul>
                    <li v-for="list, l, in list_menu" :key="l"> 
                        <a :class="list.url == idNameActiveSelect ? 'active':''"  @click="scroll(list.url)">{{ list.name }}</a>
                    </li>
                    <span class="animate" style="--i:2"></span>
                </ul>
            </nav>
            <v-btn variant="flat" class="plans text-capitalize" color="#42c1e8">
                Planos
                <span class="animate" style="--i:3"></span>
            </v-btn>
            <v-btn class="mobile-btn-side-bar" color="white" variant="text" @click="side_bar = !side_bar" :icon="side_bar ? 'mdi-close' : 'mdi-menu'">
            </v-btn>
        </div>
        <div class="mobile_menu" v-if="side_bar">
            <ul>
                <li v-for="item, i in list_menu" :key="i"> 
                    <a :class="item.url == idNameActiveSelect ? 'active':''"  @click="scroll(item.url)">{{ item.name }} </a>
                </li>
            </ul>
            <v-btn variant="flat" color="#42c1e8">
                Planos
            </v-btn>
        </div>
    </div>
</template>

<script setup>
    import { ref, onMounted, onUnmounted } from 'vue'

    const side_bar = ref(false)
    const isScrolled = ref(false)

    const list_menu = [
        {name: 'Início', icon: 'mdi-home', url: 'home'},
        {name: 'Planos', icon: 'mdi-home', url: 'plan'},
        {name: 'Avaliações', icon: 'mdi-home', url: 'avaliations'},
        {name: 'Sobre', icon: 'mdi-home', url: 'about'}
    ]

    const handleScroll = () => {
        isScrolled.value = window.scrollY > 0
    }

    const idNameActiveSelect = ref('home')

    const scroll = (refName) => {
        const element = document.getElementById(refName)
        element.scrollIntoView({behavior: "smooth"})
        idNameActiveSelect.value = refName
        side_bar.value = false
    }

   

    const escutar = () => {
        const sections = document.querySelectorAll('section')
        window.onscroll = () => {
            sections.forEach(sec => {
                let top = window.scrollY
                let offset = sec.offsetTop - 100
                let heigth = sec.offsetHeight
                let id = sec.getAttribute('id')
    
                if(top >= offset && top < offset + heigth) {
                  sec.classList.add('show-animate')
                  switchActiveId(id)
                } else {
                  sec.classList.remove('show-animate')
                }
            })
        }
    }

    const switchActiveId = (value) => {
        switch(value) {
        case 'home':
            idNameActiveSelect.value = 'home'
            break;
        case 'about':
            idNameActiveSelect.value = 'about'
            break;
        case 'avaliations':
            idNameActiveSelect.value = 'avaliations'
            break;
        case 'plan':
            idNameActiveSelect.value = 'plan'
            break;
        default:
            idNameActiveSelect.value = ''
        }
    }


    onMounted(() => {
        window.addEventListener('scroll', handleScroll)
        window.addEventListener('scroll', escutar)
    })

    onUnmounted(() => {
        window.removeEventListener('scroll', handleScroll)
        window.removeEventListener('scroll', escutar)
    })

</script>

<style lang="scss" scoped>
.header{
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100px;
    border-bottom: 1px solid var(--main-color) ;
    display: flex;
    justify-content: center;
    align-items: center;
    background: transparent;
    z-index: 100;
}

.headercolor{
    background: var(--main-color);
    border-bottom: 1px solid white ;
    transition: 1s;
}

.sub-header{
    width: min(1080px, 100%);
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 1rem;
}
.logo{
    position: relative;
    font-size: 1.5rem;
    font-weight: 600;
    color: white;
    display: flex;
    align-items: center;
}
.navbar ul{
    position: relative;
    display: flex;
    gap: 2rem;
    list-style: none;
}
.navbar ul li a {
    text-decoration: none;
    font-size: 1.2rem;
    color: white;
    font-weight: 500;
    transition: .5s;
    cursor: pointer;
}
.navbar ul li a:hover, .navbar ul li a.active, .mobile_menu ul li a.active{
    color: var(--second-color)
}
.mobile-btn-side-bar, .mobile_menu{
    display: none;
}
.mobile_menu ul{
    display: flex;
    flex-direction: column;
    align-items: center;
    font-weight: 700;
    gap: 1rem;
    list-style: none;
}
@media (max-width: 800px) {
    .header{
        height: 70px;
    }
    .logo{
        font-size: 1.5rem;
    }
    .navbar, .plans {
        display: none;
    }
    .mobile-btn-side-bar{
        display: block;
    }
    .mobile_menu{
        position: fixed;
        top: 4rem;
        display: flex;
        justify-content: center;
        flex-direction: column;
        gap: 1rem;
        background: var(--main-color);
        width: 100%;
        min-height: 20vh;
        padding: 2rem;
        color: white;
        transition: 1s;
        animation: appear .3s ease-in forwards;
        opacity: 0;
    }

}

@keyframes appear {
    from{
        opacity: 0;
        translate: 100px;
    }
    to{
        opacity: 1;
    }
}

</style>