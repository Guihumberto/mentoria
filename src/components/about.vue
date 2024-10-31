<template>
    <section id="about">
        <div class="about-content">
            <h1>Sobre<span>Mim</span><span class="animate-section" style="--i:1"></span></h1>
            <div class="about-img">
                <img src="../assets/logo_novo.png" alt="imagem">
                <span class="circle-spin"></span>
                <span class="animate-section" style="--i:2"></span>
            </div>
            <div class="about-description">
                <h3>Mentoria <span class="animate-section" style="--i:3"></span></h3>
                <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Vero hic possimus earum quam laborum beatae impedit veritatis, esse nihil eos sequi recusandae, in maiores consequuntur, totam molestias quis! Odio, molestias?
                    <span class="animate-section" style="--i:4"></span>
                </p>
            </div>
            <div class="btn-box">
                <v-btn color="var(--second-color)">Saiba Mais <span class="animate-section" style="--i:5"></span></v-btn>
            </div>
        </div>
    </section>
</template>

<script setup>
</script>

<style lang="scss" scoped>
#about.show-animate .animate-section{
    animation: show-right 1s ease forwards;
    animation-delay: calc(.3s * var(--i)) ;
}
.animate-section{
    position: absolute;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: var(--main-color);
    z-index: 98;
}
.about-content{
    margin-top: 5rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 2rem;
}
.about-content h1{
    position: relative;
    font-size: 4rem;
    margin-bottom: 2rem;
    text-align: center;
}
.about-content h1 span{
    color: var(--second-color);
}
.about-content .about-img{
    position: relative;
    width: 23rem;
    height: 23rem;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center
}
.about-content .about-img img{
    position: absolute;
    width: 90%;
    border-radius: 50%;
    border: .2rem solid var(--second-color);

}
.about-content .about-img .circle-spin{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) rotate(0);
    width: 100%;
    height: 100%;
    border-radius: 50%;
    border-top: .2rem solid var(--main-color);
    border-left: .2rem solid var(--second-color);
    border-bottom: .2rem solid var(--main-color);
    border-right: .2rem solid var(--second-color);
    animation: aboutSpinner 8s linear infinite;
}
@keyframes aboutSpinner {
    100%{
        transform: translate(-50%, -50%) rotate(360deg);
    }
}
.about-content .about-description {
    text-align: center;
}
.about-content .about-description h3{
    position: relative;
    font-size: 2.6rem;
}
.about-content .about-description p {
    position: relative;
    font-size: 1.2rem;
    margin: 2rem 0 1rem;
}
</style>