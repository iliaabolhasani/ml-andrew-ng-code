---
title: "رگرسیون خطی منظم"
date: 2020-09-13T12:59:40+04:30
draft: false
weight: 90
---

ما می‌توانیم منظم سازی را هم برای رگرسیون خطی و هم برای رگرسیون لجستیک استفاده کنیم.
که اینجا ابتدا رگرسیون خطی را بررسی می‌کنیم.

### گرادیان کاهشی

گرادیان کاهشی را اصلاح می‌کنیم تا $\theta_0$ را از بقیه پارامتر ها جدا کنیم،
زیرا نمی‌خواهیم تاثیر $\theta_0$ را کاهش دهیم و از بین ببریم:

$$
\begin{align*} & \text{Repeat}\ \lbrace \newline & \ \ \ \ \theta_0 := \theta_0 - \alpha\ \frac{1}{m}\ \sum_{i=1}^m (h_\theta(x^{(i)}) - y^{(i)})x_0^{(i)} \newline & \ \ \ \ \theta_j := \theta_j - \alpha\ \left[ \left( \frac{1}{m}\ \sum_{i=1}^m (h_\theta(x^{(i)}) - y^{(i)})x_j^{(i)} \right) + \frac{\lambda}{m}\theta_j \right] &\ \ \ \ \ \ \ \ \ \ j \in \lbrace 1,2...n\rbrace\newline & \rbrace \end{align*}
$$

قسمت $\frac{\lambda}{m}\theta_j$ منظم سازی ما را انجام می‌دهد.
و با یک مقدار دستکاری می‌توانیم $\theta_j$ را به این صورت نشان دهیم:

$$
\theta_j := \theta_j(1 - \alpha \frac{\lambda}{m} ) - \alpha \frac{1}{m} \sum_{i = 1}^m (h_\theta(x^{(i)}) - y^{(i)}) x_j ^ {(i)}
$$

قسمت اول معدله یعنی $1 - \alpha \frac{\lambda}{m}$
همیشه کم از $1$ خواهد بود، و به طور چشمی می‌بینیم که مقدار 
$\theta_j$ را در هر بروزرسانی کمتر می‌کند.

توجه داشته باشید که قسمت دوم دقیقا مثل قبل است.


### معادله نرمال

حالا منظم سازی را با یک روش جایگزین و بدون نیاز به تکرار (non-iterative) یعنی معادله نرمال بررسی می‌کنیم.

برای این کار معادله ما شبیه به معادله اصلی است، با این تفاوت که یک بخش جدید در داخل پرانتز اضافه می‌کنیم:

$$
\begin{align*}& \theta = \left( X^TX + \lambda \cdot L \right)^{-1} X^Ty \newline& \text{where}\ \ L = \begin{bmatrix} 0 & & & & \newline & 1 & & & \newline & & 1 & & \newline & & & \ddots & \newline & & & & 1 \newline\end{bmatrix}\end{align*}
$$

L یک ماتریس است که به صورت مورب از قسمت بالا سمت چپ با $0$ شروع شده و تا انتهای  بخش مورب
$1$ است.
و سایر خانه های ماتریس نیز مقدار $0$ دارند، که ابعاد آن 
$(n+1) \times (n+1)$ است.

در واقع یک <span class="top-dict" data-tipso="identity matrix">ماتریس همانی</span> است،
(اگر چه که شامل $x_0$ نمی‌شود)
که در عدد حقیقی لامبدا ضرب شده است.

**به خاطر بیاورید که:**

$$
\text{if  } m < n \text{ then  } X^TX
$$
<span class="top-dict" data-tipso="non-invertible">وارون ناپذیر</span> بود.
اگر چه وقتی ما قسمت $\lambda . L $ را اضافه می‌کنیم،
سپس $ X^TX + \lambda . L$ وارون پذیر می‌شود.