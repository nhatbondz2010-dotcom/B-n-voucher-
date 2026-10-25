# B-n-voucher-```html
<!DOCTYPE html>
<html lang="vi" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VoucherZone - Kho Deals & E-Voucher Giá Tốt Nhất</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <!-- QR Code Generator Library -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        brand: {
                            50: '#fff1f2',
                            100: '#ffe4e6',
                            500: '#f43f5e',
                            600: '#e11d48',
                            700: '#be123c',
                        },
                        accent: {
                            500: '#f97316',
                            600: '#ea580c',
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
        /* Pulse Animation for Flash Sale */
        @keyframes pulse-ring {
            0% { transform: scale(0.95); opacity: 0.8; }
            50% { transform: scale(1.05); opacity: 1; }
            100% { transform: scale(0.95); opacity: 0.8; }
        }
        .pulse-sale {
            animation: pulse-ring 2s infinite ease-in-out;
        }
    </style>
</head>
<body class="bg-gray-50 text-gray-800 font-sans antialiased flex flex-col min-h-screen">

    <!-- TOP ANNOUNCEMENT BAR -->
    <div class="bg-gradient-to-r from-brand-600 to-accent-600 text-white text-xs md:text-sm font-medium py-2 px-4 text-center flex justify-between items-center">
        <div class="container mx-auto flex justify-between items-center">
            <span class="hidden md:inline"><i class="fa-solid fa-fire mr-1"></i> Săn Deal Hot Hôm Nay: Nhập code <strong>DEAL50K</strong> giảm ngay 50.000đ cho đơn từ 200k!</span>
            <span class="md:hidden"><i class="fa-solid fa-fire mr-1"></i> Mã <strong>DEAL50K</strong> giảm ngay 50K!</span>
            <div class="flex items-center gap-4 text-xs">
                <a href="#" class="hover:underline flex items-center gap-1"><i class="fa-solid fa-headset"></i> Hotline: 1900 6868</a>
                <span class="opacity-50">|</span>
                <a href="#" class="hover:underline"><i class="fa-solid fa-mobile-screen"></i> Tải App</a>
            </div>
        </div>
    </div>

    <!-- MAIN HEADER -->
    <header class="sticky top-0 z-40 bg-white shadow-sm border-b border-gray-100">
        <div class="container mx-auto px-4 py-3 flex items-center justify-between gap-4">
            
            <!-- Logo -->
            <a href="#" onclick="switchTab('home')" class="flex items-center gap-2 group">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-brand-600 to-accent-500 flex items-center justify-center text-white font-black text-xl shadow-md group-hover:scale-105 transition-transform">
                    V
                </div>
                <div>
                    <span class="text-xl font-black bg-gradient-to-r from-brand-600 to-accent-500 bg-clip-text text-transparent tracking-tight">VoucherZone</span>
                    <span class="text-[10px] block font-semibold text-gray-400 uppercase -mt-1 tracking-widest">Săn Deal Giá Đỉnh</span>
                </div>
            </a>

            <!-- Search Bar -->
            <div class="flex-1 max-w-2xl hidden md:block">
                <div class="relative">
                    <input type="text" id="searchInput" onkeyup="handleSearch()" placeholder="Tìm kiếm buffet, spa, vé xem phim, voucher du lịch..." 
                        class="w-full pl-10 pr-24 py-2.5 rounded-full border border-gray-200 focus:outline-none focus:border-brand-500 focus:ring-2 focus:ring-brand-100 text-sm transition">
                    <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-1/2 -translate-y-1/2 text-gray-400"></i>
                    <button onclick="handleSearch()" class="absolute right-1 top-1/2 -translate-y-1/2 bg-brand-600 hover:bg-brand-700 text-white text-xs font-semibold px-4 py-1.5 rounded-full transition">
                        Tìm kiếm
                    </button>
                </div>
            </div>

            <!-- Actions Header -->
            <div class="flex items-center gap-3 md:gap-5">
                <!-- My Vouchers Link -->
                <button onclick="switchTab('my-vouchers')" class="flex items-center gap-1.5 text-sm font-medium text-gray-700 hover:text-brand-600 transition">
                    <i class="fa-solid fa-ticket text-brand-500 text-lg"></i>
                    <span class="hidden lg:inline">Voucher của tôi</span>
                </button>

                <!-- Cart Button -->
                <button onclick="toggleCartDrawer(true)" class="relative p-2 text-gray-700 hover:text-brand-600 transition rounded-full hover:bg-gray-100">
                    <i class="fa-solid fa-bag-shopping text-xl"></i>
                    <span id="cartBadge" class="absolute -top-1 -right-1 bg-brand-600 text-white text-[10px] font-bold w-5 h-5 rounded-full flex items-center justify-center border-2 border-white">0</span>
                </button>

                <!-- Account / Login -->
                <button onclick="toggleAccountModal()" class="flex items-center gap-2 pl-2 border-l border-gray-200">
                    <div class="w-8 h-8 rounded-full bg-brand-100 text-brand-600 flex items-center justify-center font-bold text-sm">
                        <i class="fa-regular fa-user"></i>
                    </div>
                    <div class="hidden sm:block text-left">
                        <span class="text-xs text-gray-400 block -mb-0.5">Xin chào,</span>
                        <span class="text-xs font-semibold text-gray-700 block" id="userDisplayName">Thành viên</span>
                    </div>
                </button>
            </div>
        </div>

        <!-- Mobile Search Bar -->
        <div class="p-3 border-t border-gray-100 md:hidden bg-white">
            <div class="relative">
                <input type="text" id="mobileSearchInput" onkeyup="handleSearch()" placeholder="Tìm kiếm voucher, thương hiệu..." 
                    class="w-full pl-9 pr-4 py-2 rounded-full border border-gray-200 focus:outline-none focus:border-brand-500 text-sm">
                <i class="fa-solid fa-magnifying-glass absolute left-3 top-1/2 -translate-y-1/2 text-gray-400 text-xs"></i>
            </div>
        </div>

        <!-- CATEGORIES NAV BAR -->
        <nav class="bg-gray-900 text-white text-xs md:text-sm font-medium overflow-x-auto whitespace-nowrap scrollbar-none">
            <div class="container mx-auto px-4 flex items-center gap-1 md:gap-6 py-2.5">
                <button onclick="filterCategory('all')" class="cat-nav-btn active px-3 py-1 rounded-full bg-brand-600 text-white hover:bg-brand-600 transition flex items-center gap-1.5">
                    <i class="fa-solid fa-border-all"></i> Tất cả
                </button>
                <button onclick="filterCategory('food')" class="cat-nav-btn px-3 py-1 rounded-full hover:bg-gray-800 transition flex items-center gap-1.5 text-gray-300 hover:text-white">
                    <i class="fa-solid fa-utensils text-amber-400"></i> Ẩm Thực
                </button>
                <button onclick="filterCategory('travel')" class="cat-nav-btn px-3 py-1 rounded-full hover:bg-gray-800 transition flex items-center gap-1.5 text-gray-300 hover:text-white">
                    <i class="fa-solid fa-plane-departure text-sky-400"></i> Du Lịch & Khách Sạn
                </button>
                <button onclick="filterCategory('beauty')" class="cat-nav-btn px-3 py-1 rounded-full hover:bg-gray-800 transition flex items-center gap-1.5 text-gray-300 hover:text-white">
                    <i class="fa-solid fa-spa text-pink-400"></i> Làm Đẹp & Spa
                </button>
                <button onclick="filterCategory('entertainment')" class="cat-nav-btn px-3 py-1 rounded-full hover:bg-gray-800 transition flex items-center gap-1.5 text-gray-300 hover:text-white">
                    <i class="fa-solid fa-film text-purple-400"></i> Giải Trí & Vé
                </button>
                <button onclick="filterCategory('shopping')" class="cat-nav-btn px-3 py-1 rounded-full hover:bg-gray-800 transition flex items-center gap-1.5 text-gray-300 hover:text-white">
                    <i class="fa-solid fa-bag-shopping text-emerald-400"></i> Mua Sắm
                </button>
            </div>
        </nav>
    </header>

    <!-- MAIN CONTENT VIEW: HOME / STORE -->
    <div id="homeView" class="flex-1">
        
        <!-- HERO SLIDER / BANNER SECTION -->
        <section class="container mx-auto px-4 my-4 md:my-6">
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-4">
                <!-- Main Slider Container -->
                <div class="lg:col-span-2 relative rounded-2xl overflow-hidden shadow-lg bg-gray-900 group min-h-[220px] sm:min-h-[300px] md:min-h-[360px] flex items-center">
                    <img id="bannerImage" src="https://images.unsplash.com/photo-1555396273-367ea4eb4db5?auto=format&fit=crop&w=1200&q=80" alt="Flash Sale Deals" class="absolute inset-0 w-full h-full object-cover opacity-60 transition-all duration-700">
                    <div class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/40 to-transparent"></div>
                    
                    <div class="relative z-10 p-6 sm:p-10 text-white max-w-xl">
                        <span id="bannerTag" class="bg-brand-600 text-white text-xs font-bold uppercase tracking-wider px-3 py-1 rounded-full inline-block mb-3">
                            <i class="fa-solid fa-bolt mr-1"></i> Siêu Deal Cuối Tuần
                        </span>
                        <h1 id="bannerTitle" class="text-2xl sm:text-4xl font-extrabold leading-tight mb-3">
                            Buffet Hải Sản Cao Cấp 5 Sao - Giảm Đến 45%
                        </h1>
                        <p id="bannerDesc" class="text-sm sm:text-base text-gray-200 mb-6 line-clamp-2">
                            Thưởng thức Tôm hùm, Cua Cà Mau & hơn 100 món Á-Âu tại chuỗi nhà hàng Sheraton. Áp dụng cho cả tuần!
                        </p>
                        <div class="flex items-center gap-3">
                            <button onclick="scrollToDeals()" class="bg-gradient-to-r from-brand-600 to-accent-500 hover:from-brand-700 hover:to-accent-600 text-white font-bold px-6 py-2.5 rounded-full shadow-lg transition transform hover:-translate-y-0.5">
                                Săn Deal Ngay
                            </button>
                            <span class="text-xs text-gray-300"><i class="fa-solid fa-shield-check text-emerald-400"></i> Cam kết hoàn tiền</span>
                        </div>
                    </div>

                    <!-- Slider Controls -->
                    <button onclick="prevBanner()" class="absolute left-3 top-1/2 -translate-y-1/2 bg-white/30 hover:bg-white text-gray-800 p-2 rounded-full backdrop-blur-sm transition opacity-0 group-hover:opacity-100">
                        <i class="fa-solid fa-chevron-left w-5 h-5 flex items-center justify-center"></i>
                    </button>
                    <button onclick="nextBanner()" class="absolute right-3 top-1/2 -translate-y-1/2 bg-white/30 hover:bg-white text-gray-800 p-2 rounded-full backdrop-blur-sm transition opacity-0 group-hover:opacity-100">
                        <i class="fa-solid fa-chevron-right w-5 h-5 flex items-center justify-center"></i>
                    </button>

                    <!-- Indicators -->
                    <div class="absolute bottom-3 right-6 flex gap-1.5 z-10" id="bannerDots">
                        <!-- Dynamic dots -->
                    </div>
                </div>

                <!-- Right Sub-Banners -->
                <div class="grid grid-cols-2 lg:grid-cols-1 gap-4">
                    <div class="relative rounded-2xl overflow-hidden shadow bg-gray-900 group h-[100px] sm:h-[140px] md:h-[170px]">
                        <img src="https://images.unsplash.com/photo-1540555700478-4be289fbecef?auto=format&fit=crop&w=600&q=80" class="w-full h-full object-cover opacity-70 group-hover:scale-105 transition duration-500" alt="Spa">
                        <div class="absolute inset-0 bg-gradient-to-r from-black/80 to-transparent p-4 flex flex-col justify-center text-white">
                            <span class="text-[10px] text-pink-300 font-bold uppercase">Spa & Relax</span>
                            <h3 class="font-bold text-sm sm:text-base leading-snug">Massage Body & Skincare -50%</h3>
                            <span class="text-xs text-amber-300 font-semibold mt-1">Chỉ từ 199.000đ</span>
                        </div>
                    </div>
                    <div class="relative rounded-2xl overflow-hidden shadow bg-gray-900 group h-[100px] sm:h-[140px] md:h-[170px]">
                        <img src="https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=600&q=80" class="w-full h-full object-cover opacity-70 group-hover:scale-105 transition duration-500" alt="Travel">
                        <div class="absolute inset-0 bg-gradient-to-r from-black/80 to-transparent p-4 flex flex-col justify-center text-white">
                            <span class="text-[10px] text-sky-300 font-bold uppercase">Nghỉ Dưỡng</span>
                            <h3 class="font-bold text-sm sm:text-base leading-snug">Resort Phú Quốc 4★ Giá Sốc</h3>
                            <span class="text-xs text-amber-300 font-semibold mt-1">Chỉ từ 1.250.000đ</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- FLASH SALE SECTION WITH COUNTDOWN -->
        <section class="container mx-auto px-4 my-8">
            <div class="bg-gradient-to-r from-red-600 via-brand-600 to-accent-600 rounded-2xl p-4 md:p-6 text-white shadow-xl">
                <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 mb-6 pb-4 border-b border-white/20">
                    <div class="flex items-center gap-3">
                        <div class="bg-white text-brand-600 text-2xl p-2.5 rounded-xl shadow-md pulse-sale">
                            <i class="fa-solid fa-bolt"></i>
                        </div>
                        <div>
                            <div class="flex items-center gap-2">
                                <h2 class="text-xl md:text-2xl font-black uppercase tracking-wider">FLASH SALE HÔM NAY</h2>
                                <span class="bg-amber-400 text-gray-900 font-extrabold text-[10px] px-2 py-0.5 rounded uppercase">SỐ LƯỢNG CÓ HẠN</span>
                            </div>
                            <p class="text-xs md:text-sm text-red-100">Các deal giảm sâu nhất được làm mới mỗi 12 giờ</p>
                        </div>
                    </div>
                    
                    <!-- Global Timer -->
                    <div class="flex items-center gap-2">
                        <span class="text-xs font-semibold uppercase tracking-wider text-red-100 hidden md:inline">Kết thúc sau:</span>
                        <div class="flex gap-1.5 font-bold text-gray-900 text-sm md:text-base">
                            <span id="flashHours" class="bg-white rounded-lg px-2.5 py-1 shadow">04</span> :
                            <span id="flashMinutes" class="bg-white rounded-lg px-2.5 py-1 shadow">28</span> :
                            <span id="flashSeconds" class="bg-white rounded-lg px-2.5 py-1 shadow text-brand-600">45</span>
                        </div>
                    </div>
                </div>

                <!-- Flash Sale Cards Container -->
                <div id="flashSaleGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
                    <!-- Dynamic Flash Sale Items Rendered Here -->
                </div>
            </div>
        </section>

        <!-- MAIN STORE SECTION: FILTER & VOUCHERS GRID -->
        <section id="dealsSection" class="container mx-auto px-4 my-8">
            
            <!-- Section Header & Filter Bar -->
            <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 mb-6 pb-4 border-b border-gray-200">
                <div>
                    <h2 class="text-xl md:text-2xl font-extrabold text-gray-900 flex items-center gap-2">
                        <i class="fa-solid fa-fire text-brand-600"></i> Danh Sách E-Voucher Hot
                    </h2>
                    <p class="text-xs md:text-sm text-gray-500">Khám phá vô vàn ưu đãi cực hời dành cho bạn</p>
                </div>

                <!-- Filter Controls -->
                <div class="flex flex-wrap items-center gap-3">
                    <!-- Location Filter -->
                    <select id="locationFilter" onchange="applyFilters()" class="bg-white border border-gray-200 text-xs md:text-sm font-medium rounded-xl px-3 py-2 text-gray-700 focus:outline-none focus:ring-2 focus:ring-brand-500 shadow-sm">
                        <option value="all">📍 Tất cả khu vực</option>
                        <option value="hcm">TP. Hồ Chí Minh</option>
                        <option value="hanoi">Hà Nội</option>
                        <option value="danang">Đà Nẵng</option>
                    </select>

                    <!-- Price Filter -->
                    <select id="priceFilter" onchange="applyFilters()" class="bg-white border border-gray-200 text-xs md:text-sm font-medium rounded-xl px-3 py-2 text-gray-700 focus:outline-none focus:ring-2 focus:ring-brand-500 shadow-sm">
                        <option value="all">💰 Khoảng giá</option>
                        <option value="under200">Dưới 200.000đ</option>
                        <option value="200to500">200.000đ - 500.000đ</option>
                        <option value="above500">Trên 500.000đ</option>
                    </select>

                    <!-- Sort By -->
                    <select id="sortBy" onchange="applyFilters()" class="bg-white border border-gray-200 text-xs md:text-sm font-medium rounded-xl px-3 py-2 text-gray-700 focus:outline-none focus:ring-2 focus:ring-brand-500 shadow-sm">
                        <option value="popular">🔥 Bán chạy nhất</option>
                        <option value="discount">📉 Giảm giá nhiều nhất</option>
                        <option value="priceAsc">💲 Giá tăng dần</option>
                        <option value="priceDesc">💲 Giá giảm dần</option>
                    </select>
                </div>
            </div>

            <!-- Active Filters Indicators -->
            <div id="activeFilterTags" class="flex flex-wrap gap-2 mb-4 hidden">
                <!-- Dynamic Tag indicators -->
            </div>

            <!-- VOUCHER GRID -->
            <div id=
