<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>فروشگاه سارا خاتون | لوازم آرایشی و بهداشتی حرفه‌ای</title>
<link href="https://fonts.googleapis.com/css2?family=Vazirmatn&display=swap" rel="stylesheet" />
<style>
  /* Reset */
  * {
    margin: 0; padding: 0; box-sizing: border-box; font-family: 'Vazirmatn', Tahoma, sans-serif;
  }
  body {
    background: #fff8fb;
    color: #444;
    line-height: 1.6;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }
  header {
    background: linear-gradient(90deg, #ff4081 0%, #f50057 100%);
    padding: 20px 40px;
    color: white;
    font-size: 2.5rem;
    font-weight: 900;
    text-align: center;
    letter-spacing: 3px;
    box-shadow: 0 4px 15px rgba(245, 0, 87, 0.5);
    user-select: none;
  }
  nav {
    display: flex;
    justify-content: center;
    background: #fce4ec;
    padding: 15px 0;
    box-shadow: inset 0 -2px 5px rgba(245,0,87,0.15);
  }
  nav a {
    color: #f50057;
    text-decoration: none;
    margin: 0 25px;
    font-weight: 700;
    font-size: 1.1rem;
    position: relative;
    transition: color 0.3s ease;
  }
  nav a::after {
    content: '';
    position: absolute;
    bottom: -6px;
    left: 0; right: 0;
    width: 0;
    height: 3px;
    background: #f50057;
    transition: width 0.3s ease;
    border-radius: 2px;
  }
  nav a:hover,
  nav a:focus {
    color: #c51162;
  }
  nav a:hover::after,
  nav a:focus::after {
    width: 100%;
  }

  .hero {
    background: url('https://images.unsplash.com/photo-1522335789203-aabd1fc54bc9?auto=format&fit=crop&w=1470&q=80') no-repeat center center/cover;
    height: 420px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    font-size: 3.8rem;
    font-weight: 900;
    text-shadow: 2px 3px 15px rgba(0,0,0,0.6);
    margin-bottom: 60px;
    user-select: none;
  }
  .container {
    max-width: 1180px;
    margin: 0 auto 60px;
    padding: 0 25px;
    flex-grow: 1;
  }
  h2 {
    color: #f50057;
    font-size: 2.6rem;
    font-weight: 900;
    margin-bottom: 35px;
    border-bottom: 4px solid #f50057;
    padding-bottom: 10px;
    user-select: none;
  }

  .products {
    display: grid;
    grid-template-columns: repeat(auto-fit,minmax(320px,1fr));
    gap: 35px;
  }
  .product-card {
    background: #fff;
    border-radius: 18px;
    box-shadow: 0 15px 30px rgba(245,0,87,0.15);
    overflow: hidden;
    transition: transform 0.35s cubic-bezier(0.4, 0, 0.2, 1), box-shadow 0.35s ease;
    cursor: pointer;
    display: flex;
    flex-direction: column;
  }
  .product-card:hover {
    transform: translateY(-15px);
    box-shadow: 0 25px 40px rgba(245,0,87,0.3);
  }
  .product-image {
    flex-shrink: 0;
    height: 260px;
    background-size: cover;
    background-position: center;
    transition: transform 0.4s ease;
  }
  .product-card:hover .product-image {
    transform: scale(1.05);
  }
  .product-info {
    padding: 25px 28px;
    flex-grow: 1;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  .product-info h3 {
    font-size: 1.5rem;
    color: #ad1457;
    margin-bottom: 14px;
    font-weight: 900;
  }
  .product-info p {
    color: #666;
    font-size: 1rem;
    flex-grow: 1;
    margin-bottom: 18px;
    line-height: 1.4;
  }
  .price {
    color: #f50057;
    font-weight: 900;
    font-size: 1.3rem;
  }

  /* مودال */
  .modal {
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background: rgba(0,0,0,0.6);
    display: none;
    align-items: center;
    justify-content: center;
    z-index: 9999;
    padding: 20px;
  }
  .modal.active {
    display: flex;
  }
  .modal-content {
    background: white;
    border-radius: 16px;
    max-width: 500px;
    width: 100%;
    max-height: 90vh;
    overflow-y: auto;
    padding: 30px 30px 40px;
    position: relative;
    box-shadow: 0 15px 40px rgba(245,0,87,0.25);
  }
  .modal-close {
    position: absolute;
    top: 15px;
    left: 15px;
    background: #f50057;
    color: white;
    border: none;
    font-size: 1.8rem;
    font-weight: 900;
    border-radius: 50%;
    width: 38px;
    height: 38px;
    cursor: pointer;
    line-height: 38px;
    text-align: center;
    transition: background 0.3s ease;
  }
  .modal-close:hover {
    background: #c51162;
  }
  .modal-content h3 {
    color: #f50057;
    font-weight: 900;
    margin-bottom: 15px;
    font-size: 2rem;
    user-select: none;
  }
  .modal-content img {
    width: 100%;
    border-radius: 14px;
    margin-bottom: 20px;
    user-select: none;
  }
  .modal-content p {
    font-size: 1.1rem;
    color: #555;
    margin-bottom: 25px;
    line-height: 1.5;
  }
  .modal-content .price {
    font-size: 1.5rem;
    font-weight: 900;
    color: #e91e63;
    margin-bottom: 30px;
  }
  /* فرم سفارش */
  form {
    display: flex;
    flex-direction: column;
  }
  label {
    font-weight: 700;
    margin-bottom: 6px;
    color: #ad1457;
    user-select: none;
  }
  input, select, textarea {
    padding: 12px 15px;
    margin-bottom: 18px;
    border: 2px solid #f50057;
    border-radius: 8px;
    font-size: 1rem;
    font-family: 'Vazirmatn', Tahoma, sans-serif;
    transition: border-color 0.3s ease;
  }
  input:focus, select:focus, textarea:focus {
    border-color: #c51162;
    outline: none;
  }
  button.submit-btn {
    background: #f50057;
    border: none;
    padding: 15px;
    font-size: 1.2rem;
    color: white;
    font-weight: 900;
    border-radius: 12px;
    cursor: pointer;
    transition: background 0.3s ease;
    user-select: none;
  }
  button.submit-btn:hover {
    background: #c51162;
  }

  /* Responsive */
  @media(max-width: 900px) {
    nav {
      flex-wrap: wrap;
      gap: 15px;
      padding: 20px 0;
    }
    nav a {
      margin: 10px 12px;
    }
    .hero {
      font-size: 2.8rem;
      height: 320px;
      padding: 0 10px;
    }
    .container {
      padding: 0 15px 50px;
    }
    h2 {
      font-size: 2rem;
      margin-bottom: 25px;
    }
  }
  @media(max-width: 480px) {
    .product-card {
      border-radius: 14px;
    }
    .product-image {
      height: 200px;
    }
    .product-info h3 {
      font-size: 1.2rem;
    }
    .product-info p {
      font-size: 0.9rem;
    }
    .price {
      font-size: 1.1rem;
    }
  }
</style>
</head>
<body>
<header>
  فروشگاه سارا خاتون
</header>
<nav>
  <a href="#">خانه</a>
  <a href="#">محصولات</a>
  <a href="#">درباره ما</a>
  <a href="#">تماس با ما</a>
</nav>

<section class="hero" aria-label="تصویر اصلی فروشگاه">
  بهترین لوازم آرایشی و بهداشتی را اینجا پیدا کنید!
</section>

<main class="container" role="main">
  <h2>محصولات ویژه</h2>
  <div class="products" role="list">
    <article class="product-card" role="listitem" tabindex="0" aria-label="کرم صورت ضدچروک ۱۵۰ هزار تومان" data-id="1" data-name="کرم صورت ضدچروک" data-desc="حفظ رطوبت و جوان‌سازی پوست با فرمولاسیون طبیعی." data-price="۱۵۰,۰۰۰ تومان" data-img="https://images.unsplash.com/photo-1522335789203-aabd1fc54bc9?auto=format&fit=crop&w=400&q=80">
      <div class="product-image" style="background-image: url('https://images.unsplash.com/photo-1522335789203-aabd1fc54bc9?auto=format&fit=crop&w=400&q=80');" alt="کرم صورت ضدچروک"></div>
      <div class="product-info">
        <h3>کرم صورت ضدچروک</h3>
        <p>حفظ رطوبت و جوان‌سازی پوست با فرمولاسیون طبیعی.</p>
        <div class="price">۱۵۰,۰۰۰ تومان</div>
      </div>
    </article>
    <article class="product-card" role="listitem" tabindex="0" aria-label="رژ لب مات مخملی ۸۰ هزار تومان" data-id="2" data-name="رژ لب مات مخملی" data-desc="رنگ‌های متنوع و ماندگاری بالا برای لب‌های زیبا." data-price="۸۰,۰۰۰ تومان" data-img="https://images.unsplash.com/photo-1501004318641-b39e6451bec6?auto=format&fit=crop&w=400&q=80">
      <div class="product-image" style="background-image: url('https://images.unsplash.com/photo-1501004318641-b39e6451bec6?auto=format&fit=crop&w=400&q=80');" alt="رژ لب مات مخملی"></div>
      <div class="product-info">
        <h3>رژ لب مات مخملی</h3>
        <p>رنگ‌های متنوع و ماندگاری بالا برای لب‌های زیبا.</p>
        <div class="price">۸۰,۰۰۰ تومان</div>
      </div>
    </article>
    <article class="product-card" role="listitem" tabindex="0" aria-label="شامپو تقویت‌کننده مو ۱۲۰ هزار تومان" data-id="3" data-name="شامپو تقویت‌کننده مو" data-desc="ترکیبات گیاهی برای افزایش حجم و شفافیت موها." data-price="۱۲۰,۰۰۰ تومان" data-img="https://images.unsplash.com/photo-1568605114967-8130f3a36994?auto=format&fit=crop&w=400&q=80">
      <div class="product-image" style="background-image: url('https://images.unsplash.com/photo-1568605114967-8130f3a36994?auto=format&fit=crop&w=400&q=80');" alt="شامپو تقویت‌کننده مو"></div>
      <div class="product-info">
        <h3>شامپو تقویت‌کننده مو</h3>
        <p>ترکیبات گیاهی برای افزایش حجم و شفافیت موها.</p>
        <div class="price">۱۲۰,۰۰۰ تومان</div>
      </div>
    </article>
    <article class="product-card" role="listitem" tabindex="0" aria-label="لوسیون بدن مرطوب‌کننده ۹۰ هزار تومان" data-id="4" data-name="لوسیون بدن مرطوب‌کننده" data-desc="نرمی و لطافت پوست با رایحه خوش طبیعی." data-price="۹۰,۰۰۰ تومان" data-img="https://images.unsplash.com/photo-1514996937319-344454492b37?auto=format&fit=crop&w=400&q=80">
      <div class="product-image" style="background-image: url('https://images.unsplash.com/photo-1514996937319-344454492b37?auto=format&fit=crop&w=400&q=80');" alt="لوسیون بدن مرطوب‌کننده"></div>
      <div class="product-info">
        <h3>لوسیون بدن مرطوب‌کننده</h3>
        <p>نرمی و لطافت پوست با رایحه خوش طبیعی.</p>
        <div class="price">۹۰,۰۰۰ تومان</div>
      </div>
    </article>
  </div>
</main>

<!-- مودال جزئیات محصول -->
<div id="productModal" class="modal" role="dialog" aria-modal="true" aria-labelledby="modalTitle" aria-describedby="modalDesc">
  <div class="modal-content">
    <button class="modal-close" aria-label="بستن پنجره">&times;</button>
    <h3 id="modalTitle">عنوان محصول</h3>
    <img src="" alt="" id="modalImg" />
    <p id="modalDesc">توضیحات محصول</p>
    <div class="price" id="modalPrice">قیمت محصول</div>

    <h3>فرم سفارش سریع</h3>
    <form id="orderForm">
      <label for="customerName">نام شما:</label>
      <input type="text" id="customerName" name="customerName" required placeholder="نام کامل خود را وارد کنید" />

      <label for="phoneNumber">شماره تماس:</label>
      <input type="tel" id="phoneNumber" name="phoneNumber" required placeholder="مثلاً 09123456789" pattern="0[0-9]{9}" />

      <label for="quantity">تعداد:</label>
      <select id="quantity" name="quantity" required>
        <option value="" disabled selected>انتخاب تعداد</option>
        <option value="1">۱</option>
        <option value="2">۲</option>
        <option value="3">۳</option>
        <option value="4">۴</option>
        <option value="5">۵</option>
      </select>

      <label for="address">آدرس تحویل:</label>
      <textarea id="address" name="address" rows="3" placeholder="آدرس دقیق خود را وارد کنید"></textarea>

      <button type="submit" class="submit-btn">ارسال سفارش</button>
    </form>
  </div>
</div>

<footer>
  © 2025 فروشگاه سارا خاتون | تمامی حقوق محفوظ است.
</footer>

<script>
  // انتخاب عناصر
  const productCards = document.querySelectorAll('.product-card');
  const modal = document.getElementById('productModal');
  const modalCloseBtn = modal.querySelector('.modal-close');
  const modalTitle = document.getElementById('modalTitle');
  const modalImg = document.getElementById('modalImg');
  const modalDesc = document.getElementById('modalDesc');
  const modalPrice = document.getElementById('modalPrice');
  const orderForm = document.getElementById('orderForm');

  // باز کردن مودال با داده محصول
  productCards.forEach(card => {
    card.addEventListener('click', () => {
      const name = card.dataset.name;
      const desc = card.dataset.desc;
      const price = card.dataset.price;
      const img = card.dataset.img;

      modalTitle.textContent = name;
      modalDesc.text