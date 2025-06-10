# sheep
تطبيق ادارة بيع الاغنام
<!DOCTYPE html>
<html dir="rtl" lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نظام إدارة الأغام</title>
    <style>
        :root {
            --primary-color: #2e7d32;
            --primary-light: #4caf50;
            --primary-dark: #1b5e20;
            --secondary-color: #ffc107;
            --accent-color: #ff6b6b;
            --background-color: #f8f9fa;
            --card-bg: #ffffff;
            --text-primary: #212529;
            --text-secondary: #6c757d;
            --border-color: #e0e0e0;
            --shadow: 0 2px 12px rgba(0,0,0,0.1);
            --radius: 16px;
            --radius-sm: 8px;
            
        }

        /* أنماط أيقونة الإحصائيات */
  .dashboard-icon-inner {
      display: flex;
      align-items: center;
      gap: 6px;
      flex-shrink: 0;
      cursor: pointer;
      padding: 8px 12px;
      border-radius: 20px;
      transition: all 0.2s ease;
  }

  .dashboard-icon-inner:hover {
      background-color: rgba(46, 125, 50, 0.1);
  }

  .dashboard-icon-inner:active {
      background-color: rgba(46, 125, 50, 0.2);
      transform: scale(0.97);
  }

  .dashboard-icon-inner svg {
      transition: transform 0.2s ease;
  }

  .dashboard-icon-inner:hover svg {
      transform: translateY(-2px);
  }

  /* تنسيق النص */
  .dashboard-icon-inner .notification {
      font-size: 12px;
      color: #dbf857;
      font-weight: 500;
      transition: color 0.2s ease;
  }

  .dashboard-icon-inner:hover .notification {
      color: var(--primary-color);
  }

  /* تعديلات للأجهزة المحمولة */
  @media (max-width: 480px) {
      .dashboard-icon-inner {
          padding: 6px;
      }
      
      .dashboard-icon-inner .notification {
          display: none; /* إخفاء النص في الشاشات الصغيرة جداً */
      }
  }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            min-height: 100vh;
            color: var(--text-primary);
        }

        /* Header */
        .header {
            background: linear-gradient(135deg, var(--primary-color) 0%, var(--primary-dark) 100%);
            color: white;
            padding: 1rem 1.5rem;
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: 2;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1000 100" fill="rgba(255,255,255,0.1)"><polygon points="1000,100 0,100 0,0 1000,20"/></svg>') no-repeat bottom;
            background-size: cover;
        }

        .header-content {
            display: flex;
            align-items: center;
            justify-content: space-between;
            position: relative;
        }

        .header-title {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .header-icon {
            width: 48px;
            height: 48px;
            background: rgba(255,255,255,0.2);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
        }

        .header h1 {
            font-size: 1.5rem;
            font-weight: 600;
        }

        /* Navigation */
        .nav-container {
            background: var(--card-bg);
            border-bottom: 1px solid var(--border-color);
            padding: 0 1rem;
        }

        .nav-tabs {
            display: flex;
            overflow-x: auto;
            gap: 0.5rem;
        }

        .nav-tab {
            padding: 1rem 1.5rem;
            background: none;
            border: none;
            color: var(--text-secondary);
            font-weight: 500;
            font-size: 0.9rem;
            cursor: pointer;
            transition: all 0.3s ease;
            border-bottom: 3px solid transparent;
            white-space: nowrap;
            position: relative;
        }

        .nav-tab:hover {
            color: var(--primary-color);
            background: rgba(46, 125, 50, 0.05);
        }

        .nav-tab.active {
            color: var(--primary-color);
            border-bottom-color: var(--primary-color);
            background: rgba(46, 125, 50, 0.1);
        }

        /* Main Container */
        .main-container {
            padding: 1.5rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .content-section {
            display: none;
        }

        .content-section.active {
            display: block;
            animation: fadeIn 0.3s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Cards */
        .card {
            background: var(--card-bg);
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border: 1px solid var(--border-color);
        }

        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
            padding-bottom: 1rem;
            border-bottom: 1px solid var(--border-color);
        }
        /* Remove bottom margin if it's for a collapsible section header that doesn't have content directly under it initially */
        .card-header[onclick] { /* Be more specific if needed */
             margin-bottom: 0; /* Adjust if content is shown */
        }


        .card-title {
            font-size: 1.2rem;
            font-weight: 600;
            color: var(--text-primary);
        }

        /* أنماط المنتجا القابلة للطي */
/* أنماط المنتجات القابلة للطي */
/* أنماط المنتجات القابلة للطي - نسخة محدة */
/* أنماط المنتات القابلة للطي - نسخة محدثة */
.product-item {
    background: var(--card-bg);
    border: 1px solid var(--border-color); /* تصغير حجم الحدود */
    border-radius: 12px; /* تصغير قليلاً */
    padding: 0.6rem 0.8rem; /* تقليل المساحة الداخلية */
    margin-bottom: 0.5rem; /* تقلل المسافة بين البلوكات */
    transition: all 0.3s ease;
    cursor: pointer;
}

.product-item:hover {
    border-color: var(--primary-light);
    box-shadow: 0 2px 6px rgba(46, 125, 50, 0.15);
    transform: translateY(-1px);
}

.product-item.collapsed .product-details {
    display: none;
    height: 0;
    overflow: hidden;
    opacity: 0;
    transform: translateY(-5px);
    transition: all 0.3s ease;
}

.product-item.expanded .product-details {
    display: block;
    height: auto;
    opacity: 1;
    transform: translateY(0);
    padding-top: 0.6rem;
    margin-top: 0.6rem;
    border-top: 1px solid var(--border-color);
}

.product-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
}

.product-name {
    font-size: 0.9rem; /* تصغير حجم الخط */
    font-weight: 600;
    color: var(--text-primary);
    display: flex;
    align-items: center;
    gap: 0.5rem;
    flex-grow: 1; /* السمح للاسم بأخذ المساحة المتبقية */
}

.product-toggle {
    color: var(--text-secondary);
    display: flex;
    align-items: center;
    margin-right: 0;
    flex-shrink: 0; /* منع انكماش عنصر التبديل */
}

/* صميم النقاط العمدية الثلاث */
.vertical-dots {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 2px;
    width: 18px;
    height: 18px;
}

.dot {
    width: 4px;
    height: 4px;
    background-color: var(--text-secondary);
    border-radius: 50%;
}

.product-badge {
    background: var(--primary-color);
    color: white;
    padding: 0.1rem 0.4rem; /* تقليل حجم البادج */
    border-radius: 12px;
    font-size: 0.7rem;
    font-weight: 500;
}

.badge-أغنام { background: var(--primary-color); }
.badge-أعلاف { background: #ff9800; }
.badge-علاجات { background: #e91e63; }

/* حال التحديد */
.product-item.selected {
    border-color: var(--primary-color);
    background: rgba(46, 125, 50, 0.05);
}

/* تصغير حقول الإدخال داخل البلوك امطوي */
.product-controls {
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 0.8rem;
    align-items: center;
}

.price-input-container {
    position: relative;
}

.price-input {
    width: 100%;
    padding: 0.6rem 0.8rem; /* تقلل الارتفاع */
    padding-left: 2.5rem;
    border: 1px solid var(--border-color);
    border-radius: 6px;
    font-size: 0.9rem;
    text-align: center;
    transition: all 0.3s ease;
}

.price-input:focus {
    outline: none;
    border-color: var(--primary-color);
    box-shadow: 0 0 0 2px rgba(46, 125, 50, 0.1);
}

.currency-symbol {
    position: absolute;
    left: 0.8rem;
    top: 50%;
    transform: translateY(-50%);
    color: var(--text-secondary);
    font-weight: 500;
    font-size: 0.9rem;
}

.quantity-control {
    display: flex;
    align-items: center;
    background: var(--background-color);
    border-radius: 6px;
    overflow: hidden;
    border: 1px solid var(--border-color);
}

.qty-btn {
    background: var(--primary-color);
    color: white;
    border: none;
    width: 32px; /* تصغي حجم الأزرار */
    height: 32px;
    font-size: 1rem;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.3s ease;
    display: flex;
    align-items: center;
    justify-content: center;
}

.qty-btn:hover {
    background: var(--primary-dark);
}

.qty-input {
    width: 60px; /* تقليل العرض */
    text-align: center;
    font-size: 0.9rem;
    font-weight: 600;
    border: none;
    background: transparent;
    padding: 0.4rem;
}

/* تحينات للأجهزة الممولة */
@media (max-width: 768px) {
    .product-controls {
        grid-template-columns: 1fr;
        gap: 0.6rem;
    }
    
    .price-input-container {
        order: 2;
    }
    
    .quantity-control {
        order: 1;
        justify-self: center;
    }
    
    .qty-btn {
        width: 36px;
        height: 36px;
        font-size: 1.2rem;
    }
    
    .qty-input {
        width: 70px;
        font-size: 1rem;
    }
}/* أناط المنتجات القالة للطي - نسخة محدثة */
.product-item {
    background: var(--card-bg);
    border: 1px solid var(--border-color); /* تصغير حجم الحدود */
    border-radius: 12px; /* تصغير قليلاً */
    padding: 0.6rem 0.8rem; /* تقليل المساحة الداخلية */
    margin-bottom: 0.5rem; /* تقليل المساة بين البلوكات */
    transition: all 0.3s ease;
    cursor: pointer;
}

.product-item:hover {
    border-color: var(--primary-light);
    box-shadow: 0 2px 6px rgba(46, 125, 50, 0.15);
    transform: translateY(-1px);
}

.product-item.collapsed .product-details {
    display: none;
    height: 0;
    overflow: hidden;
    opacity: 0;
    transform: translateY(-5px);
    transition: all 0.3s ease;
}

.product-item.expanded .product-details {
    display: block;
    height: auto;
    opacity: 1;
    transform: translateY(0);
    padding-top: 0.6rem;
    margin-top: 0.6rem;
    border-top: 1px solid var(--border-color);
}

.product-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
}

.product-name {
    font-size: 0.9rem; /* تصغير حجم الخط */
    font-weight: 600;
    color: var(--text-primary);
    display: flex;
    align-items: center;
    gap: 0.5rem;
    flex-grow: 1; /* السماح للاسم بأخذ المساحة المتبقية */
}

.product-toggle {
    color: var(--text-secondary);
    display: flex;
    align-items: center;
    margin-right: 0;
    flex-shrink: 0; /* من انكماش عنصر التبديل */
}

/* تصميم القاط العمودية الثاث */
.vertical-dots {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 2px;
    width: 18px;
    height: 18px;
}

.dot {
    width: 4px;
    height: 4px;
    background-color: var(--text-secondary);
    border-radius: 50%;
}

.product-badge {
    background: var(--primary-color);
    color: white;
    padding: 0.1rem 0.4rem; /* تقليل حجم ابادج */
    border-radius: 12px;
    font-size: 0.7rem;
    font-weight: 500;
}

.badge-أنام { background: var(--primary-color); }
.badge-أعلاف { background: #ff9800; }
.badge-علاجات { background: #e91e63; }

/* حالة التحدي */
.product-item.selected {
    border-color: var(--primary-color);
    background: rgba(46, 125, 50, 0.05);
}

/* تصغير حقول الإدخال داخل البلوك المطوي */
.product-controls {
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 0.8rem;
    align-items: center;
}

.price-input-container {
    position: relative;
}

.price-input {
    width: 100%;
    padding: 0.6rem 0.8rem; /* تقليل الارتاع */
    padding-left: 2.5rem;
    border: 1px solid var(--border-color);
    border-radius: 6px;
    font-size: 0.9rem;
    text-align: center;
    transition: all 0.3s ease;
}

.price-input:focus {
    outline: none;
    border-color: var(--primary-color);
    box-shadow: 0 0 0 2px rgba(46, 125, 50, 0.1);
}

.currency-symbol {
    position: absolute;
    left: 0.8rem;
    top: 50%;
    transform: translateY(-50%);
    color: var(--text-secondary);
    font-weight: 500;
    font-size: 0.9rem;
}

.quantity-control {
    display: flex;
    align-items: center;
    background: var(--background-color);
    border-radius: 6px;
    overflow: hidden;
    border: 1px solid var(--border-color);
}

.qty-btn {
    background: var(--primary-color);
    color: white;
    border: none;
    width: 32px; /* تصغير حجم الأزرار */
    height: 32px;
    font-size: 1rem;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.3s ease;
    display: flex;
    align-items: center;
    justify-content: center;
}

.qty-btn:hover {
    background: var(--primary-dark);
}

.qty-input {
    width: 60px; /* تقليل العرض */
    text-align: center;
    font-size: 0.9rem;
    font-weight: 600;
    border: none;
    background: transparent;
    padding: 0.4rem;
}

/* تحسينات للجهزة المحمولة */
@media (max-width: 768px) {
    .product-controls {
        grid-template-columns: 1fr;
        gap: 0.6rem;
    }
    
    .price-input-container {
        order: 2;
    }
    
    .quantity-control {
        order: 1;
        justify-self: center;
    }
    
    .qty-btn {
        width: 36px;
        height: 36px;
        font-size: 1.2rem;
    }
    
    .qty-input {
        width: 70px;
        font-size: 1rem;
    }
    /* تصميم النقاط العمودية الثلاث */
.vertical-dots {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 2px;
    width: 16px;
    height: 16px;
    margin-right: 5px; /* إضافة مسافة لى اليمين */
}

.dot {
    width: 3px;
    height: 3px;
    background-color: #999;
    border-radius: 50%;
}

/* تعيلات إضافية لتصغر البلوك أكثر */
.product-item {
    background: var(--card-bg);
    border: 1px solid var(--border-color);
    border-radius: 8px; /* تصغير الحواف أكثر */
    padding: 0.5rem 0.7rem; /* تقليل الحشو أكثر */
    margin-bottom: 0.4rem; /* تقليل المسافة بين البلكات أكثر */
    transition: all 0.2s ease;
    cursor: pointer;
}

.product-badge {
    background: var(--primary-color);
    color: white;
    padding: 0.1rem 0.35rem; /* تقليل جم البادج */
    border-radius: 10px;
    font-size: 0.65rem;
    font-weight: 500;
}

/* تعديل لمحاذاة متوى الهيدر بشكل أفضل */
.product-name {
    font-size: 0.85rem; /* تصغير حجم الخط أكثر */
    font-weight: 600;
    color: var(--text-primary);
    display: flex;
    align-items: center;
    gap: 0.4rem;
}

/* تعديل خاص للهواتف ذات اشاشات الصغيرة */
@media (max-width: 480px) {
    .product-header {
        flex-direction: row !important; /* فر توجيه أفقي */
        align-items: center !important;
        gap: 0.3rem;
    }
    
    .product-name {
        font-size: 0.8rem;
    }
    
    .product-badge {
        font-size: 0.6rem;
        padding: 0.05rem 0.3rem;
    }
}
}
/* تحسنات للأجهزة المحولة */
@media (max-width: 768px) {
    .product-controls {
        grid-template-columns: 1fr;
        gap: 0.8rem;
    }
    
    .price-input-container {
        order: 2;
    }
    
    .quantity-control {
        order: 1;
        justify-self: center;
    }
    
    .qty-btn {
        width: 45px;
        height: 45px;
        font-size: 1.4rem;
    }
    
    .qty-input {
        width: 90px;
        font-size: 1.2rem;
    }
}

        /* Summary Card */
        .summary-card {
            background: linear-gradient(135deg, var(--primary-color) 0%, var(--primary-light) 100%);
            color: white;
            text-align: center;
            position: sticky;
            top: 1rem;
        }

        .total-amount {
            font-size: 2.5rem;
            font-weight: 700;
            margin: 1rem 0;
        }

        .total-label {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        /* Form Elements */
        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--text-primary);
        }

        .form-input, .form-select {
            width: 100%;
            padding: 0.8rem 1rem;
            border: 2px solid var(--border-color);
            border-radius: var(--radius-sm);
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        .form-input:focus, .form-select:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(46, 125, 50, 0.1);
        }

        /* Payment Method */
        .payment-methods {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            gap: 1rem;
            margin: 1rem 0;
        }

        .payment-option {
            position: relative;
        }

        .payment-radio {
            display: none;
        }

        .payment-label {
            display: block;
            padding: 1rem;
            border: 2px solid var(--border-color);
            border-radius: var(--radius-sm);
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 500;
        }

        .payment-label:hover {
            border-color: var(--primary-light);
            background: rgba(46, 125, 50, 0.05);
        }

        .payment-radio:checked + .payment-label {
            border-color: var(--primary-color);
            background: var(--primary-color);
            color: white;
            transform: scale(1.02);
        }

        /* Buttons */
        .btn {
            padding: 0.8rem 1.5rem;
            border: none;
            border-radius: var(--radius-sm);
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .btn-primary {
            background: var(--primary-color);
            color: white;
        }

        .btn-primary:hover {
            background: var(--primary-dark);
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(46, 125, 50, 0.3);
        }

        .btn-secondary {
            background: var(--secondary-color);
            color: #000;
        }

        .btn-secondary:hover {
            background: #ffcd38;
            transform: translateY(-2px);
        }

        .btn-danger {
            background: #dc3545;
            color: white;
        }

        .btn-danger:hover {
            background: #c82333;
            transform: translateY(-2px);
        }

        .btn-large {
            padding: 1.2rem 2rem;
            font-size: 1.2rem;
            width: 100%;
            margin-top: 1rem;
        }

        .btn-small {
            padding: 0.5rem 1rem;
            font-size: 0.9rem;
        }

        .btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            transform: none !important;
        }

        /* Alert Messages */
        .alert {
            padding: 1rem;
            border-radius: var(--radius-sm);
            margin-bottom: 1rem;
            border-left: 4px solid;
            animation: slideIn 0.3s ease;
        }

        .alert-success {
            background: #d4edda;
            color: #155724;
            border-left-color: #28a745;
        }

        .alert-warning {
            background: #fff3cd;
            color: #856404;
            border-left-color: #ffc107;
        }

        .alert-error {
            background: #f8d7da;
            color: #721c24;
            border-left-color: #dc3545;
        }

        @keyframes slideIn {
            from { opacity: 0; transform: translateX(100%); }
            to { opacity: 1; transform: translateX(0); }
        }

        /* Items Management */
        .items-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1rem;
            margin-top: 1rem;
        }

        .item-card {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: var(--radius-sm);
            padding: 1rem;
            transition: all 0.3s ease;
        }

        .item-card:hover {
            box-shadow: var(--shadow);
            transform: translateY(-2px);
        }

        .item-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 0.5rem;
        }

        .item-name {
            font-weight: 600;
            font-size: 1.1rem;
        }

        .category-grid {
            margin-bottom: 2rem;
        }

        .category-title {
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 1rem;
            color: var(--primary-color);
            border-bottom: 2px solid var(--primary-color);
            padding-bottom: 0.5rem;
        }

        /* Expense Types */
        .expense-types {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
            margin-bottom: 1.5rem;
        }

        .expense-type {
            background: var(--card-bg);
            border: 2px solid var(--border-color);
            border-radius: var(--radius-sm);
            padding: 1rem;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .expense-type:hover {
            border-color: var(--primary-light);
            transform: translateY(-2px);
        }

        .expense-type.selected {
            border-color: var(--primary-color);
            background: rgba(46, 125, 50, 0.1);
        }

        .expense-icon {
            font-size: 2rem;
            margin-bottom: 0.5rem;
        }

        /* أنماط ذيل الصفح المحدثة */
.footer {
    background: var(--primary-dark);
    color: white;
    text-align: center;
    padding: 1.5rem;
    margin-top: 2rem;
}

.footer-content {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    flex-wrap: wrap;
}

.footer-logo-img {
    width: 45px;
    height: 45px;
    object-fit: cover;
    border-radius: 50%;
    background: rgba(255,255,255,0.2);
    box-shadow: 0 1px 3px rgba(0,0,0,0.1);
}

@media (max-width: 768px) {
    .footer-logo-img {
        width: 30px;
        height: 30px;
    }
}

        /* Responsive Design */
        @media (max-width: 768px) {
            body {
                font-size: 14px;
            }

            .header {
                padding: 0.8rem 1rem;
            }

            .header h1 {
                font-size: 1.1rem;
            }

            .header-icon {
                width: 40px;
                height: 40px;
                font-size: 1.2rem;
            }

            .main-container {
                padding: 0.8rem;
            }

            /* Sales section mobile layout */
            #sales-section > div {
                grid-template-columns: 1fr !important;
                gap: 1rem;
            }

            /* Products mobile layout */
            .product-controls {
                grid-template-columns: 1fr;
                gap: 0.8rem;
            }

            .price-input-container {
                order: 2;
            }

            .quantity-control {
                order: 1;
                justify-self: center;
            }

            .qty-btn {
                width: 50px;
                height: 50px;
                font-size: 1.5rem;
            }

            .qty-input {
                width: 100px;
                font-size: 1.3rem;
            }

            /* Summary card mobile */
            .summary-card {
                position: static;
                margin-bottom: 1rem;
            }

            .total-amount {
                font-size: 2rem;
            }

            /* Navigation mobile */
            .nav-tabs {
                display: flex;
                overflow-x: auto;
                -webkit-overflow-scrolling: touch;
                scrollbar-width: none;
                -ms-overflow-style: none;
                padding: 0 0.5rem;
            }

            .nav-tabs::-webkit-scrollbar {
                display: none;
            }

            .nav-tab {
                padding: 1rem 0.8rem;
                font-size: 0.75rem;
                min-width: 120px;
                flex-shrink: 0;
                white-space: nowrap;
                text-align: center;
                line-height: 1.2;
            }

            /* Cards mobile */
            .card {
                margin-bottom: 1rem;
                padding: 1rem;
            }

            .card-title {
                font-size: 1.1rem;
            }

            /* Form elements mobile */
            .form-input, .form-select {
                padding: 1rem 0.8rem;
                font-size: 1rem;
            }

            /* Payment methods mobile */
            .payment-methods {
                grid-template-columns: 1fr;
                gap: 0.8rem;
            }

            .payment-label {
                padding: 1.2rem;
                font-size: 1.1rem;
            }

            /* Buttons mobile */
            .btn {
                padding: 1rem 1.5rem;
                font-size: 1.1rem;
            }

            .btn-large {
                padding: 1.5rem 2rem;
                font-size: 1.3rem;
            }

            /* Expense section mobile */
            .expense-types {
                grid-template-columns: repeat(2, 1fr);
                gap: 0.8rem;
            }

            .expense-type {
                padding: 1.2rem 0.8rem;
            }

            .expense-icon {
                font-size: 2.5rem;
            }

            /* إضافة هذه الأنماط للتميم المستجيب */

/* إصلاح ظهور بلوك اإجمالي في كل التبويبات للجوال */
@media (max-width: 768px) {
    /* إعادة ترتيب بلوكات الإدخال والإجمالي في نمط الجوال */
    .expense-form > div {
        grid-template-columns: 1fr !important;
        gap: 1rem;
    }
    
    /* جعل بلوك اإجمالي يظهر في الأسفل دائماً */
    .expense-form > div > div:nth-child(2) {
        order: 2;
    }
    
    /* جعل بلوك الإدخال يظهر في الأعى */
    .expense-form > div > div:nth-child(1) {
        order: 1;
    }
    
    /* تأكيد لبطاقة الملخص */
    .summary-card {
        position: static;
        margin-bottom: 1rem;
        width: 100%;
    }
    
    /* تحسينات إضافية للعرض */
    .expense-types {
        grid-template-columns: repeat(2, 1fr);
        gap: 0.8rem;
    }
    
    .expense-type {
        padding: 1rem 0.8rem;
    }
    
    /* حجم الخط والمساحات للجوال */
    .form-input, .form-select {
        padding: 0.8rem;
        font-size: 1rem;
    }
    
    .form-label {
        font-size: 0.95rem;
    }
    
    /* تحسين زرار التسجيل */
    .btn-large {
        padding: 1.2rem;
        font-size: 1.1rem;
    }
}

/* للهواتف الأصغر */
@media (max-width: 480px) {
    .expense-types {
        grid-template-columns: repeat(2, 1fr);
    }
    
    .expense-icon {
        font-size: 1.5rem;
    }
    
    .total-amount {
        font-size: 1.8rem;
    }
}

        /* Extra small devices */
        @media (max-width: 480px) {
            .header-content {
                flex-direction: column;
                gap: 0.8rem;
                text-align: center;
            }

            /* Navigation for very small screens */
            .nav-tab {
                padding: 0.8rem 0.6rem;
                font-size: 0.7rem;
                min-width: 100px;
                line-height: 1.1;
            }

            .product-item, .expense-item {
                padding: 1rem;
            }

            .product-header {
                flex-direction: column;
                align-items: flex-start;
                gap: 0.5rem;
            }

            .expense-types {
                grid-template-columns: 1fr;
            }

            .total-amount {
                font-size: 1.8rem;
            }

            .currency-symbol {
                position: static;
                display: block;
                text-align: center;
                margin-top: 0.5rem;
            }

            .price-input {
                padding: 1rem;
                padding-left: 1rem;
            }
        }

        /* Touch-friendly improvements */
        @media (hover: none) and (pointer: coarse) {
            .btn, .qty-btn, .payment-label, .expense-type, .nav-tab {
                min-height: 44px;
            }

            .product-item, .expense-item, .item-card {
                cursor: default;
            }

            .product-item:hover, .expense-item:hover, .item-card:hover {
                transform: none;
            }

            .btn:hover, .qty-btn:hover {
                transform: none;
            }
        }

        /* Loading States */
        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid rgba(255,255,255,.3);
            border-radius: 50%;
            border-top-color: #fff;
            animation: spin 1s ease-in-out infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* Invoice print styles */
        @media print {
            body * {
                visibility: hidden;
            }

            #invoice-print, #invoice-print * {
                visibility: visible;
            }

            #invoice-print {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
            }

            .no-print {
                display: none !important;
            }
        }

        /* Invoice modal */
        .invoice-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 10000;
        }

        .invoice-content {
            background: white;
            border-radius: var(--radius);
            max-width: 600px;
            width: 90%;
            max-height: 90%;
            overflow-y: auto;
            position: relative;
        }

        .invoice-header {
            background: var(--primary-color);
            color: white;
            padding: 1.5rem;
            border-radius: var(--radius) var(--radius) 0 0;
            text-align: center;
        }

        .invoice-body {
            padding: 2rem;
        }

        .invoice-close {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background: rgba(255,255,255,0.2);
            border: none;
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            font-size: 1.5rem;
            cursor: pointer;
        }

        .invoice-print-area {
            background: white;
            color: black;
            font-family: 'Times New Roman', serif;
            line-height: 1.6;
        }

        .invoice-title {
            text-align: center;
            font-size: 2rem;
            margin-bottom: 2rem;
            color: var(--primary-color);
            border-bottom: 3px solid var(--primary-color);
            padding-bottom: 1rem;
        }

        .invoice-info {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .invoice-company {
            text-align: left;
        }

        .invoice-customer {
            text-align: right;
            border-right: 3px solid var(--primary-color);
            padding-right: 1rem;
        }

        .invoice-table {
            width: 100%;
            border-collapse: collapse;
            margin: 2rem 0;
        }

        .invoice-table th,
        .invoice-table td {
            border: 1px solid #ddd;
            padding: 12px;
            text-align: center;
        }

        .invoice-table th {
            background-color: var(--primary-color);
            color: white;
            font-weight: bold;
        }

        .invoice-table tr:nth-child(even) {
            background-color: #f9f9f9;
        }

        .invoice-total {
            text-align: left;
            font-size: 1.5rem;
            font-weight: bold;
            margin-top: 2rem;
            padding-top: 1rem;
            border-top: 3px solid var(--primary-color);
        }

        .invoice-footer {
            text-align: center;
            margin-top: 3rem;
            padding-top: 2rem;
            border-top: 1px solid #ddd;
            color: var(--text-secondary);
        }

        .invoice-actions {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 1rem;
            margin-top: 2rem;
            padding: 0 2rem 2rem;
        }
        .hide {
            display: none;
        }
    </style>
</head>
<body>
    <!-- تعليمات لتنفي أيقونة الإحصائيت القابلة للنقر -->

<header class="header">
<div class="header-content" style="
  display: flex;
  flex-direction: row; /* توزيع أفقي */
  align-items: center; /* محذاة رأسيًا في نفس السطر */
  justify-content: space-between; /* توزيع رضي */
  gap: 1rem;
  flex-wrap: nowrap; /* لا تنزل تحت أي ظرف */
">
    <!-- شعار الخروف - أقصى اليمين -->
    <div class="header-icon" style="width: 44px; height: 44px; flex-shrink: 0;">
      <img src="sheep_icon" alt="شعار" style="width: 100%; height: 100%; object-fit: cover;">
    </div>

    <!-- العنوان في الوسط -->
    <div style="flex-grow: 1; text-align: center;">
      <h1 style="font-size: 16px; font-weight: 600; margin: 0;">
        جَـــــبـْـــــر Algebra<h2></h2>  تطبيق لإدارة تربية الأغنام
      </h1>
    </div>

    <!-- أيقونة الإحصائيا - أقصى اليسار -->
    <div class="dashboard-icon-inner" onclick="switchTab('dashboard')">
      <svg xmlns="http://www.w3.org/2000/svg" 
           width="22" height="22" 
           viewBox="0 0 24 24" 
           fill="none" 
           stroke="currentColor" 
           stroke-width="2" 
           stroke-linecap="round" 
           stroke-linejoin="round">
        <line x1="4" y1="21" x2="4" y2="10"></line>
        <line x1="12" y1="21" x2="12" y2="4"></line>
        <line x1="20" y1="21" x2="20" y2="14"></line>
      </svg>
      <span class="notification">إحصائيات</span>
    </div>

  </div>
</header>



<style>
/* أنماط أيقونة SVG للداشبورد */
.dashboard-svg {
    color: white;
    width: 22px;
    height: 22px;
}

.dashboard-icon:hover .dashboard-svg {
    transform: scale(1.1);
}
</style>

    <nav class="nav-container">
        <div class="nav-tabs">
            <button class="nav-tab active" onclick="switchTab('sales')">
                💰 تسجيل الميعات
            </button>
            <button class="nav-tab" onclick="switchTab('expenses')">
                📝 المصروفات والمشتريا
            </button>
            <button class="nav-tab" onclick="switchTab('items')">
                ➕ إدارة الأناف
            </button>
            <button class="nav-tab" onclick="switchTab('dashboard')">
                📊 لوح البيانات
            </button>
        </div>
    </nav>

    <div class="main-container">
        <div id="sales-section" class="content-section active">
            <div style="display: grid; grid-template-columns: 1fr 300px; gap: 1.5rem;">
                <div>
                    </div>
            <button class="btn btn-secondary" onclick="resetCurrentForm()">
                🔄 تسجيل جديد
            </button>
        </div>
        
                    <div class="card">
                        <div class="card-header">
                            <h2 class="card-title">اتر المنتجات</h2>
                            <span id="selected-count" class="product-badge">0 منتج</span>
                        </div>

                        <div id="products-container"></div>
                    </div>

                    <div class="card">
                        <div class="form-group">
                            <label class="form-label">ملاحظات (اختيارية)</label>
                            <textarea id="sales-note" class="form-input"
                                      rows="3"
                                      placeholder="أضف أي ملاحظات أو تفاصي إضافية..."
                                      style="resize: vertical;"></textarea>
                        </div>
                    </div>

                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">طريقة الدفع</h3>
                        </div>
                        <div class="payment-methods">
                            <div class="payment-option">
                                <input type="radio" id="payment-cash" name="sales-payment" value="نقد" class="payment-radio" checked>
                                <label for="payment-cash" class="payment-label">
                                    💵 نقد
                                </label>
                            </div>
                            <div class="payment-option">
                                <input type="radio" id="payment-card" name="sales-payment" value="شبكة" class="payment-radio">
                                <label for="payment-card" class="payment-label">
                                    💳 شبة
                                </label>
                            </div>
                            <div class="payment-option">
                                <input type="radio" id="payment-transfer" name="sales-payment" value="حوالة" class="payment-radio">
                                <label for="payment-transfer" class="payment-label">
                                    🏦 حوالة
                                </label>
                            </div>
                        </div>
                    </div>

                    <div class="card" id="invoice-card-collapsible">

                <div>
                    <div class="card summary-card">
                        <h3 class="total-label">إجمالي المبلغ</h3>
                        <div class="total-amount" id="total-amount">0</div>
                        <div style="opacity: 0.9;">ريال سعودي</div>

                        <button class="btn btn-primary btn-large" onclick="confirmSales()" id="sales-submit-btn">
                            ✅ تأكيد البيع
                        </button>
                    </div>

                    <div class="card">
                        <h4 class="card-title">ملخص العملية</h4>
                        <div style="display: grid; gap: 0.8rem; margin-top: 1rem;">
                            <div style="display: flex; justify-content: space-between;">
                                <span>عدد الرؤوس:</span>
                                <strong id="total-heads">0</strong>
                            </div>
                            <div style="display: flex; justify-content: space-between;">
                                <span>متوسط السعر:</span>
                                <strong id="avg-price">0 ر.س</strong>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div id="sales-alert-container"></div>
                                    <div class="card-header" onclick="toggleInvoiceSectionCollapsible()" style="cursor: pointer; border-bottom: none; margin-bottom: 0;">
                            <h3 class="card-title">💬 إرسال الفاتورة للعميل</h3>
                            <span id="invoice-arrow-collapsible" style="font-size: 1.5rem;">⬇️</span>
                        </div>
                        <div id="invoice-content-collapsible" style="display: none; padding-top: 1.5rem; border-top: 1px solid var(--border-color); margin-top:1.5rem;">
                            <div class="form-group">
                                <label class="form-label">رقم جوال العميل</label>
                                <input type="tel" id="customer-phone" class="form-input"
                                       placeholder="05XXXXXXXX أو 966XXXXXXXXX"
                                       maxlength="15"
                                       oninput="formatPhoneNumber(this)">
                                <small style="color: var(--text-secondary); font-size: 0.85rem;">
                                    أدخل رقم الجوال مع أو بدون رمز الدولة
                                </small>
                            </div>

                            <div class="form-group">
                                <label class="form-label">اسم العمل (اختياري)</label>
                                <input type="text" id="customer-name" class="form-input"
                                       placeholder="اسم العميل">
                            </div>

                            <button class="btn btn-secondary btn-large"
                                    onclick="sendInvoiceWhatsApp()"
                                    id="whatsapp-btn"
                                    disabled>
                                📱 إرسل رسالة على الواتساب
                            </button>

                            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem;">
                                <button class="btn btn-primary"
                                        onclick="showInvoicePDF()"
                                        id="pdf-btn"
                                        disabled>
                                    📄 عرض الفاتورة
                                </button>

                                <button class="btn btn-primary"
                                        onclick="downloadInvoicePDF()"
                                        id="download-btn"
                                        disabled>
                                    💾 تحميل PDF
                                </button>
                            </div>
                        </div>
                    </div>
                </div>

        </div>

        <!-- Expenses Section Code -->
<!-- Expenses Section Code -->
<div id="expenses-section" class="content-section">
    <div class="card">
        <div class="card-header">
            <h2 class="card-title">تسجيل المصرفات والمشتريات</h2>
            <button class="btn btn-secondary" onclick="resetExpenseForm()">
                 تسجيل جديد
            </button>
        </div>

        <div class="expense-types">
            <div class="expense-type" onclick="selectExpenseType('مشتريات', this)">
                <div class="expense-icon">🛒</div>
                <div>مشتريات</div>
            </div>
            <div class="expense-type" onclick="selectExpenseType('مصاريف', this)">
                <div class="expense-icon">💳</div>
                <div>مصاريف</div>
            </div>
            <div class="expense-type" onclick="selectExpenseType('رواب', this)">
                <div class="expense-icon">👥</div>
                <div>رواتب</div>
            </div>
            <div class="expense-type" onclick="selectExpenseType('صيانة', this)">
                <div class="expense-icon"></div>
                <div>صانة</div>
            </div>
        </div>

        <!-- Expense Forms -->
        <!-- 1. مشتريات (Purchases) Form -->
        <div id="expense-form-مشتريات" class="expense-form hide">
            <div style="display: grid; grid-template-columns: 1fr 300px; gap: 1.5rem;">
                <div>
                    <div class="form-group">
                        <label class="form-label">الصنف</label>
                        <select id="expense-sheep-item" class="form-select">
                            <option value="">اختر صنف الأغام</option>
                            <!-- Will be populated with sheep items -->
                        </select>
                    </div>

                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
                        <div class="form-group">
                            <label class="form-label">الكمية</label>
                            <input type="number" id="expense-sheep-quantity" class="form-input"
                                   placeholder="عد الرؤوس" min="0" step="1">
                        </div>

                        <div class="form-group">
                            <label class="form-label">السعر</label>
                            <input type="number" id="expense-sheep-price" class="form-input"
                                   placeholder="سعر الرأس اواحد" min="0" step="0.01" oninput="calculateSheepTotal()">
                        </div>
                    </div>

                    <div class="form-group">
                        <label class="form-label">الوصف / الملاحظات</label>
                        <textarea id="expense-sheep-description" class="form-input"
                                  rows="3"
                                  placeholder="وصف المشريات أو ملاحظات إضافية..."></textarea>
                    </div>

                    <div class="form-group">
                        <label class="form-label">طريقة الدفع</label>
                        <div class="payment-methods">
                            <div class="payment-option">
                                <input type="radio" id="expense-sheep-payment-cash" name="expense-sheep-payment" value="نق" class="payment-radio" checked>
                                <label for="expense-sheep-payment-cash" class="payment-label">
                                    💵 نقد
                                </label>
                            </div>
                            <div class="payment-option">
                                <input type="radio" id="expense-sheep-payment-transfer" name="expense-sheep-payment" value="حوالة" class="payment-radio">
                                <label for="expense-sheep-payment-transfer" class="payment-label">
                                    🏦 حوالة
                                </label>
                            </div>
                        </div>
                    </div>
                </div>

                <div>
                    <div class="card summary-card">
                        <h3 class="total-label">إجمالي المشتريت</h3>
                        <div class="total-amount" id="expense-sheep-total">0</div>
                        <div style="opacity: 0.9;">ريال سعودي</div>

                        <button class="btn btn-primary btn-large" onclick="confirmSheepExpense()" id="expense-sheep-submit-btn">
                            ✅ تسجيل المشتريات
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- 2. مصاريف (General Expenses) Form -->
        <div id="expense-form-مصارف" class="expense-form hide">
            <div style="display: grid; grid-template-columns: 1fr 300px; gap: 1.5rem;">
                <div>
                    <div class="form-group">
                        <label class="form-label">التصنيف</label>
                        <select id="expense-general-category" class="form-select" onchange="updateGeneralExpenseItems()">
                            <option value="">اختر التصنيف</option>
                            <option value="أعلا">أعلاف</option>
                            <option value="علاجات">علاجات</option>
                            <option value="نقل">نقل</option>
                            <option value="أخرى">أخرى</option>
                        </select>
                    </div>

                    <div class="form-group">
                        <label class="form-label">الصنف</label>
                        <select id="expense-general-item" class="form-select">
                            <option value="">اختر الصنف</option>
                        </select>
                    </div>

                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
                        <div class="form-group">
                            <label class="form-label">الكمية</label>
                            <input type="number" id="expense-general-quantity" class="form-input"
                                   placeholder="الكمية" min="0" step="0.01">
                        </div>

                        <div class="form-group">
                            <label class="form-label">السعر</label>
                            <input type="number" id="expense-general-price" class="form-input"
                                   placeholder="السعر" min="0" step="0.01" oninput="calculateGeneralExpenseTotal()">
                        </div>
                    </div>

                    <div class="form-group">
                        <label class="form-label">الوصف / الملاحظات</label>
                        <textarea id="expense-general-description" class="form-input"
                                  rows="3"
                                  placeholder="وصف المصروف و ملاحظات إضافية..."></textarea>
                    </div>

                    <div class="form-group">
                        <label class="form-label">طريقة الدفع</label>
                        <div class="payment-methods">
                            <div class="payment-option">
                                <input type="radio" id="expense-general-payment-cash" name="expense-general-payment" value="نقد" class="payment-radio" checked>
                                <label for="expense-general-payment-cash" class="payment-label">
                                    💵 نقد
                                </label>
                            </div>
                            <div class="payment-option">
                                <input type="radio" id="expense-general-payment-transfer" name="expense-general-payment" value="حوالة" class="payment-radio">
                                <label for="expense-general-payment-transfer" class="payment-label">
                                     حوالة
                                </label>
                            </div>
                        </div>
                    </div>
                </div>

                <div>
                    <div class="card summary-card">
                        <h3 class="total-label">إجمالي المصروف</h3>
                        <div class="total-amount" id="expense-general-total">0</div>
                        <div style="opacity: 0.9;">ريال سعود</div>

                        <button class="btn btn-primary btn-large" onclick="confirmGeneralExpense()" id="expense-general-submit-btn">
                            ✅ تسجيل المروف
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- 3. رواتب (Salaries) Form -->
        <div id="expense-form-رواتب" class="expense-form hide">
            <div style="display: grid; grid-template-columns: 1fr 300px; gap: 1.5rem;">
                <div>
                    <div class="form-group">
                        <label class="form-label">المبلغ الإجمالي</label>
                        <input type="number" id="expense-salary-amount" class="form-input"
                               placeholder="إجمالي المبلغ" min="0" step="0.01" oninput="updateSalaryTotal()">
                    </div>

                    <div class="form-group">
                        <label class="form-label">الوصف / الملاحظات</label>
                        <textarea id="expense-salary-description" class="form-input"
                                  rows="3"
                                  placeholder="تفاصيل الراتب أو ملاحظات إضفية..."></textarea>
                    </div>

                    <div class="form-group">
                        <label class="form-label">طريقة الدفع</label>
                        <div class="payment-methods">
                            <div class="payment-option">
                                <input type="radio" id="expense-salary-payment-cash" name="expense-salary-payment" value="نقد" class="payment-radio" checked>
                                <label for="expense-salary-payment-cash" class="payment-label">
                                    💵 نقد
                                </label>
                            </div>
                            <div class="payment-option">
                                <input type="radio" id="expense-salary-payment-transfer" name="expense-salary-payment" value="حوالة" class="payment-radio">
                                <label for="expense-salary-payment-transfer" class="payment-label">
                                     حوالة
                                </label>
                            </div>
                        </div>
                    </div>
                </div>

                <div>
                    <div class="card summary-card">
                        <h3 class="total-label">إجمالي الراتب</h3>
                        <div class="total-amount" id="expense-salary-total">0</div>
                        <div style="opacity: 0.9;">ريال سعودي</div>

                        <button class="btn btn-primary btn-large" onclick="confirmSalaryExpense()" id="expense-salary-submit-btn">
                            ✅ تسجيل الراتب
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- 4. صيانة (Maintenance) Form -->
        <div id="expense-form-صيانة" class="expense-form hide">
            <div style="display: grid; grid-template-columns: 1fr 300px; gap: 1.5rem;">
                <div>
                    <div class="form-group">
                        <label class="form-label">المبلغ الإجمالي</label>
                        <input type="number" id="expense-maintenance-amount" class="form-input"
                               placeholder="إجمالي امبلغ" min="0" step="0.01" oninput="updateMaintenanceTotal()">
                    </div>

                    <div class="form-group">
                        <label class="form-label">الوصف / الملاحظات</label>
                        <textarea id="expense-maintenance-description" class="form-input"
                                  rows="3"
                                  placeholder="وصف أعمال الصيانة أو ملاحظات إضافية..."></textarea>
                    </div>

                    <div class="form-group">
                        <label class="form-label">طريقة الدفع</label>
                        <div class="payment-methods">
                            <div class="payment-option">
                                <input type="radio" id="expense-maintenance-payment-cash" name="expense-maintenance-payment" value="نقد" class="payment-radio" checked>
                                <label for="expense-maintenance-payment-cash" class="payment-label">
                                    💵 نقد
                                </label>
                            </div>
                            <div class="payment-option">
                                <input type="radio" id="expense-maintenance-payment-transfer" name="expense-maintenance-payment" value="حوالة" class="payment-radio">
                                <label for="expense-maintenance-payment-transfer" class="payment-label">
                                    🏦 حوالة
                                </label>
                            </div>
                        </div>
                    </div>
                </div>

                <div>
                    <div class="card summary-card">
                        <h3 class="total-label">إجملي الصيانة</h3>
                        <div class="total-amount" id="expense-maintenance-total">0</div>
                        <div style="opacity: 0.9;">ريال سعودي</div>

                        <button class="btn btn-primary btn-large" onclick="confirmMaintenanceExpense()" id="expense-maintenance-submit-btn">
                            ✅ تسجيل الصانة
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div id="expenses-alert-container"></div>
</div>

        <div id="items-section" class="content-section">
            <div class="card">
                <div class="card-header">
                    <h2 class="card-title">إدارة الأصناف</h2>
                    <button class="btn btn-primary" onclick="showAddItemModal()">
                        ➕ إضافة صنف جديد
                    </button>
                </div>

                <div id="add-item-form" class="hide">
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-bottom: 1rem;">
                        <div class="form-group">
                            <label class="form-label">اسم الصنف</label>
                            <input type="text" id="new-item-name" class="form-input"
                                   placeholder="مثال: نعجة حرية، شعير صفر، مضاد حيوي...">
                        </div>
                        <div class="form-group">
                            <label class="form-label">التصنيف</label>
                            <select id="new-item-category" class="form-select">
                                <option value="">ختر التصنيف</option>
                                <option value="أغنام">أغام</option>
                                <option value="أعلاف">أعلاف</option>
                                <option value="علاجات">علجات</option>
                            </select>
                        </div>
                    </div>
                    <div style="display: flex; gap: 1rem;">
                        <button class="btn btn-primary" onclick="addNewItem()">إضافة</button>
                        <button class="btn btn-secondary" onclick="hideAddItemModal()">إلغاء</button>
                    </div>
                </div>

                <div id="items-display">
                    <div class="category-grid">
                        <h3 class="category-title">🐑 غنام</h3>
                        <div class="items-grid" id="items-أغنام"></div>
                    </div>

                    <div class="category-grid">
                        <h3 class="category-title">🌾 أعلاف</h3>
                        <div class="items-grid" id="items-أعلاف"></div>
                    </div>

                    <div class="category-grid">
                        <h3 class="category-title">💊 علاجات</h3>
                        <div class="items-grid" id="items-علاجات"></div>
                    </div>
                </div>
            </div>

            <div id="items-alert-container"></div>
        </div>

        <div id="dashboard-section" class="content-section">
            <style>
  /* إصلاح مشكلة امتدد العناصر خارج الشاشة */
  .dashboard-table {
    width: 100%;
    max-width: 100%;
    overflow-x: auto;
  }
  
  .table-responsive {
    width: 100%;
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
  }
  
  /* إصلاح شكلة هامش الصفحة */
  body {
    overflow-x: hidden; /* منع التمرير اأفقي للصفحة بأكمها */
  }
  
  .dashboard-container, .main-container {
    max-width: 100%;
    padding-left: 0.5rem;
    padding-right: 0.5rem;
    box-sizing: border-box;
  }
  
  /* تعديل عرض عناصر الداشبورد للجوال */
  @media (max-width: 768px) {
    .metrics-strip, .stats-grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 0.75rem;
      margin-bottom: 1rem;
    }
    
    .card {
      padding: 0.75rem;
      margin-bottom: 0.75rem;
    }
    
    .card-header {
      flex-direction: column;
      align-items: flex-start;
      gap: 0.5rem;
    }
    
    /* نسيق الجدول للجول */
    .dashboard-table th,
    .dashboard-table td {
      padding: 0.5rem;
      font-size: 0.85rem;
    }
    
    /* إفاء بعض الأعمدة غير الضرورية في الوال */
    .dashboard-table th:nth-child(7),
    .dashboard-table td:nth-child(7) {
      display: none;
    }
  }
