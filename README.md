<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>维迪电生理预约管理系统</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Microsoft YaHei', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #f0f7ff 0%, #e6f0ff 100%);
            min-height: 100vh;
            padding: 20px;
            color: #333;
        }
        
        .container {
            max-width: 1600px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 40px rgba(0, 82, 204, 0.15);
            overflow: hidden;
        }
        
        header {
            background: linear-gradient(90deg, #1a6dcc, #2c8ae0);
            color: white;
            padding: 20px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .logo-icon {
            font-size: 28px;
            background: white;
            color: #1a6dcc;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .logo-text h1 {
            font-size: 26px;
            font-weight: 600;
        }
        
        .logo-text p {
            font-size: 14px;
            opacity: 0.9;
        }
        
        .main-content {
            display: flex;
            min-height: 600px;
        }
        
        .form-section {
            flex: 1;
            padding: 30px;
            background: #f9fbfd;
            border-right: 1px solid #eaeff5;
        }
        
        .list-section {
            flex: 1.5;
            padding: 30px;
            background: #ffffff;
        }
        
        .section-title {
            font-size: 22px;
            color: #2c3e50;
            margin-bottom: 25px;
            padding-bottom: 10px;
            border-bottom: 2px solid #eaeff5;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .section-title i {
            margin-right: 10px;
            color: #1a6dcc;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: #2c3e50;
        }
        
        .required::after {
            content: " *";
            color: #e74c3c;
        }
        
        input, select, textarea {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #d1d8e0;
            border-radius: 8px;
            font-size: 16px;
            transition: all 0.3s;
        }
        
        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: #3498db;
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.2);
        }
        
        .datalist-container {
            position: relative;
        }
        
        .datalist-container input {
            padding-right: 35px;
        }
        
        .datalist-icon {
            position: absolute;
            right: 12px;
            top: 50%;
            transform: translateY(-50%);
            color: #7f8c8d;
            cursor: pointer;
        }
        
        .form-row {
            display: flex;
            gap: 20px;
        }
        
        .form-row .form-group {
            flex: 1;
        }
        
        button {
            background: linear-gradient(90deg, #1a6dcc, #2c8ae0);
            color: white;
            border: none;
            padding: 14px 25px;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s;
            width: 100%;
        }
        
        button:hover {
            background: linear-gradient(90deg, #1557a3, #1a6dcc);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(26, 109, 204, 0.3);
        }
        
        .search-bar {
            display: flex;
            gap: 15px;
            margin-bottom: 25px;
        }
        
        .search-bar input {
            flex: 1;
            padding: 12px 15px;
            border-radius: 8px;
            border: 1px solid #d1d8e0;
        }
        
        .search-bar button {
            width: auto;
            padding: 12px 25px;
        }
        
        .controls {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
            flex-wrap: wrap;
            gap: 15px;
        }
        
        .sort-controls {
            display: flex;
            gap: 15px;
        }
        
        .sort-controls select {
            width: 180px;
        }
        
        .stats-controls {
            display: flex;
            gap: 15px;
            align-items: center;
        }
        
        .stats-controls select {
            width: 120px;
        }
        
        .stats-display {
            background: #f1f7fd;
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 20px;
            display: flex;
            justify-content: space-around;
            text-align: center;
        }
        
        .stat-item {
            padding: 10px;
        }
        
        .stat-value {
            font-size: 28px;
            font-weight: 700;
            color: #1a6dcc;
            margin-bottom: 5px;
        }
        
        .stat-label {
            font-size: 14px;
            color: #7f8c8d;
        }
        
        .appointment-list {
            max-height: 500px;
            overflow-y: auto;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th {
            background-color: #f1f7fd;
            color: #2c3e50;
            font-weight: 600;
            padding: 15px;
            text-align: left;
            position: sticky;
            top: 0;
            cursor: pointer;
            transition: background 0.3s;
        }
        
        th:hover {
            background-color: #e1ecf7;
        }
        
        th::after {
            content: "↕";
            margin-left: 5px;
            font-size: 12px;
            opacity: 0.5;
        }
        
        td {
            padding: 15px;
            border-bottom: 1px solid #eaeff5;
            color: #34495e;
        }
        
        tr:hover {
            background-color: #f9fbfd;
        }
        
        .status {
            padding: 5px 10px;
            border-radius: 15px;
            font-size: 13px;
            font-weight: 500;
            text-align: center;
            display: inline-block;
        }
        
        .status-pending {
            background: #ffecd9;
            color: #e67e22;
        }
        
        .status-confirmed {
            background: #d6eaff;
            color: #3498db;
        }
        
        .status-completed {
            background: #dbffe5;
            color: #27ae60;
        }
        
        .status-cancelled {
            background: #ffe5e5;
            color: #e74c3c;
        }
        
        .actions {
            display: flex;
            gap: 8px;
        }
        
        .action-btn {
            padding: 6px 10px;
            border-radius: 5px;
            font-size: 14px;
            cursor: pointer;
            border: none;
            display: flex;
            align-items: center;
            justify-content: center;
            width: 34px;
            height: 34px;
        }
        
        .edit-btn {
            background: #f39c12;
            color: white;
        }
        
        .delete-btn {
            background: #e74c3c;
            color: white;
        }
        
        .status-btn {
            background: #3498db;
            color: white;
        }
        
        .copy-btn {
            background: #9b59b6;
            color: white;
        }
        
        .no-appointments {
            text-align: center;
            padding: 40px;
            color: #7f8c8d;
            font-size: 18px;
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background: white;
            border-radius: 10px;
            padding: 30px;
            width: 400px;
            max-width: 90%;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .modal-title {
            font-size: 20px;
            font-weight: 600;
            color: #2c3e50;
        }
        
        .close-modal {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: #7f8c8d;
            width: 30px;
            height: 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
        }
        
        .close-modal:hover {
            background: #f5f5f5;
        }
        
        .modal-body {
            margin-bottom: 20px;
        }
        
        .modal-footer {
            display: flex;
            justify-content: flex-end;
            gap: 10px;
        }
        
        .modal-btn {
            padding: 10px 20px;
            border-radius: 5px;
            border: none;
            cursor: pointer;
            font-weight: 500;
        }
        
        .modal-btn.confirm {
            background: #27ae60;
            color: white;
        }
        
        .modal-btn.cancel {
            background: #e0e0e0;
            color: #333;
        }
        
        .toast {
            position: fixed;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0, 0, 0, 0.8);
            color: white;
            padding: 15px 25px;
            border-radius: 8px;
            font-size: 16px;
            z-index: 1001;
            display: none;
            align-items: center;
            gap: 10px;
        }
        
        footer {
            text-align: center;
            padding: 20px;
            color: #7f8c8d;
            font-size: 14px;
            border-top: 1px solid #eaeff5;
        }
        
        @media (max-width: 900px) {
            .main-content {
                flex-direction: column;
            }
            
            .form-section {
                border-right: none;
                border-bottom: 1px solid #eaeff5;
            }
            
            .controls {
                flex-direction: column;
            }
            
            .sort-controls, .stats-controls {
                width: 100%;
                justify-content: space-between;
            }
            
            .stats-display {
                flex-wrap: wrap;
            }
            
            .stat-item {
                flex: 1 0 40%;
                margin-bottom: 10px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <div class="logo-icon"><i class="fas fa-heartbeat"></i></div>
                <div class="logo-text">
                    <h1>维迪电生理预约管理系统</h1>
                    <p>高效、便捷的预约管理解决方案</p>
                </div>
            </div>
            <div class="current-time" id="current-time"></div>
        </header>
        
        <div class="main-content">
            <div class="form-section">
                <h2 class="section-title"><i class="fas fa-calendar-plus"></i> 新增预约</h2>
                <form id="appointment-form">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="name" class="required">患者姓名</label>
                            <div class="datalist-container">
                                <input type="text" id="name" list="name-list" required>
                                <datalist id="name-list"></datalist>
                                <span class="datalist-icon">▼</span>
                            </div>
                        </div>
                        <div class="form-group">
                            <label for="gender">性别</label>
                            <select id="gender">
                                <option value="">请选择</option>
                                <option value="男">男</option>
                                <option value="女">女</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="medical-number" class="required">诊疗号</label>
                            <div class="datalist-container">
                                <input type="text" id="medical-number" list="medical-number-list" required>
                                <datalist id="medical-number-list"></datalist>
                                <span class="datalist-icon">▼</span>
                            </div>
                        </div>
                        <div class="form-group">
                            <label for="doctor">检查医生</label>
                            <div class="datalist-container">
                                <input type="text" id="doctor" list="doctor-list">
                                <datalist id="doctor-list"></datalist>
                                <span class="datalist-icon">▼</span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="examination">检查项目</label>
                            <div class="datalist-container">
                                <input type="text" id="examination" list="examination-list">
                                <datalist id="examination-list"></datalist>
                                <span class="datalist-icon">▼</span>
                            </div>
                        </div>
                        <div class="form-group">
                            <label for="date">检查时间</label>
                            <input type="datetime-local" id="date">
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="status">预约状态</label>
                            <select id="status">
                                <option value="pending">待确认</option>
                                <option value="confirmed">已确认</option>
                                <option value="completed">已完成</option>
                                <option value="cancelled">已取消</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="notes">备注</label>
                        <textarea id="notes" rows="3"></textarea>
                    </div>
                    
                    <button type="submit"><i class="fas fa-plus-circle"></i> 提交预约</button>
                </form>
            </div>
            
            <div class="list-section">
                <h2 class="section-title"><i class="fas fa-list"></i> 预约列表</h2>
                
                <div class="search-bar">
                    <input type="text" id="search-input" placeholder="输入姓名或诊疗号进行搜索...">
                    <button id="search-btn"><i class="fas fa-search"></i> 搜索</button>
                </div>
                
                <div class="stats-display">
                    <div class="stat-item">
                        <div class="stat-value" id="today-count">0</div>
                        <div class="stat-label">今日预约</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-value" id="week-count">0</div>
                        <div class="stat-label">本周预约</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-value" id="month-count">0</div>
                        <div class="stat-label">本月预约</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-value" id="completed-count">0</div>
                        <div class="stat-label">已完成</div>
                    </div>
                </div>
                
                <div class="controls">
                    <div class="sort-controls">
                        <select id="sort-field">
                            <option value="name">按姓名排序</option>
                            <option value="medicalNumber">按诊疗号排序</option>
                            <option value="date">按时间排序</option>
                            <option value="doctor">按医生排序</option>
                            <option value="status">按状态排序</option>
                        </select>
                        <select id="sort-order">
                            <option value="asc">升序</option>
                            <option value="desc">降序</option>
                        </select>
                    </div>
                    
                    <div class="stats-controls">
                        <select id="stats-period">
                            <option value="day">日统计</option>
                            <option value="week">周统计</option>
                            <option value="month">月统计</option>
                            <option value="quarter">季度统计</option>
                            <option value="year">年统计</option>
                        </select>
                        <button id="stats-btn"><i class="fas fa-chart-bar"></i> 统计</button>
                    </div>
                    
                    <button id="reset-btn"><i class="fas fa-sync"></i> 重置搜索</button>
                </div>
                
                <div class="appointment-list">
                    <table id="appointment-table">
                        <thead>
                            <tr>
                                <th data-sort="name">姓名</th>
                                <th data-sort="gender">性别</th>
                                <th data-sort="medicalNumber">诊疗号</th>
                                <th data-sort="examination">检查项目</th>
                                <th data-sort="date">检查时间</th>
                                <th data-sort="doctor">医生</th>
                                <th data-sort="status">状态</th>
                                <th>操作</th>
                            </tr>
                        </thead>
                        <tbody id="appointment-list-body">
                            <!-- 预约记录将动态生成 -->
                        </tbody>
                    </table>
                    <div id="no-appointments" class="no-appointments">
                        <i class="fas fa-calendar-times fa-2x"></i>
                        <p>暂无预约记录</p>
                    </div>
                </div>
            </div>
        </div>
        
        <div id="password-modal" class="modal">
            <div class="modal-content">
                <div class="modal-header">
                    <h3 class="modal-title">修改状态确认</h3>
                    <button class="close-modal">&times;</button>
                </div>
                <div class="modal-body">
                    <p>您正在修改预约状态，此操作需要管理员权限。</p>
                    <div class="form-group">
                        <label for="password">请输入口令</label>
                        <input type="password" id="password" placeholder="输入口令...">
                    </div>
                    <div class="form-group">
                        <label for="new-status">选择新状态</label>
                        <select id="new-status">
                            <option value="confirmed">已确认</option>
                            <option value="completed">已完成</option>
                            <option value="cancelled">已取消</option>
                        </select>
                    </div>
                </div>
                <div class="modal-footer">
                    <button class="modal-btn cancel">取消</button>
                    <button class="modal-btn confirm">确认修改</button>
                </div>
            </div>
        </div>
        
        <div id="stats-modal" class="modal">
            <div class="modal-content">
                <div class="modal-header">
                    <h3 class="modal-title">工作量统计</h3>
                    <button class="close-modal">&times;</button>
                </div>
                <div class="modal-body">
                    <div id="stats-result">
                        <div class="stat-item">
                            <div class="stat-value" id="stats-count">0</div>
                            <div class="stat-label" id="stats-label">已完成预约</div>
                        </div>
                        <div style="text-align: center; margin-top: 20px; color: #7f8c8d;" id="stats-text">
                            <!-- 统计文本将显示在这里 -->
                        </div>
                    </div>
                </div>
                <div class="modal-footer">
                    <button class="modal-btn cancel">关闭</button>
                </div>
            </div>
        </div>
        
        <div class="toast" id="toast">
            <i class="fas fa-check-circle"></i>
            <span id="toast-message">操作成功！</span>
        </div>
        
        <footer>
            <p>维迪电生理预约管理系统 © 2025 | 版本 2.1.0</p>
        </footer>
    </div>

    <script>
        // 当前时间显示
        function updateTime() {
            const now = new Date();
            const options = { 
                year: 'numeric', 
                month: 'long', 
                day: 'numeric',
                hour: '2-digit',
                minute: '2-digit',
                second: '2-digit',
                weekday: 'long',
                hour12: false
            };
            document.getElementById('current-time').textContent = now.toLocaleString('zh-CN', options);
        }
        
        setInterval(updateTime, 1000);
        updateTime();
        
        // 预约数据管理
        let appointments = JSON.parse(localStorage.getItem('appointments')) || [];
        let historyData = JSON.parse(localStorage.getItem('historyData')) || {
            names: [],
            medicalNumbers: [],
            examinations: [],
            doctors: []
        };
        
        // 状态映射
        const statusMap = {
            'pending': {text: '待确认', class: 'status-pending'},
            'confirmed': {text: '已确认', class: 'status-confirmed'},
            'completed': {text: '已完成', class: 'status-completed'},
            'cancelled': {text: '已取消', class: 'status-cancelled'}
        };
        
        // 初始化历史数据下拉列表
        function initHistoryData() {
            const nameList = document.getElementById('name-list');
            const medicalNumberList = document.getElementById('medical-number-list');
            const examinationList = document.getElementById('examination-list');
            const doctorList = document.getElementById('doctor-list');
            
            // 清空现有选项
            nameList.innerHTML = '';
            medicalNumberList.innerHTML = '';
            examinationList.innerHTML = '';
            doctorList.innerHTML = '';
            
            historyData.names.forEach(name => {
                const option = document.createElement('option');
                option.value = name;
                nameList.appendChild(option);
            });
            
            historyData.medicalNumbers.forEach(number => {
                const option = document.createElement('option');
                option.value = number;
                medicalNumberList.appendChild(option);
            });
            
            historyData.examinations.forEach(exam => {
                const option = document.createElement('option');
                option.value = exam;
                examinationList.appendChild(option);
            });
            
            historyData.doctors.forEach(doctor => {
                const option = document.createElement('option');
                option.value = doctor;
                doctorList.appendChild(option);
            });
        }
        
        // 保存历史数据
        function saveHistoryData() {
            localStorage.setItem('historyData', JSON.stringify(historyData));
        }
        
        // 添加历史记录
        function addToHistory(value, field) {
            if (value && !historyData[field].includes(value)) {
                historyData[field].push(value);
                saveHistoryData();
                initHistoryData(); // 重新初始化下拉列表
            }
        }
        
        // 渲染预约列表
        function renderAppointments(data = appointments) {
            const tbody = document.getElementById('appointment-list-body');
            const noAppointments = document.getElementById('no-appointments');
            
            if (data.length === 0) {
                tbody.innerHTML = '';
                noAppointments.style.display = 'block';
                return;
            }
            
            noAppointments.style.display = 'none';
            tbody.innerHTML = '';
            
            data.forEach(appointment => {
                const row = document.createElement('tr');
                
                // 格式化日期时间
                const date = new Date(appointment.date);
                const formattedDate = appointment.date ? 
                    `${date.getFullYear()}-${(date.getMonth()+1).toString().padStart(2, '0')}-${date.getDate().toString().padStart(2, '0')} ${date.getHours().toString().padStart(2, '0')}:${date.getMinutes().toString().padStart(2, '0')}` : 
                    '未安排';
                
                // 获取状态信息
                const statusInfo = statusMap[appointment.status] || statusMap.pending;
                
                row.innerHTML = `
                    <td>${appointment.name}</td>
                    <td>${appointment.gender || '-'}</td>
                    <td>${appointment.medicalNumber}</td>
                    <td>${appointment.examination || '-'}</td>
                    <td>${formattedDate}</td>
                    <td>${appointment.doctor || '-'}</td>
                    <td><span class="status ${statusInfo.class}">${statusInfo.text}</span></td>
                    <td class="actions">
                        <button class="action-btn edit-btn" data-id="${appointment.id}" title="编辑"><i class="fas fa-edit"></i></button>
                        <button class="action-btn status-btn" data-id="${appointment.id}" title="修改状态"><i class="fas fa-exchange-alt"></i></button>
                        <button class="action-btn copy-btn" data-id="${appointment.id}" title="复制信息"><i class="fas fa-copy"></i></button>
                        <button class="action-btn delete-btn" data-id="${appointment.id}" title="删除"><i class="fas fa-trash"></i></button>
                    </td>
                `;
                
                tbody.appendChild(row);
            });
            
            // 更新统计信息
            updateStats();
        }
        
        // 更新统计信息
        function updateStats() {
            const now = new Date();
            const today = new Date(now.getFullYear(), now.getMonth(), now.getDate());
            const startOfWeek = new Date(today);
            startOfWeek.setDate(today.getDate() - today.getDay());
            const startOfMonth = new Date(now.getFullYear(), now.getMonth(), 1);
            
            // 今日预约
            const todayAppointments = appointments.filter(app => {
                if (!app.date) return false;
                const appDate = new Date(app.date);
                return appDate >= today && appDate < new Date(today.getTime() + 86400000);
            });
            
            // 本周预约
            const weekAppointments = appointments.filter(app => {
                if (!app.date) return false;
                const appDate = new Date(app.date);
                return appDate >= startOfWeek;
            });
            
            // 本月预约
            const monthAppointments = appointments.filter(app => {
                if (!app.date) return false;
                const appDate = new Date(app.date);
                return appDate >= startOfMonth;
            });
            
            // 已完成预约
            const completedAppointments = appointments.filter(app => app.status === 'completed');
            
            document.getElementById('today-count').textContent = todayAppointments.length;
            document.getElementById('week-count').textContent = weekAppointments.length;
            document.getElementById('month-count').textContent = monthAppointments.length;
            document.getElementById('completed-count').textContent = completedAppointments.length;
        }
        
        // 保存预约数据
        function saveAppointments() {
            localStorage.setItem('appointments', JSON.stringify(appointments));
        }
        
        // 生成唯一ID
        function generateId() {
            return Date.now().toString(36) + Math.random().toString(36).substr(2);
        }
        
        // 添加新预约
        function addAppointment(event) {
            event.preventDefault();
            
            const name = document.getElementById('name').value;
            const gender = document.getElementById('gender').value;
            const medicalNumber = document.getElementById('medical-number').value;
            const examination = document.getElementById('examination').value;
            const date = document.getElementById('date').value;
            const doctor = document.getElementById('doctor').value;
            const status = document.getElementById('status').value;
            const notes = document.getElementById('notes').value;
            
            const newAppointment = {
                id: generateId(),
                name,
                gender,
                medicalNumber,
                examination,
                date,
                doctor,
                status,
                notes,
                createdAt: new Date().toISOString()
            };
            
            appointments.push(newAppointment);
            saveAppointments();
            
            // 添加到历史记录
            addToHistory(name, 'names');
            addToHistory(medicalNumber, 'medicalNumbers');
            if (examination) addToHistory(examination, 'examinations');
            if (doctor) addToHistory(doctor, 'doctors');
            
            // 重置表单
            document.getElementById('appointment-form').reset();
            
            // 重新渲染列表
            renderAppointments();
            
            showToast('预约添加成功！');
        }
        
        // 搜索预约
        function searchAppointments() {
            const searchTerm = document.getElementById('search-input').value.toLowerCase();
            
            if (!searchTerm) {
                renderAppointments();
                return;
            }
            
            const results = appointments.filter(app => 
                app.name.toLowerCase().includes(searchTerm) || 
                app.medicalNumber.toLowerCase().includes(searchTerm)
            );
            
            renderAppointments(results);
        }
        
        // 排序预约
        function sortAppointments() {
            const field = document.getElementById('sort-field').value;
            const order = document.getElementById('sort-order').value;
            
            const sorted = [...appointments].sort((a, b) => {
                let valueA = a[field];
                let valueB = b[field];
                
                // 处理日期排序
                if (field === 'date') {
                    valueA = valueA ? new Date(valueA) : new Date(0);
                    valueB = valueB ? new Date(valueB) : new Date(0);
                }
                
                // 处理状态排序
                if (field === 'status') {
                    const statusOrder = ['pending', 'confirmed', 'completed', 'cancelled'];
                    valueA = statusOrder.indexOf(valueA);
                    valueB = statusOrder.indexOf(valueB);
                }
                
                // 处理空值
                if (!valueA) return 1;
                if (!valueB) return -1;
                
                if (valueA < valueB) return order === 'asc' ? -1 : 1;
                if (valueA > valueB) return order === 'asc' ? 1 : -1;
                return 0;
            });
            
            renderAppointments(sorted);
        }
        
        // 表头排序
        function handleHeaderSort(event) {
            const field = event.target.dataset.sort;
            if (!field) return;
            
            document.getElementById('sort-field').value = field;
            sortAppointments();
        }
        
        // 删除预约
        function deleteAppointment(id) {
            if (confirm('确定要删除此预约记录吗？')) {
                appointments = appointments.filter(app => app.id !== id);
                saveAppointments();
                renderAppointments();
                showToast('预约已删除！');
            }
        }
        
        // 编辑预约
        function editAppointment(id) {
            const appointment = appointments.find(app => app.id === id);
            if (!appointment) return;
            
            document.getElementById('name').value = appointment.name;
            document.getElementById('gender').value = appointment.gender || '';
            document.getElementById('medical-number').value = appointment.medicalNumber;
            document.getElementById('examination').value = appointment.examination || '';
            document.getElementById('date').value = appointment.date || '';
            document.getElementById('doctor').value = appointment.doctor || '';
            document.getElementById('status').value = appointment.status || 'pending';
            document.getElementById('notes').value = appointment.notes || '';
            
            // 删除原预约
            appointments = appointments.filter(app => app.id !== id);
            saveAppointments();
            
            // 滚动到表单区域
            document.querySelector('.form-section').scrollIntoView({ behavior: 'smooth' });
            
            showToast('预约已加载到编辑表单');
        }
        
        // 修改状态
        let currentAppointmentId = null;
        
        function openStatusModal(id) {
            currentAppointmentId = id;
            document.getElementById('password').value = '';
            document.getElementById('new-status').value = 'confirmed';
            document.getElementById('password-modal').style.display = 'flex';
        }
        
        function changeStatus() {
            const password = document.getElementById('password').value;
            if (password !== '666') {
                showToast('口令错误，操作未授权！');
                return;
            }
            
            const appointment = appointments.find(app => app.id === currentAppointmentId);
            if (!appointment) return;
            
            const newStatus = document.getElementById('new-status').value;
            
            if (['confirmed', 'completed', 'cancelled'].includes(newStatus)) {
                appointment.status = newStatus;
                saveAppointments();
                renderAppointments();
                showToast('状态更新成功！');
            } else {
                showToast('无效的状态值！');
            }
            
            document.getElementById('password-modal').style.display = 'none';
        }
        
        // 复制预约信息
        function copyAppointmentInfo(id) {
            const appointment = appointments.find(app => app.id === id);
            if (!appointment) return;
            
            const statusInfo = statusMap[appointment.status] || statusMap.pending;
            
            // 格式化日期时间
            let formattedDate = '未安排';
            if (appointment.date) {
                const date = new Date(appointment.date);
                formattedDate = `${date.getFullYear()}-${(date.getMonth()+1).toString().padStart(2, '0')}-${date.getDate().toString().padStart(2, '0')} ${date.getHours().toString().padStart(2, '0')}:${date.getMinutes().toString().padStart(2, '0')}`;
            }
            
            const infoText = `患者姓名：${appointment.name}
性别：${appointment.gender || '未填写'}
诊疗号：${appointment.medicalNumber}
检查项目：${appointment.examination || '未填写'}
检查时间：${formattedDate}
检查医生：${appointment.doctor || '未填写'}
预约状态：${statusInfo.text}
备注：${appointment.notes || '无'}`;
            
            // 复制到剪贴板
            navigator.clipboard.writeText(infoText).then(() => {
                showToast('预约信息已复制到剪贴板！');
            }).catch(err => {
                showToast('复制失败，请手动复制');
                console.error('复制失败:', err);
            });
        }
        
        // 统计工作量
        function calculateWorkload(period) {
            const now = new Date();
            let startDate, endDate;
            let periodName = '';
            
            switch (period) {
                case 'day':
                    startDate = new Date(now.getFullYear(), now.getMonth(), now.getDate());
                    endDate = new Date(startDate.getTime() + 86400000);
                    periodName = '今日';
                    break;
                case 'week':
                    startDate = new Date(now);
                    startDate.setDate(now.getDate() - now.getDay());
                    endDate = new Date(startDate);
                    endDate.setDate(startDate.getDate() + 7);
                    periodName = '本周';
                    break;
                case 'month':
                    startDate = new Date(now.getFullYear(), now.getMonth(), 1);
                    endDate = new Date(now.getFullYear(), now.getMonth() + 1, 1);
                    periodName = '本月';
                    break;
                case 'quarter':
                    const quarter = Math.floor(now.getMonth() / 3);
                    startDate = new Date(now.getFullYear(), quarter * 3, 1);
                    endDate = new Date(now.getFullYear(), (quarter + 1) * 3, 1);
                    periodName = '本季度';
                    break;
                case 'year':
                    startDate = new Date(now.getFullYear(), 0, 1);
                    endDate = new Date(now.getFullYear() + 1, 0, 1);
                    periodName = '本年';
                    break;
                default:
                    return {appointments: [], periodName: ''};
            }
            
            const completedAppointments = appointments.filter(app => {
                if (!app.date || app.status !== 'completed') return false;
                const appDate = new Date(app.date);
                return appDate >= startDate && appDate < endDate;
            });
            
            return {appointments: completedAppointments, periodName};
        }
        
        function showStats() {
            const period = document.getElementById('stats-period').value;
            const {appointments: completedAppointments, periodName} = calculateWorkload(period);
            
            document.getElementById('stats-count').textContent = completedAppointments.length;
            document.getElementById('stats-label').textContent = `${periodName}已完成预约`;
            
            // 生成统计文本
            let statsText = `<p>${periodName}已完成预约: <strong>${completedAppointments.length}</strong> 个</p>`;
            
            if (completedAppointments.length > 0) {
                statsText += '<p>已完成预约列表：</p><ul style="margin-top: 10px; max-height: 200px; overflow-y: auto;">';
                
                completedAppointments.forEach(app => {
                    const date = new Date(app.date);
                    const formattedDate = `${date.getFullYear()}-${(date.getMonth()+1).toString().padStart(2, '0')}-${date.getDate().toString().padStart(2, '0')}`;
                    statsText += `<li>${app.name} (${app.medicalNumber}) - ${formattedDate}</li>`;
                });
                
                statsText += '</ul>';
            } else {
                statsText += '<p>没有已完成预约记录</p>';
            }
            
            document.getElementById('stats-text').innerHTML = statsText;
            document.getElementById('stats-modal').style.display = 'flex';
        }
        
        // 显示Toast通知
        function showToast(message) {
            const toast = document.getElementById('toast');
            const toastMessage = document.getElementById('toast-message');
            
            toastMessage.textContent = message;
            toast.style.display = 'flex';
            
            setTimeout(() => {
                toast.style.opacity = '1';
            }, 10);
            
            setTimeout(() => {
                toast.style.opacity = '0';
                setTimeout(() => {
                    toast.style.display = 'none';
                }, 300);
            }, 3000);
        }
        
        // 事件监听
        document.getElementById('appointment-form').addEventListener('submit', addAppointment);
        document.getElementById('search-btn').addEventListener('click', searchAppointments);
        document.getElementById('search-input').addEventListener('keyup', function(event) {
            if (event.key === 'Enter') searchAppointments();
        });
        document.getElementById('reset-btn').addEventListener('click', function() {
            document.getElementById('search-input').value = '';
            renderAppointments();
        });
        document.getElementById('sort-field').addEventListener('change', sortAppointments);
        document.getElementById('sort-order').addEventListener('change', sortAppointments);
        document.getElementById('stats-btn').addEventListener('click', showStats);
        
        document.getElementById('appointment-table').addEventListener('click', function(event) {
            const target = event.target.closest('button');
            if (!target) return;
            
            const id = target.dataset.id;
            
            if (target.classList.contains('delete-btn')) {
                deleteAppointment(id);
            } else if (target.classList.contains('edit-btn')) {
                editAppointment(id);
            } else if (target.classList.contains('status-btn')) {
                openStatusModal(id);
            } else if (target.classList.contains('copy-btn')) {
                copyAppointmentInfo(id);
            }
        });
        
        document.querySelectorAll('th[data-sort]').forEach(th => {
            th.addEventListener('click', handleHeaderSort);
        });
        
        // 模态框事件
        document.querySelectorAll('.close-modal, .modal-btn.cancel').forEach(btn => {
            btn.addEventListener('click', function() {
                document.querySelectorAll('.modal').forEach(modal => {
                    modal.style.display = 'none';
                });
            });
        });
        
        document.querySelector('.modal-btn.confirm').addEventListener('click', changeStatus);
        
        // 初始化
        initHistoryData();
        renderAppointments();
    </script>
</body>
</html>
