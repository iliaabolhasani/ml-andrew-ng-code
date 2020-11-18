---
title: "تابع هزینه شبکه عصبی"
date: 2020-09-30T17:52:45+03:30
draft: false
weight: 10
---

اجازه دهید برای شروع چند متغیر تعریف کنیم:

| متغیر |  |
| ------:| -----------:|
| $L$ | تعداد کل لایه ها در شبکه عصبی |
| $s_l$ | تعداد گره ها در لایه $l$ ام (بدون احتساب گره بایاس) |
| $K$ | تعداد کلاس های خروجی |

به یاد بیاورید که در شبکه های عصبی ممکن است تعداد گره های خروجی زیادی داشته باشیم.
ما $h_\Theta(x)_k$ را به عنوان یک فرضیه در نظر می‌گیریم، 
که منجر به خروجی $k^{th}$ می‌شود.

تابع هزینه ما برای شبکه های عصبی تعمیم تابعی است، که برای
[رگرسیون لجستیک در هفته سوم](https://mehrdad-dev.github.io/ml-andrew-ng/week3/cost-function/)
استفاده می‌کردیم.

به عنوان یادآوری، تابع هزینه برای
[رگرسیون لجستیک منظم](https://mehrdad-dev.github.io/ml-andrew-ng/week3/regularized-logistic-regression/)
به این صورت بود:

$$
J(\theta) = - \frac{1}{m} \sum_{i=1}^m [y^{(i)} log(h_\theta(x^{(i)})) + (1 - y^{(i)}) log(1 - h_\theta(x^{(i)}) )]  + \frac{\lambda}{2m} \sum_{j=1}^n \theta_j ^ 2
$$

که برای شبکه های عصبی کمی پیچیده تر خواهد شد:
$$
\begin{gather*} J(\Theta) = - \frac{1}{m} \sum_{i=1}^m \sum_{k=1}^K \left[y^{(i)}_k \log ((h_\Theta (x^{(i)}))_k) + (1 - y^{(i)}_k)\log (1 - (h_\Theta(x^{(i)}))_k)\right] + \frac{\lambda}{2m}\sum_{l=1}^{L-1} \sum_{i=1}^{s_l} \sum_{j=1}^{s_{l+1}} ( \Theta_{j,i}^{(l)})^2\end{gather*}
$$

![andrew-meme-1.jpg](../images/andrew-meme-1.jpg?width=25pc)

<p align="center" style="margin-top:-30px; margin-bottom: 50px; color: gray;" >
فقط یک ‌ذره 😂😂😅
<p>

ما برای چند گره خروجی خود، چند <span class="top-dict" data-tipso="nested summation">جمع تو در تو</span> اضافه کرده ایم.
در قسمت اول معادله قبل از براکت ها، ما یک جمع جدید برای تعداد گره های خروجی داریم:
$ \sum_{k=1}^K $

در قسمت <span class="top-dict" data-tipso="regularization">منظم سازی</span> بعد از براکت ها،
باید چند ماتریس تتا را حساب کنیم.

تعداد ستون ها در هر ماتریس تتای ما برابر است با تعداد گره های موجود در لایه ی آن
(به همراه گره بایاس)،
و تعداد ردیف های آن برابر است با تعداد گره های موجود در لایه بعدی اش
(به استثنای گره بایاس).

