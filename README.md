# کلاس کمکی وب سرویس ثبت سفارش فروتل
<div dir="rtl">
با استفاده از این کلاس شما به راحتی می توانید از وب سرویس های ثبت سفارشات فروتل استفاده کنید.
</div>
## متدها

|متد | توضحیات|
|---: | ---:|
|frotelService | هزینه خدمات فروتل را برمیگرداند|
|fPrice | هزینه پست یک مرسوله را محاسبه می کند (مخصوص فروشندگان)|
|getPrices | محاسبه هزینه پست یک مرسوله براساس چندین روش ارسال و پرداخت (مخصوص فروشندگان)|
|separationCart | تفکیک سبد خرید براساس فروشنده و نوع محصولات|
|costCalculation | روش های ارسال و پرداخت یک سبد خرید|
|registerOrder | ثبت سفارش محصولات فیزیکی|
|registerOrderVirtual | ثبت سفارش محصولات مجازی|
|registerOrderService | ثبت سفارش محصولات خدماتی|
|tracking | رهگیری یک سفارش|
|pay | دریافت فرم ارجاع به بانک برای پرداخت نقدی سفارش|
|checkPay | بررسی وضعیت پرداخت|
|checkCoupon | بررسی کد کوپن|

## ثابت ها

|ثابت|توضحیات|
|---:|---:|
|BUY_COD| پرداخت هزینه سفارش به صورت پرداخت در محل (COD)|
|BUY_ONLINE|پرداخت هزینه سفارش به صورت نقدی (آنلاین)|
|DELIVERY_PISHTAZ|ارسال سفارش به صورت پست پیشتاز|
|DELIVERY_SEFARESHI|ارسال سفارش به صورت پست سفارشی|
|DELIVERY_FIXED|ارسال سفارش به صورت ارسال شخصی و با هزینه ثابت (مناسب برای پیاده سازی ارسال به صورت پیک موتوری یا ارسال توسط خود فروشگاه)|

## نحوه استفاده

<div dir="ltr">
استفاده از این کلاس بسیار راحت است.
</div>

```php
require_once('frotel_helper.php');
$frotel = new frotel_helper(WEBSERVICE_URL, YOUR_API_KEY);
`````
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
````
