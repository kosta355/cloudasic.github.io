<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>@cloudasic</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: Arial, Helvetica, sans-serif;
            background: #070707;
            color: #ffffff;
            overflow-x: hidden;
        }

        /* ФОНОВОЕ СВЕЧЕНИЕ */

        .glow {
            position: fixed;
            width: 500px;
            height: 500px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.06);
            filter: blur(120px);
            pointer-events: none;
            z-index: -1;
            animation: moveGlow 12s ease-in-out infinite alternate;
        }

        .glow-one {
            top: -150px;
            left: -150px;
        }

        .glow-two {
            right: -200px;
            top: 40%;
            background: rgba(180, 180, 180, 0.05);
            animation-delay: -5s;
        }

        .glow-three {
            left: 20%;
            bottom: -250px;
            background: rgba(255, 255, 255, 0.04);
            animation-delay: -8s;
        }

        @keyframes moveGlow {
            0% {
                transform: translate(0, 0) scale(1);
            }

            100% {
                transform: translate(120px, 80px) scale(1.3);
            }
        }


        /* ГЛАВНЫЙ ЭКРАН */

        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
            padding: 30px 20px;

            background:
                radial-gradient(
                    circle at 50% 35%,
                    #202020 0%,
                    #101010 38%,
                    #070707 75%
                );
        }

        .hero::after {
            content: "";
            position: absolute;
            width: 700px;
            height: 700px;
            border-radius: 50%;
            border: 1px solid rgba(255,255,255,0.03);
            animation: pulseCircle 5s ease-in-out infinite;
        }

        @keyframes pulseCircle {
            0%, 100% {
                transform: scale(0.9);
                opacity: 0.4;
            }

            50% {
                transform: scale(1.1);
                opacity: 1;
            }
        }

        .hero-content {
            position: relative;
            z-index: 2;
            animation: heroAppear 1.2s ease forwards;
        }

        @keyframes heroAppear {
            from {
                opacity: 0;
                transform: translateY(30px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }


        /* АВАТАР */

        .avatar-wrapper {
            width: 190px;
            height: 190px;
            margin: auto;
            position: relative;
        }

        .avatar-wrapper::before {
            content: "";
            position: absolute;
            inset: -12px;
            border-radius: 50%;
            background: conic-gradient(
                from 0deg,
                transparent,
                rgba(255,255,255,0.8),
                transparent,
                rgba(255,255,255,0.2),
                transparent
            );
            animation: rotateGlow 8s linear infinite;
            filter: blur(3px);
        }

        @keyframes rotateGlow {
            to {
                transform: rotate(360deg);
            }
        }

        .avatar {
            position: relative;
            width: 190px;
            height: 190px;
            border-radius: 50%;
            object-fit: cover;
            z-index: 2;

            border: 4px solid #181818;

            box-shadow:
                0 0 30px rgba(255,255,255,0.12),
                0 0 80px rgba(255,255,255,0.05),
                0 25px 60px rgba(0,0,0,0.9);
        }


        /* ТЕКСТ */

        .nickname {
            font-size: 52px;
            margin-top: 30px;
            letter-spacing: -2px;
        }

        .subtitle {
            margin-top: 13px;
            color: #8d8d8d;
            font-size: 16px;
        }

        .roles {
            margin-top: 24px;
            display: flex;
            justify-content: center;
            gap: 10px;
            flex-wrap: wrap;
        }

        .role {
            padding: 9px 16px;
            border-radius: 50px;
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.08);
            color: #bdbdbd;
            font-size: 13px;
            transition: 0.3s ease;
        }

        .role:hover {
            background: rgba(255,255,255,0.1);
            transform: translateY(-3px);
        }


        /* ОБЩИЕ СЕКЦИИ */

        section {
            position: relative;
        }

        .container {
            max-width: 800px;
            margin: auto;
        }

        .section-label {
            font-size: 12px;
            letter-spacing: 4px;
            color: #666;
            text-transform: uppercase;
            margin-bottom: 15px;
        }

        .title {
            font-size: 42px;
            letter-spacing: -1.5px;
            margin-bottom: 28px;
        }


        /* ОБО МНЕ */

        .about {
            padding: 130px 20px;
            background: linear-gradient(180deg, #101010, #141414);
        }

        .description {
            color: #a0a0a0;
            font-size: 18px;
            line-height: 1.9;
            max-width: 700px;
        }


        /* ССЫЛКИ */

        .links-section {
            padding: 130px 20px;
            background: #0a0a0a;
        }

        .links-grid {
            display: flex;
            flex-direction: column;
            gap: 17px;
            margin-top: 45px;
        }

        .link-card {
            position: relative;
            overflow: hidden;

            text-decoration: none;
            color: white;

            display: flex;
            align-items: center;
            justify-content: space-between;

            padding: 24px 26px;
            border-radius: 22px;

            background: #141414;
            border: 1px solid rgba(255,255,255,0.07);

            transition: 0.3s ease;
        }

        .link-card::before {
            content: "";
            position: absolute;
            width: 150px;
            height: 150px;

            background: rgba(255,255,255,0.07);
            filter: blur(50px);
            border-radius: 50%;

            right: -80px;
            top: -80px;

            opacity: 0;
            transition: 0.4s ease;
        }

        .link-card:hover::before {
            opacity: 1;
        }

        .link-card:hover {
            transform: translateY(-5px);
            border-color: rgba(255,255,255,0.2);

            box-shadow:
                0 15px 50px rgba(0,0,0,0.4),
                0 0 40px rgba(255,255,255,0.03);
        }

        .link-main {
            display: flex;
            align-items: center;
            gap: 18px;
            position: relative;
            z-index: 2;
        }

        .link-icon {
            width: 52px;
            height: 52px;

            display: flex;
            align-items: center;
            justify-content: center;

            background: #222;
            border: 1px solid rgba(255,255,255,0.06);

            border-radius: 17px;
            font-size: 22px;
        }

        .link-title {
            font-size: 17px;
            font-weight: 600;
        }

        .link-url {
            margin-top: 6px;
            color: #6f6f6f;
            font-size: 14px;
        }

        .arrow {
            color: #777;
            font-size: 25px;
            position: relative;
            z-index: 2;
            transition: 0.3s ease;
        }

        .link-card:hover .arrow {
            transform: translateX(7px);
            color: white;
        }


        /* ФУТЕР */

        footer {
            padding: 55px 20px;
            text-align: center;
            background: #060606;
            color: #555;
            font-size: 14px;
        }

        footer strong {
            color: #aaa;
            font-weight: 500;
        }


        /* АНИМАЦИЯ ПРИ ПРОКРУТКЕ */

        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition:
                opacity 0.8s ease,
                transform 0.8s ease;
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }


        /* ТЕЛЕФОН */

        @media (max-width: 600px) {

            .avatar-wrapper,
            .avatar {
                width: 155px;
                height: 155px;
            }

            .nickname {
                font-size: 40px;
            }

            .title {
                font-size: 32px;
            }

            .about,
            .links-section {
                padding: 90px 20px;
            }

            .description {
                font-size: 16px;
            }

            .link-card {
                padding: 19px;
            }

            .link-icon {
                width: 47px;
                height: 47px;
            }
        }
    </style>
</head>

<body>

    <!-- ДВИЖУЩЕЕСЯ СВЕЧЕНИЕ -->
    <div class="glow glow-one"></div>
    <div class="glow glow-two"></div>
    <div class="glow glow-three"></div>


    <!-- ГЛАВНЫЙ ЭКРАН -->

    <section class="hero">

        <div class="hero-content">

            <div class="avatar-wrapper">
                <img
                    src="https://cdn.phototourl.com/free/2026-09-02-c8ef6374-2958-48b2-a3fd-65d1c1770aad.jpg"
                    alt="@cloudasic"
                    class="avatar"
                >
            </div>

            <h1 class="nickname">@cloudasic</h1>

            <p class="subtitle">
                Digital · NFT · Technology
            </p>

            <div class="roles">
                <div class="role">NFT Trader</div>
                <div class="role">Программист</div>
            </div>

        </div>

    </section>


    <!-- ОБО МНЕ -->

    <section class="about">

        <div class="container reveal">

            <div class="section-label">
                Information
            </div>

            <h2 class="title">
                Немного обо мне
            </h2>

            <p class="description">
                Занимаюсь NFT, торговлей и проектами в Telegram.
                Слежу за цифровыми активами, интересными коллекциями
                и новыми возможностями в этой сфере.
                По специальности я программист и также интересуюсь
                технологиями, разработкой и созданием собственных проектов.
            </p>

        </div>

    </section>


    <!-- ССЫЛКИ -->

    <section class="links-section">

        <div class="container reveal">

            <div class="section-label">
                Links
            </div>

            <h2 class="title">
                Мои источники
            </h2>

            <div class="links-grid">

                <a
                    href="https://t.me/loffi_NFT"
                    target="_blank"
                    class="link-card"
                >

                    <div class="link-main">

                        <div class="link-icon">✈</div>

                        <div>
                            <div class="link-title">
                                NFT Telegram канал
                            </div>

                            <div class="link-url">
                                t.me/loffi_NFT
                            </div>
                        </div>

                    </div>

                    <div class="arrow">→</div>

                </a>


                <a
                    href="https://t.me/cloudasic"
                    target="_blank"
                    class="link-card"
                >

                    <div class="link-main">

                        <div class="link-icon">@</div>

                        <div>
                            <div class="link-title">
                                Мой Telegram
                            </div>

                            <div class="link-url">
                                @cloudasic
                            </div>
                        </div>

                    </div>

                    <div class="arrow">→</div>

                </a>

            </div>

        </div>

    </section>


    <footer>
        <strong>@cloudasic</strong>
        <br><br>
        NFT · Programming · Digital
    </footer>


    <script>
        const reveals = document.querySelectorAll(".reveal");

        function revealElements() {
            reveals.forEach(element => {
                const windowHeight = window.innerHeight;
                const elementTop =
                    element.getBoundingClientRect().top;

                if (elementTop < windowHeight - 100) {
                    element.classList.add("active");
                }
            });
        }

        window.addEventListener("scroll", revealElements);

        revealElements();
    </script>

</body>
</html>