</style>
            <!-- محتوى لوضعه داخل قسم dashboard-section في التطبيق ارئيسي -->

<h1 class="dashboard-title">لوحة البيانات والتحليلات</h1>

<!-- قسم الفلترة -->
<div class="card">
    <div class="card-header">
        <h2 class="card-title">تصفية البيانات</h2>
    </div>
    <div class="filter-section" style="padding: 1rem; display: flex; flex-wrap: wrap; gap: 1rem; align-items: center;">
        <div class="filter-group" style="display: flex; align-items: center; gap: 0.5rem;">
            <label class="filter-label" style="font-weight: 600;">الفترة الزمنية:</label>
            <select id="date-filter" class="form-select">
                <option value="today">اليوم</option>
                <option value="week">آخر أسبوع</option>
                <option value="month" selected>آخ شهر</option>
                <option value="quarter">آخر 3 شهور</option>
                <option value="year">السنة</option>
                <option value="custom">فترة مخصصة</option>
            </select>
        </div>
        
        <div id="custom-date-fields" class="filter-group" style="display: none; align-items: center; gap: 0.5rem;">
            <label class="form-label">من:</label>
            <input type="date" id="date-from" class="form-input">
            <label class="form-label">إلى:</label>
            <input type="date" id="date-to" class="form-input">
        </div>

        <div class="filter-group" style="display: flex; align-items: center; gap: 0.5rem;">
            <label class="filter-label" style="font-weight: 600;">التصنيف:</label>
            <select id="category-filter" class="form-select">
                <option value="all" selected>الكل</option>
                <option value="أغنام">أغنام</option>
                <option value="أعلاف">أعلاف</option>
                <option value="علاجات">علاجات</option>
            </select>
        </div>

        <div class="spacer" style="margin-left: auto;"></div>

        <button id="refresh-dashboard-btn" class="btn btn-primary">
            <span>حديث البيانات</span> 🔄
        </button>
    </div>
