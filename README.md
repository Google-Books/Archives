<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Google Books - Premium Laser Portal</title>
    <style>
        /* =============================================================
           ۱. متغیرهای رنگی پیشرفته لیزری مچ شده با تصویر ارسالی شما
           ============================================================= */
        :root {
            --bg-dark-premium: #0d1326;   /* رنگ دقیق پس‌زمینه تیره و لوکس پوسته تصویر */
            --row-bg: rgba(255, 255, 255, 0.02); /* پس‌زمینه شیشه‌ای فوق‌العاده ملایم ردیف‌ها */
            --laser-glow-color: rgba(139, 92, 246, 0.25); /* هاله نئونی لیزری بنفش-فیروزه‌ای */
            --text-gray-muted: #7f92a5;   /* خاکستری ملایم برای توضیحات ارشیوها */
            --transition-smooth: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
            
            /* متغیرهای اضافه شده برای چوکات لیزری */
            --laser-blue: #00f0ff;
            --btn-blue: #2481cc;
            --btn-shadow: rgba(11, 44, 71, 0.95);
        }

        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', system-ui, sans-serif; }

        body {
            background-color: var(--bg-dark-premium); color: #ffffff; display: flex; flex-direction: column;
            align-items: center; justify-content: flex-start; min-height: 100vh; padding: 60px 24px;
            overflow-x: hidden; -webkit-font-smoothing: antialiased;
        }

        /* =============================================================
           ۲. ساختار هدر و عنوان اصلی صفحه
           ============================================================= */
        .header-container { width: 100%; max-width: 900px; margin-bottom: 20px; }
        
        .back-btn {
            display: inline-flex; align-items: center; color: #ffffff; text-decoration: none;
            font-size: 16px; font-weight: 600; margin-bottom: 35px; transition: var(--transition-smooth);
        }
        .back-btn:hover { transform: translateX(-4px); color: #00f0ff; }

        .main-title { 
            font-size: 2.4rem; font-weight: 900; text-align: center; line-height: 1.35; letter-spacing: -0.5px;
            background: linear-gradient(180deg, #ffffff 0%, #b0c4de 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            text-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
        }

        /* =============================================================
           استایل‌های بخش چوکات لیزری مایع (اضافه شده)
           ============================================================= */
        .premium-request-container {
            width: 100%;
            max-width: 900px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 24px;
            margin-bottom: 50px;
            perspective: 1000px;
        }
        .laser-chokat {
            width: 100%;
            min-height: 140px;
            background: linear-gradient(270deg, #111c24, #192d3d, #111c24);
            background-size: 400% 400%;
            animation: gradientFluid 12s ease infinite;
            border: 2px solid rgba(0, 240, 255, 0.3);
            border-radius: 24px;
            position: relative;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 30px 24px;
            text-align: center;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.4), 0 0 25px rgba(0, 240, 255, 0.15);
            transform: rotateX(6deg);
            transition: var(--transition-smooth);
        }
        .laser-chokat:hover {
            transform: rotateX(2deg) translateY(-2px);
            border-color: rgba(0, 240, 255, 0.5);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.5), 0 0 35px rgba(0, 240, 255, 0.3);
        }
        @keyframes gradientFluid {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        .laser-shapes-layer {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            pointer-events: none;
            overflow: hidden;
            z-index: 1;
        }
        .laser-svg {
            position: absolute;
            stroke: var(--laser-blue);
            stroke-width: 1.2;
            fill: none;
            opacity: 0.18;
            filter: drop-shadow(0 0 5px var(--laser-blue));
            animation: shapeLiquidMove 16s ease-in-out infinite alternate;
        }
        @keyframes shapeLiquidMove {
            0% { transform: translate(0, 0) rotate(0deg) scale(1); }
            50% { transform: translate(30px, -20px) rotate(15deg) scale(1.1); }
            100% { transform: translate(-20px, 25px) rotate(-15deg) scale(0.95); }
        }
        .laser-bubble {
            position: absolute;
            background: rgba(0, 240, 255, 0.05);
            border: 1px solid rgba(0, 240, 255, 0.3);
            border-radius: 50%;
            bottom: -30px;
            filter: drop-shadow(0 0 4px var(--laser-blue));
            animation: bubbleRise 9s infinite linear;
            z-index: 1;
        }
        @keyframes bubbleRise {
            0% { transform: translateY(0) translateX(0); opacity: 0; }
            15% { opacity: 0.5; }
            85% { opacity: 0.5; }
            100% { transform: translateY(-200px) translateX(25px); opacity: 0; }
        }
        .chokat-text {
            position: relative;
            z-index: 2;
            font-size: 1.15rem;
            font-weight: 600;
            color: #ffffff;
            line-height: 1.6;
            letter-spacing: 0.3px;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.8), 0 0 10px rgba(0, 240, 255, 0.3);
            max-width: 850px;
        }
        
        .chokat-btn { max-width: 320px; z-index: 2; display: block; margin: 0 auto; }
        
        .card-btn { 
            width: 100%; background-color: var(--btn-blue); color: #ffffff; text-decoration: none; 
            text-align: center; padding: 14px 20px; border-radius: 16px; font-size: 16px; font-weight: 600; 
            box-shadow: 0 10px 22px var(--btn-shadow); border: 1px solid rgba(255, 255, 255, 0.08); 
            transition: all 0.5s cubic-bezier(0.16, 1, 0.3, 1); 
        }
        .card-btn:hover { background-color: #2b96eb; box-shadow: 0 12px 28px rgba(36, 129, 204, 0.5); transform: translateY(-1px); }

        /* =============================================================
           ۳. استایل ردیف‌های آرشیو با دیواره خط لیزری بسیار قشنگ
           ============================================================= */
        .archive-list { width: 100%; max-width: 900px; display: flex; flex-direction: column; gap: 18px; }

        .archive-row {
            display: flex; align-items: center; width: 100%; background-color: var(--row-bg);
            border: 1px solid rgba(139, 92, 246, 0.2); border-radius: 20px; padding: 22px 28px;
            text-decoration: none; color: #ffffff; transition: var(--transition-smooth);
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2), 0 0 10px var(--laser-glow-color);
        }
        
        .archive-row:hover {
            background-color: rgba(255, 255, 255, 0.04); 
            border-color: #00f0ff;
            transform: translateY(-3px) scale(1.01); 
            box-shadow: 0 12px 30px rgba(0, 0, 0, 0.5), 0 0 20px rgba(0, 240, 255, 0.3);
        }

        /* حفظ فریم کپسولی/دایره‌ای شیک دور آیکون‌ها */
        .icon-box { 
            display: flex; align-items: center; justify-content: center; width: 56px; height: 56px;
            background: rgba(139, 92, 246, 0.1); border: 1px solid rgba(139, 92, 246, 0.3);
            border-radius: 50%; margin-right: 24px; flex-shrink: 0; transition: var(--transition-smooth);
        }
        .archive-row:hover .icon-box { background: rgba(0, 240, 255, 0.15); border-color: #00f0ff; box-shadow: 0 0 12px rgba(0, 240, 255, 0.4); }

        /* استایل آیکون‌های شاهکار چندرنگ */
        .book-icon-master { width: 34px; height: 34px; transition: var(--transition-smooth); }
        .archive-row:hover .book-icon-master { transform: scale(1.1) rotate(-3deg); filter: drop-shadow(0 0 8px #00f0ff); }

        .text-box { display: flex; flex-direction: column; gap: 6px; }
        .archive-title { font-size: 18px; font-weight: 700; letter-spacing: -0.1px; transition: var(--transition-smooth); }
        .archive-row:hover .archive-title { color: #00f0ff; text-shadow: 0 0 8px rgba(0, 240, 255, 0.3); }
        .archive-desc { font-size: 14px; color: var(--text-gray-muted); line-height: 1.45; }

        /* واکنش‌گرایی موبایل */
        @media (max-width: 600px) {
            body { padding: 40px 16px; }
            .main-title { font-size: 1.6rem; }
            .archive-row { padding: 18px; border-radius: 16px; }
            .icon-box { margin-right: 16px; width: 46px; height: 46px; }
            .book-icon-master { width: 28px; height: 28px; }
            .archive-title { font-size: 16px; }
            .archive-desc { font-size: 12px; }
            
            /* تنظیمات موبایل چوکات */
            .premium-request-container { margin-bottom: 40px; gap: 16px; }
            .laser-chokat { padding: 20px 15px; min-height: 110px; border-radius: 18px; }
            .chokat-text { font-size: 0.95rem; line-height: 1.5; }
            .card-btn { font-size: 14px; padding: 12px 10px; }
        }
    </style>
</head>
<body>

    <div class="header-container">
       <a href="https://Google-Books.github.io/MainPage/" class="back-btn">&larr; Back</a>
        <h1 class="main-title">We Try Our Best To Provide You The Best And Largest Sources!</h1>
    </div>

    <!-- چوکات لیزری اضافه شده دقیقاً زیر عنوان -->
    <div class="premium-request-container">
        <div class="laser-chokat">
            <div class="laser-shapes-layer">
                <svg class="laser-svg" style="top: 15%; left: 8%; animation-delay: 0s; width: 35px; height: 35px;" viewBox="0 0 24 24"><path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04c.39-.39.39-1.02 0-1.41l-2.34-2.34c-.39-.39-1.02-.39-1.41 0l-1.83 1.83 3.75 3.75 1.83-1.83z"/></svg>
                <svg class="laser-svg" style="top: 55%; left: 15%; animation-delay: -3s; width: 40px; height: 40px;" viewBox="0 0 24 24"><path d="M18 2H6c-1.1 0-2 .9-2 2v16c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm0 18H6V4h12v16z"/></svg>
                <svg class="laser-svg" style="top: 20%; right: 12%; animation-delay: -6s; width: 38px; height: 38px;" viewBox="0 0 24 24"><path d="M21 3c-1.66 0-3 1.34-3 3 0 .7.24 1.33.64 1.85L11.5 15.0L9 12.5l-1.5 1.5 4 4 8-8.5c.53.37 1.17.5 1.85.5 1.66 0 3-1.34 3-3s-1.34-3-3-3z"/></svg>
                <svg class="laser-svg" style="top: 50%; right: 7%; animation-delay: -9s; width: 45px; height: 45px;" viewBox="0 0 24 24"><path d="M12 6c-1.5-2-5-2.5-7-2.5v14c2 0 5.5.5 7 2.5 1.5-2 5-2.5 7-2.5V3.5c-2 0-5.5.5-7 2.5z"/></svg>
                <div class="laser-bubble" style="left: 20%; width: 12px; height: 12px; animation-duration: 7s; animation-delay: 1s;"></div>
                <div class="laser-bubble" style="left: 45%; width: 8px; height: 8px; animation-duration: 10s; animation-delay: 3s;"></div>
                <div class="laser-bubble" style="left: 70%; width: 14px; height: 14px; animation-duration: 8s; animation-delay: 0s;"></div>
                <div class="laser-bubble" style="right: 25%; width: 10px; height: 10px; animation-duration: 11s; animation-delay: 5s;"></div>
            </div>
            <div class="chokat-text">
                Couldn't find your book? Click the button below and request it from support.
            </div>
        </div>
        <a href="https://google-books.github.io/Request/" class="card-btn chokat-btn">Request Book</a>
    </div>

    <div class="archive-list">

        <!-- آرشیو ۱: اقیانوس کتاب‌ها - شاهکار کتاب کریستالی باز شده سه‌بعدی با هاله صورتی و فیروزه‌ای -->
        <a href="https://oceanofpdf.com" target="_blank" class="archive-row">
            <div class="icon-box">
                <svg class="book-icon-master" viewBox="0 0 32 32">
                    <defs>
                        <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="100%">
                            <stop offset="0%" style="stop-color:#00f0ff;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#ec4899;stop-opacity:1" />
                        </linearGradient>
                    </defs>
                    <path d="M2 26s5-4 14-4 14 4 14 4V6s-5-4-14-4-14 4-14 4v20z" fill="url(#grad1)" />
                    <path d="M16 2v20" stroke="#ffffff" stroke-width="1.5" stroke-linecap="round"/>
                    <path d="M6 8h6M6 12h6M6 16h4M20 8h6M20 12h6M22 16h4" stroke="#ffffff" stroke-width="1.5" stroke-linecap="round"/>
                </svg>
            </div>
            <div class="text-box">
                <div class="archive-title">The First Archive</div>
                <div class="archive-desc">The fastest and safest library in the world with new books and romances.</div>
            </div>
        </a>

        <!-- آرشیو ۲: وی‌لیب - نماد رادار جستجوی لیزری روی کتاب باز نقره‌ای متمایز -->
        <a href="https://welib.st" target="_blank" class="archive-row">
            <div class="icon-box">
                <svg class="book-icon-master" viewBox="0 0 32 32">
                    <defs>
                        <linearGradient id="grad2" x1="0%" y1="0%" x2="100%" y2="100%">
                            <stop offset="0%" style="stop-color:#38bdf8;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#a855f7;stop-opacity:1" />
                        </linearGradient>
                    </defs>
                    <path d="M4 24s4-3 12-3 12 3 12 3V7s-4-3-12-3-12 3-12 3v17z" fill="url(#grad2)" opacity="0.8"/>
                    <circle cx="16" cy="14" r="6" fill="none" stroke="#00f0ff" stroke-width="2" />
                    <line x1="20.5" y1="18.5" x2="26" y2="24" stroke="#00f0ff" stroke-width="2.5" stroke-linecap="round"/>
                </svg>
            </div>
            <div class="text-box">
                <div class="archive-title">The Second Archive</div>
                <div class="archive-desc">PDF search engine with an extensive categorized database.</div>
            </div>
        </a>

        <!-- آرشیو ۳: اینترنت آرشیو - عمارت سه‌بعدی یونانی بنا شده بر روی کتاب طلایی غول‌پیکر تجسم علم -->
        <a href="https://archive.org" target="_blank" class="archive-row">
            <div class="icon-box">
                <svg class="book-icon-master" viewBox="0 0 32 32">
                    <defs>
                        <linearGradient id="grad3" x1="0%" y1="0%" x2="0%" y2="100%">
                            <stop offset="0%" style="stop-color:#eab308;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#3b82f6;stop-opacity:1" />
                        </linearGradient>
                    </defs>
                    <path d="M4 24h24v3H4z" fill="#eab308"/>
                    <path d="M6 21h3v3H6zm5 0h3v3h-3zm5 0h3v3h-3zm5 0h3v3h-3zm5 0h3v3h-3z" fill="#ffffff"/>
                    <path d="M5 11l11-7 11 7v3H5z" fill="url(#grad3)"/>
                    <path d="M2 25c0 1.1.9 2 2 2h24c1.1 0 2-.9 2-2s-.9-2-2-2H4c-1.1 0-2 .9-2 2z" fill="#ffffff"/>
                </svg>
            </div>
            <div class="text-box">
                <div class="archive-title">The Third Archive</div>
                <div class="archive-desc">Digital library with millions of books, articles, magazines, plus movies, music.</div>
            </div>
        </a>
        <!-- آرشیو ۴: ویکی‌سورس - تومار و لوح چاپی نئون یاقوتی اصیل نماد مستندات تاریخی -->
        <a href="https://wikisource.org" target="_blank" class="archive-row">
            <div class="icon-box">
                <svg class="book-icon-master" viewBox="0 0 32 32">
                    <defs>
                        <linearGradient id="grad4" x1="0%" y1="0%" x2="100%" y2="100%">
                            <stop offset="0%" style="stop-color:#f43f5e;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#f97316;stop-opacity:1" />
                        </linearGradient>
                    </defs>
                    <path d="M19 2H6c-1.1 0-2 .9-2 2v24c0 1.1.9 2 2 2h20c1.1 0 2-.9 2-2V11l-9-9z" fill="url(#grad4)"/>
                    <path d="M19 2v9h9M8 12h10M8 17h16M8 22h16" stroke="#ffffff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
            </div>
            <div class="text-box">
                <div class="archive-title">The Fourth Archive</div>
                <div class="archive-desc">Free digital library with full-text books, novels, historical documents, and speeches.</div>
            </div>
        </a>

        <!-- آرشیو ۵: اوپن لایبرری - نماد کتابخانه لایو و قفسه کتاب شیشه‌ای چندرنگ جهانی -->
        <a href="https://openlibrary.org" target="_blank" class="archive-row">
            <div class="icon-box">
                <svg class="book-icon-master" viewBox="0 0 32 32">
                    <defs>
                        <linearGradient id="grad5" x1="0%" y1="0%" x2="100%" y2="100%">
                            <stop offset="0%" style="stop-color:#10b981;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#059669;stop-opacity:1" />
                        </linearGradient>
                    </defs>
                    <rect x="4" y="4" width="24" height="24" rx="4" fill="url(#grad5)"/>
                    <path d="M9 8h2v16H9zm5 0h3v16h-3zm6 0h3v16h-3z" fill="#ffffff" opacity="0.9"/>
                    <line x1="4" y1="14" x2="28" y2="14" stroke="#0d1326" stroke-width="2"/>
                    <line x1="4" y1="20" x2="28" y2="20" stroke="#0d1326" stroke-width="2"/>
                </svg>
            </div>
            <div class="text-box">
                <div class="archive-title">The Fifth Archive</div>
                <div class="archive-desc">Old archive with millions of valuable scanned vintage books.</div>
            </div>
        </a>

        <!-- آرشیو ۶: گوگل اسکالر - کلاه‌فارغ‌التحصیلی لوکس و سلطنتی زمردین معلق بر روی کتاب مرجع علم -->
        <a href="https://gutenberg.org" target="_blank" class="archive-row">
            <div class="icon-box">
                <svg class="book-icon-master" viewBox="0 0 32 32">
                    <defs>
                        <linearGradient id="grad6" x1="0%" y1="0%" x2="100%" y2="100%">
                            <stop offset="0%" style="stop-color:#06b6d4;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#3b82f6;stop-opacity:1" />
                        </linearGradient>
                    </defs>
                    <path d="M16 4L3 10l13 6 13-6-13-6z" fill="url(#grad6)"/>
                    <path d="M7 13.5V20c0 2 4 4 9 4s9-2 9-4v-6.5" fill="none" stroke="#00f0ff" stroke-width="2"/>
                    <path d="M25 11v8" fill="none" stroke="#ffffff" stroke-width="2"/>
                    <circle cx="25" cy="19" r="2" fill="#ffffff"/>
                </svg>
            </div>
            <div class="text-box">
                <div class="archive-title">The Sixth Archive</div>
                <div class="archive-desc">The oldest digital library project focused on classic works.</div>
            </div>
        </a>

        <!-- آرشیو ۷: منی‌بوکس - کتاب طلایی درخشان باز شده مجهز به نشان ستاره فروزان ۵ ستاره اصالت -->
        <a href="https://manybooks.net" target="_blank" class="archive-row">
            <div class="icon-box">
                <svg class="book-icon-master" viewBox="0 0 32 32">
                    <path d="M2 26s5-4 14-4 14 4 14 4V6s-5-4-14-4-14 4-14 4v20z" fill="#f59e0b" />
                    <path d="M16 2v20" stroke="#0d1326" stroke-width="2"/>
                    <polygon points="16,8 18,12 22,12 19,15 20,19 16,17 12,19 13,15 10,12 14,12" fill="#ffffff"/>
                </svg>
            </div>
            <div class="text-box">
                <div class="archive-title">The Seventh Archive</div>
                <div class="archive-desc">Simple and beautiful interface with suggested book topics.</div>
            </div>
        </a>

        <!-- آرشیو ۸: اوپن‌استکس - دو کتاب سه‌بعدی تابلوی روی هم چیده شده دانشگاهی با زاویه دید خارق‌العاده -->
        <a href="https://openstax.org" target="_blank" class="archive-row">
            <div class="icon-box">
                <svg class="book-icon-master" viewBox="0 0 32 32">
                    <defs>
                        <linearGradient id="grad8" x1="0%" y1="0%" x2="100%" y2="0%">
                            <stop offset="0%" style="stop-color:#6366f1;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#4f46e5;stop-opacity:1" />
                        </linearGradient>
                    </defs>
                    <rect x="6" y="12" width="20" height="14" rx="3" fill="url(#grad8)"/>
                    <rect x="4" y="6" width="20" height="14" rx="3" fill="#38bdf8"/>
                    <path d="M4 16h20M6 22h20" stroke="#ffffff" stroke-width="2"/>
                </svg>
            </div>
            <div class="text-box">
                <div class="archive-title">The Eighth Archive</div>
                <div class="archive-desc">Millions of high-quality, standard-compliant textbooks (specially designed for students).</div>
            </div>
        </a>

        <!-- آرشیو ۹: استاندارد ایبوکس - منشور چندوجهی الماس کریستالی بر روی لوح چاپی لوکس -->
        <a href="https://standardebooks.org" target="_blank" class="archive-row">
            <div class="icon-box">
                <svg class="book-icon-master" viewBox="0 0 32 32">
                    <defs>
                        <linearGradient id="grad9" x1="0%" y1="0%" x2="100%" y2="100%">
                            <stop offset="0%" style="stop-color:#a855f7;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#ec4899;stop-opacity:1" />
                        </linearGradient>
                    </defs>
                    <polygon points="16,2 28,10 24,26 8,26 4,10" fill="url(#grad9)"/>
                    <polygon points="16,6 24,12 20,22 12,22 8,12" fill="#ffffff" opacity="0.3"/>
                    <path d="M12 14h8M10 18h12" stroke="#ffffff" stroke-width="1.5" stroke-linecap="round"/>
                </svg>
            </div>
            <div class="text-box">
                <div class="archive-title">The Ninth Archive</div>
                <div class="archive-desc">Free high-quality classic ebooks in EPUB and Kindle formats.</div>
            </div>
        </a>

        <!-- آرشیو ۱۰: بوک‌بون - کتاب هندسی چندبعدی باز شده با برگه طلایی متصل به فناوری یادگیری الکترونیک -->
        <a href="https://bookboon.com" target="_blank" class="archive-row">
            <div class="icon-box">
                <svg class="book-icon-master" viewBox="0 0 32 32">
                    <path d="M16 4L4 12v12l12 4 12-4V12L16 4z" fill="#1d4ed8"/>
                    <path d="M16 4v24l12-4V12L16 4z" fill="#2563eb"/>
                    <path d="M7 13.5l9 3.5 9-3.5" fill="none" stroke="#00f0ff" stroke-width="2"/>
                </svg>
            </div>
            <div class="text-box">
                <div class="archive-title">The Tenth Archive</div>
                <div class="archive-desc">Free academic and business books, great for students and learning skills.</div>
            </div>
        </a>

        <!-- آرشیو ۱۱: فری ایبوکس - نماد خلاقانه ابر دیجیتال نگهبان باران پی‌دی‌اف و کتاب‌های دانلودی -->
        <a href="https://free-ebooks.net" target="_blank" class="archive-row">
            <div class="icon-box">
                <svg class="book-icon-master" viewBox="0 0 32 32">
                    <defs>
                        <linearGradient id="grad11" x1="0%" y1="0%" x2="100%" y2="100%">
                            <stop offset="0%" style="stop-color:#00f0ff;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#3b82f6;stop-opacity:1" />
                        </linearGradient>
                    </defs>
                    <path d="M26 15a7 7 0 0 0-13.93-1A5.5 5.5 0 0 0 3 19.5 5.5 5.5 0 0 0 8.5 25h17a4.5 4.5 0 0 0 0-9z" fill="url(#grad11)"/>
                    <path d="M12 14v6h4l-4 4-4-4h4v-6z" fill="#ffffff"/>
                </svg>
            </div>
            <div class="text-box">
                <div class="archive-title">The Eleventh Archive</div>
                <div class="archive-desc">Free e-Books Thousands of novels, educational and scientific ebooks in PDF or EPUB.</div>
            </div>
        </a>

    </div> <!-- انتهای کانتینر .archive-list -->

<!-- سوشیال بار - همیشه فعال -->
<script src="https://speedingdeadlyplays.com/b3/e9/4d/b3e94d023432c8cb40b981d7804166a2.js"></script>

<!-- بنر شناور پایین صفحه -->
<div id="floating-ad"></div>

<style>
#floating-ad{
    position:fixed;
    left:50%;
    transform:translateX(-50%);
    bottom:0;
    z-index:999999999;

    width:auto;
    height:auto;

    display:flex;
    justify-content:center;
    align-items:center;

    pointer-events:auto;
}

/* فاصله برای اینکه محتوا زیر بنر نرود */
body{
    padding-bottom:110px;
}
</style>

<script>

(function(){

let key="";
let width=0;
let height=0;

const w=window.innerWidth;

/* موبایل کوچک */
if(w<=360){

key="3b8048b78e2b0fb0b882483f96fca8a2";
width=320;
height=50;

}

/* موبایل بزرگ و تبلت */
else if(w<=768){

key="27bf67bdd07dd3734a6fdff8c7879c99";
width=468;
height=60;

}

/* دسکتاپ */
else{

key="30c18b6ace1c2676949453fd6ac33776";
width=728;
height=90;

}

window.atOptions={
key:key,
format:'iframe',
height:height,
width:width,
params:{}
};

const s=document.createElement("script");

s.src=
"https://speedingdeadlyplays.com/"
+key+
"/invoke.js";

s.async=true;

document
.getElementById("floating-ad")
.appendChild(s);

})();

</script>

</body>
</html>
