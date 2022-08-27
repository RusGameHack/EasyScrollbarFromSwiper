# EasyScrollbarFromSwiper

После того, как построите верстку свайпера, нужно добавить блок таймера и настроить его скрипт:

    '<div class="swiper mySwiper">
        <div class="swiper-wrapper">
            <div class="swiper-slide">1</div>
            <div class="swiper-slide">2</div>
            <div class="swiper-slide">3</div>
            <div class="swiper-slide">4</div>
            <div class="swiper-slide">5</div>
        </div>
        <div class="swiper-pagination"></div>
        <div class="timer-swiper"><div class="timer-swiperAfter"></div></div>//Необходимый блок свайпера
    </div>'

var swiper = new Swiper(".mySwiper", {
    direction: "horizontal",
    slidesPerView: 1,
    spaceBetween: 30,
    loop: true,
    autoplay: {
        delay: 5000,
        disableOnInteraction: false,
    },
    on: {
        slideChange: ()=> { //Нас интересует именно этот метод. Здесь мы либо добавляем, либо удаляем класс 'active', который в основном и твоит волшебство. 
            document.querySelector('.timer-swiperAfter').classList.remove('active');
            setTimeout(() => {
                document.querySelector('.timer-swiperAfter').classList.add('active');
            }, 50);
        },
    },
    pagination: {
      el: ".swiper-pagination",
      clickable: true
    }
});

//CSS
.timer-swiper{
    position: absolute;
    bottom: 0;
    right: 0;
    width: 100%;
    height: 10px;
    background: white;
    z-index: 2;
}
.timer-swiperAfter{
    background: #007aff;
    height: 100%;
    width: 0;
    height: 10px;
    display: block;
}
.timer-swiperAfter.active{
    width: 100%;
    transition: 5s all;
}
