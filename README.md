<!DOCTYPE html>
<html lang="fa">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ثبت‌نام جشنواره نوروزی ۱۴۰۵</title>
<link href="https://fonts.googleapis.com/css2?family=Vazir&display=swap" rel="stylesheet">
<style>
    /* Reset و تنظیم فونت */
    * {margin:0; padding:0; box-sizing:border-box;}
    body {
        font-family: 'Vazir', sans-serif;
        background: linear-gradient(135deg, #ffecd2, #fcb69f);
        min-height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    /* صفحه آغازین */
    #intro {
        position: absolute;
        width: 100%;
        height: 100%;
        background: linear-gradient(to bottom right, #ff7e5f, #feb47b);
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        color: #fff;
        animation: fadeIn 1s ease forwards;
    }
    #intro h1 {
        font-size: 2.5rem;
        margin-bottom: 20px;
        text-shadow: 2px 2px 5px rgba(0,0,0,0.3);
    }
    #intro button {
        padding: 15px 30px;
        font-size: 1.2rem;
        border: none;
        border-radius: 12px;
        background: #fff;
        color: #ff7e5f;
        cursor: pointer;
        box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        transition: 0.3s;
    }
    #intro button:hover {
        background: #ffe7d6;
        transform: scale(1.05);
    }

    @keyframes fadeIn {
        0% {opacity:0;}
        100% {opacity:1;}
    }

    /* فرم اصلی */
    form {
        background: #fff;
        padding: 30px;
        border-radius: 20px;
        box-shadow: 0 15px 40px rgba(0,0,0,0.2);
        width: 90%;
        max-width: 500px;
        display: none;
        flex-direction: column;
        animation: slideUp 0.8s ease forwards;
    }
    @keyframes slideUp {
        0% {opacity:0; transform: translateY(50px);}
        100% {opacity:1; transform: translateY(0);}
    }

    h1 { text-align: center; color: #ff6f61; margin-bottom: 20px;}

    label { display: block; margin-top: 15px; font-weight: bold; }
    input, select, textarea {
        width: 100%;
        padding: 12px;
        margin-top: 5px;
        border-radius: 10px;
        border: 1px solid #ccc;
        transition: 0.3s;
    }
    input:focus, select:focus, textarea:focus {
        border-color: #ff6f61;
        box-shadow: 0 0 5px #ff6f61;
        outline: none;
    }

    button.submit {
        background: linear-gradient(45deg, #ff6f61, #ff9478);
        color: #fff;
        padding: 15px;
        margin-top: 20px;
        border: none;
        border-radius: 15px;
        cursor: pointer;
        font-size: 16px;
        width: 100%;
        transition: 0.3s;
    }
    button.submit:hover {
        background: linear-gradient(45deg, #ff9478, #ff6f61);
        transform: scale(1.03);
    }

    .hidden { display: none; }

    /* Responsive موبایل */
    @media(max-width:600px){
        h1 { font-size: 2rem; }
        #intro h1 { font-size: 2rem; }
        input, select, textarea, button { font-size: 1rem; }
    }
</style>
</head>
<body>

<!-- صفحه آغازین -->
<div id="intro">
    <h1>🌸 جشنواره نوروزی ۱۴۰۵ 🌸</h1>
    <button id="startBtn">شروع ثبت‌نام</button>
</div>

<!-- فرم اصلی -->
<form id="festivalForm" action="https://formspree.io/f/xnjbvjnj" method="POST">
    <h1>ثبت‌نام جشنواره نوروزی ۱۴۰۵</h1>
    
    <label>نام و نام خانوادگی</label>
    <input type="text" name="name" required>
    
    <label>سن</label>
    <input type="number" name="age" required>
    
    <label>شهر محل سکونت</label>
    <input type="text" name="city" required>
    
    <label>شماره تماس</label>
    <input type="text" name="phone" required>
    
    <label>آیدی تلگرام / ایتا</label>
    <input type="text" name="telegram">
    
    <label>انتخاب بخش مورد علاقه</label>
    <select name="section" id="section" required>
        <option value="">انتخاب کنید</option>
        <option value="مهارتی">دوره مهارتی</option>
        <option value="درسی">دوره درسی</option>
        <option value="مسابقات">مسابقات</option>
        <option value="عمومی">برنامه‌های عمومی</option>
    </select>
    
    <div id="skillSection" class="hidden">
        <label>انتخاب دوره مهارتی</label>
        <input type="text" name="skill_course">
        
        <label>میزان آشنایی با موضوع</label>
        <select name="skill_level">
            <option value="مبتدی">مبتدی</option>
            <option value="متوسط">متوسط</option>
            <option value="پیشرفته">پیشرفته</option>
        </select>
    </div>
    
    <label>نحوه آشنایی با جشنواره</label>
    <textarea name="how_found" rows="3"></textarea>
    
    <label>توضیحات یا سوالات</label>
    <textarea name="notes" rows="3"></textarea>
    
    <button type="submit" class="submit">ثبت‌نام</button>
</form>

<script>
    const startBtn = document.getElementById('startBtn');
    const intro = document.getElementById('intro');
    const form = document.getElementById('festivalForm');
    const section = document.getElementById('section');
    const skillSection = document.getElementById('skillSection');

    // رفتن از صفحه آغازین به فرم
    startBtn.addEventListener('click', () => {
        intro.style.display = 'none';
        form.style.display = 'flex';
    });

    // منطق شرطی دوره مهارتی
    section.addEventListener('change', () => {
        if(section.value === 'مهارتی'){
            skillSection.classList.remove('hidden');
        } else {
            skillSection.classList.add('hidden');
        }
    });
</script>

</body>
</html>