</div>

<!-- شريط المؤشرات العلوي -->
<div class="metrics-strip" style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1rem; margin-bottom: 1.5rem;">
    <div class="card">
        <div style="padding: 1rem;">
            <div style="font-size: 0.85rem; color: var(--text-secondary); margin-bottom: 0.5rem;">إجمالي الميعات</div>
            <div id="total-sales" style="font-size: 1.5rem; font-weight: 700; color: var(--success-color);">35,250 ر.س</div>
        </div>
    </div>
    <div class="card">
        <div style="padding: 1rem;">
            <div style="font-size: 0.85rem; color: var(--text-secondary); margin-bottom: 0.5rem;">إجمالي المصروفات</div>
            <div id="total-expenses" style="font-size: 1.5rem; font-weight: 700; color: var(--danger-color);">18,720 ر.س</div>
        </div>
    </div>
    <div class="card">
        <div style="padding: 1rem;">
            <div style="font-size: 0.85rem; color: var(--text-secondary); margin-bottom: 0.5rem;">صافي الربح</div>
            <div id="net-profit" style="font-size: 1.5rem; font-weight: 700; color: var(--primary-color);">16,530 ر.س</div>
        </div>
    </div>
    <div class="card">
        <div style="padding: 1rem;">
            <div style="font-size: 0.85rem; color: var(--text-secondary); margin-bottom: 0.5rem;">متوسط سعر الرأس</div>
            <div id="avg-price" style="font-size: 1.5rem; font-weight: 700; color: var(--info-color);">1,250 ر.س</div>
        </div>
    </div>
