---
title: "طبقه بندی"
date: 2020-09-10T12:51:11+04:30
draft: false
weight : 20
---

### <span class="top-dict" data-tipso="logistic regression">رگرسیون لجستیک</span>

اینجا از مسائل رگرسیون به مسائل طبقه بندی
می‌رویم، اما با اسم رگرسیون لجستیک گیج نشوید!
این اسم به دلایل تاریخی نامگذاری شده که در واقع
رویکردی برای حل مسائل طبقه بندی است نه رگرسیون!

![image86.png](../images/image86.png?width=18pc)

### <span class="top-dict" data-tipso="binary classification">طبقه دودویی</span>

به جای اینکه خروجی یعنی $y$  مقداری پیوسته در یک
محدوده باشد، فقط $0$ یا $1$ است، یعنی : $ y \in \text{{0,1}} $


به طوری که معمولا به $0$، negative class   و به $1$ هم
positive class می‌گوییم، اما شما آزاد هستید که هر
اسم دلخواهی را برای نام‌گذاری آن ها انتخاب کنید!

فعلا فقط دو تا کلاس داریم که به این نوع از مسئله
طبقه بندی دودویی می‌گوییم.

فرض کنید از رگرسیون خطی استفاده کنیم و نتیجه
تمام پیش بینی های بیشتر از $0.5$ را به عنوان 1 در
نظر بگیریم (نگاشت کنیم) ، و هم چنین تمام موارد
کوچکتر از $0.5$ را $0$ در نظر بگیریم.

<!-- 
**آیا این متد برای مسائل طبقه بندی دودویی خوب است؟**

{{% expand "برای پاسخ کلیک کن" %}}
naghes
{{% /expand %}} -->


### ارائه فرضیه

تابع فرضیه ما باید به این شکل باشد:

$$ h_\theta(x) = g(\theta^T x)  \hspace{2cm} 0 \leqslant h_\theta(x) \leqslant 1  $$

$$ g(z) = \frac{1}{1 + e^{-z}} \hspace{2cm} z = \theta^Tx $$

که به این فرم جدید **تابع <span class="top-dict" data-tipso="sigmoid">سیگموئید</span>** یا **تابع لجستیک**
می‌گوییم.


{{% notice note %}}
کار با نمودار تعاملی تابع سیگموئید:
http://desmos.com/calculator/bgontvxotm
{{% /notice %}}


تابع $g(z)$ در اینجا اعداد حقیقی را به عددی بین $0$ و
$1$ نگاشت می‌کند.

$h_\theta(x)$ به ما احتمال اینکه خروجی ما $1$ است را می‌دهد
برای مثال $h_\theta(x) = 0.7$ احتمال 70 درصدی را به ما
می‌دهد که خروجی $1$ باشد.

و احتمال اینکه پیش بینی ما در کلاس $0$ باشد متمم
احتمال کلاس 0 است، که اینجا $\text{30%} $ می‌شود.

$$ h_\theta(x)  = P (y=1 | x;\theta) =  1 - P (y = 0 | x;\theta) $$
$$ P (y=0 | x;\theta) + P (y=1 | x;\theta) = 1 $$


### <span class="top-dict" data-tipso="decision boundary">مرز تصمیم گیری</span> 

برای مجزا کردن کلاس های $0$ و $1$ طبقه بندی باید
خروجی تابع فرضیه را به این صورت تبدیل کنیم:

$$ h_\theta(x) \geqslant 0.5 \rightarrow y = 1 \hspace{2cm} h_\theta(x) < 0.5  \rightarrow  y = 0  $$

نحوه عملکرد تابع لجستیکی $g$ ما به این صورت است
که وقتی ورودی آن بزرگتر یا برابر 0 باشد، خروجی
آن بزرگ تر یا مساوی $0.5$ می‌شود:

$$ g(z) \geqslant 0.5 $$
$$ \text{ when } z \geqslant 0 $$


به یاد داشته باشید که:
$$z = 0, e^0 = 1 \Rightarrow g(z) = \frac{1}{2} $$
$$ z \rightarrow \infty, e^{-\infty} \rightarrow 0 \Rightarrow  g(z) = 1 $$
$$ z \rightarrow -\infty, e^{\infty} \rightarrow \infty \Rightarrow  g(z) = 0 $$

و اگر ورودی تابع g ،$ \theta^T x $ باشد به این معنی است که:

$$ h_\theta(x) = g(\theta^T x) \geqslant 0.5 \hspace{1.5cm} \text{when } \theta^T x \geqslant 0 $$

حالا می‌توانیم بگوییم که:

$$ \theta^T x \geqslant 0 \Rightarrow y = 1 \hspace{1cm} \theta^T x < 0  \Rightarrow  y = 0  $$

مرز تصمیم گیری، خطی است که قسمتی که 1=y است 
را از قسمت های 0=y جدا می‌کند، که این خط توسط
تابع فرضیه ساخته می‌شود.
