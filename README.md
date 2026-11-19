[3.0版本.html](https://github.com/user-attachments/files/35063868/3.0.html)
# -WW-ay-.github.io<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>阿也网 登陆</title>
    <style>
        /* 定义颜色变量，实现跟随手机系统的黑白模式 */
        :root {
            --bg-color: #ffffff;
            --text-color: #000000;
            --border-color: #000000;
            --input-line: #000000;
        }

        /* 当系统处于暗黑模式时应用以下颜色 */
        @media (prefers-color-scheme: dark) {
            :root {
                --bg-color: #121212;
                --text-color: #ffffff;
                --border-color: #ffffff;
                --input-line: #ffffff;
            }
        }

        /* 基础重置 */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: "Microsoft YaHei", "PingFang SC", sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            transition: background-color 0.3s, color 0.3s;
        }

        /* 左上角红字标题 */
        .top-left-title {
            position: absolute;
            top: 20px;
            left: 20px;
            color: red;
            font-size: 24px;
            font-weight: bold;
            letter-spacing: 2px;
        }

        /* 登录框外框（固定蓝框） */
        .login-container {
            border: 3px solid #00FFFF; /* 保持蓝色不变 */
            padding: 40px 30px;
            width: 90%;
            max-width: 350px;
            background-color: transparent;
            position: relative;
        }

        /* 标题 */
        .title {
            text-align: center;
            font-size: 32px;
            font-weight: bold;
            margin-bottom: 40px;
            letter-spacing: 10px;
            color: var(--text-color);
        }

        /* 输入行容器 */
        .input-group {
            margin-bottom: 30px;
            position: relative;
        }

        /* 标签文字 */
        .label {
            font-size: 18px;
            font-weight: bold;
            display: block;
            margin-bottom: 5px;
        }

        /* 输入框样式（仅保留底边） */
        .input-field {
            width: 100%;
            background: transparent;
            border: none;
            border-bottom: 4px solid var(--input-line); /* 粗黑线或粗白线 */
            color: var(--text-color);
            font-size: 20px;
            padding: 5px;
            outline: none;
            letter-spacing: 2px;
            transition: border-color 0.3s;
        }

        /* 去除输入框自带的清除图标 */
        .input-field::-ms-clear { display: none; }
        .input-field::-webkit-clear-button { display: none; }

        /* 显示/隐藏密码按钮 */
        .toggle-password {
            position: absolute;
            right: 5px;
            bottom: 10px;
            font-size: 14px;
            color: var(--text-color);
            cursor: pointer;
            background: transparent;
            border: 1px solid var(--text-color);
            padding: 2px 5px;
            user-select: none;
            font-weight: bold;
        }

        /* 底部按钮容器 */
        .button-group {
            display: flex;
            justify-content: space-between;
            margin-top: 50px;
        }

        /* 清空和确定按钮 */
        .btn {
            width: 45%;
            padding: 10px 0;
            background: transparent;
            border: 3px solid var(--border-color);
            color: var(--text-color);
            font-size: 20px;
            font-weight: bold;
            cursor: pointer;
            text-align: center;
            letter-spacing: 5px;
            transition: all 0.2s;
        }

        /* 点击按钮的反馈效果 */
        .btn:active {
            opacity: 0.6;
        }

        /* 屏幕中间提示框 (Toast) */
        #toast {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: rgba(0, 0, 0, 0.85);
            color: #ffffff;
            padding: 15px 20px;
            border-radius: 8px;
            font-size: 16px;
            text-align: center;
            display: none;
            z-index: 9999;
            width: 80%;
            max-width: 300px;
            line-height: 1.5;
            box-shadow: 0 4px 12px rgba(0,0,0,0.3);
            pointer-events: none; /* 让提示框不阻挡点击 */
        }

        /* 成功后的全屏文字 */
        .success-message {
            display: none;
            text-align: center;
            font-size: 24px;
            font-weight: bold;
            color: var(--text-color);
            padding: 20px;
            line-height: 1.6;
            animation: fadeIn 1s;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

    </style>
</head>
<body>

    <!-- 左上角标志 -->
    <div class="top-left-title" id="site-title">阿也网（测试专用网站不代表正式网站）</div>

    <!-- 登录框 -->
    <div class="login-container" id="login-container">
        <div class="title">登陆</div>

        <!-- 编号输入 -->
        <div class="input-group">
            <label class="label">编号：</label>
            <input type="text" id="username" class="input-field" autocomplete="off">
        </div>

        <!-- 密码输入 -->
        <div class="input-group">
            <label class="label">密码：</label>
            <input type="password" id="password" class="input-field" autocomplete="off">
            <div class="toggle-password" id="toggle-btn">显示密码</div>
        </div>

        <!-- 按钮组 -->
        <div class="button-group">
            <button class="btn" id="clear-btn">清空</button>
            <button class="btn" id="confirm-btn">确定</button>
        </div>
    </div>

    <!-- 成功后的显示区域 -->
    <div class="success-message" id="success-message">
        由于该网站是测试专用网站，不算是正式网站。  （网站测试3.0版本）
    </div>

    <!-- 提示框 -->
    <div id="toast"></div>

    <script>
        // 获取DOM元素
        const usernameInput = document.getElementById('username');
        const passwordInput = document.getElementById('password');
        const toggleBtn = document.getElementById('toggle-btn');
        const clearBtn = document.getElementById('clear-btn');
        const confirmBtn = document.getElementById('confirm-btn');
        const toast = document.getElementById('toast');
        const loginContainer = document.getElementById('login-container');
        const siteTitle = document.getElementById('site-title');
        const successMessage = document.getElementById('success-message');

        // 正确的账号密码
        const CORRECT_USER = 'WMWMWM123';
        const CORRECT_PASS = '123com';

        let toastTimeout;

        // 显示中间提示框的函数
        function showToast(message) {
            toast.innerText = message;
            toast.style.display = 'block';
            
            // 清除之前的定时器，防止多个提示重叠
            clearTimeout(toastTimeout);
            
            // 2.5秒后自动隐藏
            toastTimeout = setTimeout(() => {
                toast.style.display = 'none';
            }, 2500);
        }

        // 密码显示/隐藏切换
        toggleBtn.addEventListener('click', () => {
            if (passwordInput.type === 'password') {
                passwordInput.type = 'text';
                toggleBtn.innerText = '关闭显示';
            } else {
                passwordInput.type = 'password';
                toggleBtn.innerText = '显示密码';
            }
        });

        // 清空按钮功能
        clearBtn.addEventListener('click', () => {
            usernameInput.value = '';
            passwordInput.value = '';
            // 重置密码输入框状态
            passwordInput.type = 'password';
            toggleBtn.innerText = '显示密码';
            usernameInput.focus();
        });

        // 确定按钮功能与逻辑判断
        confirmBtn.addEventListener('click', () => {
            const userVal = usernameInput.value.trim();
            const passVal = passwordInput.value.trim();

            // 情况1：都没有输入
            if (userVal === '' && passVal === '') {
                showToast('当前没有输入编号和密码，请输入再尝试！');
                return;
            }

            // 情况2：只输入了编号
            if (userVal !== '' && passVal === '') {
                showToast('当前只输入编号没有输入密码，请输入完整再尝试！');
                return;
            }

            // 情况3：只输入了密码
            if (userVal === '' && passVal !== '') {
                showToast('当前只输入密码没有输入编号，请输入完整再尝试！');
                return;
            }

            // 情况4：都输入了，判断是否正确
            if (userVal !== CORRECT_USER || passVal !== CORRECT_PASS) {
                showToast('编号和密码输入错误，请重新输入！');
                return;
            }

            // 情况5：输入完全正确
            // 隐藏登录框和左上角标题
            loginContainer.style.display = 'none';
            siteTitle.style.display = 'none';
            
            // 显示全屏成功提示
            successMessage.style.display = 'block';
        });
    </script>
</body>
</html>