</div>

<!-- إحصئيات سريعة -->
<div class="stats-grid" style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 1rem; margin-bottom: 1.5rem;">
    <div class="card" style="border-top: 5px solid var(--primary-color);">
        <div style="padding: 1rem; position: relative;">
            <div style="position: absolute; top: 1rem; left: 1rem; font-size: 2rem; opacity: 0.2;">🐑</div>
            <div style="font-size: 1rem; color: var(--text-secondary); margin-bottom: 0.5rem;">عدد الأغنام المباعة</div>
            <div id="total-sheep-sold" style="font-size: 1.8rem; font-weight: 700; margin-bottom: 0.5rem;">28</div>
            <div style="font-size: 0.85rem; color: var(--success-color);">+15% مقارنة بالشهر الماضي</div>
        </div>
    </div>

    <div class="card" style="border-top: 5px solid var(--success-color);">
        <div style="padding: 1rem; position: relative;">
            <div style="position: absolute; top: 1rem; left: 1rem; font-size: 2rem; opacity: 0.2;">💰</div>
            <div style="font-size: 1rem; color: var(--text-secondary); margin-bottom: 0.5rem;">الإيرادات اليومي</div>
            <div id="daily-revenue" style="font-size: 1.8rem; font-weight: 700; margin-bottom: 0.5rem;">3,500 ر.س</div>
            <div style="font-size: 0.85rem; color: var(--success-color);">+8% مقارنة بلأمس</div>
        </div>
    </div>

    <div class="card" style="border-top: 5px solid var(--warning-color);">
        <div style="padding: 1rem; position: relative;">
            <div style="position: absolute; top: 1rem; left: 1rem; font-size: 2rem; opacity: 0.2;">🛒</div>
            <div style="font-size: 1rem; color: var(--text-secondary); margin-bottom: 0.5rem;">عدد عمليات الشراء</div>
            <div id="purchase-count" style="font-size: 1.8rem; font-weight: 700; margin-bottom: 0.5rem;">12</div>
            <div style="font-size: 0.85rem; color: var(--danger-color);">-5% مقارنة بالشهر الماضي</div>
        </div>
    </div>

    <div class="card" style="border-top: 5px solid var(--danger-color);">
        <div style="padding: 1rem; position: relative;">
            <div style="position: absolute; top: 1rem; left: 1rem; font-size: 2rem; opacity: 0.2;">📉</div>
            <div style="font-size: 1rem; color: var(--text-secondary); margin-bottom: 0.5rem;">إجمالي المصروفات</div>
            <div id="expense-total" style="font-size: 1.8rem; font-weight: 700; margin-bottom: 0.5rem;">18,720 ر.س</div>
            <div style="font-size: 0.85rem; color: var(--success-color);">-3% مقارنة بالشهر الماضي</div>
        </div>
    </div>
</div>

<!-- جول المعاملات الأيرة -->
<div class="card">
    <div class="card-header">
        <h2 class="card-title">آخر المعاملات</h2>
        <select id="transaction-type" class="form-select" style="max-width: 150px;">
            <option value="all">الكل</option>
            <option value="بع">المبيعات</option>
            <option value="شراء">المشتريات</option>
            <option value="مصوفات">المصروفات</option>
        </select>
    </div>

    <div class="table-responsive">
        <table class="dashboard-table" style="width: 100%; border-collapse: collapse;">
            <thead>
                <tr>
                    <th style="padding: 0.75rem 1rem; text-align: right; background-color: rgba(46, 125, 50, 0.1); color: var(--primary-dark); font-weight: 600; border-bottom: 2px solid var(--primary-color);">التاريخ</th>
                    <th style="padding: 0.75rem 1rem; text-align: right; background-color: rgba(46, 125, 50, 0.1); color: var(--primary-dark); font-weight: 600; border-bottom: 2px solid var(--primary-color);">لنوع</th>
                    <th style="padding: 0.75rem 1rem; text-align: right; background-color: rgba(46, 125, 50, 0.1); color: var(--primary-dark); font-weight: 600; border-bottom: 2px solid var(--primary-color);">الصنف</th>
                    <th style="padding: 0.75rem 1rem; text-align: right; background-color: rgba(46, 125, 50, 0.1); color: var(--primary-dark); font-weight: 600; border-bottom: 2px solid var(--primary-color);">الكمية</th>
                    <th style="padding: 0.75rem 1rem; text-align: right; background-color: rgba(46, 125, 50, 0.1); color: var(--primary-dark); font-weight: 600; border-bottom: 2px solid var(--primary-color);">السعر</th>
                    <th style="padding: 0.75rem 1rem; text-align: right; background-color: rgba(46, 125, 50, 0.1); color: var(--primary-dark); font-weight: 600; border-bottom: 2px solid var(--primary-color);">الإجمالي</th>
                    <th style="padding: 0.75rem 1rem; text-align: right; background-color: rgba(46, 125, 50, 0.1); color: var(--primary-dark); font-weight: 600; border-bottom: 2px solid var(--primary-color);">طريقة الدف</th>
                </tr>
            </thead>
            <tbody id="transactions-table-body">
                <tr style="border-bottom: 1px solid var(--border-color);">
                    <td style="padding: 0.75rem 1rem; text-align: right;">2025/05/20</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">بيع</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">نعيمي</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">5</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">1,300 ر.س</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">6,500 ر.س</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">نقد</td>
                </tr>
                <tr style="border-bottom: 1px solid var(--border-color); background-color: rgba(0,0,0,0.02);">
                    <td style="padding: 0.75rem 1rem; text-align: right;">2025/05/19</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">شراء</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">شعير</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">200 كجم</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">1.2 ر.س</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">240 ر.س</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">حوالة</td>
                </tr>
                <tr style="border-bottom: 1px solid var(--border-color);">
                    <td style="padding: 0.75rem 1rem; text-align: right;">2025/05/18</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">بيع</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">حري</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">3</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">1,200 ر.س</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">3,600 ر.س</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">شبكة</td>
                </tr>
                <tr style="border-bottom: 1px solid var(--border-color); background-color: rgba(0,0,0,0.02);">
                    <td style="padding: 0.75rem 1rem; text-align: right;">2025/05/18</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">مصرفات</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">روات</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">1</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">3,000 ر.س</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">3,000 ر.س</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">حوالة</td>
                </tr>
                <tr>
                    <td style="padding: 0.75rem 1rem; text-align: right;">2025/05/17</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">بيع</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">نجدي</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">4</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">1,350 ر.</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">5,400 ر.س</td>
                    <td style="padding: 0.75rem 1rem; text-align: right;">نقد</td>
                </tr>
                <!-- أضف هذه الصفوف بعد الصفوف الحالية في جدول المعاملا -->
<tr style="border-bottom: 1px solid var(--border-color);">
    <td style="padding: 0.75rem 1rem; text-align: right;">2025/05/16</td>
    <td style="padding: 0.75rem 1rem; text-align: right;">مصروفات</td>
    <td style="padding: 0.75rem 1rem; text-align: right;">فيتاميات</td>
    <td style="padding: 0.75rem 1rem; text-align: right;">10 عبوات</td>
    <td style="padding: 0.75rem 1rem; text-align: right;">35 ر.س</td>
    <td style="padding: 0.75rem 1rem; text-align: right;">350 ر.س</td>
    <td style="padding: 0.75rem 1rem; text-align: right;">نقد</td>
</tr>
<tr style="border-bottom: 1px solid var(--border-color); background-color: rgba(0,0,0,0.02);">
    <td style="padding: 0.75rem 1rem; text-align: right;">2025/05/15</td>
    <td style="padding: 0.75rem 1rem; text-align: right;">مصروفات</td>
    <td style="padding: 0.75rem 1rem; text-align: right;">مضاد حيوي</td>
    <td style="padding: 0.75rem 1rem; text-align: right;">5 عبوت</td>
    <td style="padding: 0.75rem 1rem; text-align: right;">45 ر.س</td>
    <td style="padding: 0.75rem 1rem; text-align: right;">225 ر.س</td>
    <td style="padding: 0.75rem 1rem; text-align: right;">نقد</td>
</tr>
            </tbody>
        </table>
    </div>
    <!-- أضف هذا الكود أسف جدول الداشبورد مباشرة بعد إغلاق div.table-responsive -->
