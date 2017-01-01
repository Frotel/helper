# کلاس کمکی وب سرویس ثبت سفارش فروتل
<div dir="rtl">
با استفاده از این کلاس شما به راحتی می توانید از وب سرویس های ثبت سفارشات فروتل استفاده کنید.
</div>
## متدها

| توضحیات|متد |
|---: | ---:|
| هزینه خدمات فروتل را برمیگرداند|frotelService |
|<div dir="rtl"> هزینه پست یک مرسوله را محاسبه می کند (مخصوص فروشندگان)</div>|fPrice |
|<div dir="rtl"> محاسبه هزینه پست یک مرسوله براساس چندین روش ارسال و پرداخت (مخصوص فروشندگان)</div>|getPrices |
| تفکیک سبد خرید براساس فروشنده و نوع محصولات|separationCart |
| روش های ارسال و پرداخت یک سبد خرید|costCalculation |
| ثبت سفارش محصولات فیزیکی|registerOrder |
| ثبت سفارش محصولات مجازی|registerOrderVirtual |
| ثبت سفارش محصولات خدماتی|registerOrderService |
| رهگیری یک سفارش|tracking |
| دریافت فرم ارجاع به بانک برای پرداخت نقدی سفارش|pay |
| بررسی وضعیت پرداخت|checkPay |
| بررسی کد کوپن|checkCoupon |

## ثابت ها

|توضحیات|ثابت|
|---:|---:|
|<div dir="rtl">پرداخت هزینه سفارش به صورت پرداخت در محل (COD)</div>|BUY_COD|
|<div dir="rtl">پرداخت هزینه سفارش به صورت نقدی (آنلاین)</div>|BUY_ONLINE|
|ارسال سفارش به صورت پست پیشتاز|DELIVERY_PISHTAZ|
|ارسال سفارش به صورت پست سفارشی|DELIVERY_SEFARESHI|
|<div dir="rtl">ارسال سفارش به صورت ارسال شخصی و با هزینه ثابت (مناسب برای پیاده سازی ارسال به صورت پیک موتوری یا ارسال توسط خود فروشگاه)</div>|DELIVERY_FIXED|

## نحوه استفاده

<div dir="rtl">
استفاده از این کلاس بسیار راحت است.
</div>

```php
require_once('frotel_helper.php');
$frotel = new frotel_helper(WEBSERVICE_URL, YOUR_API_KEY);
```
<div dir="rtl">
برای فراخونی هر یک از متدهای وب سرویس کافیست آن متد را از شئی جدیدی که ساختید صدا بزنید.
</div>

```php
try {
    $result = $frotel->frotelService();
    echo 'Frotel Service : '.$result;
} catch (FrotelWebserviceException $e) {
    // در این قسمت خطایی که وب سرویس برگردانده قابل دسترسی است
    echo 'Error ';
    echo $e->getMessage();
    // var_dump($frotel->getErrors());
} catch (FrotelResponseException $e) {
    // زمانی که وب سرویس قطع باشد و یا پاسخ مناسبی به درخواست ندهد این قسمت اجرا می شود
    echo 'Fatal Error ';
    echo $e->getMessage();
}
```
