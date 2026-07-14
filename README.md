<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>保定中城德瑞种苗有限公司 · 现代农业园区</title>
    <!-- Font Awesome 图标库 -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
        }

        body {
            background: #f5f8f0;
            color: #1e3a2e;
            line-height: 1.6;
        }

        /* 导航栏 - 复用 */
        nav {
            background: linear-gradient(145deg, #1d4a2b, #2a6e3a);
            padding: 0.8rem 2rem;
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: space-between;
            box-shadow: 0 4px 12px rgba(0,30,10,0.2);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 8px;
            color: #f5ffe0;
            font-size: 1.5rem;
            font-weight: 600;
            letter-spacing: 1px;
        }

        .logo i {
            font-size: 2rem;
            color: #f9d56e;
        }

        .nav-links {
            display: flex;
            flex-wrap: wrap;
            gap: 0.2rem 0.8rem;
        }

        .nav-links a {
            color: #f0f7e6;
            text-decoration: none;
            padding: 0.5rem 0.8rem;
            border-radius: 30px;
            font-weight: 500;
            transition: 0.2s;
            font-size: 0.95rem;
            display: inline-flex;
            align-items: center;
            gap: 6px;
        }

        .nav-links a:hover {
            background: #f9d56e;
            color: #1e3a2e;
            box-shadow: 0 2px 8px rgba(0,0,0,0.2);
        }

        .nav-links a.active {
            background: #f9d56e;
            color: #1d4a2b;
        }

        .page {
            max-width: 1300px;
            margin: 2rem auto;
            padding: 0 1.5rem 3rem;
            display: none;
            animation: fade 0.3s ease;
        }

        .page.active-page {
            display: block;
        }

        @keyframes fade {
            0% { opacity: 0.5; transform: translateY(8px); }
            100% { opacity: 1; transform: translateY(0); }
        }

        /* 卡片通用 */
        .card-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 2rem;
            margin: 2rem 0;
        }

        .card {
            background: white;
            border-radius: 32px;
            padding: 1.8rem 1.5rem;
            box-shadow: 0 12px 28px rgba(0,30,10,0.08);
            transition: 0.2s;
            border: 1px solid #e3f0da;
        }

        .card:hover {
            transform: translateY(-6px);
            box-shadow: 0 20px 32px rgba(30, 70, 40, 0.12);
        }

        .card i {
            font-size: 2.4rem;
            color: #2a6e3a;
            margin-bottom: 0.8rem;
        }

        .btn {
            display: inline-block;
            background: #2a6e3a;
            color: white;
            padding: 0.4rem 1.4rem;
            border-radius: 40px;
            text-decoration: none;
            font-weight: 500;
            font-size: 0.9rem;
            margin-top: 1rem;
            transition: 0.2s;
            border: none;
            cursor: pointer;
        }

        .btn-outline {
            background: transparent;
            border: 2px solid #2a6e3a;
            color: #2a6e3a;
        }

        .btn-outline:hover {
            background: #2a6e3a;
            color: white;
        }

        .btn-small {
            padding: 0.2rem 1.2rem;
            font-size: 0.8rem;
        }

        /* 首页横幅 */
        .hero {
            background: linear-gradient(135deg, #e5f4dc, #cbe5bc);
            border-radius: 48px;
            padding: 2.8rem 2.5rem;
            margin-bottom: 2.5rem;
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: space-between;
        }

        .hero h1 {
            font-size: 2.6rem;
            font-weight: 700;
            color: #174a26;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 600px;
            color: #1f4d2a;
        }

        .hero-img i {
            font-size: 6rem;
            color: #2f7a44;
            opacity: 0.5;
        }

        /* 种苗服务 - 详情弹窗 */
        .modal {
            display: none;
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.4);
            backdrop-filter: blur(3px);
            justify-content: center;
            align-items: center;
            z-index: 999;
        }

        .modal-content {
            background: white;
            max-width: 500px;
            width: 90%;
            padding: 2rem 2.5rem;
            border-radius: 48px;
            position: relative;
            box-shadow: 0 40px 60px rgba(0,0,0,0.3);
            animation: fade 0.25s ease;
        }

        .modal-close {
            position: absolute;
            top: 15px; right: 20px;
            font-size: 2rem;
            cursor: pointer;
            color: #555;
        }

        /* 新闻卡片 */
        .news-item {
            background: white;
            border-radius: 24px;
            padding: 1.5rem;
            margin-bottom: 1.2rem;
            box-shadow: 0 4px 10px rgba(0,0,0,0.02);
            border-left: 6px solid #2a6e3a;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
        }

        .news-item a {
            color: #1d4a2b;
            font-weight: 600;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }

        .news-item a i {
            transition: 0.2s;
        }

        .news-item a:hover i {
            transform: translateX(5px);
            color: #f9d56e;
        }

        .news-date {
            color: #4d6b53;
            font-size: 0.85rem;
        }

        .tag {
            background: #dff0d6;
            padding: 0.2rem 1rem;
            border-radius: 40px;
            font-size: 0.75rem;
            font-weight: 600;
            color: #1d4a2b;
        }
