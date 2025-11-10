# Students-Management-System
To control students and teachers 
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>آکادمی پیشرفته | Academy Pro</title>

  <!-- Bootstrap 5 -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet"/>
  <!-- Animate.css -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"/>
  <!-- Font Awesome -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css"/>
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@400;500;700&family=Roboto:wght@400;500;700&display=swap" rel="stylesheet"/>

  <style>
    :root {
      --primary: #4361ee;
      --success: #06d6a0;
      --warning: #ffd166;
      --danger: #ef476f;
      --dark: #212529;
      --light: #f8f9fa;
      --gray: #6c757d;
    }
    [data-theme="dark"] {
      --primary: #5e81ff;
      --success: #06d6a0;
      --warning: #ffe066;
      --danger: #ff6b6b;
      --dark: #f8f9fa;
      --light: #1a1a1a;
      --gray: #adb5bd;
      background-color: #121212 !important;
      color: #e0e0e0 !important;
    }
    body {
      font-family: 'Vazirmatn', 'Roboto', sans-serif;
      transition: all 0.4s ease;
      background-color: var(--light);
      color: var(--dark);
      min-height: 100vh;
    }
    .navbar-brand img { height: 40px; border-radius: 50%; }
    .hero {
      background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.7)), url('https://images.unsplash.com/photo-1524178232363-1fb2b075b655?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80');
      background-size: cover; background-position: center;
      color: white; padding: 120px 0; text-align: center;
    }
    .card { transition: all 0.3s; border: none; box-shadow: 0 4px 12px rgba(0,0,0,0.1); }
    .card:hover { transform: translateY(-8px); box-shadow: 0 12px 24px rgba(0,0,0,0.15); }
    .course-card { position: relative; overflow: hidden; }
    .course-card img { transition: transform 0.5s; }
    .course-card:hover img { transform: scale(1.1); }
    .badge-fee { position: absolute; top: 10px; left: 10px; font-weight: bold; }
    .table th { background-color: var(--primary); color: white; }
    .modal-header { background-color: var(--primary); color: white; }
    .lang-switch, .theme-switch { cursor: pointer; }
    .dropdown-menu { min-width: 180px; }
    .dashboard-card { background: linear-gradient(135deg, var(--primary), var(--success)); color: white; }
    .footer { background-color: var(--dark); color: #ccc; padding: 20px 0; margin-top: 50px; }
    @media (max-width: 768px) {
      .navbar-nav { text-align: center; }
      .hero { padding: 80px 0; }
      .d-mobile-none { display: none; }
    }
    .hidden { display: none; }
    .search-input { max-width: 300px; }
  </style>
</head>
<body>

<!-- Navbar -->
<nav class="navbar navbar-expand-lg navbar-dark bg-primary sticky-top shadow-sm">
  <div class="container">
    <a class="navbar-brand" href="#home">
      <img src="https://via.placeholder.com/40x40/4361ee/fff?text=آ" alt="Logo"/>
      آکادمی پیشرفته
    </a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav me-auto" id="navLinks">
        <li class="nav-item"><a class="nav-link active" href="#home" data-key="home">خانه</a></li>
        <li class="nav-item"><a class="nav-link" href="#courses" data-key="courses">کورس‌ها</a></li>
        <li class="nav-item"><a class="nav-link" href="#students" data-key="students">شاگردان</a></li>
        <li class="nav-item"><a class="nav-link" href="#teachers" data-key="teachers">اساتید</a></li>
        <li class="nav-item"><a class="nav-link" href="#library" data-key="library">کتابخانه</a></li>
        <li class="nav-item"><a class="nav-link" href="#about" data-key="about">درباره ما</a></li>
        <li class="nav-item"><a class="nav-link" href="#contact" data-key="contact">تماس</a></li>
        <li class="nav-item"><a class="nav-link" href="#dashboard" data-key="dashboard">داشبورد</a></li>
      </ul>
      <ul class="navbar-nav">
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown">
            <i class="fas fa-globe"></i> <span data-key="language">زبان</span>
          </a>
          <ul class="dropdown-menu">
            <li><a class="dropdown-item lang-switch" data-lang="fa">فارسی</a></li>
            <li><a class="dropdown-item lang-switch" data-lang="en">English</a></li>
          </ul>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown">
            <i class="fas fa-moon"></i> <span data-key="theme">تم</span>
          </a>
          <ul class="dropdown-menu">
            <li><a class="dropdown-item theme-switch" data-theme="light">روشن</a></li>
            <li><a class="dropdown-item theme-switch" data-theme="dark">تیره</a></li>
          </ul>
        </li>
        <li class="nav-item" id="authSection">
          <a class="nav-link" href="#" id="loginBtn" data-key="login">ورود</a>
        </li>
      </ul>
    </div>
  </div>
</nav>

<!-- Pages Container -->
<div class="container mt-4" id="pageContainer">

  <!-- Home -->
  <section id="home" class="page">
    <div class="hero animate__animated animate__fadeIn">
      <h1 class="display-4" data-key="welcome">به آکادمی پیشرفته خوش آمدید</h1>
      <p class="lead" data-key="slogan">یادگیری مدرن، موفقیت تضمینی</p>
      <a href="#students" class="btn btn-warning btn-lg" data-key="register_now">ثبت‌نام کنید</a>
    </div>
    <div class="row mt-5">
      <div class="col-md-4"><div class="card dashboard-card p-4 text-center animate__animated animate__zoomIn"><h3 id="totalStudents">0</h3><p data-key="total_students">شاگرد</p></div></div>
      <div class="col-md-4"><div class="card dashboard-card p-4 text-center animate__animated animate__zoomIn" style="animation-delay:0.1s"><h3 id="totalTeachers">0</h3><p data-key="total_teachers">استاد</p></div></div>
      <div class="col-md-4"><div class="card dashboard-card p-4 text-center animate__animated animate__zoomIn" style="animation-delay:0.2s"><h3 id="totalCourses">15</h3><p data-key="total_courses">کورس</p></div></div>
    </div>
  </section>

  <!-- Courses -->
  <section id="courses" class="page hidden">
    <h2 class="mb-4" data-key="courses">کورس‌های ما</h2>
    <div class="row" id="coursesList">
      <!-- Courses will be injected here -->
    </div>
  </section>

  <!-- Students -->
  <section id="students" class="page hidden">
    <div class="d-flex justify-content-between align-items-center mb-3">
      <h2 data-key="students">مدیریت شاگردان</h2>
      <button class="btn btn-success" data-bs-toggle="modal" data-bs-target="#studentModal" id="addStudentBtn" data-key="add_student">افزودن شاگرد</button>
    </div>
    <input type="text" class="form-control search-input mb-3" placeholder="جستجو..." id="searchStudents">
    <div class="table-responsive">
      <table class="table table-striped" id="studentsTable">
        <thead><tr><th>نام</th><th>تخلص</th><th>ایمیل</th><th>موقعیت</th><th>تایم</th><th>کورس</th><th>فیس</th><th>عملیات</th></tr></thead>
        <tbody></tbody>
      </table>
    </div>
  </section>

  <!-- Teachers -->
  <section id="teachers" class="page hidden">
    <div class="d-flex justify-content-between align-items-center mb-3">
      <h2 data-key="teachers">مدیریت اساتید</h2>
      <button class="btn btn-success" data-bs-toggle="modal" data-bs-target="#teacherModal" id="addTeacherBtn" data-key="add_teacher">افزودن استاد</button>
    </div>
    <div class="table-responsive">
      <table class="table table-striped" id="teachersTable">
        <thead><tr><th>نام</th><th>تخلص</th><th>ایمیل</th><th>رشته</th><th>کلاس‌ها</th><th>عملیات</th></tr></thead>
        <tbody></tbody>
      </table>
    </div>
  </section>

  <!-- Library -->
  <section id="library" class="page hidden">
    <h2 class="mb-4" data-key="library">کتابخانه دیجیتال</h2>
    <div class="row" id="libraryList">
      <div class="col-md-4"><div class="card"><div class="card-body text-center"><i class="fas fa-file-pdf fa-4x text-danger"></i><h5>ICDL Guide</h5><a href="#" class="btn btn-sm btn-outline-primary">دانلود</a></div></div></div>
      <div class="col-md-4"><div class="card"><div class="card-body text-center"><i class="fas fa-book fa-4x text-success"></i><h5>Python Basics</h5><a href="#" class="btn btn-sm btn-outline-primary">دانلود</a></div></div></div>
      <div class="col-md-4"><div class="card"><div class="card-body text-center"><i class="fas fa-calculator fa-4x text-warning"></i><h5>ریاضیات عالی</h5><a href="#" class="btn btn-sm btn-outline-primary">دانلود</a></div></div></div>
    </div>
  </section>

  <!-- About -->
  <section id="about" class="page hidden">
    <h2 class="mb-4" data-key="about">درباره ما</h2>
    <div class="row">
      <div class="col-md-6 animate__animated animate__fadeInLeft">
        <p>آکادمی ما با بیش از ۱۰ سال سابقه، بهترین کورس‌های آموزشی را در زمینه‌های زبان، ریاضی و کامپیوتر ارائه می‌دهد.</p>
        <ul>
          <li>اساتید مجرب و حرفه‌ای</li>
          <li>محیط آموزشی مدرن</li>
          <li>گواهینامه معتبر</li>
          <li>پشتیبانی ۲۴ ساعته</li>
        </ul>
      </div>
      <div class="col-md-6 animate__animated animate__fadeInRight">
        <img src="https://images.unsplash.com/photo-1522202176988-66273c2fd55f?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" class="img-fluid rounded shadow" alt="About">
      </div>
    </div>
  </section>

  <!-- Contact -->
  <section id="contact" class="page hidden">
    <h2 class="mb-4" data-key="contact">تماس با ما</h2>
    <div class="row">
      <div class="col-md-6">
        <form id="contactForm">
          <div class="mb-3"><input type="text" class="form-control" placeholder="نام" required></div>
          <div class="mb-3"><input type="email" class="form-control" placeholder="ایمیل" required></div>
          <div class="mb-3"><textarea class="form-control" rows="5" placeholder="پیام" required></textarea></div>
          <button type="submit" class="btn btn-primary" data-key="send">ارسال</button>
        </form>
      </div>
      <div class="col-md-6">
        <p><i class="fas fa-map-marker-alt"></i> کابل، افغانستان</p>
        <p><i class="fas fa-phone"></i> +93 700 123 456</p>
        <p><i class="fas fa-envelope"></i> info@academy.af</p>
      </div>
    </div>
  </section>

  <!-- Dashboard -->
  <section id="dashboard" class="page hidden">
    <h2 class="mb-4" data-key="dashboard">داشبورد ادمین</h2>
    <div class="row">
      <div class="col-md-3"><div class="card p-3 text-center bg-primary text-white"><h4 id="dashStudents">0</h4><p>شاگردان</p></div></div>
      <div class="col-md-3"><div class="card p-3 text-center bg-success text-white"><h4 id="dashTeachers">0</h4><p>اساتید</p></div></div>
      <div class="col-md-3"><div class="card p-3 text-center bg-warning text-white"><h4 id="dashRevenue">0</h4><p>درآمد ماهانه (افغانی)</p></div></div>
      <div class="col-md-3"><div class="card p-3 text-center bg-danger text-white"><h4 id="dashPending">0</h4><p>ثبت‌نام‌های جدید</p></div></div>
    </div>
    <canvas id="revenueChart" class="mt-4" height="100"></canvas>
  </section>

</div>

<!-- Student Modal -->
<div class="modal fade" id="studentModal" tabindex="-1">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" data-key="add_student">افزودن شاگرد</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
      </div>
      <div class="modal-body">
        <form id="studentForm">
          <input type="hidden" id="studentId">
          <div class="mb-3"><input type="text" class="form-control" id="sName" placeholder="نام" required></div>
          <div class="mb-3"><input type="text" class="form-control" id="sLastname" placeholder="تخلص" required></div>
          <div class="mb-3"><input type="email" class="form-control" id="sEmail" placeholder="ایمیل" required></div>
          <div class="mb-3"><input type="text" class="form-control" id="sLocation" placeholder="موقعیت" required></div>
          <div class="mb-3"><input type="text" class="form-control" id="sTime" placeholder="تایم (مثلاً ۸-۱۰ صبح)" required></div>
          <div class="mb-3">
            <select class="form-select" id="sCourse" required>
              <option value="">کورس را انتخاب کنید</option>
            </select>
          </div>
          <button type="submit" class="btn btn-primary w-100" data-key="save">ذخیره</button>
        </form>
      </div>
    </div>
  </div>
</div>

<!-- Teacher Modal -->
<div class="modal fade" id="teacherModal" tabindex="-1">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" data-key="add_teacher">افزودن استاد</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
      </div>
      <div class="modal-body">
        <form id="teacherForm">
          <input type="hidden" id="teacherId">
          <div class="mb-3"><input type="text" class="form-control" id="tName" placeholder="نام" required></div>
          <div class="mb-3"><input type="text" class="form-control" id="tLastname" placeholder="تخلص" required></div>
          <div class="mb-3"><input type="email" class="form-control" id="tEmail" placeholder="ایمیل" required></div>
          <div class="mb-3">
            <select class="form-select" id="tSubject" required>
              <option value="">رشته</option>
              <option value="انگلیسی">انگلیسی</option>
              <option value="ریاضی">ریاضی</option>
              <option value="کمپیوتر">کمپیوتر</option>
            </select>
          </div>
          <button type="submit" class="btn btn-primary w-100" data-key="save">ذخیره</button>
        </form>
      </div>
    </div>
  </div>
</div>

<!-- Login Modal -->
<div class="modal fade" id="loginModal" tabindex="-1">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" data-key="login">ورود ادمین</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
      </div>
      <div class="modal-body">
        <form id="loginForm">
          <div class="mb-3"><input type="email" class="form-control" placeholder="admin@example.com" required></div>
          <div class="mb-3"><input type="password" class="form-control" placeholder="123" required></div>
          <button type="submit" class="btn btn-primary w-100" data-key="login">ورود</button>
        </form>
      </div>
    </div>
  </div>
</div>

<!-- Footer -->
<footer class="footer text-center">
  <p>© 2025 آکادمی پیشرفته. تمامی حقوق محفوظ است.</p>
</footer>

<!-- Scripts -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<script>
// === داده‌ها ===
const courses = [
  {name: "انگلیسی Level 1", fee: 1000, img: "https://images.unsplash.com/photo-1456513080510-7bf3a84b82f8", category: "انگلیسی"},
  {name: "انگلیسی Level 2", fee: 1000, img: "https://images.unsplash.com/photo-1581093450021-4a7360e9a6b5", category: "انگلیسی"},
  {name: "انگلیسی Level 3", fee: 1000, img: "https://images.unsplash.com/photo-1581093450021-4a7360e9a6b5", category: "انگلیسی"},
  {name: "انگلیسی Level 4", fee: 1000, img: "https://images.unsplash.com/photo-1581093450021-4a7360e9a6b5", category: "انگلیسی"},
  {name: "انگلیسی Level 5", fee: 1000, img: "https://images.unsplash.com/photo-1581093450021-4a7360e9a6b5", category: "انگلیسی"},
  {name: "انگلیسی Level 6", fee: 1000, img: "https://images.unsplash.com/photo-1581093450021-4a7360e9a6b5", category: "انگلیسی"},
  {name: "حساب", fee: 800, img: "https://images.unsplash.com/photo-1509228628310-2e7f6a7f62b0", category: "ریاضی"},
  {name: "الجبر", fee: 800, img: "https://images.unsplash.com/photo-1509228628310-2e7f6a7f62b0", category: "ریاضی"},
  {name: "ریاضیات عالی", fee: 800, img: "https://images.unsplash.com/photo-1509228628310-2e7f6a7f62b0", category: "ریاضی"},
  {name: "ICDL", fee: 900, img: "https://images.unsplash.com/photo-1517430816045-df4b7de11d41", category: "کمپیوتر"},
  {name: "Python", fee: 900, img: "https://images.unsplash.com/photo-1526379090798-d5b6d9a718a7", category: "کمپیوتر"},
  {name: "Web Design", fee: 900, img: "https://images.unsplash.com/photo-1498050108023-c5249f4df085", category: "کمپیوتر"},
  {name: "Fullstack", fee: 900, img: "https://images.unsplash.com/photo-1461749280684-dccba630e2f6", category: "کمپیوتر"}
];

// ترجمه‌ها
const translations = {
  fa: { home: "خانه", courses: "کورس‌ها", students: "شاگردان", teachers: "اساتید", library: "کتابخانه", about: "درباره ما", contact: "تماس", dashboard: "داشبورد", login: "ورود", logout: "خروج", language: "زبان", theme: "تم", welcome: "به آکادمی پیشرفته خوش آمدید", slogan: "یادگیری مدرن، موفقیت تضمینی", register_now: "ثبت‌نام کنید", add_student: "افزودن شاگرد", add_teacher: "افزودن استاد", save: "ذخیره", send: "ارسال", total_students: "شاگرد", total_teachers: "استاد", total_courses: "کورس" },
  en: { home: "Home", courses: "Courses", students: "Students", teachers: "Teachers", library: "Library", about: "About", contact: "Contact", dashboard: "Dashboard", login: "Login", logout: "Logout", language: "Language", theme: "Theme", welcome: "Welcome to Pro Academy", slogan: "Modern Learning, Guaranteed Success", register_now: "Register Now", add_student: "Add Student", add_teacher: "Add Teacher", save: "Save", send: "Send", total_students: "Students", total_teachers: "Teachers", total_courses: "Courses" }
};

// تغییر زبان
function setLanguage(lang) {
  localStorage.setItem('lang', lang);
  document.documentElement.lang = lang;
  document.documentElement.dir = lang === 'fa' ? 'rtl' : 'ltr';
  document.querySelectorAll('[data-key]').forEach(el => {
    const key = el.getAttribute('data-key');
    el.textContent = translations[lang][key] || el.textContent;
  });
  updateCourses();
}
document.querySelectorAll('.lang-switch').forEach(el => el.addEventListener('click', () => setLanguage(el.dataset.lang)));
const savedLang = localStorage.getItem('lang') || 'fa';
setLanguage(savedLang);

// تم
function setTheme(theme) {
  localStorage.setItem('theme', theme);
  document.documentElement.setAttribute('data-theme', theme === 'dark' ? 'dark' : '');
}
document.querySelectorAll('.theme-switch').forEach(el => el.addEventListener('click', () => setTheme(el.dataset.theme)));
const savedTheme = localStorage.getItem('theme') || 'light';
setTheme(savedTheme);

// ورود
let isLoggedIn = false;
document.getElementById('loginBtn').addEventListener('click', () => new bootstrap.Modal(document.getElementById('loginModal')).show());
document.getElementById('loginForm').addEventListener('submit', e => {
  e.preventDefault();
  const email = e.target[0].value, pass = e.target[1].value;
  if (email === 'admin@example.com' && pass === '123') {
    isLoggedIn = true;
    document.getElementById('authSection').innerHTML = `<a class="nav-link" href="#" id="logoutBtn" data-key="logout">خروج</a>`;
    bootstrap.Modal.getInstance(document.getElementById('loginModal')).hide();
    document.getElementById('logoutBtn').addEventListener('click', () => {
      isLoggedIn = false;
      document.getElementById('authSection').innerHTML = `<a class="nav-link" href="#" id="loginBtn" data-key="login">ورود</a>`;
      document.getElementById('loginBtn').addEventListener('click', () => new bootstrap.Modal(document.getElementById('loginModal')).show());
    });
    loadAllData();
  } else alert('ایمیل یا رمز اشتباه!');
});

// نمایش صفحات
function showPage(pageId) {
  document.querySelectorAll('.page').forEach(p => p.classList.add('hidden'));
  document.getElementById(pageId).classList.remove('hidden');
  document.querySelectorAll('.nav-link').forEach(l => l.classList.remove('active'));
  document.querySelector(`a[href="#${pageId}"]`).classList.add('active');
}
document.querySelectorAll('.nav-link').forEach(link => {
  link.addEventListener('click', e => {
    e.preventDefault();
    const id = link.getAttribute('href').substring(1);
    showPage(id);
    if (id === 'dashboard' && !isLoggedIn) {
      alert('لطفاً ابتدا وارد شوید!');
      showPage('home');
    }
  });
});

// کورس‌ها
function updateCourses() {
  const list = document.getElementById('coursesList');
  list.innerHTML = courses.map(c => `
    <div class="col-md-4 mb-4">
      <div class="card course-card h-100">
        <img src="${c.img}" class="card-img-top" alt="${c.name}" style="height:200px; object-fit:cover;">
        <div class="card-body d-flex flex-column">
          <h5 class="card-title">${c.name}</h5>
          <p class="card-text">${c.category}</p>
          <span class="badge bg-success badge-fee">${c.fee} افغانی/ماه</span>
          <a href="#" class="btn btn-primary mt-auto" data-key="register_now">ثبت‌نام</a>
        </div>
      </div>
    </div>
  `).join('');
}
updateCourses();

// شاگردان
function loadStudents() {
  const students = JSON.parse(localStorage.getItem('students') || '[]');
  const tbody = document.querySelector('#studentsTable tbody');
  tbody.innerHTML = students.map((s, i) => `
    <tr>
      <td>${s.name}</td><td>${s.lastname}</td><td>${s.email}</td><td>${s.location}</td><td>${s.time}</td>
      <td>${s.course}</td><td>${s.fee} افغانی</td>
      <td>
        <button class="btn btn-sm btn-warning edit-student" data-id="${i}">ویرایش</button>
        <button class="btn btn-sm btn-danger delete-student" data-id="${i}">حذف</button>
      </td>
    </tr>
  `).join('');
  document.getElementById('totalStudents').textContent = students.length;
  document.getElementById('dashStudents').textContent = students.length;
}
document.getElementById('addStudentBtn').addEventListener('click', () => {
  document.getElementById('studentForm').reset();
  document.getElementById('studentId').value = '';
});
document.getElementById('studentForm').addEventListener('submit', e => {
  e.preventDefault();
  const id = document.getElementById('studentId').value;
  const course = document.getElementById('sCourse').value;
  const fee = courses.find(c => c.name === course)?.fee || 0;
  const student = {
    name: e.target[1].value, lastname: e.target[2].value, email: e.target[3].value,
    location: e.target[4].value, time: e.target[5].value, course, fee
  };
  const students = JSON.parse(localStorage.getItem('students') || '[]');
  if (id) students[id] = student; else students.push(student);
  localStorage.setItem('students', JSON.stringify(students));
  bootstrap.Modal.getInstance(document.getElementById('studentModal')).hide();
  loadStudents();
});
document.querySelector('#studentsTable tbody').addEventListener('click', e => {
  if (e.target.classList.contains('edit-student')) {
    const i = e.target.dataset.id;
    const students = JSON.parse(localStorage.getItem('students') || '[]');
    const s = students[i];
    document.getElementById('studentId').value = i;
    document.getElementById('sName').value = s.name;
    document.getElementById('sLastname').value = s.lastname;
    document.getElementById('sEmail').value = s.email;
    document.getElementById('sLocation').value = s.location;
    document.getElementById('sTime').value = s.time;
    document.getElementById('sCourse').value = s.course;
    new bootstrap.Modal(document.getElementById('studentModal')).show();
  }
  if (e.target.classList.contains('delete-student')) {
    if (confirm('آیا مطمئن هستید؟')) {
      const students = JSON.parse(localStorage.getItem('students') || '[]');
      students.splice(e.target.dataset.id, 1);
      localStorage.setItem('students', JSON.stringify(students));
      loadStudents();
    }
  }
});
document.getElementById('searchStudents').addEventListener('input', e => {
  const term = e.target.value;
  const rows = document.querySelectorAll('#studentsTable tbody tr');
  rows.forEach(r => r.style.display = r.textContent.includes(term) ? '' : 'none');
});

// اساتید
function loadTeachers() {
  const teachers = JSON.parse(localStorage.getItem('teachers') || '[]');
  const tbody = document.querySelector('#teachersTable tbody');
  tbody.innerHTML = teachers.map((t, i) => `
    <tr>
      <td>${t.name}</td><td>${t.lastname}</td><td>${t.email}</td><td>${t.subject}</td>
      <td>${t.classes || 0}</td>
      <td>
        <button class="btn btn-sm btn-warning edit-teacher" data-id="${i}">ویرایش</button>
        <button class="btn btn-sm btn-danger delete-teacher" data-id="${i}">حذف</button>
      </td>
    </tr>
  `).join('');
  document.getElementById('totalTeachers').textContent = teachers.length;
  document.getElementById('dashTeachers').textContent = teachers.length;
}
document.getElementById('teacherForm').addEventListener('submit', e => {
  e.preventDefault();
  const id = document.getElementById('teacherId').value;
  const teacher = {
    name: e.target[1].value, lastname: e.target[2].value, email: e.target[3].value,
    subject: e.target[4].value, classes: 0
  };
  const teachers = JSON.parse(localStorage.getItem('teachers') || '[]');
  if (id) teachers[id] = teacher; else teachers.push(teacher);
  localStorage.setItem('teachers', JSON.stringify(teachers));
  bootstrap.Modal.getInstance(document.getElementById('teacherModal')).hide();
  loadTeachers();
});
document.querySelector('#teachersTable tbody').addEventListener('click', e => {
  if (e.target.classList.contains('edit-teacher')) {
    const i = e.target.dataset.id;
    const teachers = JSON.parse(localStorage.getItem('teachers') || '[]');
    const t = teachers[i];
    document.getElementById('teacherId').value = i;
    document.getElementById('tName').value = t.name;
    document.getElementById('tLastname').value = t.lastname;
    document.getElementById('tEmail').value = t.email;
    document.getElementById('tSubject').value = t.subject;
    new bootstrap.Modal(document.getElementById('teacherModal')).show();
  }
  if (e.target.classList.contains('delete-teacher')) {
    if (confirm('آیا مطمئن هستید؟')) {
      const teachers = JSON.parse(localStorage.getItem('teachers') || '[]');
      teachers.splice(e.target.dataset.id, 1);
      localStorage.setItem('teachers', JSON.stringify(teachers));
      loadTeachers();
    }
  }
});

// داشبورد
function loadDashboard() {
  const students = JSON.parse(localStorage.getItem('students') || '[]');
  const revenue = students.reduce((a, s) => a + s.fee, 0);
  document.getElementById('dashRevenue').textContent = revenue.toLocaleString();
  document.getElementById('dashPending').textContent = students.filter(s => !s.paid).length;
}

// بارگذاری اولیه
function loadAllData() {
  loadStudents();
  loadTeachers();
  loadDashboard();
  // پر کردن کورس‌ها در فرم
  const select = document.getElementById('sCourse');
  select.innerHTML = '<option value="">کورس را انتخاب کنید</option>' + 
    [...new Set(courses.map(c => c.name))].map(n => `<option value="${n}">${n}</option>`).join('');
}
loadAllData();

// نمودار
const ctx = document.getElementById('revenueChart').getContext('2d');
new Chart(ctx, {
  type: 'line',
  data: {
    labels: ['فروردین', 'اردیبهشت', 'خرداد', 'تیر', 'مرداد', 'شهریور'],
    datasets: [{
      label: 'درآمد ماهانه (افغانی)',
      data: [120000, 150000, 180000, 160000, 200000, 220000],
      borderColor: '#06d6a0',
      backgroundColor: 'rgba(6, 214, 160, 0.1)',
      tension: 0.4
    }]
  }
});
</script>

</body>
</html>