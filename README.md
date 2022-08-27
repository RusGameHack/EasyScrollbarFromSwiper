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

var swiper = new Swiper(".mySwiper", {<br>
    direction: "horizontal",<br>
    slidesPerView: 1,<br>
    spaceBetween: 30,<br>
    loop: true,<br>
    autoplay: {</div><br>
        delay: 5000,<br>
        disableOnInteraction: false,<br>
    },<br>
    on: {<br>
        slideChange: ()=> { //Нас интересует именно этот метод. Здесь мы либо добавляем, либо удаляем класс 'active', который в основном и твоит волшебство. <br>
            document.querySelector('.timer-swiperAfter').classList.remove('active');<br>
            setTimeout(() => {<br>
                document.querySelector('.timer-swiperAfter').classList.add('active');<br>
            }, 50);<br>
        },<br>
    },<br>
    pagination: {<br>
      el: ".swiper-pagination",<br>
      clickable: true<br>
    }<br>
});<br>

<br>//CSS
<br>.timer-swiper{
    <br>position: absolute;
    <br>bottom: 0;
    <br>right: 0;
    <br>width: 100%;
    <br>height: 10px;
    <br>background: white;
    <br>z-index: 2;
<br>}
<br>.timer-swiperAfter{
    <br>background: #007aff;
    <br>height: 100%;
    <br>width: 0;
    <br>height: 10px;
    <br>display: block;
<br>}
<br>.timer-swiperAfter.active{
    <br>width: 100%;
    <br>transition: 5s all;
<br>}
