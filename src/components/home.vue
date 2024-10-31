<template>
    <section id="home">
        <span class="animate bg"></span>
        <!-- <span class="animate-section" style="--i:i"></span> -->
        <div class="cta">
            <h1>Mentoria para concursos<span class="animate" style="--i:4"></span></h1>
            <h1 class="title">Estudo acompanhado com <span class="animate" style="--i:5"></span></h1>
            <h1> João <span>Humberto</span> <span class="animate" style="--i:6"></span></h1>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Modi cumque esse, illum, consequuntur assumenda veniam ad 
                eligendi aliquam mollitia dolorum quo qui nemo eaque possimus quibusdam harum magni deserunt dicta?
                <span class="animate" style="--i:7"></span>
            </p>
            <div class="cta-btns">
                <v-btn color="#42c1e8" variant="flat"> Contato</v-btn>
                <v-btn class="btn" variant="flat">Plano</v-btn>
                <span class="animate" style="--i:8"></span>
            </div>
            <div class="social-media">
                <v-btn variant="flat" icon="mdi-instagram"></v-btn>
                <v-btn variant="flat" icon="mdi-whatsapp"></v-btn>
                <v-btn variant="flat" icon="mdi-facebook"></v-btn>
                <span class="animate" style="--i:9"></span>
            </div>
        </div>
    </section>
</template>

<script setup>
</script>

<style lang="scss" scoped>
#home.show-animate .animate-section{
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
#home{
    position: relative;
    display: flex;
    align-items: center;
    padding: 50px 2% 0;
    background: url('../assets/logo_tres.png') no-repeat;
    background-size: 700px;
    background-position: 440px;
}
.cta{
    position: relative;
    max-width: 630px;
}
.cta h1{
    font-size: 2.8rem;
    line-height: 1.2;
    position: relative;
}
.cta h1:nth-child(3){
    background: linear-gradient(#59ffff, #1952ab);
    -webkit-background-clip: text;
    color: transparent;
}
.cta p {
    position: relative;
    font-size: 1rem;
    margin: 25px 0 30px;
}
.cta .cta-btns {
    position: relative;
    display: flex;
    justify-content: flex-start;
    gap: 1rem;
    margin-bottom: 2rem;
}
.btn{
    background: transparent;
    border: 2px solid var(--second-color);
    border-radius: 6px;
    color: var(--second-color);
    letter-spacing: 1px;
    transition: .5s;
}
.btn:hover{
    background: var(--second-color);
    color: #01003f;
}
.cta .social-media{
    position: relative;
    display: flex;
    gap: 1rem;
}

@media (max-width: 800px) {
    #home{
        flex-direction: column-reverse;
        justify-content: center;
        align-items: center;
        background: url('../assets/logo_tres.png') no-repeat;
        background-size: 300px;
        background-position: 200px 400px;
    }
}
</style>