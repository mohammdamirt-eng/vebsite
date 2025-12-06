
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سیستم مدیریت مدرسه شهید فهمیده</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.rtl.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #1a5276;
            --secondary-color: #c70039;
            --accent-color: #f1c40f;
            --success-color: #28a745;
            --warning-color: #ffc107;
            --danger-color: #dc3545;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .login-container {
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            overflow: hidden;
            max-width: 400px;
            width: 100%;
        }

        .main-container {
            background: #f8f9fa;
            min-height: 100vh;
            width: 100%;
            display: none;
        }

        .login-header {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: white;
            padding: 40px 30px;
            text-align: center;
        }

        .school-logo {
            width: 80px;
            height: 80px;
            background: var(--accent-color);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: var(--primary-color);
            margin: 0 auto 20px;
            font-size: 1.5rem;
        }

        .login-form {
            padding: 40px 30px;
        }

        .form-control {
            border: 2px solid #e9ecef;
            border-radius: 10px;
            padding: 12px 15px;
            margin-bottom: 20px;
            transition: all 0.3s;
        }

        .form-control:focus {
            border-color: var(--primary-color);
            box-shadow: 0 0 0 0.2rem rgba(26, 82, 118, 0.25);
        }

        .btn-login {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            border: none;
            padding: 15px;
            border-radius: 10px;
            font-weight: bold;
            width: 100%;
            color: white;
            transition: all 0.3s;
        }

        .btn-login:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(199, 0, 57, 0.3);
        }

        .user-type-selector {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        .user-type-btn {
            flex: 1;
            padding: 12px;
            border: 2px solid #e9ecef;
            border-radius: 10px;
            background: white;
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
        }

        .user-type-btn.active {
            border-color: var(--primary-color);
            background: var(--primary-color);
            color: white;
        }

        .sidebar {
            background: linear-gradient(135deg, var(--primary-color), #2c3e50);
            color: white;
            min-height: 100vh;
            position: fixed;
            width: 280px;
            height: 100vh;
            overflow-y: auto;
            z-index: 1000;
        }

        .main-content {
            margin-right: 280px;
            padding: 20px;
            min-height: 100vh;
            overflow-y: auto;
        }

        .header {
            background: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }

        .stats-card {
            background: white;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }

        .student-card {
            background: white;
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .grade-card {
            background: white;
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 15px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            border-left: 5px solid var(--primary-color);
        }

        .attendance-card {
            background: white;
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 15px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            border-left: 5px solid var(--warning-color);
        }

        .discipline-card {
            background: white;
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 15px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            border-left: 5px solid var(--danger-color);
        }

        .exam-card {
            background: white;
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 20px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            border: 2px solid var(--primary-color);
        }

        .question-card {
            background: #f8f9fa;
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 15px;
            border: 1px solid #dee2e6;
        }

        .report-card {
            background: linear-gradient(135deg, #1a5276, #2c3e50);
            color: white;
            border-radius: 15px;
            padding: 30px;
            margin-bottom: 20px;
        }

        .grade-input {
            width: 80px;
            text-align: center;
            border: 2px solid #e9ecef;
            border-radius: 8px;
            padding: 8px;
            font-weight: bold;
        }

        .grade-input:focus {
            border-color: var(--primary-color);
            outline: none;
        }

        .grade-badge {
            padding: 8px 15px;
            border-radius: 20px;
            font-weight: bold;
            font-size: 0.9rem;
        }

        .grade-excellent { background: var(--success-color); color: white; }
        .grade-good { background: var(--warning-color); color: black; }
        .grade-average { background: #fd7e14; color: white; }
        .grade-poor { background: var(--danger-color); color: white; }

        .discipline-warning { background: var(--warning-color); color: black; }
        .discipline-serious { background: var(--danger-color); color: white; }
        .discipline-solved { background: var(--success-color); color: white; }

        .attendance-present { background: var(--success-color); color: white; }
        .attendance-absent { background: var(--danger-color); color: white; }
        .attendance-late { background: var(--warning-color); color: black; }

        .user-avatar {
            width: 50px;
            height: 50px;
            background: var(--accent-color);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: var(--primary-color);
        }

        .nav-link {
            color: rgba(255,255,255,0.8);
            padding: 12px 20px;
            margin: 5px 0;
            border-radius: 8px;
            transition: all 0.3s;
        }

        .nav-link:hover, .nav-link.active {
            background: rgba(255,255,255,0.1);
            color: white;
        }

        .subject-table {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .average-display {
            font-size: 2.5rem;
            font-weight: bold;
            text-align: center;
            margin: 20px 0;
        }

        .semester-selector {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        .semester-btn {
            flex: 1;
            padding: 10px;
            border: 2px solid #e9ecef;
            border-radius: 10px;
            background: white;
            cursor: pointer;
            text-align: center;
            transition: all 0.3s;
        }

        .semester-btn.active {
            border-color: var(--primary-color);
            background: var(--primary-color);
            color: white;
        }

        .attendance-selector {
            display: flex;
            gap: 5px;
        }

        .attendance-btn {
            flex: 1;
            padding: 8px;
            border: 2px solid #e9ecef;
            border-radius: 8px;
            background: white;
            cursor: pointer;
            text-align: center;
            transition: all 0.3s;
            font-size: 0.85rem;
        }

        .attendance-btn.active {
            border-color: var(--primary-color);
            background: var(--primary-color);
            color: white;
        }

        .stats-number {
            font-size: 2.5rem;
            font-weight: bold;
            color: var(--primary-color);
        }

        .attendance-summary {
            display: flex;
            justify-content: space-around;
            margin-top: 20px;
            text-align: center;
        }

        .attendance-summary-item {
            padding: 15px;
        }

        .attendance-summary-number {
            font-size: 1.8rem;
            font-weight: bold;
        }

        .attendance-summary-present { color: var(--success-color); }
        .attendance-summary-absent { color: var(--danger-color); }
        .attendance-summary-late { color: var(--warning-color); }

        .timer {
            font-size: 2rem;
            font-weight: bold;
            color: var(--danger-color);
            text-align: center;
            padding: 10px;
            background: #fff3cd;
            border-radius: 10px;
            margin: 20px 0;
        }

        .exam-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
        }

        .exam-item {
            background: white;
            border-radius: 15px;
            padding: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transition: all 0.3s;
            border: 2px solid transparent;
        }

        .exam-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
            border-color: var(--primary-color);
        }

        .exam-status-active {
            background: var(--success-color);
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.8rem;
        }

        .exam-status-finished {
            background: var(--warning-color);
            color: black;
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.8rem;
        }

        .option-label {
            display: block;
            padding: 10px;
            margin: 5px 0;
            border: 2px solid #e9ecef;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .option-label:hover {
            background: #f8f9fa;
            border-color: var(--primary-color);
        }

        .option-label.selected {
            background: #d1ecf1;
            border-color: #17a2b8;
        }

        .option-input {
            margin-left: 10px;
        }

        .result-card {
            background: white;
            border-radius: 15px;
            padding: 30px;
            text-align: center;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .result-score {
            font-size: 3rem;
            font-weight: bold;
            color: var(--primary-color);
            margin: 20px 0;
        }

        .teacher-classes {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin-top: 10px;
        }

        .class-badge {
            background: var(--primary-color);
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.9rem;
        }

        .question-number {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 10px;
        }

        .form-check-inline {
            margin-left: 15px;
        }

        .form-check-label {
            margin-right: 5px;
        }

        .discipline-item {
            padding: 15px;
            border-bottom: 1px solid #eee;
        }

        .discipline-item:last-child {
            border-bottom: none;
        }

        .discipline-alert {
            background: #fff3cd;
            border: 1px solid #ffeaa7;
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 20px;
        }

        .notification-badge {
            position: absolute;
            top: 5px;
            right: 5px;
            background: var(--danger-color);
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            font-size: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .assignment-card {
            background: white;
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 15px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            border-left: 5px solid var(--success-color);
        }

        .message-card {
            background: white;
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 15px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            border-left: 5px solid #17a2b8;
        }

        .notification-card {
            background: white;
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 15px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            border-left: 5px solid var(--accent-color);
        }

        .filter-bar {
            background: white;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .progress-bar-custom {
            height: 10px;
            border-radius: 5px;
            margin-top: 10px;
        }

        .chart-container {
            background: white;
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .calendar-day {
            padding: 10px;
            text-align: center;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .calendar-day:hover {
            background: #f8f9fa;
        }

        .calendar-day.today {
            background: var(--primary-color);
            color: white;
        }

        .calendar-day.event {
            background: #d1ecf1;
            color: #0c5460;
        }

        .back-button {
            background: #6c757d;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            margin-bottom: 20px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .back-button:hover {
            background: #5a6268;
        }

        /* استایل برای اسکرول‌بار زیبا */
        .sidebar::-webkit-scrollbar {
            width: 8px;
        }

        .sidebar::-webkit-scrollbar-track {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 4px;
        }

        .sidebar::-webkit-scrollbar-thumb {
            background: rgba(255, 255, 255, 0.3);
            border-radius: 4px;
        }

        .sidebar::-webkit-scrollbar-thumb:hover {
            background: rgba(255, 255, 255, 0.5);
        }

        .main-content::-webkit-scrollbar {
            width: 10px;
        }

        .main-content::-webkit-scrollbar-track {
            background: #f1f1f1;
            border-radius: 4px;
        }

        .main-content::-webkit-scrollbar-thumb {
            background: var(--primary-color);
            border-radius: 4px;
        }

        .main-content::-webkit-scrollbar-thumb:hover {
            background: var(--secondary-color);
        }

        /* استایل برای موبایل */
        @media (max-width: 768px) {
            .sidebar {
                width: 100%;
                height: auto;
                position: relative;
            }

            .main-content {
                margin-right: 0;
                padding: 15px;
            }

            .main-container .row {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <!-- صفحه ورود -->
    <div class="login-container" id="loginPage">
        <div class="login-header">
            <div class="school-logo">شف</div>
            <h3>مدرسه شهید فهمیده اراک</h3>
            <p>سال تحصیلی ۱۴۰۴-۱۴۰۵</p>
        </div>

        <div class="login-form">
            <div class="user-type-selector">
                <div class="user-type-btn active" data-type="student">دانش‌آموز</div>
                <div class="user-type-btn" data-type="teacher">معلم</div>
                <div class="user-type-btn" data-type="admin">مدیریت</div>
            </div>

            <form id="loginForm">
                <input type="text" class="form-control" id="username" placeholder="نام کاربری" required>
                <input type="password" class="form-control" id="password" placeholder="رمز عبور" required>
                <button type="submit" class="btn-login">ورود به سیستم</button>
            </form>

            <div class="mt-3 text-center">
                <small class="text-muted">دانش‌آموز: student_901_01 / 123456</small><br>
                <small class="text-muted">معلم: teacher1 / 123456</small><br>
                <small class="text-muted">مدیر: admin / admin123</small>
            </div>
        </div>
    </div>

    <!-- صفحه اصلی -->
    <div class="main-container" id="mainPage">
        <div class="container-fluid">
            <div class="row">
                <!-- نوار کناری -->
                <nav class="sidebar col-md-3 col-lg-2 d-md-block">
                    <div class="position-sticky">
                        <div class="text-center p-4">
                            <div class="school-logo mx-auto mb-3">شف</div>
                            <h5>مدرسه شهید فهمیده</h5>
                            <p class="text-muted">سال تحصیلی ۱۴۰۴-۱۴۰۵</p>
                        </div>

                        <ul class="nav flex-column" id="sidebarMenu">
                            <!-- منو بر اساس نوع کاربر نمایش داده می‌شود -->
                        </ul>
                    </div>
                </nav>

                <!-- محتوای اصلی -->
                <main class="main-content col-md-9 ms-sm-auto col-lg-10 px-md-4">
                    <!-- هدر -->
                    <div class="header">
                        <div class="d-flex justify-content-between align-items-center">
                            <div>
                                <h4 id="welcomeMessage">خوش آمدید</h4>
                                <p class="text-muted mb-0" id="userRole">سیستم مدیریت مدرسه</p>
                            </div>
                            <div class="d-flex align-items-center">
                                <div class="user-avatar me-3" id="userAvatar">مد</div>
                                <div>
                                    <span class="fw-bold" id="userName">کاربر</span>
                                    <div class="text-muted small">آخرین ورود: امروز <span id="loginTime"></span></div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- محتوای داینامیک بر اساس نوع کاربر -->
                    <div id="dynamicContent">
                        <!-- محتوا اینجا بارگذاری می‌شود -->
                    </div>
                </main>
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    <script>
        // بارگیری داده‌ها از localStorage
        function loadFromLocalStorage() {
            const savedGrades = localStorage.getItem('schoolSystem_grades');
            const savedAttendance = localStorage.getItem('schoolSystem_attendance');
            const savedExams = localStorage.getItem('schoolSystem_exams');
            const savedDiscipline = localStorage.getItem('schoolSystem_discipline');
            const savedAssignments = localStorage.getItem('schoolSystem_assignments');
            const savedNotifications = localStorage.getItem('schoolSystem_notifications');
            const savedMessages = localStorage.getItem('schoolSystem_messages');
            const savedExamResults = localStorage.getItem('schoolSystem_examResults');
            const savedAllClasses = localStorage.getItem('schoolSystem_allClasses');

            if (savedGrades) grades = JSON.parse(savedGrades);
            if (savedAttendance) attendance = JSON.parse(savedAttendance);
            if (savedExams) exams = JSON.parse(savedExams);
            if (savedDiscipline) disciplineRecords = JSON.parse(savedDiscipline);
            if (savedAssignments) assignments = JSON.parse(savedAssignments);
            if (savedNotifications) notifications = JSON.parse(savedNotifications);
            if (savedMessages) messages = JSON.parse(savedMessages);
            if (savedExamResults) examResults = JSON.parse(savedExamResults);
            if (savedAllClasses) allClasses = JSON.parse(savedAllClasses);
        }

        // ذخیره داده‌ها در localStorage
        function saveToLocalStorage() {
            localStorage.setItem('schoolSystem_grades', JSON.stringify(grades));
            localStorage.setItem('schoolSystem_attendance', JSON.stringify(attendance));
            localStorage.setItem('schoolSystem_exams', JSON.stringify(exams));
            localStorage.setItem('schoolSystem_discipline', JSON.stringify(disciplineRecords));
            localStorage.setItem('schoolSystem_assignments', JSON.stringify(assignments));
            localStorage.setItem('schoolSystem_notifications', JSON.stringify(notifications));
            localStorage.setItem('schoolSystem_messages', JSON.stringify(messages));
            localStorage.setItem('schoolSystem_examResults', JSON.stringify(examResults));
            localStorage.setItem('schoolSystem_allClasses', JSON.stringify(allClasses));
        }

        // داده‌های اولیه - معلمان با کلاس‌های مشخص
        const teachers = [
            {
                id: 1,
                username: "teacher1",
                password: "123456",
                name: "استاد عبدی",
                subject: "ریاضی",
                classes: ["804", "704", "904"]
            },
            {
                id: 2,
                username: "teacher2",
                password: "123456",
                name: "استاد بادکوبه",
                subject: "علوم",
                classes: ["801", "802"]
            },
            {
                id: 3,
                username: "teacher3",
                password: "123456",
                name: "استاد روشنایی",
                subject: "ادبیات",
                classes: ["901", "902"]
            }
        ];

        // ایجاد 35 دانش‌آموز برای هر کلاس
        function generateStudentsForClass(className, count = 35) {
            const students = [];
            const firstNames = ["علی", "محمد", "حسین", "رضا", "مهدی", "امیر", "کاظم", "جواد", "مرتضی", "سجاد"];
            const lastNames = ["محمدی", "رضایی", "کریمی", "حسینی", "جعفری", "احمدی", "قاسمی", "اکبری", "امیری", "نوری"];

            for (let i = 1; i <= count; i++) {
                const firstName = firstNames[Math.floor(Math.random() * firstNames.length)];
                const lastName = lastNames[Math.floor(Math.random() * lastNames.length)];
                const studentNumber = i.toString().padStart(2, '0');

                students.push({
                    id: parseInt(className + studentNumber),
                    firstName: firstName,
                    lastName: lastName,
                    grade: className.charAt(0) + "ام",
                    class: className,
                    username: `student_${className}_${studentNumber}`,
                    password: "123456"
                });
            }
            return students;
        }

        // ایجاد دانش‌آموزان برای تمام کلاس‌ها
        let students = [];
        let allClasses = ["704", "801", "802", "804", "901", "902", "904"];

        allClasses.forEach(className => {
            students = students.concat(generateStudentsForClass(className));
        });

        // اضافه کردن چند دانش‌آموز تست
        students.push({
            id: 1001,
            firstName: "محمد",
            lastName: "رضایی",
            grade: "نهم",
            class: "901",
            username: "student_901_01",
            password: "123456"
        });

        const admins = [
            {
                username: "admin",
                password: "admin123",
                name: "مدیر مدرسه",
                type: "admin"
            }
        ];

        // داده‌های نمرات
        let grades = {};
        students.forEach(student => {
            grades[student.username] = {
                "ریاضی": { firstSemester: 16 + Math.random() * 4, secondSemester: 15 + Math.random() * 5, final: 16 + Math.random() * 4 },
                "علوم": { firstSemester: 15 + Math.random() * 5, secondSemester: 14 + Math.random() * 6, final: 15 + Math.random() * 5 },
                "ادبیات": { firstSemester: 14 + Math.random() * 6, secondSemester: 13 + Math.random() * 7, final: 14 + Math.random() * 6 }
            };
        });

        // داده‌های حضور و غیاب
        let attendance = {};
        students.forEach(student => {
            attendance[student.username] = {
                "1404/07/01": { "ریاضی": "حاضر", "علوم": "حاضر", "ادبیات": "حاضر" },
                "1404/07/02": { "ریاضی": "غایب", "علوم": "حاضر", "ادبیات": "تأخیر" },
                "1404/07/03": { "ریاضی": "حاضر", "علوم": "غایب", "ادبیات": "حاضر" },
                "1404/07/04": { "ریاضی": "حاضر", "علوم": "حاضر", "ادبیات": "حاضر" },
                "1404/07/05": { "ریاضی": "تأخیر", "علوم": "حاضر", "ادبیات": "غایب" }
            };
        });

        // داده‌های امتحانات
        let exams = [
            {
                id: 1,
                title: "امتحان ریاضی نیم‌سال اول",
                subject: "ریاضی",
                teacherId: 1,
                teacherName: "استاد عبدی",
                classes: ["804", "904"],
                duration: 30,
                date: "1404/07/10",
                status: "active",
                questions: [
                    {
                        id: 1,
                        text: "مشتق تابع f(x) = x² + 3x - 5 چیست؟",
                        options: ["2x + 3", "2x - 3", "x + 3", "x² + 3"],
                        correctAnswer: 0
                    },
                    {
                        id: 2,
                        text: "حاصل انتگرال ∫(2x + 3) dx چیست؟",
                        options: ["x² + 3x + C", "2x² + 3x + C", "x² + 3", "2x + 3 + C"],
                        correctAnswer: 0
                    },
                    {
                        id: 3,
                        text: "حاصل حد lim(x→2) (x² - 4)/(x - 2) چیست؟",
                        options: ["0", "2", "4", "تعریف نشده"],
                        correctAnswer: 2
                    }
                ]
            },
            {
                id: 2,
                title: "آزمون علوم تجربی",
                subject: "علوم",
                teacherId: 2,
                teacherName: "استاد بادکوبه",
                classes: ["801", "802"],
                duration: 45,
                date: "1404/07/12",
                status: "active",
                questions: [
                    {
                        id: 1,
                        text: "کدام یک از گزینه‌ها از عناصر تشکیل‌دهنده هوا نیست؟",
                        options: ["نیتروژن", "اکسیژن", "کربن دی‌اکسید", "آهن"],
                        correctAnswer: 3
                    }
                ]
            }
        ];

        // داده‌های موارد انضباطی
        let disciplineRecords = {
            "student_901_01": [
                {
                    id: 1,
                    date: "1404/07/01",
                    type: "warning",
                    subject: "ریاضی",
                    teacher: "استاد عبدی",
                    description: "تأخیر در تحویل تکلیف",
                    status: "فعال",
                    points: 2
                },
                {
                    id: 2,
                    date: "1404/07/03",
                    type: "serious",
                    subject: "ادبیات",
                    teacher: "استاد روشنایی",
                    description: "عدم انجام تکلیف کلاسی",
                    status: "فعال",
                    points: 5
                }
            ],
            "student_901_02": [
                {
                    id: 3,
                    date: "1404/07/02",
                    type: "warning",
                    subject: "علوم",
                    teacher: "استاد بادکوبه",
                    description: "بی‌نظمی در کلاس",
                    status: "حل شده",
                    points: 3
                }
            ]
        };

        // داده‌های تکالیف
        let assignments = {
            "student_901_01": [
                {
                    id: 1,
                    title: "تکلیف صفحه 45 ریاضی",
                    subject: "ریاضی",
                    teacher: "استاد عبدی",
                    dueDate: "1404/07/15",
                    status: "در انتظار",
                    grade: null
                },
                {
                    id: 2,
                    title: "پروژه علوم - فصل 3",
                    subject: "علوم",
                    teacher: "استاد بادکوبه",
                    dueDate: "1404/07/20",
                    status: "تحویل داده شده",
                    grade: 18
                }
            ]
        };

        // داده‌های اطلاع‌رسانی
        let notifications = {
            "student_901_01": [
                {
                    id: 1,
                    title: "امتحان ریاضی",
                    message: "امتحان ریاضی فردا ساعت 10 صبح برگزار می‌شود",
                    date: "1404/07/09",
                    read: false
                },
                {
                    id: 2,
                    title: "جلسه اولیا و مربیان",
                    message: "جلسه اولیا و مربیان روز پنجشنبه برگزار می‌شود",
                    date: "1404/07/08",
                    read: true
                }
            ]
        };

        // داده‌های پیام‌ها
        let messages = {
            "student_901_01": [
                {
                    id: 1,
                    from: "استاد عبدی",
                    message: "تکلیف ریاضی را فراموش نکنید",
                    date: "1404/07/08",
                    read: false
                },
                {
                    id: 2,
                    from: "مدیر مدرسه",
                    message: "تقدیر از عملکرد تحصیلی شما",
                    date: "1404/07/06",
                    read: true
                }
            ]
        };

        // نتایج امتحانات
        let examResults = {};

        let currentUser = null;
        let currentSemester = 'firstSemester';
        let currentAttendanceDate = '1404/07/01';
        let currentExam = null;
        let examTimer = null;
        let examTimeLeft = 0;
        let examAnswers = {};

        // مدیریت رویدادهای صفحه
        document.addEventListener('DOMContentLoaded', function() {
            loadFromLocalStorage();
            initializeLoginPage();

            // ذخیره خودکار هر 30 ثانیه
            setInterval(saveToLocalStorage, 30000);
        });

        // راه‌اندازی صفحه ورود
        function initializeLoginPage() {
            // مدیریت انتخاب نوع کاربر
            document.querySelectorAll('.user-type-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    document.querySelectorAll('.user-type-btn').forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                });
            });

            // مدیریت فرم ورود
            document.getElementById('loginForm').addEventListener('submit', function(e) {
                e.preventDefault();
                handleLogin();
            });
        }

        // مدیریت ورود به سیستم
        function handleLogin() {
            const username = document.getElementById('username').value.trim();
            const password = document.getElementById('password').value.trim();
            const userType = document.querySelector('.user-type-btn.active').dataset.type;

            if (!username || !password) {
                alert('لطفاً نام کاربری و رمز عبور را وارد کنید!');
                return;
            }

            let user = null;

            if (userType === 'student') {
                user = students.find(s => s.username === username && s.password === password);
            } else if (userType === 'teacher') {
                user = teachers.find(t => t.username === username && t.password === password);
            } else if (userType === 'admin') {
                user = admins.find(a => a.username === username && a.password === password);
            }

            if (user) {
                currentUser = { ...user, type: userType };
                showMainPage();
            } else {
                alert('نام کاربری یا رمز عبور اشتباه است!');
            }
        }

        // نمایش صفحه اصلی
        function showMainPage() {
            document.getElementById('loginPage').style.display = 'none';
            document.getElementById('mainPage').style.display = 'block';

            // به‌روزرسانی اطلاعات کاربر
            updateUserInfo();

            // بارگذاری منو و محتوای مناسب
            loadSidebarMenu();
            loadContentBasedOnUserType();
        }

        // به‌روزرسانی اطلاعات کاربر
        function updateUserInfo() {
            document.getElementById('welcomeMessage').textContent = `خوش آمدید ${currentUser.firstName || currentUser.name}`;
            document.getElementById('userName').textContent = currentUser.firstName || currentUser.name;
            document.getElementById('userRole').textContent =
                currentUser.type === 'student' ? 'دانش‌آموز' :
                currentUser.type === 'teacher' ? 'معلم' : 'مدیریت';

            document.getElementById('userAvatar').textContent =
                currentUser.type === 'student' ? 'د' :
                currentUser.type === 'teacher' ? 'م' : 'مد';

            document.getElementById('loginTime').textContent = new Date().toLocaleTimeString('fa-IR');
        }

        // بارگذاری منوی کناری
        function loadSidebarMenu() {
            const menuContainer = document.getElementById('sidebarMenu');
            let menuHTML = '';

            if (currentUser.type === 'student') {
                menuHTML = `
                    <li class="nav-item">
                        <a class="nav-link active" href="#" data-content="reportCard">
                            <i class="fas fa-chart-line me-2"></i>کارنامه تحصیلی
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="examsList">
                            <i class="fas fa-file-alt me-2"></i>امتحانات
                            ${getUnreadNotificationCount() > 0 ? `<span class="notification-badge">${getUnreadNotificationCount()}</span>` : ''}
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="examResults">
                            <i class="fas fa-poll me-2"></i>نتایج امتحانات
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="attendanceReport">
                            <i class="fas fa-calendar-check me-2"></i>حضور و غیاب
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="studentAssignments">
                            <i class="fas fa-tasks me-2"></i>تکالیف
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="disciplineRecords">
                            <i class="fas fa-exclamation-triangle me-2"></i>موارد انضباطی
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="studentNotifications">
                            <i class="fas fa-bell me-2"></i>اعلانات
                            ${getUnreadNotificationCount() > 0 ? `<span class="notification-badge">${getUnreadNotificationCount()}</span>` : ''}
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="studentMessages">
                            <i class="fas fa-envelope me-2"></i>پیام‌ها
                            ${getUnreadMessageCount() > 0 ? `<span class="notification-badge">${getUnreadMessageCount()}</span>` : ''}
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="studentInfo">
                            <i class="fas fa-user-graduate me-2"></i>اطلاعات شخصی
                        </a>
                    </li>
                `;
            } else if (currentUser.type === 'teacher') {
                menuHTML = `
                    <li class="nav-item">
                        <a class="nav-link active" href="#" data-content="teacherDashboard">
                            <i class="fas fa-tachometer-alt me-2"></i>داشبورد معلم
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="createExam">
                            <i class="fas fa-plus-circle me-2"></i>ایجاد امتحان جدید
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="manageExams">
                            <i class="fas fa-edit me-2"></i>مدیریت امتحانات
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="gradeManagement">
                            <i class="fas fa-edit me-2"></i>مدیریت نمرات
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="attendanceManagement">
                            <i class="fas fa-user-check me-2"></i>حضور و غیاب
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="assignmentManagement">
                            <i class="fas fa-tasks me-2"></i>مدیریت تکالیف
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="disciplineManagement">
                            <i class="fas fa-gavel me-2"></i>مدیریت انضباطی
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="teacherStudents">
                            <i class="fas fa-users me-2"></i>دانش‌آموزان من
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="teacherMessages">
                            <i class="fas fa-envelope me-2"></i>پیام‌ها
                        </a>
                    </li>
                `;
            } else {
                menuHTML = `
                    <li class="nav-item">
                        <a class="nav-link active" href="#" data-content="adminDashboard">
                            <i class="fas fa-tachometer-alt me-2"></i>داشبورد مدیریت
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="adminStudents">
                            <i class="fas fa-user-graduate me-2"></i>مدیریت دانش‌آموزان
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="adminTeachers">
                            <i class="fas fa-chalkboard-teacher me-2"></i>مدیریت معلمان
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="adminExams">
                            <i class="fas fa-file-alt me-2"></i>مدیریت امتحانات
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="addClass">
                            <i class="fas fa-plus me-2"></i>افزودن کلاس
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="addStudent">
                            <i class="fas fa-user-plus me-2"></i>افزودن دانش‌آموز
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="addTeacher">
                            <i class="fas fa-chalkboard-teacher me-2"></i>افزودن معلم
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="adminDiscipline">
                            <i class="fas fa-exclamation-triangle me-2"></i>مدیریت موارد انضباطی
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="adminAttendance">
                            <i class="fas fa-calendar-alt me-2"></i>گزارشات حضور و غیاب
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="adminReports">
                            <i class="fas fa-chart-bar me-2"></i>گزارشات آماری
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-content="adminSettings">
                            <i class="fas fa-cog me-2"></i>تنظیمات سیستم
                        </a>
                    </li>
                `;
            }

            menuHTML += `
                <li class="nav-item mt-4">
                    <a class="nav-link text-danger" href="#" id="logoutBtn">
                        <i class="fas fa-sign-out-alt me-2"></i>خروج از سیستم
                    </a>
                </li>
            `;

            menuContainer.innerHTML = menuHTML;

            // اضافه کردن event listener به منو
            document.querySelectorAll('.nav-link[data-content]').forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();

                    // آپدیت وضعیت فعال
                    document.querySelectorAll('.nav-link').forEach(l => l.classList.remove('active'));
                    this.classList.add('active');

                    // بارگذاری محتوا
                    const contentType = this.getAttribute('data-content');
                    loadContent(contentType);
                });
            });

            // مدیریت خروج
            document.getElementById('logoutBtn').addEventListener('click', function(e) {
                e.preventDefault();
                handleLogout();
            });
        }

        // شمارش اعلانات خوانده نشده
        function getUnreadNotificationCount() {
            const userNotifications = notifications[currentUser.username] || [];
            return userNotifications.filter(n => !n.read).length;
        }

        // شمارش پیام‌های خوانده نشده
        function getUnreadMessageCount() {
            const userMessages = messages[currentUser.username] || [];
            return userMessages.filter(m => !m.read).length;
        }

        // بارگذاری محتوا بر اساس نوع کاربر
        function loadContentBasedOnUserType() {
            if (currentUser.type === 'student') {
                loadContent('reportCard');
            } else if (currentUser.type === 'teacher') {
                loadContent('teacherDashboard');
            } else {
                loadContent('adminDashboard');
            }
        }

        // بارگذاری محتوای داینامیک
        function loadContent(contentType) {
            const contentContainer = document.getElementById('dynamicContent');
            contentContainer.innerHTML = '';

            // اضافه کردن دکمه بازگشت برای برخی صفحات
            if (contentType !== 'reportCard' && contentType !== 'teacherDashboard' && contentType !== 'adminDashboard') {
                contentContainer.innerHTML = `
                    <button class="back-button" onclick="loadContentBasedOnUserType()">
                        <i class="fas fa-arrow-right me-2"></i>بازگشت به داشبورد
                    </button>
                `;
            }

            let contentHTML = '';

            switch(contentType) {
                case 'reportCard':
                    contentHTML = generateReportCard();
                    break;
                case 'examsList':
                    contentHTML = generateExamsList();
                    break;
                case 'takeExam':
                    contentHTML = generateExamPage();
                    break;
                case 'examResults':
                    contentHTML = generateStudentExamResults();
                    break;
                case 'attendanceReport':
                    contentHTML = generateAttendanceReport();
                    break;
                case 'studentAssignments':
                    contentHTML = generateStudentAssignments();
                    break;
                case 'disciplineRecords':
                    contentHTML = generateStudentDisciplineRecords();
                    break;
                case 'studentNotifications':
                    contentHTML = generateStudentNotifications();
                    break;
                case 'studentMessages':
                    contentHTML = generateStudentMessages();
                    break;
                case 'studentInfo':
                    contentHTML = generateStudentInfo();
                    break;
                case 'teacherDashboard':
                    contentHTML = generateTeacherDashboard();
                    break;
                case 'createExam':
                    contentHTML = generateCreateExam();
                    break;
                case 'manageExams':
                    contentHTML = generateManageExams();
                    break;
                case 'gradeManagement':
                    contentHTML = generateGradeManagement();
                    break;
                case 'attendanceManagement':
                    contentHTML = generateAttendanceManagement();
                    break;
                case 'assignmentManagement':
                    contentHTML = generateAssignmentManagement();
                    break;
                case 'disciplineManagement':
                    contentHTML = generateDisciplineManagement();
                    break;
                case 'teacherStudents':
                    contentHTML = generateTeacherStudents();
                    break;
                case 'teacherMessages':
                    contentHTML = generateTeacherMessages();
                    break;
                case 'adminDashboard':
                    contentHTML = generateAdminDashboard();
                    break;
                case 'adminStudents':
                    contentHTML = generateAdminStudents();
                    break;
                case 'adminTeachers':
                    contentHTML = generateAdminTeachers();
                    break;
                case 'adminExams':
                    contentHTML = generateAdminExams();
                    break;
                case 'addClass':
                    contentHTML = generateAddClass();
                    break;
                case 'addStudent':
                    contentHTML = generateAddStudent();
                    break;
                case 'addTeacher':
                    contentHTML = generateAddTeacher();
                    break;
                case 'adminDiscipline':
                    contentHTML = generateAdminDiscipline();
                    break;
                case 'adminAttendance':
                    contentHTML = generateAdminAttendance();
                    break;
                case 'adminReports':
                    contentHTML = generateAdminReports();
                    break;
                case 'adminSettings':
                    contentHTML = generateAdminSettings();
                    break;
            }

            contentContainer.innerHTML += contentHTML;
        }

        // ==================== توابع دانش‌آموز ====================

        // تولید کارنامه دانش‌آموز
        function generateReportCard() {
            const studentGrades = grades[currentUser.username] || {};
            let total = 0;
            let subjectCount = 0;

            let gradesHTML = '';
            for (const [subject, gradeData] of Object.entries(studentGrades)) {
                const grade = gradeData[currentSemester];
                total += grade;
                subjectCount++;

                let gradeClass = 'grade-average';
                if (grade >= 18) gradeClass = 'grade-excellent';
                else if (grade >= 15) gradeClass = 'grade-good';
                else if (grade < 12) gradeClass = 'grade-poor';

                gradesHTML += `
                    <tr>
                        <td>${subject}</td>
                        <td>${grade.toFixed(1)}</td>
                        <td><span class="grade-badge ${gradeClass}">${getGradeStatus(grade)}</span></td>
                        <td>${getTeacherBySubject(subject)}</td>
                    </tr>
                `;
            }

            const average = subjectCount > 0 ? (total / subjectCount).toFixed(2) : '0.00';

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-chart-line me-2"></i>کارنامه تحصیلی</h4>

                    <div class="semester-selector">
                        <div class="semester-btn ${currentSemester === 'firstSemester' ? 'active' : ''}"
                             onclick="changeSemester('firstSemester')">نیم‌سال اول</div>
                        <div class="semester-btn ${currentSemester === 'secondSemester' ? 'active' : ''}"
                             onclick="changeSemester('secondSemester')">نیم‌سال دوم</div>
                        <div class="semester-btn ${currentSemester === 'final' ? 'active' : ''}"
                             onclick="changeSemester('final')">پایان سال</div>
                    </div>

                    <div class="report-card text-center">
                        <h5>کارنامه ${currentUser.firstName} ${currentUser.lastName}</h5>
                        <p>پایه ${currentUser.grade} - کلاس ${currentUser.class}</p>
                        <div class="average-display">${average}</div>
                        <p>معدل ${getSemesterName(currentSemester)}</p>
                    </div>

                    <div class="table-responsive mt-4">
                        <table class="table table-striped">
                            <thead>
                                <tr>
                                    <th>درس</th>
                                    <th>نمره</th>
                                    <th>وضعیت</th>
                                    <th>دبیر</th>
                                </tr>
                            </thead>
                            <tbody>
                                ${gradesHTML}
                            </tbody>
                        </table>
                    </div>
                </div>
            `;
        }

        // تولید لیست امتحانات برای دانش‌آموز
        function generateExamsList() {
            const studentExams = exams.filter(exam =>
                exam.classes.includes(currentUser.class) && exam.status === 'active'
            );

            let examsHTML = '';
            if (studentExams.length === 0) {
                examsHTML = `
                    <div class="alert alert-info">
                        <i class="fas fa-info-circle me-2"></i>
                        در حال حاضر هیچ امتحان فعالی برای شما وجود ندارد.
                    </div>
                `;
            } else {
                studentExams.forEach(exam => {
                    examsHTML += `
                        <div class="exam-item">
                            <div class="d-flex justify-content-between align-items-start mb-3">
                                <div>
                                    <h5>${exam.title}</h5>
                                    <p class="text-muted mb-1">${exam.subject} - ${exam.teacherName}</p>
                                    <p class="mb-0">تاریخ: ${exam.date} | مدت زمان: ${exam.duration} دقیقه</p>
                                </div>
                                <span class="exam-status-active">فعال</span>
                            </div>
                            <button class="btn-login w-100" onclick="startExam(${exam.id})">
                                <i class="fas fa-play me-2"></i>شروع امتحان
                            </button>
                        </div>
                    `;
                });
            }

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-file-alt me-2"></i>امتحانات فعال</h4>
                    <p class="text-muted mb-4">لیست امتحاناتی که می‌توانید در آنها شرکت کنید</p>
                    <div class="exam-list">
                        ${examsHTML}
                    </div>
                </div>
            `;
        }

        // تولید صفحه امتحان
        function generateExamPage() {
            if (!currentExam) {
                return `
                    <div class="stats-card">
                        <div class="alert alert-danger">
                            <i class="fas fa-exclamation-circle me-2"></i>
                            امتحانی یافت نشد!
                        </div>
                    </div>
                `;
            }

            let questionsHTML = '';
            currentExam.questions.forEach((question, index) => {
                questionsHTML += `
                    <div class="question-card">
                        <div class="question-number">سوال ${index + 1}: ${question.text}</div>
                        <div class="options">
                            ${question.options.map((option, optIndex) => `
                                <label class="option-label" onclick="selectAnswer(${question.id}, ${optIndex})" id="option_${question.id}_${optIndex}">
                                    ${String.fromCharCode(0x0627 + optIndex)}) ${option}
                                    <input type="radio" name="q${question.id}" class="option-input" value="${optIndex}">
                                </label>
                            `).join('')}
                        </div>
                    </div>
                `;
            });

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-file-alt me-2"></i>${currentExam.title}</h4>
                    <div class="timer">
                        <i class="fas fa-clock me-2"></i>
                        زمان باقی‌مانده: <span id="examTimer">${Math.floor(currentExam.duration)}:00</span>
                    </div>

                    <div class="alert alert-info">
                        <i class="fas fa-info-circle me-2"></i>
                        مدت زمان امتحان: ${currentExam.duration} دقیقه | درس: ${currentExam.subject}
                    </div>

                    <div class="questions-container">
                        ${questionsHTML}
                    </div>

                    <div class="text-center mt-4">
                        <button class="btn-login" style="background: var(--success-color);" onclick="submitExam()">
                            <i class="fas fa-paper-plane me-2"></i>پایان امتحان و ارسال پاسخ‌ها
                        </button>
                    </div>
                </div>
            `;
        }

        // تولید نتایج امتحانات دانش‌آموز
        function generateStudentExamResults() {
            const studentResults = examResults[currentUser.username] || [];

            let resultsHTML = '';
            if (studentResults.length === 0) {
                resultsHTML = `
                    <div class="alert alert-info">
                        <i class="fas fa-info-circle me-2"></i>
                        هنوز هیچ نتیجه امتحانی ثبت نشده است.
                    </div>
                `;
            } else {
                studentResults.forEach(result => {
                    const exam = exams.find(e => e.id === result.examId);
                    if (exam) {
                        const percentage = (result.score / exam.questions.length) * 100;
                        let gradeClass = 'grade-average';
                        if (percentage >= 90) gradeClass = 'grade-excellent';
                        else if (percentage >= 75) gradeClass = 'grade-good';
                        else if (percentage < 50) gradeClass = 'grade-poor';

                        resultsHTML += `
                            <div class="exam-item">
                                <h5>${exam.title}</h5>
                                <p class="text-muted mb-2">${exam.subject} - ${exam.teacherName}</p>
                                <div class="d-flex justify-content-between align-items-center">
                                    <div>
                                        <p class="mb-0">تاریخ: ${result.date}</p>
                                        <p class="mb-0">نمره: <strong>${result.score} از ${exam.questions.length}</strong></p>
                                    </div>
                                    <div class="result-score">
                                        <span class="grade-badge ${gradeClass}">${percentage.toFixed(1)}%</span>
                                    </div>
                                </div>
                            </div>
                        `;
                    }
                });
            }

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-poll me-2"></i>نتایج امتحانات</h4>
                    <p class="text-muted mb-4">نتایج تمام امتحانات شما</p>
                    <div class="exam-list">
                        ${resultsHTML}
                    </div>
                </div>
            `;
        }

        // تولید گزارش حضور و غیاب دانش‌آموز
        function generateAttendanceReport() {
            const studentAttendance = attendance[currentUser.username] || {};

            let attendanceHTML = '';
            let presentCount = 0, absentCount = 0, lateCount = 0;

            for (const [date, subjects] of Object.entries(studentAttendance)) {
                for (const [subject, status] of Object.entries(subjects)) {
                    let badgeClass = 'attendance-present';
                    if (status === 'غایب') {
                        badgeClass = 'attendance-absent';
                        absentCount++;
                    } else if (status === 'تأخیر') {
                        badgeClass = 'attendance-late';
                        lateCount++;
                    } else {
                        presentCount++;
                    }

                    attendanceHTML += `
                        <tr>
                            <td>${date}</td>
                            <td>${subject}</td>
                            <td><span class="grade-badge ${badgeClass}">${status}</span></td>
                        </tr>
                    `;
                }
            }

            const total = presentCount + absentCount + lateCount;
            const presentPercentage = total > 0 ? ((presentCount / total) * 100).toFixed(1) : 0;

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-calendar-check me-2"></i>گزارش حضور و غیاب</h4>

                    <div class="report-card text-center mb-4">
                        <h5>نسبت حضور ${currentUser.firstName} ${currentUser.lastName}</h5>
                        <div class="average-display">${presentPercentage}%</div>
                        <p>میزان حضور در کلاس‌ها</p>
                    </div>

                    <div class="attendance-summary mb-4">
                        <div class="attendance-summary-item">
                            <div class="attendance-summary-number attendance-summary-present">${presentCount}</div>
                            <div>حاضر</div>
                        </div>
                        <div class="attendance-summary-item">
                            <div class="attendance-summary-number attendance-summary-absent">${absentCount}</div>
                            <div>غایب</div>
                        </div>
                        <div class="attendance-summary-item">
                            <div class="attendance-summary-number attendance-summary-late">${lateCount}</div>
                            <div>تأخیر</div>
                        </div>
                    </div>

                    <div class="progress mb-4">
                        <div class="progress-bar bg-success" role="progressbar"
                             style="width: ${presentPercentage}%" aria-valuenow="${presentPercentage}"
                             aria-valuemin="0" aria-valuemax="100">
                            ${presentPercentage}%
                        </div>
                    </div>

                    <h5 class="mb-3">جزئیات حضور و غیاب:</h5>
                    <div class="table-responsive">
                        <table class="table table-striped">
                            <thead>
                                <tr>
                                    <th>تاریخ</th>
                                    <th>درس</th>
                                    <th>وضعیت</th>
                                </tr>
                            </thead>
                            <tbody>
                                ${attendanceHTML}
                            </tbody>
                        </table>
                    </div>
                </div>
            `;
        }

        // تولید تکالیف دانش‌آموز
        function generateStudentAssignments() {
            const studentAssignments = assignments[currentUser.username] || [];

            let assignmentsHTML = '';
            if (studentAssignments.length === 0) {
                assignmentsHTML = `
                    <div class="alert alert-info">
                        <i class="fas fa-info-circle me-2"></i>
                        هیچ تکلیفی برای شما ثبت نشده است.
                    </div>
                `;
            } else {
                studentAssignments.forEach(assignment => {
                    let statusBadge = '';
                    if (assignment.status === 'در انتظار') {
                        statusBadge = '<span class="grade-badge grade-average">در انتظار</span>';
                    } else if (assignment.status === 'تحویل داده شده') {
                        statusBadge = '<span class="grade-badge grade-excellent">تحویل داده شده</span>';
                    } else {
                        statusBadge = '<span class="grade-badge grade-poor">تأخیر</span>';
                    }

                    assignmentsHTML += `
                        <div class="assignment-card">
                            <div class="d-flex justify-content-between align-items-start mb-2">
                                <div>
                                    <h5>${assignment.title}</h5>
                                    <p class="text-muted mb-1">${assignment.subject} - ${assignment.teacher}</p>
                                </div>
                                ${statusBadge}
                            </div>
                            <p class="mb-2">مهلت تحویل: ${assignment.dueDate}</p>
                            ${assignment.grade ? `<p class="mb-0">نمره: <strong>${assignment.grade}</strong> از 20</p>` : ''}
                        </div>
                    `;
                });
            }

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-tasks me-2"></i>تکالیف</h4>
                    <p class="text-muted mb-4">لیست تکالیف شما</p>
                    <div>
                        ${assignmentsHTML}
                    </div>
                </div>
            `;
        }

        // تولید موارد انضباطی دانش‌آموز
        function generateStudentDisciplineRecords() {
            const studentDiscipline = disciplineRecords[currentUser.username] || [];

            let disciplineHTML = '';
            if (studentDiscipline.length === 0) {
                disciplineHTML = `
                    <div class="alert alert-success">
                        <i class="fas fa-check-circle me-2"></i>
                        مورد انضباطی برای شما ثبت نشده است.
                    </div>
                `;
            } else {
                studentDiscipline.forEach(record => {
                    const badgeClass = record.type === 'warning' ? 'discipline-warning' :
                                     record.type === 'serious' ? 'discipline-serious' : 'discipline-solved';
                    const badgeText = record.type === 'warning' ? 'هشدار' :
                                    record.type === 'serious' ? 'جدی' : 'حل شده';

                    disciplineHTML += `
                        <div class="discipline-item">
                            <div class="d-flex justify-content-between align-items-start">
                                <div>
                                    <h6>${record.subject} - ${record.teacher}</h6>
                                    <p class="mb-1">${record.description}</p>
                                    <small class="text-muted">تاریخ: ${record.date} | امتیاز منفی: ${record.points}</small>
                                </div>
                                <span class="grade-badge ${badgeClass}">${badgeText}</span>
                            </div>
                        </div>
                    `;
                });
            }

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-exclamation-triangle me-2"></i>موارد انضباطی</h4>
                    <p class="text-muted mb-4">موارد انضباطی ثبت شده برای ${currentUser.firstName} ${currentUser.lastName}</p>
                    <div class="discipline-card">
                        ${disciplineHTML}
                    </div>
                </div>
            `;
        }

        // تولید اعلانات دانش‌آموز
        function generateStudentNotifications() {
            const studentNotifications = notifications[currentUser.username] || [];

            let notificationsHTML = '';
            if (studentNotifications.length === 0) {
                notificationsHTML = `
                    <div class="alert alert-info">
                        <i class="fas fa-info-circle me-2"></i>
                        هیچ اعلانی وجود ندارد.
                    </div>
                `;
            } else {
                studentNotifications.forEach(notification => {
                    const readClass = notification.read ? 'text-muted' : 'fw-bold';
                    notificationsHTML += `
                        <div class="notification-card" onclick="markNotificationAsRead(${notification.id})">
                            <div class="d-flex justify-content-between align-items-start">
                                <div class="${readClass}">
                                    <h6>${notification.title}</h6>
                                    <p class="mb-1">${notification.message}</p>
                                    <small class="text-muted">تاریخ: ${notification.date}</small>
                                </div>
                                ${!notification.read ? '<span class="notification-badge">جدید</span>' : ''}
                            </div>
                        </div>
                    `;
                });
            }

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-bell me-2"></i>اعلانات</h4>
                    <p class="text-muted mb-4">آخرین اعلانات و اطلاعیه‌ها</p>
                    <div>
                        ${notificationsHTML}
                    </div>
                    <div class="text-center mt-4">
                        <button class="btn-login" onclick="markAllNotificationsAsRead()">
                            <i class="fas fa-check-double me-2"></i>علامت‌گذاری همه به عنوان خوانده شده
                        </button>
                    </div>
                </div>
            `;
        }

        // تولید پیام‌های دانش‌آموز
        function generateStudentMessages() {
            const studentMessages = messages[currentUser.username] || [];

            let messagesHTML = '';
            if (studentMessages.length === 0) {
                messagesHTML = `
                    <div class="alert alert-info">
                        <i class="fas fa-info-circle me-2"></i>
                        هیچ پیامی وجود ندارد.
                    </div>
                `;
            } else {
                studentMessages.forEach(message => {
                    const readClass = message.read ? 'text-muted' : 'fw-bold';
                    messagesHTML += `
                        <div class="message-card" onclick="markMessageAsRead(${message.id})">
                            <div class="d-flex justify-content-between align-items-start">
                                <div class="${readClass}">
                                    <h6>از: ${message.from}</h6>
                                    <p class="mb-1">${message.message}</p>
                                    <small class="text-muted">تاریخ: ${message.date}</small>
                                </div>
                                ${!message.read ? '<span class="notification-badge">جدید</span>' : ''}
                            </div>
                        </div>
                    `;
                });
            }

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-envelope me-2"></i>پیام‌ها</h4>
                    <p class="text-muted mb-4">پیام‌های دریافتی شما</p>
                    <div>
                        ${messagesHTML}
                    </div>
                    <div class="text-center mt-4">
                        <button class="btn-login" onclick="markAllMessagesAsRead()">
                            <i class="fas fa-check-double me-2"></i>علامت‌گذاری همه به عنوان خوانده شده
                        </button>
                    </div>
                </div>
            `;
        }

        // تولید اطلاعات شخصی دانش‌آموز
        function generateStudentInfo() {
            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-user-graduate me-2"></i>اطلاعات شخصی</h4>

                    <div class="row">
                        <div class="col-md-3 text-center">
                            <div class="user-avatar mx-auto mb-3" style="width: 100px; height: 100px; font-size: 2rem;">
                                ${currentUser.firstName.charAt(0)}
                            </div>
                        </div>
                        <div class="col-md-9">
                            <div class="row mb-3">
                                <div class="col-md-6">
                                    <p><strong>نام:</strong> ${currentUser.firstName}</p>
                                    <p><strong>نام خانوادگی:</strong> ${currentUser.lastName}</p>
                                    <p><strong>کد ملی:</strong> ۰۰۱۲۳۴۵۶۷۸</p>
                                </div>
                                <div class="col-md-6">
                                    <p><strong>پایه:</strong> ${currentUser.grade}</p>
                                    <p><strong>کلاس:</strong> ${currentUser.class}</p>
                                    <p><strong>شماره دانش‌آموزی:</strong> ${currentUser.id}</p>
                                </div>
                            </div>

                            <h5 class="mt-4 mb-3">اطلاعات تماس:</h5>
                            <div class="row">
                                <div class="col-md-6">
                                    <p><strong>تلفن:</strong> ۰۹۱۲۳۴۵۶۷۸۹</p>
                                    <p><strong>آدرس:</strong> اراک، خیابان امام، کوچه ۱۰</p>
                                </div>
                                <div class="col-md-6">
                                    <p><strong>پست الکترونیک:</strong> student@shahidfahmideh.ir</p>
                                    <p><strong>نام پدر:</strong> احمد</p>
                                </div>
                            </div>

                            <div class="alert alert-info mt-4">
                                <i class="fas fa-info-circle me-2"></i>
                                برای تغییر اطلاعات شخصی با مدیر مدرسه تماس بگیرید.
                            </div>
                        </div>
                    </div>
                </div>
            `;
        }

        // ==================== توابع معلم ====================

        // تولید داشبورد معلم
        function generateTeacherDashboard() {
            const teacherClasses = currentUser.classes || [];
            const teacherExams = exams.filter(exam => exam.teacherId === currentUser.id);
            const teacherStudents = students.filter(student =>
                teacherClasses.includes(student.class)
            );

            let classesHTML = '';
            teacherClasses.forEach(className => {
                const classStudents = teacherStudents.filter(s => s.class === className);
                classesHTML += `
                    <div class="col-md-4">
                        <div class="stats-card text-center">
                            <div class="stats-number">${className}</div>
                            <div>کلاس</div>
                            <p class="mt-2 mb-0">${classStudents.length} دانش‌آموز</p>
                        </div>
                    </div>
                `;
            });

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-tachometer-alt me-2"></i>داشبورد ${currentUser.name}</h4>

                    <div class="row mb-4">
                        <div class="col-md-12">
                            <div class="stats-card">
                                <h5><i class="fas fa-chalkboard-teacher me-2"></i>اطلاعات معلم</h5>
                                <div class="row mt-3">
                                    <div class="col-md-6">
                                        <p><strong>نام:</strong> ${currentUser.name}</p>
                                        <p><strong>درس:</strong> ${currentUser.subject}</p>
                                    </div>
                                    <div class="col-md-6">
                                        <p><strong>تعداد کلاس‌ها:</strong> ${teacherClasses.length}</p>
                                        <p><strong>تعداد دانش‌آموزان:</strong> ${teacherStudents.length}</p>
                                    </div>
                                </div>
                                <div class="teacher-classes">
                                    ${teacherClasses.map(cls => `<span class="class-badge">${cls}</span>`).join('')}
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="row mb-4">
                        <div class="col-md-4">
                            <div class="stats-card text-center">
                                <div class="stats-number">${teacherExams.length}</div>
                                <div>امتحانات طراحی شده</div>
                            </div>
                        </div>
                        <div class="col-md-4">
                            <div class="stats-card text-center">
                                <div class="stats-number">${teacherStudents.length}</div>
                                <div>دانش‌آموزان</div>
                            </div>
                        </div>
                        <div class="col-md-4">
                            <div class="stats-card text-center">
                                <div class="stats-number">${teacherClasses.length}</div>
                                <div>کلاس‌ها</div>
                            </div>
                        </div>
                    </div>

                    <h5 class="mb-3">کلاس‌های شما:</h5>
                    <div class="row">
                        ${classesHTML}
                    </div>

                    <div class="mt-4 text-center">
                        <button class="btn-login me-3" onclick="loadContent('disciplineManagement')">
                            <i class="fas fa-gavel me-2"></i>ثبت مورد انضباطی
                        </button>
                        <button class="btn-login me-3" style="background: var(--warning-color);" onclick="loadContent('teacherStudents')">
                            <i class="fas fa-users me-2"></i>مشاهده دانش‌آموزان
                        </button>
                        <button class="btn-login" style="background: var(--success-color);" onclick="loadContent('createExam')">
                            <i class="fas fa-plus-circle me-2"></i>ایجاد امتحان جدید
                        </button>
                    </div>
                </div>
            `;
        }

        // تولید صفحه ایجاد امتحان جدید
        function generateCreateExam() {
            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-plus-circle me-2"></i>ایجاد امتحان جدید</h4>

                    <div class="row mb-4">
                        <div class="col-md-6">
                            <div class="form-group mb-3">
                                <label for="examTitle">عنوان امتحان:</label>
                                <input type="text" id="examTitle" class="form-control" placeholder="مثال: امتحان ریاضی نیم‌سال اول">
                            </div>

                            <div class="form-group mb-3">
                                <label for="examSubject">درس:</label>
                                <input type="text" id="examSubject" class="form-control" value="${currentUser.subject}" readonly>
                            </div>

                            <div class="form-group mb-3">
                                <label for="examDuration">مدت زمان (دقیقه):</label>
                                <input type="number" id="examDuration" class="form-control" value="30" min="5" max="180">
                            </div>
                        </div>

                        <div class="col-md-6">
                            <div class="form-group mb-3">
                                <label for="examDate">تاریخ برگزاری:</label>
                                <input type="text" id="examDate" class="form-control" placeholder="مثال: 1404/07/10">
                            </div>

                            <div class="form-group mb-3">
                                <label>کلاس‌های مورد نظر:</label>
                                <div class="form-check">
                                    ${currentUser.classes.map(className => `
                                        <div class="form-check form-check-inline">
                                            <input class="form-check-input class-checkbox" type="checkbox" id="class_${className}" value="${className}" checked>
                                            <label class="form-check-label" for="class_${className}">${className}</label>
                                        </div>
                                    `).join('')}
                                </div>
                            </div>
                        </div>
                    </div>

                    <div id="questionsContainer">
                        <h5 class="mb-3">سوالات:</h5>
                        <div class="question-card" id="questionTemplate">
                            <div class="d-flex justify-content-between align-items-center mb-3">
                                <h6>سوال 1</h6>
                                <button class="btn btn-danger btn-sm" onclick="removeQuestion(this)">
                                    <i class="fas fa-trash me-1"></i>حذف سوال
                                </button>
                            </div>
                            <div class="form-group mb-3">
                                <label>متن سوال:</label>
                                <textarea class="form-control question-text" rows="2" placeholder="متن سوال را وارد کنید..."></textarea>
                            </div>
                            <div class="form-group mb-3">
                                <label>گزینه‌ها:</label>
                                ${['الف', 'ب', 'ج', 'د'].map((letter, index) => `
                                    <div class="input-group mb-2">
                                        <span class="input-group-text">${letter}</span>
                                        <input type="text" class="form-control option-input" placeholder="متن گزینه ${letter}">
                                        <div class="input-group-text">
                                            <input class="form-check-input correct-answer" type="radio" name="correctAnswer" value="${index}">
                                        </div>
                                    </div>
                                `).join('')}
                            </div>
                        </div>
                    </div>

                    <div class="text-center mb-4">
                        <button class="btn-login" onclick="addQuestion()">
                            <i class="fas fa-plus me-2"></i>افزودن سوال جدید
                        </button>
                    </div>

                    <div class="text-center">
                        <button class="btn-login" style="background: var(--success-color);" onclick="saveExam()">
                            <i class="fas fa-save me-2"></i>ذخیره امتحان
                        </button>
                    </div>
                </div>
            `;
        }

        // تولید مدیریت امتحانات معلم
        function generateManageExams() {
            const teacherExams = exams.filter(exam => exam.teacherId === currentUser.id);

            let examsHTML = '';
            if (teacherExams.length === 0) {
                examsHTML = `
                    <div class="alert alert-info">
                        <i class="fas fa-info-circle me-2"></i>
                        هنوز امتحانی ایجاد نکرده‌اید.
                    </div>
                `;
            } else {
                teacherExams.forEach(exam => {
                    const statusBadge = exam.status === 'active' ?
                        '<span class="exam-status-active">فعال</span>' :
                        '<span class="exam-status-finished">پایان یافته</span>';

                    examsHTML += `
                        <div class="exam-item">
                            <div class="d-flex justify-content-between align-items-start mb-3">
                                <div>
                                    <h5>${exam.title}</h5>
                                    <p class="text-muted mb-1">${exam.subject} - کلاس‌های: ${exam.classes.join(', ')}</p>
                                    <p class="mb-0">تاریخ: ${exam.date} | مدت زمان: ${exam.duration} دقیقه</p>
                                    <p class="mb-0">تعداد سوالات: ${exam.questions.length}</p>
                                </div>
                                <div>
                                    ${statusBadge}
                                    <div class="mt-2">
                                        <button class="btn btn-sm btn-outline-primary" onclick="editExam(${exam.id})">
                                            <i class="fas fa-edit me-1"></i>ویرایش
                                        </button>
                                        <button class="btn btn-sm btn-outline-danger" onclick="deleteExam(${exam.id})">
                                            <i class="fas fa-trash me-1"></i>حذف
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    `;
                });
            }

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-edit me-2"></i>مدیریت امتحانات</h4>
                    <p class="text-muted mb-4">امتحانات ایجاد شده توسط شما</p>
                    <div class="exam-list">
                        ${examsHTML}
                    </div>
                </div>
            `;
        }

        // تولید مدیریت نمرات معلم
        function generateGradeManagement() {
            const teacherStudents = students.filter(student =>
                currentUser.classes.includes(student.class)
            );

            let studentsHTML = '';
            teacherStudents.forEach(student => {
                const studentGrades = grades[student.username] || {};
                const currentGrade = studentGrades[currentUser.subject] || {};
                const gradeValue = currentGrade[currentSemester] || 0;

                studentsHTML += `
                    <div class="student-card">
                        <div class="row align-items-center">
                            <div class="col-md-4">
                                <h6>${student.firstName} ${student.lastName}</h6>
                                <p class="text-muted mb-0">کلاس ${student.class}</p>
                            </div>
                            <div class="col-md-4">
                                <div class="semester-selector">
                                    <div class="semester-btn ${currentSemester === 'firstSemester' ? 'active' : ''}"
                                         onclick="changeStudentSemester('firstSemester', '${student.username}')">نیم‌سال اول</div>
                                    <div class="semester-btn ${currentSemester === 'secondSemester' ? 'active' : ''}"
                                         onclick="changeStudentSemester('secondSemester', '${student.username}')">نیم‌سال دوم</div>
                                    <div class="semester-btn ${currentSemester === 'final' ? 'active' : ''}"
                                         onclick="changeStudentSemester('final', '${student.username}')">پایان سال</div>
                                </div>
                            </div>
                            <div class="col-md-4">
                                <input type="number" class="grade-input"
                                       value="${gradeValue.toFixed(1)}"
                                       step="0.25" min="0" max="20"
                                       onchange="updateStudentGrade('${student.username}', this.value)">
                                <span class="grade-badge ${getGradeClass(gradeValue)} ms-2">
                                    ${getGradeStatus(gradeValue)}
                                </span>
                            </div>
                        </div>
                    </div>
                `;
            });

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-edit me-2"></i>مدیریت نمرات</h4>
                    <p class="text-muted mb-4">نمرات دانش‌آموزان کلاس ${currentUser.classes.join('، ')} - درس ${currentUser.subject}</p>
                    <div class="mb-4">
                        <div class="alert alert-info">
                            <i class="fas fa-info-circle me-2"></i>
                            برای تغییر نمره هر دانش‌آموز، عدد را ویرایش کرده و Enter بزنید.
                        </div>
                    </div>
                    ${studentsHTML}
                </div>
            `;
        }

        // تولید مدیریت حضور و غیاب معلم
        function generateAttendanceManagement() {
            const teacherStudents = students.filter(student =>
                currentUser.classes.includes(student.class)
            );

            let studentsHTML = '';
            teacherStudents.forEach(student => {
                const studentAttendance = attendance[student.username] || {};
                const todayAttendance = studentAttendance[currentAttendanceDate] || {};
                const attendanceValue = todayAttendance[currentUser.subject] || 'حاضر';

                studentsHTML += `
                    <div class="student-card">
                        <div class="row align-items-center">
                            <div class="col-md-3">
                                <h6>${student.firstName} ${student.lastName}</h6>
                                <p class="text-muted mb-0">کلاس ${student.class}</p>
                            </div>
                            <div class="col-md-6">
                                <div class="attendance-selector">
                                    <div class="attendance-btn ${attendanceValue === 'حاضر' ? 'active' : ''}"
                                         onclick="updateAttendance('${student.username}', 'حاضر')">حاضر</div>
                                    <div class="attendance-btn ${attendanceValue === 'غایب' ? 'active' : ''}"
                                         onclick="updateAttendance('${student.username}', 'غایب')">غایب</div>
                                    <div class="attendance-btn ${attendanceValue === 'تأخیر' ? 'active' : ''}"
                                         onclick="updateAttendance('${student.username}', 'تأخیر')">تأخیر</div>
                                    <div class="attendance-btn ${attendanceValue === 'معذور' ? 'active' : ''}"
                                         onclick="updateAttendance('${student.username}', 'معذور')">معذور</div>
                                </div>
                            </div>
                            <div class="col-md-3">
                                <span class="grade-badge ${getAttendanceClass(attendanceValue)}">
                                    ${attendanceValue}
                                </span>
                            </div>
                        </div>
                    </div>
                `;
            });

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-user-check me-2"></i>مدیریت حضور و غیاب</h4>

                    <div class="filter-bar mb-4">
                        <div class="row">
                            <div class="col-md-6">
                                <label>تاریخ:</label>
                                <input type="text" id="attendanceDate" class="form-control"
                                       value="${currentAttendanceDate}"
                                       onchange="changeAttendanceDate(this.value)">
                            </div>
                            <div class="col-md-6">
                                <label>درس:</label>
                                <input type="text" class="form-control" value="${currentUser.subject}" readonly>
                            </div>
                        </div>
                    </div>

                    <div class="mb-4">
                        <div class="alert alert-info">
                            <i class="fas fa-info-circle me-2"></i>
                            برای ثبت وضعیت حضور و غیاب هر دانش‌آموز روی گزینه مورد نظر کلیک کنید.
                        </div>
                    </div>
                    ${studentsHTML}
                </div>
            `;
        }

        // تولید مدیریت تکالیف معلم
        function generateAssignmentManagement() {
            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-tasks me-2"></i>مدیریت تکالیف</h4>

                    <div class="row mb-4">
                        <div class="col-md-6">
                            <div class="form-group mb-3">
                                <label for="assignmentTitle">عنوان تکلیف:</label>
                                <input type="text" id="assignmentTitle" class="form-control" placeholder="مثال: تکلیف صفحه 45">
                            </div>

                            <div class="form-group mb-3">
                                <label for="assignmentDescription">شرح تکلیف:</label>
                                <textarea id="assignmentDescription" class="form-control" rows="3" placeholder="توضیحات تکلیف..."></textarea>
                            </div>
                        </div>

                        <div class="col-md-6">
                            <div class="form-group mb-3">
                                <label for="assignmentDueDate">مهلت تحویل:</label>
                                <input type="text" id="assignmentDueDate" class="form-control" placeholder="1404/07/15">
                            </div>

                            <div class="form-group mb-3">
                                <label>کلاس‌های مورد نظر:</label>
                                <div class="form-check">
                                    ${currentUser.classes.map(className => `
                                        <div class="form-check form-check-inline">
                                            <input class="form-check-input assignment-class-checkbox" type="checkbox" id="assignment_class_${className}" value="${className}" checked>
                                            <label class="form-check-label" for="assignment_class_${className}">${className}</label>
                                        </div>
                                    `).join('')}
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="text-center">
                        <button class="btn-login" style="background: var(--success-color);" onclick="createAssignment()">
                            <i class="fas fa-plus me-2"></i>ایجاد تکلیف جدید
                        </button>
                    </div>
                </div>
            `;
        }

        // تولید مدیریت موارد انضباطی برای معلم
        function generateDisciplineManagement() {
            const teacherStudents = students.filter(student =>
                currentUser.classes.includes(student.class)
            );

            let studentsHTML = '';
            teacherStudents.forEach(student => {
                const studentDiscipline = disciplineRecords[student.username] || [];
                const activeDiscipline = studentDiscipline.filter(d => d.status === 'فعال');

                studentsHTML += `
                    <div class="student-card">
                        <div class="row align-items-center">
                            <div class="col-md-4">
                                <h6>${student.firstName} ${student.lastName}</h6>
                                <p class="text-muted mb-0">کلاس ${student.class}</p>
                                <p class="mb-0">موارد فعال: ${activeDiscipline.length}</p>
                            </div>
                            <div class="col-md-8">
                                <div class="row">
                                    <div class="col-md-3">
                                        <select class="form-control mb-2" id="disciplineType_${student.username}">
                                            <option value="warning">هشدار</option>
                                            <option value="serious">مورد جدی</option>
                                        </select>
                                    </div>
                                    <div class="col-md-3">
                                        <select class="form-control mb-2" id="disciplinePoints_${student.username}">
                                            <option value="1">۱ امتیاز</option>
                                            <option value="2">۲ امتیاز</option>
                                            <option value="3">۳ امتیاز</option>
                                            <option value="5">۵ امتیاز</option>
                                            <option value="10">۱۰ امتیاز</option>
                                        </select>
                                    </div>
                                    <div class="col-md-6">
                                        <input type="text" class="form-control mb-2" id="disciplineDesc_${student.username}"
                                               placeholder="شرح مورد انضباطی">
                                    </div>
                                </div>
                                <button class="btn-login btn-sm" onclick="addDisciplineRecord('${student.username}')">
                                    <i class="fas fa-plus me-2"></i>ثبت مورد انضباطی
                                </button>
                            </div>
                        </div>
                    </div>
                `;
            });

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-gavel me-2"></i>مدیریت موارد انضباطی</h4>
                    <p class="text-muted mb-4">ثبت موارد انضباطی برای دانش‌آموزان کلاس ${currentUser.classes.join('، ')}</p>
                    <div class="alert alert-warning mb-4">
                        <i class="fas fa-exclamation-triangle me-2"></i>
                        موارد انضباطی بر روی سابقه تحصیلی دانش‌آموزان تأثیرگذار است.
                    </div>
                    ${studentsHTML}
                </div>
            `;
        }

        // تولید لیست دانش‌آموزان معلم
        function generateTeacherStudents() {
            const teacherStudents = students.filter(student =>
                currentUser.classes.includes(student.class)
            );

            let studentsHTML = '';
            teacherStudents.forEach(student => {
                const studentGrades = grades[student.username] || {};
                const currentGrade = studentGrades[currentUser.subject] || {};
                const gradeValue = currentGrade[currentSemester] || 0;

                studentsHTML += `
                    <div class="student-card">
                        <div class="row align-items-center">
                            <div class="col-md-2">
                                <div class="user-avatar">
                                    ${student.firstName.charAt(0)}
                                </div>
                            </div>
                            <div class="col-md-3">
                                <h6>${student.firstName} ${student.lastName}</h6>
                                <p class="text-muted mb-0">کلاس ${student.class}</p>
                                <p class="mb-0">کد: ${student.username}</p>
                            </div>
                            <div class="col-md-3">
                                <p class="mb-1">نمره ${currentUser.subject}:</p>
                                <span class="grade-badge ${getGradeClass(gradeValue)}">
                                    ${gradeValue.toFixed(1)} - ${getGradeStatus(gradeValue)}
                                </span>
                            </div>
                            <div class="col-md-4">
                                <div class="d-flex gap-2">
                                    <button class="btn btn-outline-primary btn-sm" onclick="viewStudentDetails('${student.username}')">
                                        <i class="fas fa-eye me-1"></i>مشاهده
                                    </button>
                                    <button class="btn btn-outline-success btn-sm" onclick="sendMessageToStudent('${student.username}')">
                                        <i class="fas fa-envelope me-1"></i>پیام
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
            });

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-users me-2"></i>دانش‌آموزان من</h4>
                    <p class="text-muted mb-4">لیست دانش‌آموزان کلاس ${currentUser.classes.join('، ')}</p>

                    <div class="filter-bar mb-4">
                        <div class="row">
                            <div class="col-md-4">
                                <input type="text" class="form-control" placeholder="جستجوی دانش‌آموز..." id="studentSearch">
                            </div>
                            <div class="col-md-4">
                                <select class="form-control" id="classFilter">
                                    <option value="">همه کلاس‌ها</option>
                                    ${currentUser.classes.map(cls => `<option value="${cls}">${cls}</option>`).join('')}
                                </select>
                            </div>
                            <div class="col-md-4">
                                <button class="btn-login w-100" onclick="searchStudents()">
                                    <i class="fas fa-search me-2"></i>جستجو
                                </button>
                            </div>
                        </div>
                    </div>

                    ${studentsHTML}
                </div>
            `;
        }

        // تولید پیام‌های معلم
        function generateTeacherMessages() {
            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-envelope me-2"></i>پیام‌ها</h4>

                    <div class="row mb-4">
                        <div class="col-md-6">
                            <div class="form-group mb-3">
                                <label for="messageRecipient">گیرنده:</label>
                                <select class="form-control" id="messageRecipient">
                                    <option value="">انتخاب دانش‌آموز</option>
                                    ${students.filter(s => currentUser.classes.includes(s.class))
                                        .map(s => `<option value="${s.username}">${s.firstName} ${s.lastName} - ${s.class}</option>`)
                                        .join('')}
                                </select>
                            </div>
                        </div>
                        <div class="col-md-6">
                            <div class="form-group mb-3">
                                <label for="messageSubject">عنوان:</label>
                                <input type="text" id="messageSubject" class="form-control" placeholder="عنوان پیام">
                            </div>
                        </div>
                    </div>

                    <div class="form-group mb-3">
                        <label for="messageContent">متن پیام:</label>
                        <textarea id="messageContent" class="form-control" rows="5" placeholder="متن پیام خود را بنویسید..."></textarea>
                    </div>

                    <div class="text-center">
                        <button class="btn-login" style="background: var(--success-color);" onclick="sendMessage()">
                            <i class="fas fa-paper-plane me-2"></i>ارسال پیام
                        </button>
                    </div>
                </div>
            `;
        }

        // ==================== توابع مدیر ====================

        // تولید داشبورد مدیریت
        function generateAdminDashboard() {
            const totalStudents = students.length;
            const totalTeachers = teachers.length;
            const totalClasses = allClasses.length;

            // محاسبه آمار
            let activeExams = 0;
            let totalDiscipline = 0;
            let totalAssignments = 0;

            exams.forEach(exam => {
                if (exam.status === 'active') activeExams++;
            });

            Object.values(disciplineRecords).forEach(records => {
                totalDiscipline += records.length;
            });

            Object.values(assignments).forEach(assignmentList => {
                totalAssignments += assignmentList.length;
            });

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-tachometer-alt me-2"></i>داشبورد مدیریت مدرسه</h4>

                    <div class="row mb-4">
                        <div class="col-md-3">
                            <div class="stats-card text-center">
                                <div class="stats-number">${totalStudents}</div>
                                <div>دانش‌آموز</div>
                            </div>
                        </div>
                        <div class="col-md-3">
                            <div class="stats-card text-center">
                                <div class="stats-number">${totalTeachers}</div>
                                <div>معلم</div>
                            </div>
                        </div>
                        <div class="col-md-3">
                            <div class="stats-card text-center">
                                <div class="stats-number">${totalClasses}</div>
                                <div>کلاس</div>
                            </div>
                        </div>
                        <div class="col-md-3">
                            <div class="stats-card text-center">
                                <div class="stats-number">${activeExams}</div>
                                <div>امتحان فعال</div>
                            </div>
                        </div>
                    </div>

                    <div class="row mb-4">
                        <div class="col-md-6">
                            <div class="stats-card">
                                <h5><i class="fas fa-chart-pie me-2"></i>آمار سریع</h5>
                                <div class="row mt-3">
                                    <div class="col-md-6">
                                        <p><i class="fas fa-exclamation-triangle text-warning me-2"></i>موارد انضباطی: ${totalDiscipline}</p>
                                        <p><i class="fas fa-tasks text-success me-2"></i>تکالیف: ${totalAssignments}</p>
                                    </div>
                                    <div class="col-md-6">
                                        <p><i class="fas fa-calendar-check text-primary me-2"></i>امتحانات: ${exams.length}</p>
                                        <p><i class="fas fa-bell text-danger me-2"></i>اعلانات: ${Object.values(notifications).flat().length}</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="col-md-6">
                            <div class="stats-card">
                                <h5><i class="fas fa-calendar me-2"></i>رویدادهای پیش‌رو</h5>
                                <div class="mt-3">
                                    <div class="event-item mb-2">
                                        <strong>امتحان ریاضی:</strong> 1404/07/10
                                    </div>
                                    <div class="event-item mb-2">
                                        <strong>جلسه اولیا و مربیان:</strong> 1404/07/15
                                    </div>
                                    <div class="event-item">
                                        <strong>تحویل کارنامه:</strong> 1404/07/20
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="row">
                        <div class="col-md-12">
                            <div class="stats-card">
                                <h5><i class="fas fa-bolt me-2"></i>دسترسی سریع</h5>
                                <div class="row mt-3 text-center">
                                    <div class="col-md-3">
                                        <button class="btn-login w-100 mb-2" onclick="loadContent('adminStudents')">
                                            <i class="fas fa-user-graduate me-2"></i>دانش‌آموزان
                                        </button>
                                    </div>
                                    <div class="col-md-3">
                                        <button class="btn-login w-100 mb-2" style="background: var(--warning-color);" onclick="loadContent('adminTeachers')">
                                            <i class="fas fa-chalkboard-teacher me-2"></i>معلمان
                                        </button>
                                    </div>
                                    <div class="col-md-3">
                                        <button class="btn-login w-100 mb-2" style="background: var(--success-color);" onclick="loadContent('addClass')">
                                            <i class="fas fa-plus me-2"></i>افزودن کلاس
                                        </button>
                                    </div>
                                    <div class="col-md-3">
                                        <button class="btn-login w-100 mb-2" style="background: #6c757d;" onclick="loadContent('adminReports')">
                                            <i class="fas fa-chart-bar me-2"></i>گزارشات
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            `;
        }

        // تولید مدیریت دانش‌آموزان برای مدیر
        function generateAdminStudents() {
            let studentsHTML = '';
            students.forEach(student => {
                studentsHTML += `
                    <div class="student-card">
                        <div class="row align-items-center">
                            <div class="col-md-1">
                                <div class="user-avatar">
                                    ${student.firstName.charAt(0)}
                                </div>
                            </div>
                            <div class="col-md-3">
                                <h6>${student.firstName} ${student.lastName}</h6>
                                <p class="text-muted mb-0">پایه ${student.grade} - کلاس ${student.class}</p>
                                <p class="mb-0">کد: ${student.username}</p>
                            </div>
                            <div class="col-md-3">
                                <p class="mb-1">وضعیت تحصیلی:</p>
                                <span class="grade-badge ${getStudentStatusClass(student.username)}">
                                    ${getStudentStatus(student.username)}
                                </span>
                            </div>
                            <div class="col-md-5">
                                <div class="d-flex gap-2 justify-content-end">
                                    <button class="btn btn-outline-primary btn-sm" onclick="editStudent('${student.username}')">
                                        <i class="fas fa-edit me-1"></i>ویرایش
                                    </button>
                                    <button class="btn btn-outline-info btn-sm" onclick="viewStudentDetails('${student.username}')">
                                        <i class="fas fa-eye me-1"></i>مشاهده
                                    </button>
                                    <button class="btn btn-outline-success btn-sm" onclick="promoteStudent('${student.username}')">
                                        <i class="fas fa-graduation-cap me-1"></i>ارتقاء
                                    </button>
                                    <button class="btn btn-outline-danger btn-sm" onclick="deleteStudent('${student.username}')">
                                        <i class="fas fa-trash me-1"></i>حذف
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
            });

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-user-graduate me-2"></i>مدیریت دانش‌آموزان</h4>

                    <div class="filter-bar mb-4">
                        <div class="row">
                            <div class="col-md-4">
                                <input type="text" class="form-control" placeholder="جستجوی نام یا نام خانوادگی..." id="adminStudentSearch">
                            </div>
                            <div class="col-md-3">
                                <select class="form-control" id="adminClassFilter">
                                    <option value="">همه کلاس‌ها</option>
                                    ${allClasses.map(cls => `<option value="${cls}">${cls}</option>`).join('')}
                                </select>
                            </div>
                            <div class="col-md-3">
                                <select class="form-control" id="adminGradeFilter">
                                    <option value="">همه پایه‌ها</option>
                                    <option value="هفتم">هفتم</option>
                                    <option value="هشتم">هشتم</option>
                                    <option value="نهم">نهم</option>
                                </select>
                            </div>
                            <div class="col-md-2">
                                <button class="btn-login w-100" onclick="adminSearchStudents()">
                                    <i class="fas fa-search me-2"></i>جستجو
                                </button>
                            </div>
                        </div>
                    </div>

                    <div class="text-end mb-3">
                        <button class="btn-login" onclick="loadContent('addStudent')">
                            <i class="fas fa-plus me-2"></i>دانش‌آموز جدید
                        </button>
                    </div>

                    ${studentsHTML}
                </div>
            `;
        }

        // تولید مدیریت معلمان برای مدیر
        function generateAdminTeachers() {
            let teachersHTML = '';
            teachers.forEach(teacher => {
                teachersHTML += `
                    <div class="student-card">
                        <div class="row align-items-center">
                            <div class="col-md-1">
                                <div class="user-avatar">
                                    ${teacher.name.charAt(0)}
                                </div>
                            </div>
                            <div class="col-md-3">
                                <h6>${teacher.name}</h6>
                                <p class="text-muted mb-0">${teacher.subject}</p>
                                <p class="mb-0">نام کاربری: ${teacher.username}</p>
                            </div>
                            <div class="col-md-3">
                                <p class="mb-1">کلاس‌ها:</p>
                                <div class="teacher-classes">
                                    ${teacher.classes.map(cls => `<span class="class-badge">${cls}</span>`).join('')}
                                </div>
                            </div>
                            <div class="col-md-5">
                                <div class="d-flex gap-2 justify-content-end">
                                    <button class="btn btn-outline-primary btn-sm" onclick="editTeacher(${teacher.id})">
                                        <i class="fas fa-edit me-1"></i>ویرایش
                                    </button>
                                    <button class="btn btn-outline-info btn-sm" onclick="viewTeacherDetails(${teacher.id})">
                                        <i class="fas fa-eye me-1"></i>مشاهده
                                    </button>
                                    <button class="btn btn-outline-danger btn-sm" onclick="deleteTeacher(${teacher.id})">
                                        <i class="fas fa-trash me-1"></i>حذف
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
            });

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-chalkboard-teacher me-2"></i>مدیریت معلمان</h4>

                    <div class="filter-bar mb-4">
                        <div class="row">
                            <div class="col-md-5">
                                <input type="text" class="form-control" placeholder="جستجوی نام یا درس..." id="teacherSearch">
                            </div>
                            <div class="col-md-5">
                                <select class="form-control" id="teacherSubjectFilter">
                                    <option value="">همه دروس</option>
                                    <option value="ریاضی">ریاضی</option>
                                    <option value="علوم">علوم</option>
                                    <option value="ادبیات">ادبیات</option>
                                </select>
                            </div>
                            <div class="col-md-2">
                                <button class="btn-login w-100" onclick="searchTeachers()">
                                    <i class="fas fa-search me-2"></i>جستجو
                                </button>
                            </div>
                        </div>
                    </div>

                    <div class="text-end mb-3">
                        <button class="btn-login" onclick="loadContent('addTeacher')">
                            <i class="fas fa-plus me-2"></i>معلم جدید
                        </button>
                    </div>

                    ${teachersHTML}
                </div>
            `;
        }

        // تولید مدیریت امتحانات برای مدیر
        function generateAdminExams() {
            let examsHTML = '';
            exams.forEach(exam => {
                const teacher = teachers.find(t => t.id === exam.teacherId);
                const statusBadge = exam.status === 'active' ?
                    '<span class="exam-status-active">فعال</span>' :
                    '<span class="exam-status-finished">پایان یافته</span>';

                examsHTML += `
                    <div class="exam-item">
                        <div class="d-flex justify-content-between align-items-start mb-3">
                            <div>
                                <h5>${exam.title}</h5>
                                <p class="text-muted mb-1">${exam.subject} - ${teacher ? teacher.name : 'نامشخص'}</p>
                                <p class="mb-0">کلاس‌های: ${exam.classes.join(', ')}</p>
                                <p class="mb-0">تاریخ: ${exam.date} | مدت زمان: ${exam.duration} دقیقه</p>
                            </div>
                            <div>
                                ${statusBadge}
                                <div class="mt-2">
                                    <button class="btn btn-sm btn-outline-info" onclick="viewExamDetails(${exam.id})">
                                        <i class="fas fa-eye me-1"></i>مشاهده
                                    </button>
                                    <button class="btn btn-sm btn-outline-danger" onclick="adminDeleteExam(${exam.id})">
                                        <i class="fas fa-trash me-1"></i>حذف
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
            });

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-file-alt me-2"></i>مدیریت امتحانات</h4>

                    <div class="filter-bar mb-4">
                        <div class="row">
                            <div class="col-md-4">
                                <input type="text" class="form-control" placeholder="جستجوی عنوان..." id="examSearch">
                            </div>
                            <div class="col-md-3">
                                <select class="form-control" id="examStatusFilter">
                                    <option value="">همه وضعیت‌ها</option>
                                    <option value="active">فعال</option>
                                    <option value="finished">پایان یافته</option>
                                </select>
                            </div>
                            <div class="col-md-3">
                                <select class="form-control" id="examSubjectFilter">
                                    <option value="">همه دروس</option>
                                    <option value="ریاضی">ریاضی</option>
                                    <option value="علوم">علوم</option>
                                    <option value="ادبیات">ادبیات</option>
                                </select>
                            </div>
                            <div class="col-md-2">
                                <button class="btn-login w-100" onclick="searchExams()">
                                    <i class="fas fa-search me-2"></i>جستجو
                                </button>
                            </div>
                        </div>
                    </div>

                    <div class="exam-list">
                        ${examsHTML}
                    </div>
                </div>
            `;
        }

        // تولید صفحه افزودن کلاس جدید
        function generateAddClass() {
            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-plus-circle me-2"></i>افزودن کلاس جدید</h4>

                    <div class="row mb-4">
                        <div class="col-md-6">
                            <div class="form-group mb-3">
                                <label for="newClassName">نام کلاس:</label>
                                <input type="text" id="newClassName" class="form-control" placeholder="مثال: 905">
                                <small class="text-muted">نام کلاس باید به صورت عددی باشد (مثال: 905)</small>
                            </div>

                            <div class="form-group mb-3">
                                <label for="newClassGrade">پایه:</label>
                                <select class="form-control" id="newClassGrade">
                                    <option value="">انتخاب پایه</option>
                                    <option value="هفتم">هفتم</option>
                                    <option value="هشتم">هشتم</option>
                                    <option value="نهم">نهم</option>
                                    <option value="دهم">دهم</option>
                                    <option value="یازدهم">یازدهم</option>
                                    <option value="دوازدهم">دوازدهم</option>
                                </select>
                            </div>
                        </div>

                        <div class="col-md-6">
                            <div class="form-group mb-3">
                                <label for="newClassCapacity">ظرفیت کلاس:</label>
                                <input type="number" id="newClassCapacity" class="form-control" value="35" min="10" max="50">
                            </div>

                            <div class="form-group mb-3">
                                <label for="newClassTeacher">دبیر راهنما:</label>
                                <select class="form-control" id="newClassTeacher">
                                    <option value="">انتخاب دبیر</option>
                                    ${teachers.map(teacher => `
                                        <option value="${teacher.id}">${teacher.name} - ${teacher.subject}</option>
                                    `).join('')}
                                </select>
                            </div>
                        </div>
                    </div>

                    <div class="form-group mb-4">
                        <label for="newClassDescription">شرح کلاس (اختیاری):</label>
                        <textarea class="form-control" id="newClassDescription" rows="3" placeholder="توضیحات مربوط به کلاس..."></textarea>
                    </div>

                    <div class="text-center">
                        <button class="btn-login" style="background: var(--success-color);" onclick="saveNewClass()">
                            <i class="fas fa-save me-2"></i>ذخیره کلاس جدید
                        </button>
                    </div>
                </div>
            `;
        }

        // تولید صفحه افزودن دانش‌آموز جدید
        function generateAddStudent() {
            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-user-plus me-2"></i>افزودن دانش‌آموز جدید</h4>

                    <div class="row mb-4">
                        <div class="col-md-6">
                            <div class="form-group mb-3">
                                <label for="newStudentFirstName">نام:</label>
                                <input type="text" id="newStudentFirstName" class="form-control" placeholder="مثال: علی">
                            </div>

                            <div class="form-group mb-3">
                                <label for="newStudentLastName">نام خانوادگی:</label>
                                <input type="text" id="newStudentLastName" class="form-control" placeholder="مثال: محمدی">
                            </div>

                            <div class="form-group mb-3">
                                <label for="newStudentNationalCode">کد ملی:</label>
                                <input type="text" id="newStudentNationalCode" class="form-control" placeholder="مثال: 0012345678">
                            </div>
                        </div>

                        <div class="col-md-6">
                            <div class="form-group mb-3">
                                <label for="newStudentClass">کلاس:</label>
                                <select class="form-control" id="newStudentClass">
                                    <option value="">انتخاب کلاس</option>
                                    ${allClasses.map(cls => `
                                        <option value="${cls}">${cls}</option>
                                    `).join('')}
                                </select>
                            </div>

                            <div class="form-group mb-3">
                                <label for="newStudentFatherName">نام پدر:</label>
                                <input type="text" id="newStudentFatherName" class="form-control" placeholder="مثال: رضا">
                            </div>

                            <div class="form-group mb-3">
                                <label for="newStudentPhone">تلفن:</label>
                                <input type="text" id="newStudentPhone" class="form-control" placeholder="مثال: 09123456789">
                            </div>
                        </div>
                    </div>

                    <div class="form-group mb-4">
                        <label for="newStudentAddress">آدرس:</label>
                        <textarea class="form-control" id="newStudentAddress" rows="3" placeholder="آدرس کامل..."></textarea>
                    </div>

                    <div class="text-center">
                        <button class="btn-login" style="background: var(--success-color);" onclick="saveNewStudent()">
                            <i class="fas fa-save me-2"></i>ذخیره دانش‌آموز جدید
                        </button>
                    </div>
                </div>
            `;
        }

        // تولید صفحه افزودن معلم جدید
        function generateAddTeacher() {
            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-chalkboard-teacher me-2"></i>افزودن معلم جدید</h4>

                    <div class="row mb-4">
                        <div class="col-md-6">
                            <div class="form-group mb-3">
                                <label for="newTeacherName">نام و نام خانوادگی:</label>
                                <input type="text" id="newTeacherName" class="form-control" placeholder="مثال: استاد عبدی">
                            </div>

                            <div class="form-group mb-3">
                                <label for="newTeacherSubject">درس:</label>
                                <select class="form-control" id="newTeacherSubject">
                                    <option value="">انتخاب درس</option>
                                    <option value="ریاضی">ریاضی</option>
                                    <option value="علوم">علوم</option>
                                    <option value="ادبیات">ادبیات</option>
                                    <option value="فیزیک">فیزیک</option>
                                    <option value="شیمی">شیمی</option>
                                    <option value="زیست شناسی">زیست شناسی</option>
                                    <option value="زبان انگلیسی">زبان انگلیسی</option>
                                    <option value="عربی">عربی</option>
                                    <option value="دینی">دینی</option>
                                    <option value="ورزش">ورزش</option>
                                </select>
                            </div>

                            <div class="form-group mb-3">
                                <label for="newTeacherUsername">نام کاربری:</label>
                                <input type="text" id="newTeacherUsername" class="form-control" placeholder="مثال: teacher4">
                            </div>
                        </div>

                        <div class="col-md-6">
                            <div class="form-group mb-3">
                                <label for="newTeacherPassword">رمز عبور:</label>
                                <input type="password" id="newTeacherPassword" class="form-control" placeholder="رمز عبور">
                            </div>

                            <div class="form-group mb-3">
                                <label for="newTeacherPhone">تلفن:</label>
                                <input type="text" id="newTeacherPhone" class="form-control" placeholder="مثال: 09123456789">
                            </div>

                            <div class="form-group mb-3">
                                <label for="newTeacherEmail">پست الکترونیک:</label>
                                <input type="email" id="newTeacherEmail" class="form-control" placeholder="مثال: teacher@shahidfahmideh.ir">
                            </div>
                        </div>
                    </div>

                    <div class="form-group mb-4">
                        <label>کلاس‌هایی که این معلم تدریس می‌کند:</label>
                        <div class="form-check">
                            ${allClasses.map(className => `
                                <div class="form-check form-check-inline">
                                    <input class="form-check-input teacher-class-checkbox" type="checkbox" id="teacher_class_${className}" value="${className}">
                                    <label class="form-check-label" for="teacher_class_${className}">${className}</label>
                                </div>
                            `).join('')}
                        </div>
                    </div>

                    <div class="text-center">
                        <button class="btn-login" style="background: var(--success-color);" onclick="saveNewTeacher()">
                            <i class="fas fa-save me-2"></i>ذخیره معلم جدید
                        </button>
                    </div>
                </div>
            `;
        }

        // تولید مدیریت موارد انضباطی برای مدیر
        function generateAdminDiscipline() {
            let allDisciplineHTML = '';
            let totalActive = 0;
            let totalSolved = 0;

            // جمع‌آوری تمام موارد انضباطی
            for (const student of students) {
                const studentDiscipline = disciplineRecords[student.username] || [];

                if (studentDiscipline.length > 0) {
                    let studentDisciplineHTML = '';
                    studentDiscipline.forEach(record => {
                        const badgeClass = record.type === 'warning' ? 'discipline-warning' :
                                         record.type === 'serious' ? 'discipline-serious' : 'discipline-solved';
                        const badgeText = record.type === 'warning' ? 'هشدار' :
                                        record.type === 'serious' ? 'جدی' : 'حل شده';

                        if (record.status === 'فعال') totalActive++;
                        else totalSolved++;

                        studentDisciplineHTML += `
                            <div class="discipline-item">
                                <div class="d-flex justify-content-between align-items-start">
                                    <div>
                                        <h6>${student.firstName} ${student.lastName} - ${record.subject}</h6>
                                        <p class="mb-1">${record.description}</p>
                                        <small class="text-muted">تاریخ: ${record.date} | معلم: ${record.teacher}</small>
                                    </div>
                                    <div>
                                        <span class="grade-badge ${badgeClass} me-2">${badgeText}</span>
                                        <span class="grade-badge ${record.status === 'فعال' ? 'grade-poor' : 'grade-excellent'}">
                                            ${record.status}
                                        </span>
                                        <button class="btn btn-sm btn-outline-success mt-1" onclick="resolveDiscipline(${record.id}, '${student.username}')">
                                            <i class="fas fa-check me-1"></i>حل شده
                                        </button>
                                    </div>
                                </div>
                            </div>
                        `;
                    });

                    allDisciplineHTML += `
                        <div class="stats-card">
                            <h5>${student.firstName} ${student.lastName} - کلاس ${student.class}</h5>
                            <div class="discipline-card">
                                ${studentDisciplineHTML}
                            </div>
                        </div>
                    `;
                }
            }

            if (allDisciplineHTML === '') {
                allDisciplineHTML = `
                    <div class="alert alert-success">
                        <i class="fas fa-check-circle me-2"></i>
                        مورد انضباطی فعالی وجود ندارد.
                    </div>
                `;
            }

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-exclamation-triangle me-2"></i>مدیریت موارد انضباطی</h4>

                    <div class="row mb-4">
                        <div class="col-md-4">
                            <div class="stats-card text-center">
                                <div class="stats-number">${totalActive}</div>
                                <div>موارد فعال</div>
                            </div>
                        </div>
                        <div class="col-md-4">
                            <div class="stats-card text-center">
                                <div class="stats-number">${totalSolved}</div>
                                <div>حل شده</div>
                            </div>
                        </div>
                        <div class="col-md-4">
                            <div class="stats-card text-center">
                                <div class="stats-number">${totalActive + totalSolved}</div>
                                <div>کل موارد</div>
                            </div>
                        </div>
                    </div>

                    ${allDisciplineHTML}
                </div>
            `;
        }

        // تولید گزارشات حضور و غیاب برای مدیر
        function generateAdminAttendance() {
            // محاسبه آمار کلی
            let totalPresent = 0;
            let totalAbsent = 0;
            let totalLate = 0;

            Object.values(attendance).forEach(studentAttendance => {
                Object.values(studentAttendance).forEach(dailyAttendance => {
                    Object.values(dailyAttendance).forEach(status => {
                        if (status === 'حاضر') totalPresent++;
                        else if (status === 'غایب') totalAbsent++;
                        else if (status === 'تأخیر') totalLate++;
                    });
                });
            });

            const total = totalPresent + totalAbsent + totalLate;
            const presentPercentage = total > 0 ? ((totalPresent / total) * 100).toFixed(1) : 0;

            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-calendar-alt me-2"></i>گزارشات حضور و غیاب</h4>

                    <div class="row mb-4">
                        <div class="col-md-8">
                            <div class="chart-container">
                                <h5>آمار کلی حضور و غیاب</h5>
                                <div class="attendance-summary mb-4">
                                    <div class="attendance-summary-item">
                                        <div class="attendance-summary-number attendance-summary-present">${totalPresent}</div>
                                        <div>حاضر</div>
                                    </div>
                                    <div class="attendance-summary-item">
                                        <div class="attendance-summary-number attendance-summary-absent">${totalAbsent}</div>
                                        <div>غایب</div>
                                    </div>
                                    <div class="attendance-summary-item">
                                        <div class="attendance-summary-number attendance-summary-late">${totalLate}</div>
                                        <div>تأخیر</div>
                                    </div>
                                </div>

                                <div class="progress mb-2">
                                    <div class="progress-bar bg-success" role="progressbar"
                                         style="width: ${presentPercentage}%" aria-valuenow="${presentPercentage}"
                                         aria-valuemin="0" aria-valuemax="100">
                                        ${presentPercentage}% حضور
                                    </div>
                                </div>
                                <p class="text-center text-muted">نسبت حضور کل دانش‌آموزان</p>
                            </div>
                        </div>
                        <div class="col-md-4">
                            <div class="stats-card">
                                <h5>فیلتر گزارش</h5>
                                <div class="form-group mb-3">
                                    <label>تاریخ شروع:</label>
                                    <input type="text" class="form-control" value="1404/07/01">
                                </div>
                                <div class="form-group mb-3">
                                    <label>تاریخ پایان:</label>
                                    <input type="text" class="form-control" value="1404/07/05">
                                </div>
                                <div class="form-group mb-3">
                                    <label>کلاس:</label>
                                    <select class="form-control">
                                        <option value="">همه کلاس‌ها</option>
                                        ${allClasses.map(cls => `<option value="${cls}">${cls}</option>`).join('')}
                                    </select>
                                </div>
                                <button class="btn-login w-100">
                                    <i class="fas fa-filter me-2"></i>اعمال فیلتر
                                </button>
                            </div>
                        </div>
                    </div>

                    <div class="table-responsive">
                        <table class="table table-striped">
                            <thead>
                                <tr>
                                    <th>نام دانش‌آموز</th>
                                    <th>کلاس</th>
                                    <th>تعداد حضور</th>
                                    <th>تعداد غیاب</th>
                                    <th>تعداد تأخیر</th>
                                    <th>درصد حضور</th>
                                </tr>
                            </thead>
                            <tbody>
                                ${students.map(student => {
                                    const studentAttendance = attendance[student.username] || {};
                                    let studentPresent = 0, studentAbsent = 0, studentLate = 0;

                                    Object.values(studentAttendance).forEach(dailyAttendance => {
                                        Object.values(dailyAttendance).forEach(status => {
                                            if (status === 'حاضر') studentPresent++;
                                            else if (status === 'غایب') studentAbsent++;
                                            else if (status === 'تأخیر') studentLate++;
                                        });
                                    });

                                    const studentTotal = studentPresent + studentAbsent + studentLate;
                                    const studentPercentage = studentTotal > 0 ? ((studentPresent / studentTotal) * 100).toFixed(1) : 0;

                                    return `
                                        <tr>
                                            <td>${student.firstName} ${student.lastName}</td>
                                            <td>${student.class}</td>
                                            <td>${studentPresent}</td>
                                            <td>${studentAbsent}</td>
                                            <td>${studentLate}</td>
                                            <td>
                                                <span class="grade-badge ${studentPercentage >= 90 ? 'grade-excellent' : studentPercentage >= 80 ? 'grade-good' : studentPercentage >= 70 ? 'grade-average' : 'grade-poor'}">
                                                    ${studentPercentage}%
                                                </span>
                                            </td>
                                        </tr>
                                    `;
                                }).join('')}
                            </tbody>
                        </table>
                    </div>
                </div>
            `;
        }

        // تولید گزارشات آماری برای مدیر
        function generateAdminReports() {
            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-chart-bar me-2"></i>گزارشات آماری</h4>

                    <div class="row mb-4">
                        <div class="col-md-6">
                            <div class="stats-card">
                                <h5>گزارشات انتخابی</h5>
                                <div class="list-group">
                                    <a href="#" class="list-group-item list-group-item-action" onclick="generateReport('grades')">
                                        <i class="fas fa-chart-line me-2"></i>گزارش نمرات
                                    </a>
                                    <a href="#" class="list-group-item list-group-item-action" onclick="generateReport('attendance')">
                                        <i class="fas fa-calendar-check me-2"></i>گزارش حضور و غیاب
                                    </a>
                                    <a href="#" class="list-group-item list-group-item-action" onclick="generateReport('discipline')">
                                        <i class="fas fa-exclamation-triangle me-2"></i>گزارش موارد انضباطی
                                    </a>
                                    <a href="#" class="list-group-item list-group-item-action" onclick="generateReport('exams')">
                                        <i class="fas fa-file-alt me-2"></i>گزارش امتحانات
                                    </a>
                                </div>
                            </div>
                        </div>
                        <div class="col-md-6">
                            <div class="stats-card">
                                <h5>تنظیمات گزارش</h5>
                                <div class="form-group mb-3">
                                    <label>نوع گزارش:</label>
                                    <select class="form-control" id="reportType">
                                        <option value="grades">نمرات</option>
                                        <option value="attendance">حضور و غیاب</option>
                                        <option value="discipline">موارد انضباطی</option>
                                    </select>
                                </div>
                                <div class="form-group mb-3">
                                    <label>فرمت خروجی:</label>
                                    <select class="form-control" id="reportFormat">
                                        <option value="html">HTML</option>
                                        <option value="pdf">PDF</option>
                                        <option value="excel">Excel</option>
                                    </select>
                                </div>
                                <div class="form-group mb-3">
                                    <label>بازه زمانی:</label>
                                    <select class="form-control" id="reportPeriod">
                                        <option value="current">نیم‌سال جاری</option>
                                        <option value="year">سال تحصیلی</option>
                                        <option value="custom">سفارشی</option>
                                    </select>
                                </div>
                                <button class="btn-login w-100" onclick="generateCustomReport()">
                                    <i class="fas fa-download me-2"></i>تولید گزارش
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            `;
        }

        // تولید تنظیمات سیستم برای مدیر
        function generateAdminSettings() {
            return `
                <div class="stats-card">
                    <h4 class="mb-4"><i class="fas fa-cog me-2"></i>تنظیمات سیستم</h4>

                    <div class="row">
                        <div class="col-md-6">
                            <div class="stats-card">
                                <h5>تنظیمات عمومی</h5>
                                <div class="form-group mb-3">
                                    <label>نام مدرسه:</label>
                                    <input type="text" class="form-control" value="مدرسه شهید فهمیده">
                                </div>
                                <div class="form-group mb-3">
                                    <label>سال تحصیلی:</label>
                                    <input type="text" class="form-control" value="۱۴۰۴-۱۴۰۵">
                                </div>
                                <div class="form-group mb-3">
                                    <label>آدرس:</label>
                                    <input type="text" class="form-control" value="اراک، خیابان امام">
                                </div>
                                <button class="btn-login">
                                    <i class="fas fa-save me-2"></i>ذخیره تنظیمات
                                </button>
                            </div>
                        </div>
                        <div class="col-md-6">
                            <div class="stats-card">
                                <h5>امنیت سیستم</h5>
                                <div class="form-group mb-3">
                                    <label>تغییر رمز عبور مدیر:</label>
                                    <input type="password" class="form-control" placeholder="رمز عبور جدید">
                                </div>
                                <div class="form-group mb-3">
                                    <label>تکرار رمز عبور:</label>
                                    <input type="password" class="form-control" placeholder="تکرار رمز عبور">
                                </div>
                                <div class="form-group mb-3">
                                    <label>تعداد دفعات تلاش ناموفق:</label>
                                    <input type="number" class="form-control" value="3" min="1" max="10">
                                </div>
                                <button class="btn-login" style="background: var(--danger-color);">
                                    <i class="fas fa-lock me-2"></i>به‌روزرسانی امنیت
                                </button>
                            </div>
                        </div>
                    </div>

                    <div class="stats-card mt-4">
                        <h5>عملیات سیستم</h5>
                        <div class="row text-center">
                            <div class="col-md-4">
                                <button class="btn-login w-100 mb-2" style="background: #6c757d;" onclick="backupData()">
                                    <i class="fas fa-database me-2"></i>پشتیبان‌گیری
                                </button>
                            </div>
                            <div class="col-md-4">
                                <button class="btn-login w-100 mb-2" style="background: var(--warning-color);" onclick="restoreData()">
                                    <i class="fas fa-undo me-2"></i>بازیابی
                                </button>
                            </div>
                            <div class="col-md-4">
                                <button class="btn-login w-100 mb-2" style="background: var(--danger-color);" onclick="clearData()">
                                    <i class="fas fa-trash me-2"></i>پاک کردن داده‌ها
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            `;
        }

        // ==================== توابع کمکی ====================

        function changeSemester(semester) {
            currentSemester = semester;
            if (currentUser.type === 'student') {
                loadContent('reportCard');
            } else if (currentUser.type === 'teacher') {
                loadContent('gradeManagement');
            }
        }

        function changeStudentSemester(semester, studentUsername) {
            currentSemester = semester;
            // فقط UI را آپدیت می‌کنیم
            document.querySelectorAll('.semester-btn').forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');
        }

        function changeAttendanceDate(date) {
            currentAttendanceDate = date;
            loadContent('attendanceManagement');
        }

        function getSemesterName(semester) {
            const names = {
                'firstSemester': 'نیم‌سال اول',
                'secondSemester': 'نیم‌سال دوم',
                'final': 'پایان سال'
            };
            return names[semester] || semester;
        }

        function getGradeStatus(grade) {
            if (grade >= 18) return 'عالی';
            if (grade >= 15) return 'خوب';
            if (grade >= 12) return 'متوسط';
            return 'نیاز به تلاش';
        }

        function getGradeClass(grade) {
            if (grade >= 18) return 'grade-excellent';
            if (grade >= 15) return 'grade-good';
            if (grade >= 12) return 'grade-average';
            return 'grade-poor';
        }

        function getAttendanceClass(attendance) {
            if (attendance === 'حاضر') return 'attendance-present';
            if (attendance === 'غایب') return 'attendance-absent';
            if (attendance === 'تأخیر') return 'attendance-late';
            return 'grade-average';
        }

        function getTeacherBySubject(subject) {
            const teacher = teachers.find(t => t.subject === subject);
            return teacher ? teacher.name : 'ثبت نشده';
        }

        function getStudentStatus(studentUsername) {
            const studentDiscipline = disciplineRecords[studentUsername] || [];
            const activeDiscipline = studentDiscipline.filter(d => d.status === 'فعال');

            if (activeDiscipline.length > 2) return 'نیازمند توجه';

            const studentGrades = grades[student.username] || {};
            let total = 0;
            let count = 0;

            for (const subjectGrades of Object.values(studentGrades)) {
                if (subjectGrades.final) {
                    total += subjectGrades.final;
                    count++;
                }
            }

            const average = count > 0 ? total / count : 0;

            if (average >= 17) return 'برتر';
            if (average >= 15) return 'خوب';
            if (average >= 12) return 'متوسط';
            return 'نیاز به تلاش';
        }

        function getStudentStatusClass(studentUsername) {
            const status = getStudentStatus(studentUsername);
            if (status === 'برتر') return 'grade-excellent';
            if (status === 'خوب') return 'grade-good';
            if (status === 'متوسط') return 'grade-average';
            return 'grade-poor';
        }

        // ==================== توابع امتحان ====================

        function startExam(examId) {
            const exam = exams.find(e => e.id === examId);
            if (!exam) {
                alert('امتحان یافت نشد!');
                return;
            }

            currentExam = exam;
            examTimeLeft = exam.duration * 60;
            examAnswers = {};

            loadContent('takeExam');
            startExamTimer();
        }

        function startExamTimer() {
            if (examTimer) clearInterval(examTimer);

            examTimer = setInterval(() => {
                examTimeLeft--;

                const minutes = Math.floor(examTimeLeft / 60);
                const seconds = examTimeLeft % 60;

                document.getElementById('examTimer').textContent =
                    `${minutes}:${seconds.toString().padStart(2, '0')}`;

                if (examTimeLeft <= 0) {
                    clearInterval(examTimer);
                    submitExam();
                    alert('زمان امتحان به پایان رسید!');
                }
            }, 1000);
        }

        function selectAnswer(questionId, optionIndex) {
            examAnswers[questionId] = optionIndex;

            // آپدیت UI
            document.querySelectorAll(`[id^="option_${questionId}_"]`).forEach(option => {
                option.classList.remove('selected');
            });
            document.getElementById(`option_${questionId}_${optionIndex}`).classList.add('selected');
        }

        function submitExam() {
            if (!currentExam) return;

            clearInterval(examTimer);

            // محاسبه نمره
            let score = 0;
            currentExam.questions.forEach(question => {
                if (examAnswers[question.id] === question.correctAnswer) {
                    score++;
                }
            });

            // ذخیره نتیجه
            if (!examResults[currentUser.username]) {
                examResults[currentUser.username] = [];
            }

            const result = {
                examId: currentExam.id,
                score: score,
                total: currentExam.questions.length,
                date: new Date().toLocaleDateString('fa-IR'),
                answers: examAnswers
            };

            examResults[currentUser.username].push(result);
            saveToLocalStorage();

            // نمایش نتیجه
            const percentage = (score / currentExam.questions.length) * 100;
            alert(`امتحان با موفقیت ثبت شد!\n\nنمره شما: ${score} از ${currentExam.questions.length}\nدرصد: ${percentage.toFixed(1)}%`);

            loadContent('examResults');
        }

        // ==================== توابع معلم ====================

        function addQuestion() {
            const questionsContainer = document.getElementById('questionsContainer');
            const questionCount = questionsContainer.querySelectorAll('.question-card').length + 1;

            const questionHTML = `
                <div class="question-card">
                    <div class="d-flex justify-content-between align-items-center mb-3">
                        <h6>سوال ${questionCount}</h6>
                        <button class="btn btn-danger btn-sm" onclick="removeQuestion(this)">
                            <i class="fas fa-trash me-1"></i>حذف سوال
                        </button>
                    </div>
                    <div class="form-group mb-3">
                        <label>متن سوال:</label>
                        <textarea class="form-control question-text" rows="2" placeholder="متن سوال را وارد کنید..."></textarea>
                    </div>
                    <div class="form-group mb-3">
                        <label>گزینه‌ها:</label>
                        ${['الف', 'ب', 'ج', 'د'].map((letter, index) => `
                            <div class="input-group mb-2">
                                <span class="input-group-text">${letter}</span>
                                <input type="text" class="form-control option-input" placeholder="متن گزینه ${letter}">
                                <div class="input-group-text">
                                    <input class="form-check-input correct-answer" type="radio" name="correctAnswer${questionCount}" value="${index}">
                                </div>
                            </div>
                        `).join('')}
                    </div>
                </div>
            `;

            questionsContainer.insertAdjacentHTML('beforeend', questionHTML);
        }

        function removeQuestion(button) {
            if (document.querySelectorAll('.question-card').length > 1) {
                button.closest('.question-card').remove();
                updateQuestionNumbers();
            }
        }

        function updateQuestionNumbers() {
            document.querySelectorAll('.question-card').forEach((card, index) => {
                card.querySelector('h6').textContent = `سوال ${index + 1}`;
            });
        }

        function saveExam() {
            const title = document.getElementById('examTitle').value.trim();
            const duration = parseInt(document.getElementById('examDuration').value);
            const date = document.getElementById('examDate').value.trim();

            if (!title || !duration || !date) {
                alert('لطفاً تمام فیلدهای الزامی را پر کنید!');
                return;
            }

            const selectedClasses = Array.from(document.querySelectorAll('.class-checkbox:checked'))
                .map(cb => cb.value);

            if (selectedClasses.length === 0) {
                alert('حداقل یک کلاس را انتخاب کنید!');
                return;
            }

            const questions = [];
            document.querySelectorAll('.question-card').forEach((card, index) => {
                const questionText = card.querySelector('.question-text').value.trim();
                const options = Array.from(card.querySelectorAll('.option-input'))
                    .map(input => input.value.trim());
                const correctAnswer = Array.from(card.querySelectorAll('.correct-answer'))
                    .findIndex(radio => radio.checked);

                if (questionText && options.every(opt => opt) && correctAnswer !== -1) {
                    questions.push({
                        id: index + 1,
                        text: questionText,
                        options: options,
                        correctAnswer: correctAnswer
                    });
                }
            });

            if (questions.length === 0) {
                alert('حداقل یک سوال معتبر اضافه کنید!');
                return;
            }

            const newExam = {
                id: exams.length + 1,
                title: title,
                subject: currentUser.subject,
                teacherId: currentUser.id,
                teacherName: currentUser.name,
                classes: selectedClasses,
                duration: duration,
                date: date,
                status: 'active',
                questions: questions
            };

            exams.push(newExam);
            saveToLocalStorage();

            alert('امتحان با موفقیت ایجاد شد!');
            loadContent('manageExams');
        }

        function updateStudentGrade(studentUsername, grade) {
            const gradeValue = parseFloat(grade);

            if (isNaN(gradeValue) || gradeValue < 0 || gradeValue > 20) {
                alert('نمره باید بین 0 تا 20 باشد!');
                return;
            }

            if (!grades[studentUsername]) {
                grades[studentUsername] = {};
            }

            if (!grades[studentUsername][currentUser.subject]) {
                grades[studentUsername][currentUser.subject] = {};
            }

            grades[studentUsername][currentUser.subject][currentSemester] = gradeValue;
            saveToLocalStorage();

            // آپدیت UI
            const badge = event.target.nextElementSibling;
            badge.className = `grade-badge ${getGradeClass(gradeValue)} ms-2`;
            badge.textContent = getGradeStatus(gradeValue);
        }

        function updateAttendance(studentUsername, status) {
            if (!attendance[studentUsername]) {
                attendance[studentUsername] = {};
            }

            if (!attendance[studentUsername][currentAttendanceDate]) {
                attendance[studentUsername][currentAttendanceDate] = {};
            }

            attendance[studentUsername][currentAttendanceDate][currentUser.subject] = status;
            saveToLocalStorage();

            // آپدیت UI
            const card = event.target.closest('.student-card');
            const badge = card.querySelector('.grade-badge');
            badge.className = `grade-badge ${getAttendanceClass(status)}`;
            badge.textContent = status;

            // آپدیت دکمه‌های فعال
            card.querySelectorAll('.attendance-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
        }

        function addDisciplineRecord(studentUsername) {
            const type = document.getElementById(`disciplineType_${studentUsername}`).value;
            const points = parseInt(document.getElementById(`disciplinePoints_${studentUsername}`).value);
            const description = document.getElementById(`disciplineDesc_${studentUsername}`).value;

            if (!description.trim()) {
                alert('لطفاً شرح مورد انضباطی را وارد کنید');
                return;
            }

            if (!disciplineRecords[studentUsername]) {
                disciplineRecords[studentUsername] = [];
            }

            const newRecord = {
                id: Date.now(),
                date: new Date().toLocaleDateString('fa-IR'),
                type: type,
                subject: currentUser.subject,
                teacher: currentUser.name,
                description: description,
                status: 'فعال',
                points: points
            };

            disciplineRecords[studentUsername].push(newRecord);
            saveToLocalStorage();

            // پاک کردن فیلدها
            document.getElementById(`disciplineDesc_${studentUsername}`).value = '';

            alert('مورد انضباطی با موفقیت ثبت شد!');
        }

        function createAssignment() {
            const title = document.getElementById('assignmentTitle').value.trim();
            const description = document.getElementById('assignmentDescription').value.trim();
            const dueDate = document.getElementById('assignmentDueDate').value.trim();

            if (!title || !description || !dueDate) {
                alert('لطفاً تمام فیلدهای الزامی را پر کنید!');
                return;
            }

            const selectedClasses = Array.from(document.querySelectorAll('.assignment-class-checkbox:checked'))
                .map(cb => cb.value);

            if (selectedClasses.length === 0) {
                alert('حداقل یک کلاس را انتخاب کنید!');
                return;
            }

            // اضافه کردن تکلیف برای هر دانش‌آموز در کلاس‌های انتخاب شده
            selectedClasses.forEach(className => {
                const classStudents = students.filter(s => s.class === className);

                classStudents.forEach(student => {
                    if (!assignments[student.username]) {
                        assignments[student.username] = [];
                    }

                    const newAssignment = {
                        id: Date.now() + Math.random(),
                        title: title,
                        subject: currentUser.subject,
                        teacher: currentUser.name,
                        description: description,
                        dueDate: dueDate,
                        status: 'در انتظار',
                        grade: null
                    };

                    assignments[student.username].push(newAssignment);
                });
            });

            saveToLocalStorage();
            alert('تکلیف با موفقیت برای دانش‌آموزان ایجاد شد!');

            // پاک کردن فیلدها
            document.getElementById('assignmentTitle').value = '';
            document.getElementById('assignmentDescription').value = '';
            document.getElementById('assignmentDueDate').value = '';
        }

        // ==================== توابع اطلاع‌رسانی ====================

        function markNotificationAsRead(notificationId) {
            const userNotifications = notifications[currentUser.username];
            if (userNotifications) {
                const notification = userNotifications.find(n => n.id === notificationId);
                if (notification) {
                    notification.read = true;
                    saveToLocalStorage();
                    loadContent('studentNotifications');
                }
            }
        }

        function markAllNotificationsAsRead() {
            const userNotifications = notifications[currentUser.username];
            if (userNotifications) {
                userNotifications.forEach(notification => {
                    notification.read = true;
                });
                saveToLocalStorage();
                loadContent('studentNotifications');
            }
        }

        function markMessageAsRead(messageId) {
            const userMessages = messages[currentUser.username];
            if (userMessages) {
                const message = userMessages.find(m => m.id === messageId);
                if (message) {
                    message.read = true;
                    saveToLocalStorage();
                    loadContent('studentMessages');
                }
            }
        }

        function markAllMessagesAsRead() {
            const userMessages = messages[currentUser.username];
            if (userMessages) {
                userMessages.forEach(message => {
                    message.read = true;
                });
                saveToLocalStorage();
                loadContent('studentMessages');
            }
        }

        function sendMessage() {
            const recipient = document.getElementById('messageRecipient').value;
            const subject = document.getElementById('messageSubject').value.trim();
            const content = document.getElementById('messageContent').value.trim();

            if (!recipient || !subject || !content) {
                alert('لطفاً تمام فیلدهای الزامی را پر کنید!');
                return;
            }

            if (!messages[recipient]) {
                messages[recipient] = [];
            }

            const newMessage = {
                id: Date.now(),
                from: currentUser.name,
                message: content,
                date: new Date().toLocaleDateString('fa-IR'),
                read: false,
                subject: subject
            };

            messages[recipient].push(newMessage);
            saveToLocalStorage();

            alert('پیام با موفقیت ارسال شد!');

            // پاک کردن فیلدها
            document.getElementById('messageRecipient').value = '';
            document.getElementById('messageSubject').value = '';
            document.getElementById('messageContent').value = '';
        }

        // ==================== توابع مدیر ====================

        function resolveDiscipline(recordId, studentUsername) {
            const studentDiscipline = disciplineRecords[studentUsername];
            if (studentDiscipline) {
                const record = studentDiscipline.find(r => r.id === recordId);
                if (record) {
                    record.status = 'حل شده';
                    saveToLocalStorage();
                    loadContent('adminDiscipline');
                }
            }
        }

        function editStudent(username) {
            const student = students.find(s => s.username === username);
            if (student) {
                const newFirstName = prompt('نام جدید:', student.firstName);
                const newLastName = prompt('نام خانوادگی جدید:', student.lastName);
                const newClass = prompt('کلاس جدید:', student.class);

                if (newFirstName && newLastName && newClass) {
                    student.firstName = newFirstName;
                    student.lastName = newLastName;
                    student.class = newClass;
                    student.grade = newClass.charAt(0) + "ام";
                    saveToLocalStorage();
                    loadContent('adminStudents');
                }
            }
        }

        function deleteStudent(username) {
            if (confirm('آیا از حذف این دانش‌آموز اطمینان دارید؟')) {
                const index = students.findIndex(s => s.username === username);
                if (index !== -1) {
                    students.splice(index, 1);
                    delete grades[username];
                    delete attendance[username];
                    delete disciplineRecords[username];
                    delete assignments[username];
                    delete notifications[username];
                    delete messages[username];
                    delete examResults[username];
                    saveToLocalStorage();
                    loadContent('adminStudents');
                }
            }
        }

        function editTeacher(teacherId) {
            const teacher = teachers.find(t => t.id === teacherId);
            if (teacher) {
                const newName = prompt('نام جدید:', teacher.name);
                const newSubject = prompt('درس جدید:', teacher.subject);
                const newClasses = prompt('کلاس‌ها (با کاما جدا کنید):', teacher.classes.join(','));

                if (newName && newSubject && newClasses) {
                    teacher.name = newName;
                    teacher.subject = newSubject;
                    teacher.classes = newClasses.split(',');
                    saveToLocalStorage();
                    loadContent('adminTeachers');
                }
            }
        }

        function deleteTeacher(teacherId) {
            if (confirm('آیا از حذف این معلم اطمینان دارید؟')) {
                const index = teachers.findIndex(t => t.id === teacherId);
                if (index !== -1) {
                    teachers.splice(index, 1);
                    saveToLocalStorage();
                    loadContent('adminTeachers');
                }
            }
        }

        // ==================== توابع جدید برای افزودن کلاس، دانش‌آموز و معلم ====================

        function saveNewClass() {
            const className = document.getElementById('newClassName').value.trim();
            const classGrade = document.getElementById('newClassGrade').value;
            const classCapacity = parseInt(document.getElementById('newClassCapacity').value);
            const classTeacher = document.getElementById('newClassTeacher').value;
            const classDescription = document.getElementById('newClassDescription').value.trim();

            if (!className || !classGrade || !classCapacity) {
                alert('لطفاً فیلدهای الزامی را پر کنید!');
                return;
            }

            if (allClasses.includes(className)) {
                alert('این کلاس قبلاً وجود دارد!');
                return;
            }

            // اضافه کردن کلاس به لیست کلاس‌ها
            allClasses.push(className);

            // اضافه کردن کلاس به معلم مربوطه
            if (classTeacher) {
                const teacher = teachers.find(t => t.id === parseInt(classTeacher));
                if (teacher && !teacher.classes.includes(className)) {
                    teacher.classes.push(className);
                }
            }

            saveToLocalStorage();
            alert('کلاس جدید با موفقیت اضافه شد!');

            // پاک کردن فیلدها
            document.getElementById('newClassName').value = '';
            document.getElementById('newClassGrade').value = '';
            document.getElementById('newClassCapacity').value = '35';
            document.getElementById('newClassTeacher').value = '';
            document.getElementById('newClassDescription').value = '';
        }

        function saveNewStudent() {
            const firstName = document.getElementById('newStudentFirstName').value.trim();
            const lastName = document.getElementById('newStudentLastName').value.trim();
            const nationalCode = document.getElementById('newStudentNationalCode').value.trim();
            const studentClass = document.getElementById('newStudentClass').value;
            const fatherName = document.getElementById('newStudentFatherName').value.trim();
            const phone = document.getElementById('newStudentPhone').value.trim();
            const address = document.getElementById('newStudentAddress').value.trim();

            if (!firstName || !lastName || !nationalCode || !studentClass || !fatherName || !phone) {
                alert('لطفاً فیلدهای الزامی را پر کنید!');
                return;
            }

            // تولید نام کاربری و رمز عبور
            const studentCount = students.filter(s => s.class === studentClass).length + 1;
            const studentNumber = studentCount.toString().padStart(2, '0');
            const username = `student_${studentClass}_${studentNumber}`;
            const password = "123456";
            const grade = studentClass.charAt(0) + "ام";

            // ایجاد دانش‌آموز جدید
            const newStudent = {
                id: parseInt(studentClass + studentNumber),
                firstName: firstName,
                lastName: lastName,
                grade: grade,
                class: studentClass,
                username: username,
                password: password,
                nationalCode: nationalCode,
                fatherName: fatherName,
                phone: phone,
                address: address
            };

            // اضافه کردن دانش‌آموز
            students.push(newStudent);

            // ایجاد رکوردهای خالی برای دانش‌آموز جدید
            grades[username] = {
                "ریاضی": { firstSemester: 0, secondSemester: 0, final: 0 },
                "علوم": { firstSemester: 0, secondSemester: 0, final: 0 },
                "ادبیات": { firstSemester: 0, secondSemester: 0, final: 0 }
            };

            attendance[username] = {};
            assignments[username] = [];
            notifications[username] = [];
            messages[username] = [];
            examResults[username] = [];

            saveToLocalStorage();
            alert(`دانش‌آموز جدید با موفقیت اضافه شد!\n\nنام کاربری: ${username}\nرمز عبور: ${password}`);

            // پاک کردن فیلدها
            document.getElementById('newStudentFirstName').value = '';
            document.getElementById('newStudentLastName').value = '';
            document.getElementById('newStudentNationalCode').value = '';
            document.getElementById('newStudentClass').value = '';
            document.getElementById('newStudentFatherName').value = '';
            document.getElementById('newStudentPhone').value = '';
            document.getElementById('newStudentAddress').value = '';
        }

        function saveNewTeacher() {
            const name = document.getElementById('newTeacherName').value.trim();
            const subject = document.getElementById('newTeacherSubject').value;
            const username = document.getElementById('newTeacherUsername').value.trim();
            const password = document.getElementById('newTeacherPassword').value;
            const phone = document.getElementById('newTeacherPhone').value.trim();
            const email = document.getElementById('newTeacherEmail').value.trim();

            if (!name || !subject || !username || !password) {
                alert('لطفاً فیلدهای الزامی را پر کنید!');
                return;
            }

            // بررسی وجود نام کاربری
            if (teachers.find(t => t.username === username)) {
                alert('این نام کاربری قبلاً استفاده شده است!');
                return;
            }

            // دریافت کلاس‌های انتخاب شده
            const selectedClasses = Array.from(document.querySelectorAll('.teacher-class-checkbox:checked'))
                .map(cb => cb.value);

            // ایجاد معلم جدید
            const newTeacher = {
                id: teachers.length + 1,
                username: username,
                password: password,
                name: name,
                subject: subject,
                classes: selectedClasses,
                phone: phone,
                email: email
            };

            // اضافه کردن معلم
            teachers.push(newTeacher);

            saveToLocalStorage();
            alert('معلم جدید با موفقیت اضافه شد!');

            // پاک کردن فیلدها
            document.getElementById('newTeacherName').value = '';
            document.getElementById('newTeacherSubject').value = '';
            document.getElementById('newTeacherUsername').value = '';
            document.getElementById('newTeacherPassword').value = '';
            document.getElementById('newTeacherPhone').value = '';
            document.getElementById('newTeacherEmail').value = '';

            // پاک کردن انتخاب کلاس‌ها
            document.querySelectorAll('.teacher-class-checkbox').forEach(cb => {
                cb.checked = false;
            });
        }

        // ==================== توابع دیگر ====================

        function handleLogout() {
            if (confirm('آیا از سیستم خارج می‌شوید؟')) {
                currentUser = null;
                document.getElementById('mainPage').style.display = 'none';
                document.getElementById('loginPage').style.display = 'block';

                // ریست کردن فرم ورود
                document.getElementById('loginForm').reset();
                document.querySelectorAll('.user-type-btn').forEach(btn => btn.classList.remove('active'));
                document.querySelector('.user-type-btn[data-type="student"]').classList.add('active');
            }
        }

        // مدیریت خروج
        function handleLogout() {
            if (confirm('آیا از سیستم خارج می‌شوید؟')) {
                currentUser = null;
                document.getElementById('mainPage').style.display = 'none';
                document.getElementById('loginPage').style.display = 'block';

                // ریست کردن فرم ورود
                document.getElementById('loginForm').reset();
                document.querySelectorAll('.user-type-btn').forEach(btn => btn.classList.remove('active'));
                document.querySelector('.user-type-btn[data-type="student"]').classList.add('active');
            }
        }
    </script>
</body>
</html>