<div style="display: flex; justify-content: flex-end; margin-top: 1rem;">
    <button id="export-excel-btn" class="btn btn-primary" style="display: flex; align-items: center; gap: 0.5rem; background-color: #217346; border-color: #217346;">
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" viewBox="0 0 16 16">
            <path d="M14 14V4.5L9.5 0H4a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h8a2 2 0 0 0 2-2zM9.5 3A1.5 1.5 0 0 0 11 4.5h2V9H3V2a1 1 0 0 1 1-1h5.5v2zM3 12v-2h2v2H3zm0 1h2v2H4a1 1 0 0 1-1-1v-1zm3 2v-2h3v2H6zm4 0v-2h2v1a1 1 0 0 1-1 1h-1zm2-3h-2v-2h2v2zm-3 0v-2h3v2H9zm-3 0v-2h2v2H6z"/>
        </svg>
        تصدير إلى Excel
    </button>
</div>
</div>
<!-- أضف هذا الكود قبل نهاية قسم الداشبورد (قبل إغلاق div#dashboard-section) -->
<script src="https://cdn.jsdelivr.net/npm/xlsx@0.18.5/dist/xlsx.full.min.js"></script>
<script>
    // وظيفة تصدير الجدول إلى ملف Excel
    document.getElementById('export-excel-btn').addEventListener('click', function() {
        // إظهار حالة التحميل
        const originalText = this.innerHTML;
        this.innerHTML = '<span class="loading"></span> جاري التصدير...';
        this.disabled = true;
        
        setTimeout(() => {
            try {
                // الصول على الجدول
                const table = document.querySelector('.dashboard-table');
                
                // إنشاء مصفوف لتخزين البيانات
                const data = [];
                
                // إضافة العناوين
                const headers = [];
                table.querySelectorAll('thead th').forEach(th => {
                    headers.push(th.textContent.trim());
                });
                data.push(headers);
                
                // إافة الصفوف المرئة فقط (غير المخفي بواسطة التصفية)
                table.querySelectorAll('tbody tr').forEach(tr => {
                    // تجال الصفوف المخفية
                    if (tr.style.display !== 'none') {
                        const rowData = [];
                        tr.querySelectorAll('td').forEach(td => {
                            rowData.push(td.textContent.trim());
                        });
                        data.push(rowData);
                    }
                });
                
                // إنشاء كتاب عمل Excel
                const wb = XLSX.utils.book_new();
                const ws = XLSX.utils.aoa_to_sheet(data);
                
                // إضافة ورقة العمل إلى الكتاب
                XLSX.utils.book_append_sheet(wb, ws, "تقرير المعاملات");
                
                // تنيق العرض للغة العربية (من اليمين لليسار)
                ws['!cols'] = headers.map(() => ({ wch: 20 })); // عرض الأعمدة
                
                // تحميل الملف
                const today = new Date();
                const dateStr = today.getFullYear() + '-' + (today.getMonth() + 1) + '-' + today.getDate();
                XLSX.writeFile(wb, `تقري_المعاملات_${dateStr}.xlsx`);
                
                // عرض رسالة نجاح
                showAlert('تم تصدير التقرير بنجاح!', 'success', 'dashboard');
            } catch (error) {
                console.error('خطأ في تصدير الملف:', error);
                showAlert('حدث خطأ أثاء تصدير الملف. يجى المحاولة مرة أخرى.', 'error', 'dashboard');
            }
            
            // إعادة الزر لى حالته الأصلية
            this.innerHTML = originalText;
            this.disabled = false;
        }, 500);
    });
</script>
<!-- سكريبت خاص بالداشبورد -->
<script>
    
    // مدير أحداث لفلتر التايخ
    document.getElementById('date-filter').addEventListener('change', function() {
        const customFields = document.getElementById('custom-date-fields');
        if (this.value === 'custom') {
            customFields.style.display = 'flex';
        } else {
            customFields.style.display = 'none';
        }
        updateDashboardData();
    });

    // مدير أحداث لفلتر التصيف
    document.getElementById('category-filter').addEventListener('change', function() {
        updateDashboardData();
    });

    // مدير أحداث لزر التحديث
    document.getElementById('refresh-dashboard-btn').addEventListener('click', function() {
        // إهار حالة التحميل
        const originalText = this.innerHTML;
        this.innerHTML = '<span class="loading"></span> جاري التحديث...';
        this.disabled = true;
        
        // محاكاة التحميل
        setTimeout(() => {
            this.innerHTML = originalText;
            this.disabled = false;
            updateDashboardData();
            showAlert('تم تحديث البيانات بنجاح!', 'success', 'dashboard');
        }, 1000);
    });

    // مير أحداث لفلتر المعاملات
    document.getElementById('transaction-type').addEventListener('change', function() {
        updateTransactionsTable();
    });

    // تحديث بيانات الداشبورد
    function updateDashboardData() {
        const dateFilter = document.getElementById('date-filter').value;
        const categoryFilter = document.getElementById('category-filter').value;
        
        console.log(`تحديث البيانات: ترة=${dateFilter}, تصني=${categoryFilter}`);
        
        // هنا يمكنك جب البيانات من LocalStorage أو مصدر آخر
        // وتحديث العناصر في الداشبورد
        
        // للتوضيح، نقوم بتحديث بعض ابيانات بشكل عشواي
        const randomChange = (Math.random() * 20 - 10).toFixed(1);
        document.getElementById('total-sales').textContent = (35250 + Math.random() * 5000).toLocaleString() + ' ر.س';
        document.getElementById('total-sheep-sold').textContent = Math.floor(28 + Math.random() * 5);
        
        // تحديث التغيير
        const changeElems = document.querySelectorAll('.stat-change');
        changeElems.forEach(elem => {
            const isPositive = Math.random() > 0.5;
            elem.textContent = `${isPositive ? '+' : '-'}${Math.random() * 15 + 5}% مقارنة بالشهر الماضي`;
            
            if (isPositive) {
                elem.className = 'stat-change stat-change-positive';
            } else {
                elem.className = 'stat-change stat-change-negative';
            }
        });
        
        // تحديث جدول المعاملات
        updateTransactionsTable();
    }
    
    // تحديث جدول المعاملات
    function updateTransactionsTable() {
        const transactionType = document.getElementById('transaction-type').value;
        const tableBody = document.getElementById('transactions-table-body');
        const rows = tableBody.getElementsByTagName('tr');
        
        // تصفية الصفوف حسب النوع
        for(let i = 0; i < rows.length; i++) {
            const typeCell = rows[i].getElementsByTagName('td')[1];
            if (typeCell) {
                const type = typeCell.textContent;
                if (transactionType === 'all' || type === transactionType) {
                    rows[i].style.display = '';
                } else {
                    rows[i].style.display = 'none';
                }
            }
        }
    }

    // وظيفة عرض التنبيهات (إعادة استخدام وظيفة موجودة في التطبي الرئيسي)
    function showAlert(message, type = 'success', section = 'dashboard') {
        // التحقق من وجود وظيفة showAlert في اتطبيق الرئيسي
        if (typeof window.showAlert === 'function') {
            window.showAlert(message, type, section);
        } else {
            console.log(`${type}: ${message}`);
            alert(message);
        }
    }

    // تحديث البيانات عند حميل الصفحة
    document.addEventListener('DOMContentLoaded', function() {
        // تعيين تاريخ اليو لحقل التاريخ "إل"
        const today = new Date();
        const dateToInput = document.getElementById('date-to');
        if (dateToInput) {
            dateToInput.valueAsDate = today;
        }
        
        // تعيين تاريخ قبل شهر لحقل التاريخ "من"
        const oneMonthAgo = new Date();
        oneMonthAgo.setMonth(oneMonthAgo.getMonth() - 1);
        const dateFromInput = document.getElementById('date-from');
        if (dateFromInput) {
            dateFromInput.valueAsDate = oneMonthAgo;
        }
        
        // تحديث البيانات الأولية
        updateDashboardData();
    });
</script>

    <div id="invoice-modal" class="invoice-modal">
        <div class="invoice-content">
            <button class="invoice-close no-print" onclick="closeInvoiceModal()">×</button>
            <div id="invoice-print" class="invoice-print-area">
                </div>
            <div class="invoice-actions no-print">
                <button class="btn btn-primary" onclick="printInvoice()">
                    ️ طباعة
                </button>
                <button class="btn btn-secondary" onclick="downloadInvoicePDF()">
                    💾 تحمي PDF
                </button>
                <button class="btn btn-secondary" onclick="sendInvoiceWhatsApp()">
                    📱 إرسال واتسب
                </button>
                <button class="btn btn-danger" onclick="closeInvoiceModal()">
                    إغلاق
                </button>
            </div>
        </div>
    </div>

    <footer class="footer">
        <div class="footer-content">
        <img src="my_site_icon.png" alt="شار الموقع" class="footer-logo-img">
            <div>
                <div>أحد اللول الرقمية المقمة من <strong>Nalhumaid.com</strong></div>
                <div style="font-size: 0.9rem; opacity: 0.8;">نحو كفاءة تشغيلية... واستدامة حقيقية © 2025م</div>
            </div>
        </div>
    </footer>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
    <script>
        // Global Variables
        let currentItems = [
            {name: 'نعيمي', category: 'أغنام'},
            {name: 'حري', category: 'أغنام'},
            {name: 'نجدي', category: 'أغنام'},
            {name: 'تيوس', category: 'أغنام'},
            {name: 'شعير', category: 'أعلاف'},
            {name: 'برسيم', category: 'أعلاف'},
            {name: 'ذرة صفراء', category: 'أعلاف'},
            {name: 'فيدكو', category: 'أعلاف'},
            {name: 'فيتامينات', category: 'علاجات'},
            {name: 'مضاد حيوي', category: 'علاجات'}
        ];
        let selectedCount = 0;
        let currentExpenseType = '';
        let lastSalesData = null; // Store last sale for invoice generation

        // Initialize the app
        document.addEventListener('DOMContentLoaded', function() {
            loadItems();
            renderProducts();
            renderItems();

            // Force collapsible invoice section to be collapsed on page load
            const invoiceContentCollapsible = document.getElementById('invoice-content-collapsible');
            const invoiceArrowCollapsible = document.getElementById('invoice-arrow-collapsible');

            if (invoiceContentCollapsible && invoiceArrowCollapsible) {
                invoiceContentCollapsible.style.display = 'none';
                invoiceArrowCollapsible.textContent = '️';
                 // Adjust card-header style if content is hidden
                const header = invoiceContentCollapsible.previousElementSibling;
                if (header && header.classList.contains('card-header')) {
                    header.style.borderBottom = '1px solid var(--border-color)';
                    header.style.marginBottom = '1.5rem';
                }
            }

             // Initial state for the non-collapsible invoice section (if it still exists or was planned)
            const invoiceContent = document.getElementById('invoice-content'); // Assuming this was the ID for the old non-collapsible version
            const invoiceCard = document.getElementById('invoice-card'); // Assuming this was the ID for the old non-collapsible version
            const invoiceArrow = document.getElementById('invoice-arrow'); // Assuming this was the ID for the old non-collapsible version

            if (invoiceContent && invoiceArrow && invoiceCard) {
                invoiceContent.style.display = 'none';
                invoiceArrow.textContent = '⬇️';
                invoiceCard.classList.remove('expanded');
            }
        });

        // Tab Switching
        function switchTab(tabName) {
            // Hide all sections
            document.querySelectorAll('.content-section').forEach(section => {
                section.classList.remove('active');
            });

            // Remove active class from all tabs
            document.querySelectorAll('.nav-tab').forEach(tab => {
                tab.classList.remove('active');
            });

            // Show selected section
            document.getElementById(tabName + '-section').classList.add('active');

            // Add active class to clicked tab
            event.target.classList.add('active');
        }

        // Load items from localStorage or use defaults
        function loadItems() {
            const saved = localStorage.getItem('sheepItems');
            if (saved) {
                currentItems = JSON.parse(saved);
            }
        }

        // Save items to localStorage
        function saveItems() {
            localStorage.setItem('sheepItems', JSON.stringify(currentItems));
        }

        // Render products for sales
        // Render products for sales
// Render products for sales
// Render products for sales
function renderProducts() {
    const container = document.getElementById('products-container');
    container.innerHTML = '';

    const sheepItems = currentItems.filter(item => item.category === 'أغنام');

    sheepItems.forEach(item => {
        const productHTML = `
            <div class="product-item collapsed" data-item="${item.name}" onclick="toggleProductItem(this, event)">
                <div class="product-header">
                    <div class="product-name">
                        🐑 ${item.name}
                        <span class="product-badge badge-${item.category}">${item.category}</span>
                    </div>
                    <div class="product-toggle">
                        <div class="vertical-dots">
                            <div class="dot"></div>
                            <div class="dot"></div>
                            <div class="dot"></div>
                        </div>
                    </div>
                </div>
                <div class="product-details">
                    <div class="product-controls">
                        <div class="price-input-container">
                            <input type="number"
                                   class="price-input"
                                   placeholder="سعر الرأس"
                                   oninput="updateTotal()"
                                   onclick="event.stopPropagation()">
                            <span class="currency-symbol">ر.س</span>
                        </div>
                        <div class="quantity-control">
                            <button class="qty-btn" onclick="changeQty('${item.name}', -1); event.stopPropagation()">-</button>
                            <input type="text" class="qty-input" value="0" readonly onclick="event.stopPropagation()">
                            <button class="qty-btn" onclick="changeQty('${item.name}', 1); event.stopPropagation()">+</button>
                        </div>
                    </div>
                </div>
            </div>
        `;
        container.insertAdjacentHTML('beforeend', productHTML);
    });

    if (sheepItems.length === 0) {
        container.innerHTML = '<p style="text-align: center; color: var(--text-secondary); padding: 2rem;">لا توجد أصنا أغنام متاحة. أضف بعض الأصناف في قس إدارة الأصناف.</p>';
    }
}
        // Quantity Management
        // Quantity Management
function changeQty(itemName, delta) {
    const productItem = document.querySelector(`[data-item="${itemName}"]`);
    if (!productItem) return;
    
    const qtyInput = productItem.querySelector('.qty-input');
    let currentQty = parseInt(qtyInput.value) || 0;

    currentQty = Math.max(0, currentQty + delta);
    qtyInput.value = currentQty;

    // تحديث حالة المنتج المرئية
    updateProductState(productItem, currentQty);
    updateTotal();
    updateSelectedCount();
    
    // إذا تم زيادة لكمية عن 0، افتح البلوك
    if (currentQty > 0) {
        productItem.classList.remove('collapsed');
        productItem.classList.add('expanded');
    }
}
        

        // تحديث حالة المنتج المرئية
function updateProductState(productItem, qty) {
    if (qty > 0) {
        productItem.classList.add('selected');
        productItem.classList.remove('collapsed');
        productItem.classList.add('expanded');
    } else {
        productItem.classList.remove('selected');
        // نحافظ عى الحالة الحالية للطي عند الكمية 0
    }
}
        
        // Total Calculation
        function updateTotal() {
            let total = 0;
            let totalHeads = 0;
            let totalValue = 0;

            document.querySelectorAll('.product-item.selected').forEach(productItem => { // Iterate only selected items
                const qty = parseInt(productItem.querySelector('.qty-input').value) || 0;
                const price = parseFloat(productItem.querySelector('.price-input').value) || 0;

                if (qty > 0 && price > 0) { // Ensure price is also entered
                    total += qty * price;
                    totalHeads += qty;
                    totalValue += qty * price;
                }
            });

            document.getElementById('total-amount').textContent = total.toLocaleString();
            document.getElementById('total-heads').textContent = totalHeads;

            const avgPrice = totalHeads > 0 ? (totalValue / totalHeads) : 0;
            document.getElementById('avg-price').textContent = avgPrice.toLocaleString(undefined, { minimumFractionDigits: 2, maximumFractionDigits: 2 }) + ' .س';

            // Enable/disable invoice buttons based on total and phone input
            const phone = document.getElementById('customer-phone').value.trim();
            const hasValidPhone = phone.length >= 10; // Or your specific validation
            const salesConfirmedAndHasData = lastSalesData !== null; // Check if sale was confirmed

            document.getElementById('whatsapp-btn').disabled = !(hasValidPhone && salesConfirmedAndHasData && total > 0);
            document.getElementById('pdf-btn').disabled = !(salesConfirmedAndHasData && total > 0);
            document.getElementById('download-btn').disabled = !(salesConfirmedAndHasData && total > 0);

        }

        function toggleProductItem(element, event) {
    // إيقاف انشار الحدث للأزرا الداخلية
    if (event.target.classList.contains('qty-btn') || 
        event.target.classList.contains('price-input') || 
        event.target.classList.contains('qty-input')) {
        return;
    }
    

    // تبديل حالة الطي
    if (element.classList.contains('collapsed')) {
        element.classList.remove('collapsed');
        element.classList.add('expanded');
    } else {
        // اتركه مفتوحًا إذا كان محددًا (الكمية أكبر من 0)
        if (!element.classList.contains('selected')) {
            element.classList.remove('expanded');
            element.classList.add('collapsed');
        }
    }
}
        function updateSelectedCount() {
            selectedCount = 0;
            document.querySelectorAll('.product-item').forEach(productItem => {
                const qty = parseInt(productItem.querySelector('.qty-input').value) || 0;
                if (qty > 0) selectedCount++;
            });

            document.getElementById('selected-count').textContent = selectedCount + ' منتج';
        }

        // Form Reset Functions
        function resetCurrentForm() {
            const activeSection = document.querySelector('.content-section.active');
            if (!activeSection) return;
            const sectionId = activeSection.id;

            if (sectionId === 'sales-section') {
                resetSalesForm();
            } else if (sectionId === 'expenses-section') {
                resetExpenseForm();
            }
        }

        function resetSalesForm() {
            // Reset quantities and prices
            document.querySelectorAll('.qty-input').forEach(input => input.value = '0');
            document.querySelectorAll('.price-input').forEach(input => input.value = '');

            // Reset payment method
            document.getElementById('payment-cash').checked = true;

            // Reset notes
            document.getElementById('sales-note').value = '';

            // Reset button state
            const submitBtn = document.getElementById('sales-submit-btn');
            submitBtn.disabled = false;
            submitBtn.innerHTML = '✅ أكيد البيع';
            submitBtn.style.backgroundColor = ''; // Reset to default

            // Update visuals
            document.querySelectorAll('.product-item').forEach(item => {
                item.classList.remove('selected');
                // item.style.borderColor = 'var(--border-color)'; // Reset border, or rely on CSS
            });

            updateTotal();
            updateSelectedCount();
            clearAlerts('sales');

            // Reset and collapse invoice section (the new collapsible one)
            document.getElementById('customer-phone').value = '';
            document.getElementById('customer-name').value = '';
            document.getElementById('whatsapp-btn').disabled = true;
            document.getElementById('pdf-btn').disabled = true;
            document.getElementById('download-btn').disabled = true;

            // Force collapse the new collapsible invoice section
            const invoiceContentCollapsible = document.getElementById('invoice-content-collapsible');
            const invoiceArrowCollapsible = document.getElementById('invoice-arrow-collapsible');

            if (invoiceContentCollapsible && invoiceArrowCollapsible) {
                invoiceContentCollapsible.style.display = 'none';
                invoiceArrowCollapsible.textContent = '⬇️';
                const header = invoiceContentCollapsible.previousElementSibling;
                 if (header && header.classList.contains('card-header')) {
                    header.style.borderBottom = '1px solid var(--border-color)'; // Restore border if needed
                    header.style.marginBottom = '1.5rem'; // Restore margin
                }
            }

            lastSalesData = null;
        }


        function resetExpenseForm() {
            // Reset expense type selection
            document.querySelectorAll('.expense-type').forEach(type => {
                type.classList.remove('selected');
            });

            // Hide expense form
            document.getElementById('expense-form').classList.add('hide');

            // Reset form fields
            document.getElementById('expense-category').value = '';
            document.getElementById('expense-item').innerHTML = '<option value="">اختر الصنف</option>'; // Clear items
            document.getElementById('expense-quantity').value = '';
            document.getElementById('expense-price').value = '';
            document.getElementById('expense-description').value = '';
            document.getElementById('expense-payment-cash').checked = true;

            // Reset total
            document.getElementById('expense-total').textContent = '0';

            // Reset button
            const submitBtn = document.getElementById('expense-submit-btn');
            submitBtn.disabled = false;
            submitBtn.innerHTML = '✅ تسجيل المصروف';
            submitBtn.style.backgroundColor = ''; // Reset to default


            currentExpenseType = '';
            clearAlerts('expenses');
        }

        // Alert System
        function showAlert(message, type = 'success', section = 'sales') {
            const alertContainer = document.getElementById(section + '-alert-container');
            if (!alertContainer) return;
            const alertDiv = document.createElement('div');
            alertDiv.className = `alert alert-${type}`;
            alertDiv.textContent = message;

            // Remove existing alerts of the same type to avoid clutter
            const existingAlert = alertContainer.querySelector(`.alert-${type}`);
            if(existingAlert) existingAlert.remove();

            alertContainer.appendChild(alertDiv);

            // Auto remove after 5 seconds
            setTimeout(() => {
                if (alertDiv.parentNode === alertContainer) { // Check if it's still there
                    alertDiv.remove();
                }
            }, 5000);
        }


        function clearAlerts(section = 'sales') {
            const alertContainer = document.getElementById(section + '-alert-container');
            if (alertContainer) {
                alertContainer.innerHTML = '';
            }
        }

        // Send to Google Sheets
        function sendToSheet(payload) {
            return fetch("https://script.google.com/macros/s/AKfycbxxk28xPro_jaIMsvMdnOuK2eSEESeHaAnckVTxct2x_M6QrlmXVxNDd1xkMAzGze3FUA/exec", {
                method: "POST",
                mode: "no-cors", // Important for simple POST to Sheets web app
                headers: {
                    "Content-Type": "application/json", // Though with no-cors, this might not be fully processed by Sheets
                },
                body: JSON.stringify(payload), // Ensure payload is an object for Sheets to parse
            }).then(() => {
                console.log("✅ تم الإرسال إلى الشيت (أو لطلب تم بدون انتظار رد بسبب no-cors)");
            }).catch(err => {
                console.error("❌ خطأ أثناء محاولة لإرسال (ملاحظة: م no-cors، الخطأ قد لا يكون واضحًا):", err);
                 // showAlert('حدث خطأ أثناء محالة حفظ البيانات. رجى المحاولة مرة أخرى.', 'error', payload.type === "بيع" ? 'sales' : 'expenses');
            });
        }


        // Sales Confirmation
        function confirmSales() {
            const submitBtn = document.getElementById('sales-submit-btn');

            if (submitBtn.disabled) return;

            // Get form data
            const paymentMethod = document.querySelector('input[name="sales-payment"]:checked')?.value || '';
            const note = document.getElementById('sales-note').value;

            // Validate payment method
            if (!paymentMethod) {
                showAlert('يرجى اختيار طريقة الدفع', 'warning', 'sales');
                return;
            }

            // Collect sales data
            const salesDataItems = []; // Renamed for clarity
            let currentTotal = 0;
            document.querySelectorAll('.product-item.selected').forEach(productItem => {
                const itemName = productItem.getAttribute('data-item');
                const qty = parseInt(productItem.querySelector('.qty-input').value) || 0;
                const price = parseFloat(productItem.querySelector('.price-input').value) || 0;

                if (qty > 0 && price > 0) { // Ensure price is also valid
                    const itemTotal = qty * price;
                    salesDataItems.push({
                        type: "بيع",
                        category: "أغنام", // Assuming all sales are for 'أغنم'
                        item: itemName,
                        qty: qty,
                        price: price,
                        total: itemTotal,
                        payment: paymentMethod,
                        note: note,
                        timestamp: new Date().toISOString() // Add timestamp for better record keeping
                    });
                    currentTotal += itemTotal;
                }
            });

            if (salesDataItems.length === 0) {
                showAlert('يرجى إدخا بيانات صحيحة على الأقل لصنف واحد (مية وسعر)', 'warning', 'sales');
                return;
            }

            // Send each item separately
            salesDataItems.forEach(item => sendToSheet(item));

            // Store sales data for invoice generation
            lastSalesData = {
                items: salesDataItems,
                total: currentTotal, // Use the calculated total
                date: new Date().toLocaleDateString('ar-SA-u-nu-arab'), // Arabic numerals for date
                time: new Date().toLocaleTimeString('ar-SA-u-nu-arab', {hour: '2-digit', minute: '2-digit'}), // Arabic numerals for time
                payment: paymentMethod,
                note: note,
                invoiceNumber: generateInvoiceNumber() // Generate and store invoice number
            };

            // Enable invoice buttons now that sale is confirmed and data is ready
            const phone = document.getElementById('customer-phone').value.trim();
            const hasValidPhone = phone.length >= 10; // Your validation
            document.getElementById('whatsapp-btn').disabled = !(hasValidPhone && lastSalesData.total > 0);
            document.getElementById('pdf-btn').disabled = !(lastSalesData.total > 0);
            document.getElementById('download-btn').disabled = !(lastSalesData.total > 0);


            // Auto-open the collapsible invoice section after successful sale
            const invoiceContentCollapsible = document.getElementById('invoice-content-collapsible');
            const invoiceArrowCollapsible = document.getElementById('invoice-arrow-collapsible');

            if (invoiceContentCollapsible && invoiceArrowCollapsible && (invoiceContentCollapsible.style.display === "none" || invoiceContentCollapsible.style.display === "")) {
                toggleInvoiceSectionCollapsible(); // This will open it
            }

            // Update button state
            submitBtn.disabled = true;
            submitBtn.style.backgroundColor = '#999'; // Visually indicate it's disabled
            submitBtn.innerHTML = '<span class="loading"></span> جاري التسجيل...'; // Loading state
            setTimeout(() => {
                 submitBtn.innerHTML = '✅ م التسجيل';
                 showAlert('تم تسجيل المبيعات بنجاح - مكنك الآن إرسال الفاتورة للعميل', 'success', 'sales');
            }, 1500); // Simulate processing time
        }


        // Expense Management
        // Expense Type Management
function selectExpenseType(type, element) {
    // Remove previous selection
    document.querySelectorAll('.expense-type').forEach(item => {
        item.classList.remove('selected');
    });

    // Add selection to clicked item
    element.classList.add('selected');
    currentExpenseType = type;

    // Hide all expense forms
    document.querySelectorAll('.expense-form').forEach(form => {
        form.classList.add('hide');
    });

    // Show the specific form for this expense type
    const formId = `expense-form-${type}`;
    const formElement = document.getElementById(formId);
    if (formElement) {
        formElement.classList.remove('hide');
        
        // Initialize form specific data if needed
        if (type === 'مشريات') {
            populateSheepItems();
        } else if (type === 'مصاريف') {
            document.getElementById('expense-general-category').value = '';
            updateGeneralExpenseItems();
        }
    }
}

// Populate sheep items in purchases form
function populateSheepItems() {
    const sheepSelect = document.getElementById('expense-sheep-item');
    if (!sheepSelect) return;
    
    // Clear previous options
    sheepSelect.innerHTML = '<option value="">اختر صنف الأغنام</option>';
    
    // Add sheep items from current items
    const sheepItems = currentItems.filter(item => item.category === 'أغنام');
    sheepItems.forEach(item => {
        const option = document.createElement('option');
        option.value = item.name;
        option.textContent = item.name;
        sheepSelect.appendChild(option);
    });
}

// Update general expense items based on selected category
function updateGeneralExpenseItems() {
    const category = document.getElementById('expense-general-category').value;
    const itemSelect = document.getElementById('expense-general-item');
    
    // Clear previous options
    itemSelect.innerHTML = '<option value="">اختر الصنف</option>';
    
    if (category === 'أعلاف' || category === 'علاجات') {
        // Load items from our current items list
        const items = currentItems.filter(item => item.category === category);
        items.forEach(item => {
            const option = document.createElement('option');
            option.value = item.name;
            option.textContent = item.name;
            itemSelect.appendChild(option);
        });
    } else if (category) { // For other non-empty categories
        const option = document.createElement('option');
        option.value = 'أخرى - ' + category; // Make it more specific
        option.textContent = 'أخرى (سيتم تحديدها في الوصف)';
        itemSelect.appendChild(option);
        itemSelect.value = 'أخرى - ' + category; // Auto-select if 'أخرى'
    }
}

// Calculate totals for each expense type
function calculateSheepTotal() {
    const quantity = parseInt(document.getElementById('expense-sheep-quantity').value) || 0;
    const price = parseFloat(document.getElementById('expense-sheep-price').value) || 0;
    const total = quantity * price;
    
    document.getElementById('expense-sheep-total').textContent = total.toLocaleString();
}

function calculateGeneralExpenseTotal() {
    const quantity = parseFloat(document.getElementById('expense-general-quantity').value) || 0;
    const price = parseFloat(document.getElementById('expense-general-price').value) || 0;
    const total = quantity * price;
    
    document.getElementById('expense-general-total').textContent = total.toLocaleString();
}

function updateSalaryTotal() {
    const amount = parseFloat(document.getElementById('expense-salary-amount').value) || 0;
    document.getElementById('expense-salary-total').textContent = amount.toLocaleString();
}

function updateMaintenanceTotal() {
    const amount = parseFloat(document.getElementById('expense-maintenance-amount').value) || 0;
    document.getElementById('expense-maintenance-total').textContent = amount.toLocaleString();
}

// Confirm expense for each type
function confirmSheepExpense() {
    const submitBtn = document.getElementById('expense-sheep-submit-btn');
    if (submitBtn.disabled) return;
    
    // Get form data
    const item = document.getElementById('expense-sheep-item').value;
    const quantity = parseInt(document.getElementById('expense-sheep-quantity').value) || 0;
    const price = parseFloat(document.getElementById('expense-sheep-price').value) || 0;
    const description = document.getElementById('expense-sheep-description').value;
    const paymentMethod = document.querySelector('input[name="expense-sheep-payment"]:checked')?.value || '';
    
    // Validation
    if (!item) {
        showAlert('يرجى اختيار صنف الأغنام', 'warning', 'expenses');
        return;
    }
    
    if (quantity <= 0) {
        showAlert('يرجى إدخال عدد الؤوس', 'warning', 'expenses');
        return;
    }
    
    if (price <= 0) {
        showAlert('يرجى إدخال سعر الرأس', 'warning', 'expenses');
        return;
    }
    
    // Prepare data for submission
    const expenseData = {
        type: 'مشتريات',
        category: 'أغنام',
        item: item,
        qty: quantity,
        price: price,
        total: quantity * price,
        payment: paymentMethod,
        note: description,
        timestamp: new Date().toISOString()
    };
    
    // Send to sheet
    sendToSheet(expenseData);
    
    // Update button state
    updateSubmitButtonState(submitBtn, 'تم تسجيل المشتريات');
}

function confirmGeneralExpense() {
    const submitBtn = document.getElementById('expense-general-submit-btn');
    if (submitBtn.disabled) return;
    
    // Get form data
    const category = document.getElementById('expense-general-category').value;
    const item = document.getElementById('expense-general-item').value;
    const quantity = parseFloat(document.getElementById('expense-general-quantity').value) || 0;
    const price = parseFloat(document.getElementById('expense-general-price').value) || 0;
    const description = document.getElementById('expense-general-description').value;
    const paymentMethod = document.querySelector('input[name="expense-general-payment"]:checked')?.value || '';
    
    // Validation
    if (!category) {
        showAlert('يرجى اختيار التصنيف', 'warning', 'expenses');
        return;
    }
    
    if (!item) {
        showAlert('يرجى اختيار الصنف', 'warning', 'expenses');
        return;
    }
    
    if (item.startsWith('أخرى - ') && !description.trim()) {
        showAlert('يرجى كتابة وصف للصنف "أخرى"', 'warning', 'expenses');
        return;
    }
    
    if (quantity <= 0 || price <= 0) {
        showAlert('يرجى إدخال كمية وسعر صحيحين', 'warning', 'expenses');
        return;
    }
    
    // Prepare data for submission
    const expenseData = {
        type: 'مصاريف',
        category: category,
        item: item,
        qty: quantity,
        price: price,
        total: quantity * price,
        payment: paymentMethod,
        note: description,
        timestamp: new Date().toISOString()
    };
    
    // Send to sheet
    sendToSheet(expenseData);
    
    // Update button state
    updateSubmitButtonState(submitBtn, 'تم تسجيل المصروف');
}

function confirmSalaryExpense() {
    const submitBtn = document.getElementById('expense-salary-submit-btn');
    if (submitBtn.disabled) return;
    
    // Get form data
    const amount = parseFloat(document.getElementById('expense-salary-amount').value) || 0;
    const description = document.getElementById('expense-salary-description').value;
    const paymentMethod = document.querySelector('input[name="expense-salary-payment"]:checked')?.value || '';
    
    // Validation
    if (amount <= 0) {
        showAlert('يرجى إدخال مبغ الراتب', 'warning', 'expenses');
        return;
    }
    
    // Prepare data for submission
    const expenseData = {
        type: 'رواتب',
        category: 'عمالة',
        item: 'راتب',
        qty: 1,
        price: amount, // Store full amount as price
        total: amount,
        payment: paymentMethod,
        note: description,
        timestamp: new Date().toISOString()
    };
    
    // Send to sheet
    sendToSheet(expenseData);
    
    // Update button state
    updateSubmitButtonState(submitBtn, 'تم تسجيل الراتب');
}

function confirmMaintenanceExpense() {
    const submitBtn = document.getElementById('expense-maintenance-submit-btn');
    if (submitBtn.disabled) return;
    
    // Get form data
    const amount = parseFloat(document.getElementById('expense-maintenance-amount').value) || 0;
    const description = document.getElementById('expense-maintenance-description').value;
    const paymentMethod = document.querySelector('input[name="expense-maintenance-payment"]:checked')?.value || '';
    
    // Validation
    if (amount <= 0) {
        showAlert('يرجى إدخال مبلغ الصيانة', 'warning', 'expenses');
        return;
    }
    
    if (!description.trim()) {
        showAlert('رجى كتابة وصف أعمال الصيانة', 'warning', 'expenses');
        return;
    }
    
    // Prepare data for submission
    const expenseData = {
        type: 'صيانة',
        category: 'صيانة',
        item: 'صيانة',
        qty: 1,
        price: amount, // Store full amount as price
        total: amount,
        payment: paymentMethod,
        note: description,
        timestamp: new Date().toISOString()
    };
    
    // Send to sheet
    sendToSheet(expenseData);
    
    // Update button state
    updateSubmitButtonState(submitBtn, 'تم تسجيل الصيانة');
}

// Helper function for updating submit button state
function updateSubmitButtonState(button, successMessage) {
    button.disabled = true;
    button.style.backgroundColor = '#999';
    button.innerHTML = '<span class="loading"></span> جار التسجيل...';
    
    setTimeout(() => {
        button.innerHTML = '✅ ' + successMessage;
        showAlert(successMessage + ' بنجاح', 'success', 'expenses');
    }, 1500);
}

// Reset the expense form completely
function resetExpenseForm() {
    // Reset expense type selection
    document.querySelectorAll('.expense-type').forEach(type => {
        type.classList.remove('selected');
    });
    
    // Hide all expense forms
    document.querySelectorAll('.expense-form').forEach(form => {
        form.classList.add('hide');
    });
    
    // Reset sheep purchases form
    if (document.getElementById('expense-sheep-item')) {
        document.getElementById('expense-sheep-item').value = '';
        document.getElementById('expense-sheep-quantity').value = '';
        document.getElementById('expense-sheep-price').value = '';
        document.getElementById('expense-sheep-description').value = '';
        document.getElementById('expense-sheep-payment-cash').checked = true;
        document.getElementById('expense-sheep-total').textContent = '0';
        resetSubmitButton('expense-sheep-submit-btn', 'تسجيل المشتريات');
    }
    
    // Reset general expenses form
    if (document.getElementById('expense-general-category')) {
        document.getElementById('expense-general-category').value = '';
        document.getElementById('expense-general-item').innerHTML = '<option value="">اخر الصنف</option>';
        document.getElementById('expense-general-quantity').value = '';
        document.getElementById('expense-general-price').value = '';
        document.getElementById('expense-general-description').value = '';
        document.getElementById('expense-general-payment-cash').checked = true;
        document.getElementById('expense-general-total').textContent = '0';
        resetSubmitButton('expense-general-submit-btn', 'تسجيل المصروف');
    }
    
    // Reset salary form
    if (document.getElementById('expense-salary-amount')) {
        document.getElementById('expense-salary-amount').value = '';
        document.getElementById('expense-salary-description').value = '';
        document.getElementById('expense-salary-payment-cash').checked = true;
        document.getElementById('expense-salary-total').textContent = '0';
        resetSubmitButton('expense-salary-submit-btn', 'تسجيل الراتب');
    }
    
    // Reset maintenance form
    if (document.getElementById('expense-maintenance-amount')) {
        document.getElementById('expense-maintenance-amount').value = '';
        document.getElementById('expense-maintenance-description').value = '';
        document.getElementById('expense-maintenance-payment-cash').checked = true;
        document.getElementById('expense-maintenance-total').textContent = '0';
        resetSubmitButton('expense-maintenance-submit-btn', 'تسجيل الصيانة');
    }
    
    currentExpenseType = '';
    clearAlerts('expenses');
}

// Helper to reset a submit button
function resetSubmitButton(buttonId, defaultText) {
    const btn = document.getElementById(buttonId);
    if (btn) {
        btn.disabled = false;
        btn.style.backgroundColor = '';
        btn.innerHTML = '✅ ' + defaultText;
    }
}

// Initialize expenses section
document.addEventListener('DOMContentLoaded', function() {
    // Add this to your existing DOMContentLoaded event or create a new one
    const resetExpenseButton = document.querySelector('#expenses-section .btn-secondary');
    if (resetExpenseButton) {
        resetExpenseButton.onclick = resetExpenseForm;
    }
    
    // Set up input listeners for expense calculations
    document.addEventListener('input', function(e) {
        // For sheep purchases
        if (e.target.id === 'expense-sheep-quantity' || e.target.id === 'expense-sheep-price') {
            calculateSheepTotal();
        }
        
        // For general expenses
        if (e.target.id === 'expense-general-quantity' || e.target.id === 'expense-general-price') {
            calculateGeneralExpenseTotal();
        }
        
        // For salaries
        if (e.target.id === 'expense-salary-amount') {
            updateSalaryTotal();
        }
        
        // For maintenance
        if (e.target.id === 'expense-maintenance-amount') {
            updateMaintenanceTotal();
        }
    });// وظيفة لتبديل حالة النصر القابل للطي
function toggleProductItem(element, event) {
    // إيقاف اتشار الحدث للأزرر الداخلية
    if (event.target.classList.contains('qty-btn') || 
        event.target.classList.contains('price-input') || 
        event.target.classList.contains('qty-input')) {
        return;
    }

    // تديل حالة الطي
    if (element.classList.contains('collapsed')) {
        element.classList.remove('collapsed');
        element.classList.add('expanded');
    } else {
        // تركه مفتوحًا إذا كان محددًا (الكمي أكبر من 0)
        if (!element.classList.contains('selected')) {
            element.classList.remove('expanded');
            element.classList.add('collapsed');
        }
    }
}
});

        // Items Management
        function renderItems() {
            const categories = ['أغنام', 'أعلاف', 'عاجات'];

            categories.forEach(category => {
                const container = document.getElementById('items-' + category);
                if (!container) return;
                container.innerHTML = '';

                const itemsInCategory = currentItems.filter(item => item.category === category); // Renamed for clarity

                itemsInCategory.forEach(item => {
                    const itemHTML = `
                        <div class="item-card">
                            <div class="item-header">
                                <span class="item-name">${item.name}</span>
                                <button class="btn btn-danger btn-small" onclick="deleteItem('${item.name}', '${item.category}')">
                                    🗑️ حذف
                                </button>
                            </div>
                            <div class="product-badge badge-${item.category.replace(/\s+/g, '-')}">${item.category}</div>
                        </div>
                    `;
                    container.insertAdjacentHTML('beforeend', itemHTML);
                });

                if (itemsInCategory.length === 0) {
                    container.innerHTML = `<p style="text-align: center; color: var(--text-secondary); padding: 1rem;">لا توجد أصناف في هذا التصنيف (${category})</p>`;
                }
            });
        }


        function showAddItemModal() {
            document.getElementById('add-item-form').classList.remove('hide');
        }

        function hideAddItemModal() {
            document.getElementById('add-item-form').classList.add('hide');
            document.getElementById('new-item-name').value = '';
            document.getElementById('new-item-category').value = '';
            clearAlerts('items'); // Clear any previous alerts in this section
        }


        function addNewItem() {
            const nameInput = document.getElementById('new-item-name');
            const categorySelect = document.getElementById('new-item-category');
            const name = nameInput.value.trim();
            const category = categorySelect.value;

            if (!name) {
                showAlert('يرج إدخال اسم الصنف', 'warning', 'items');
                nameInput.focus();
                return;
            }

            if (!category) {
                showAlert('يرجى اختيار التصنيف', 'warning', 'items');
                categorySelect.focus();
                return;
            }

            // Check if item already exists (case-insensitive check for name)
            const exists = currentItems.some(item =>
                item.name.toLowerCase() === name.toLowerCase() && item.category === category
            );

            if (exists) {
                showAlert(`الصنف "${name}" مجود مسبقاً في تصنيف "${category}".`, 'warning', 'items');
                return;
            }

            // Add new item
            currentItems.push({ name, category });
            saveItems();
            renderItems(); // Update display in Items Management
            renderProducts(); // Update products list in Sales section
            hideAddItemModal(); // Hide form and clear inputs

            showAlert(`تم إافة الصنف "${name}" بجاح إلى "${category}"`, 'success', 'items');
        }


        function deleteItem(name, category) {
            if (confirm(`هل أنت متأكد من حذف الصنف "${name}" ن تصنيف "${category}"؟ ذا الإجراء لا يمكن التراجع عنه.`)) {
                currentItems = currentItems.filter(item =>
                    !(item.name === name && item.category === category)
                );
                saveItems();
                renderItems(); // Update display in Items Management
                renderProducts(); // Update products list in Sales section

                showAlert(`تم حذف الصنف "${name}" نجاح.`, 'success', 'items');
            }
        }


        // Auto-calculate when quantity or price changes & handle phone input
        document.addEventListener('input', function(e) {
            if (e.target.id === 'expense-quantity' || e.target.id === 'expense-price') {
                calculateExpenseTotal();
            }

            // Enable/disable buttons based on phone input and sales data
            if (e.target.id === 'customer-phone' || e.target.classList.contains('price-input') || e.target.classList.contains('qty-input')) {
                updateTotal(); // This function now handles button disabling/enabling
            }
        });


        // Phone number formatting
        function formatPhoneNumber(input) {
            let value = input.value.replace(/\D/g, ''); // Remove non-digits

            // Add country code if starts with 05 and is a Saudi number candidate
            if (value.startsWith('05') && value.length >= 9) { // Check length before assuming it's a full local number
                if (value.length === 9) { // 05xxxxxxxx
                     // Don't add 966 yet, wait for more digits or focus out.
                } else if (value.length >= 10 && !value.startsWith('96605')) { // e.g. 05xxxxxxxxx
                    value = '966' + value.substring(1);
                }
            } else if (value.startsWith('5') && value.length >= 9 && !value.startsWith('9665')) { // Handles case where user types 5 directly
                 value = '966' + value;
            }


            // Limit length (966 + 9 digits = 12)
            if (value.length > 12) {
                value = value.substring(0, 12);
            }

            input.value = value;
            updateTotal(); // Update button states based on phone validity
        }


        // Generate invoice text for WhatsApp
        function generateInvoiceText() {
            if (!lastSalesData) return '';

            const customerName = document.getElementById('customer-name').value.trim();
            const customerGreeting = customerName ? `السلام عليكم ورحمة لله وبركاته، الأ/ ${customerName}` : 'السلم عليكم ورحمة الله وبركاته';

            let invoiceText = `${customerGreeting}

🧾 *فاتورة مبيعات أغنام*
رقم الفاتورة: ${lastSalesData.invoiceNumber}
📅 التاريخ: ${lastSalesData.date}
🕐 اوقت: ${lastSalesData.time}

`;
            invoiceText += `◦○◦━◦○◦━◦○◦━◦○◦━◦○◦━○◦━\n`;
            invoiceText += `📦 *تفاصيل الطلب:*\n\n`;

            // Add items
            lastSalesData.items.forEach((item, index) => {
                invoiceText += `${index + 1}. *${item.item}*
   🐑 الكمية: ${item.qty} رأس
   💰 سعر الأس: ${item.price.toLocaleString()} ر.س
   💵 الإجمالي للصنف: ${item.total.toLocaleString()} ر.س
\n`;
            });

            invoiceText += `━◦○◦━◦○◦━◦○◦━◦○◦━◦◦━◦○◦━\n`;
            invoiceText += `💳 *طريقة الدفع:* ${lastSalesData.payment}\n`;
            invoiceText += `💸 *المبلغ الإجمالي للفاتورة:* *${lastSalesData.total.toLocaleString()} ريال سعودي*\n`;

            if (lastSalesData.note && lastSalesData.note.trim() !== "") {
                invoiceText += `📝 *ملاحظت:* ${lastSalesData.note.trim()}\n`;
            }

            invoiceText += `
شكرًا لتعاملكم معنا، ونتطلع لخدمتكم مرة أرى 🙏

━◦○◦━◦◦━◦○◦━◦○◦━○◦━◦○◦━
🏢 *Nalhumaid.com*
نحو كفاءة شغيلية... واستدام حقيقية`;

            return invoiceText;
        }


        // Generate Arabic invoice number
        function generateInvoiceNumber() {
            const now = new Date();
            // YYYYMMDD-HHMMSS format
            const year = now.getFullYear();
            const month = String(now.getMonth() + 1).padStart(2, '0');
            const day = String(now.getDate()).padStart(2, '0');
            const hours = String(now.getHours()).padStart(2, '0');
            const minutes = String(now.getMinutes()).padStart(2, '0');
            const seconds = String(now.getSeconds()).padStart(2, '0');
            return `INV-${year}${month}${day}-${hours}${minutes}${seconds}`;
        }


        // Generate PDF-ready invoice HTML
        function generateInvoiceHTML(forPDF = false) { // Added parameter
            if (!lastSalesData) return '';

            const customerName = document.getElementById('customer-name').value.trim() || 'عميل ريم';
            const customerPhone = document.getElementById('customer-phone').value.trim();
            // const invoiceNumber = lastSalesData.invoiceNumber || generateInvoiceNumber(); // Use stored or generate new if missing

            let itemsHTML = '';
            let itemCounter = 1;

            lastSalesData.items.forEach(item => {
                itemsHTML += `
                    <tr>
                        <td>${itemCounter}</td>
                        <td>${item.item}</td>
                        <td>${item.qty}</td>
                        <td>${item.price.toLocaleString()} ر.س</td>
                        <td>${item.total.toLocaleString()} ر.س</td>
                    </tr>
                `;
                itemCounter++;
            });

            const companyName = "مؤسسة [اسم ؤسستك هنا]"; // Replace with your actual company name
            const companyAddress = "العنوان: [عنوانك هنا]"; // Replace
            const companyPhone = "الجوال: [رقم جوالك هنا]"; // Replace
            const companyVAT = "الرقم الضيبي: [رقمك الضريب إن وجد]"; // Replace or remove

            // QR Code for ZATCA (Simplified - for actual compliance, use ZATCA SDK/API)
            // This is a placeholder. For real ZATCA e-invoicing, you need a cryptographic stamp.
            // const zatcaQRData = `Seller: ${companyName}\nVAT No: ${companyVAT.replace("الرقم الضريبي: ", "")}\nTimestamp: ${new Date(lastSalesData.items[0].timestamp).toISOString()}\nTotal: ${lastSalesData.total}\nVAT Amount: 0`; // Assuming no VAT for simplicity here
            // For a visual QR, you'd use a library. For now, we'll just mention it.


            let htmlContent = `
                <div class="invoice-header" style="background: #f0f0f0; color: #333; padding: 20px; text-align: center; border-bottom: 2px solid var(--primary-color);">
                    <h1 style="margin:0; font-size: 1.8em;">${companyName}</h1>
                    <p style="margin:5px 0;">${companyAddress} | ${companyPhone}</p>
                    ${companyVAT ? `<p style="margin:5px 0;">${companyVAT}</p>` : ''}
                </div>

                <div class="invoice-body" style="padding: 25px;">
                    <div class="invoice-title" style="font-size: 2.2em; margin-bottom:25px; color: var(--primary-color); border-bottom: none; padding-bottom: 0;">فاتور مبيعات${forPDF ? '' : ' (معاينة)'}</div>

                    <div class="invoice-info" style="font-size:0.95em;">
                        <div class="invoice-customer" style="text-align: right; border-right: none; padding-right:0; border-left: 3px solid var(--primary-color); padding-left: 1rem;">
                            <h3><u>بيانات العميل:</u></h3>
                            <p><strong>الاسم:</strong> ${customerName}</p>
                            ${customerPhone ? `<p><strong>الجوال:</strong> ${customerPhone}</p>` : ''}
                        </div>
                        <div class="invoice-company" style="text-align: right;">
                             <h3><u>تفاصيل الفاتورة:</u></h3>
                            <p><strong>رقم الفاتورة:</strong> ${lastSalesData.invoiceNumber}</p>
                            <p><strong>التاريخ:</strong> ${lastSalesData.date}</p>
                            <p><strong>الوقت:</strong> ${lastSalesData.time}</p>
                        </div>
                    </div>

                    <table class="invoice-table" style="margin: 25px 0; font-size:0.9em;">
                        <thead>
                            <tr>
                                <th>م</th>
                                <th>الصنف</th>
                                <th>الكمية (رأس)</th>
                                <th>سعر الوحدة (ر.س)</th>
                                <th>الإجمالي (ر.س)</th>
                            </tr>
                        </thead>
                        <tbody>
                            ${itemsHTML}
                        </tbody>
                        <tfoot>
                            <tr>
                                <td colspan="4" style="text-align:left; font-weight:bold; border-top: 2px solid var(--primary-color); padding-top:10px;">الإمالي قبل الضريبة (إن وجدت)</td>
                                <td style="font-weight:bold; border-top: 2px solid var(--primary-color); padding-top:10px;">${lastSalesData.total.toLocaleString()} ر.س</td>
                            </tr>
                            <tr>
                                <td colspan="4" style="text-align:left; font-weight:bold; font-size:1.2em; color:var(--primary-color);">المبلغ الإجمالي المستحق</td>
                                <td style="font-weight:bold; font-size:1.2em; color:var(--primary-color);">${lastSalesData.total.toLocaleString()} ريال سودي</td>
                            </tr>
                        </tfoot>
                    </table>

                    <div class="invoice-total" style="text-align:right; border-top:none; padding-top:0;">
                        <p style="font-size:1em;"><strong>طريقة ادفع:</strong> ${lastSalesData.payment}</p>
                        ${lastSalesData.note && lastSalesData.note.trim() !== "" ? `<p style="font-size:1em;"><strong>ملاحظات:</strong> ${lastSalesData.note.trim()}</p>` : ''}
                    </div>
                     <div class="invoice-footer" style="font-size:0.85em;">
                        <p>شكرًا لتعاملم معنا!</p>
                        <p>تم إنشاء هه الفاتورة بواسط نظام إدارة الأغنام - Nalhumaid.com</p>
                    </div>
                </div>`;
            if (forPDF) {
                // For PDF, wrap in a basic HTML structure for html2pdf
                return `<html><head><meta charset="UTF-8"><style>
                            body { font-family: 'DejaVu Sans', sans-serif; direction: rtl; } /* DejaVu Sans for Arabic */
                            .invoice-header, .invoice-body, .invoice-info, .invoice-customer, .invoice-company, .invoice-total, .invoice-footer { box-sizing: border-box; }
                            .invoice-table { width: 100%; border-collapse: collapse; }
                            .invoice-table th, .invoice-table td { border: 1px solid #ddd; padding: 8px; text-align: center; }
                            .invoice-table th { background-color: #f2f2f2; }
                            :root { --primary-color: #2e7d32; } /* Define primary color for PDF if not inherited */
                        </style></head><body>${htmlContent}</body></html>`;
            }
            return htmlContent;

        }


        // Show invoice modal (for viewing)
        function showInvoicePDF() {
            if (!lastSalesData) {
                showAlert('لا توجد بيانات ميعات لعرضها. يرجى إكمال عملية بيع أولاً.', 'warning', 'sales');
                return;
            }

            const invoiceHTML = generateInvoiceHTML(false); // false for modal view
            document.getElementById('invoice-print').innerHTML = invoiceHTML;
            document.getElementById('invoice-modal').style.display = 'flex';
        }


        // Close invoice modal
        function closeInvoiceModal() {
            document.getElementById('invoice-modal').style.display = 'none';
            document.getElementById('invoice-print').innerHTML = ''; // Clear content
        }


        // Print invoice from modal
        function printInvoice() {
            const printContent = document.getElementById('invoice-print').innerHTML;
            const originalContent = document.body.innerHTML;

            // Temporarily replace body content with invoice for printing
            // This is a common workaround but can have side effects on complex pages.
            // A better way for complex apps is an iframe or a dedicated print stylesheet.
            document.body.innerHTML = `<div class="invoice-print-area" style="font-family: 'Arial', sans-serif; direction:rtl;">${printContent}</div>`;
            window.print();
            document.body.innerHTML = originalContent; // Restore original content

            // Re-initialize event listeners or states if they were lost
            // This is a major downside of the innerHTML replacement method.
            // For this app, we might need to re-run parts of DOMContentLoaded or re-attach listeners.
            // For simplicity now, we'll assume it's mostly okay, but in a larger app, this is problematic.
            // A quick-fix might be to re-run essential setup functions.
            // Re-attach event listeners for dynamically added elements if necessary.
            // However, given the current structure, a page reload or re-navigation might be cleaner
            // if printing significantly disrupts the page state.

            // For now, let's just re-enable buttons if they were part of the original body.
            // And re-render products etc.
            loadItems(); // Reload items as they might be stored in currentItems array
            renderProducts();
            renderItems();
            // Reset tab to sales if it was changed
            // switchTab('sales'); // This might be too disruptive, user might want to stay on current tab
            // Re-attach specific listeners if known to be lost
            // Example: document.getElementById('sales-submit-btn').onclick = confirmSales;
            // This indicates a more robust print solution (iframe or print CSS) is better long-term.
            showAlert("تم إرسال الفاتورة للطباعة.", "success", "sales");

        }


        // Download Invoice as PDF
        function downloadInvoicePDF() {
            if (!lastSalesData) {
                showAlert('لا توجد بيانات مبيعات لتحميلها. يرجى إكمال عملية بيع أولاً.', 'warning', 'sales');
                return;
            }

            const invoiceHTMLForPDF = generateInvoiceHTML(true); // true for PDF generation
            const invoiceNumber = lastSalesData.invoiceNumber || 'فاتورة';
            const customerName = document.getElementById('customer-name').value.trim().replace(/\s+/g, '_') || 'عمي';


            const opt = {
              margin:       [0.5, 0.2, 0.5, 0.2], // top, left, bottom, right in inches
              filename:     `${invoiceNumber}_${customerName}.pdf`,
              image:        { type: 'jpeg', quality: 0.98 },
              html2canvas:  { scale: 2, useCORS: true, letterRendering: true, windowWidth: document.documentElement.offsetWidth }, // Added windowWidth
              jsPDF:        { unit: 'in', format: 'a4', orientation: 'portrait' },
              pagebreak:    { mode: ['avoid-all', 'css', 'legacy'] }
            };

            // Use a temporary element for html2pdf to ensure styles are applied correctly
            const tempElement = document.createElement('div');
            tempElement.innerHTML = invoiceHTMLForPDF;
            document.body.appendChild(tempElement); // Append to body for styles to be computed

            html2pdf().from(tempElement).set(opt).save().then(() => {
                document.body.removeChild(tempElement); // Clean up
                showAlert('تم تحميل الفاتورة كملف PDF بنجاح!', 'success', 'sales');
            }).catch(err => {
                document.body.removeChild(tempElement); // Clean up
                showAlert('حدث خطأ أثناء تحمي الفاتورة. ' + err.message, 'error', 'sales');
                console.error("PDF Generation Error: ", err);
            });
             closeInvoiceModal(); // Close modal after initiating download
        }



        // Send invoice via WhatsApp
        function sendInvoiceWhatsApp() {
            const phoneInput = document.getElementById('customer-phone');
            let phone = phoneInput.value.trim();

            if (!phone) {
                showAlert('يجى إدخال رقم جوال العميل', 'warning', 'sales');
                phoneInput.focus();
                return;
            }
             // Basic validation for Saudi numbers (966 followed by 9 digits, or 05 followed by 8 digits which becomes 9 after 0)
            if (!/^9665\d{8}$/.test(phone) && !/^05\d{8}$/.test(phone.startsWith('966') ? phone.substring(3) : phone )) {
                // showAlert('الرجاء إدخال رقم جوال سعودي صحيح (مثال: 9665XXXXXXXX أ 05XXXXXXXX)', 'warning', 'sales');
                // phoneInput.focus();
                // return; // Commented out to allow other formats if needed, but strict validation is better
            }
             // Ensure it has 966 prefix for WhatsApp link
            if (phone.startsWith('05')) {
                phone = '966' + phone.substring(1);
            } else if (phone.startsWith('5') && !phone.startsWith('966')) { // User typed 5xxxxxxxxx
                 phone = '966' + phone;
            }


            if (!lastSalesData) {
                showAlert('لا توجد بيانات مبيعات لإرسالها. يرجى إكمال عملية بيع أواً.', 'warning', 'sales');
                return;
            }

            const invoiceText = generateInvoiceText();
            const whatsappUrl = `https://wa.me/${phone}?text=${encodeURIComponent(invoiceText)}`;

            // Open WhatsApp in new tab
            window.open(whatsappUrl, '_blank');

            showAlert('تم تجهيز سالة الواتساب. يرجى إرسالها الآن. يمكنك أيضاً تحميل لفاتورة كـ PDF وإراقها.', 'success', 'sales');

            // Close modal if open
            closeInvoiceModal();
        }


        // Toggle Collapsible Invoice Section
        function toggleInvoiceSectionCollapsible() {
            const content = document.getElementById("invoice-content-collapsible");
            const arrow = document.getElementById("invoice-arrow-collapsible");
            const header = content.previousElementSibling; // Get the .card-header

            if (content.style.display === "none" || content.style.display === "") {
                content.style.display = "block";
                arrow.textContent = "⬆️";
                if (header && header.classList.contains('card-header')) {
                    header.style.borderBottom = "none"; // Remove border when expanded
                    header.style.marginBottom = "0"; // Remove margin when expanded
                }
            } else {
                content.style.display = "none";
                arrow.textContent = "⬇️";
                 if (header && header.classList.contains('card-header')) {
                    header.style.borderBottom = "1px solid var(--border-color)"; // Restore border
                    header.style.marginBottom = "1.5rem"; // Restore margin
                }
            }
        }


        // This function might be a remnant if you had another invoice toggle logic.
        // If 'invoice-card', 'invoice-content', 'invoice-arrow' IDs are only for the modal, this can be removed.
        // If they were for a different on-page invoice section that is now replaced by the collapsible one,
        // ensure it's no longer needed or update its logic.
        // For now, I'll assume the collapsible one is the primary on-page invoice interaction.
        /*
        function toggleInvoiceSection() { // This is the OLDER toggle function, ensure it's still needed or remove
            const content = document.getElementById("invoice-content"); // This ID might be used by the modal now.
            const arrow = document.getElementById("invoice-arrow");
            const card = document.getElementById("invoice-card");

            if (content && arrow && card) { // Check if elements exist
                if (content.style.display === "none" || content.style.display === "") {
                    content.style.display = "block";
                    arrow.textContent = "⬆️";
                    card.classList.add("expanded");
                } else {
                    content.style.display = "none";
                    arrow.textContent = "⬇️";
                    card.classList.remove("expanded");
                }
            }
        }
        */

    </script>
</body>
</html>