# js-autotest
###   <h3 align="left">Автотест на JavaScript для сайта бронирования гостиниц <a href="https://automationintesting.online/">Restful Booker</a></h3>

```js

const puppeteer = require('puppeteer');
const URL_TEST = 'https://automationintesting.online/';
async function testResult() {
    console.log('Запуск браузера');
    const browser = await puppeteer.launch({headless: false, slowMo: 100});
    console.log('Создание новой вкладки в браузере');
    const page = await browser.newPage();
    await page.setViewport({width: 1920, height: 1080});
    console.log('Переход по ссылке');
    await page.goto(URL_TEST);
    console.log('Шаг 1: ввод в поле Name');
    const nameInput = await page.$('#name');
    await nameInput.type('Александра');
    console.log('Шаг 2: ввод в поле Email');
    const emaiInput = await page.$('#email');
    await emaiInput.type('test@test.ru');
    console.log('Шаг 3: ввод в поле Phone');
    const phoneInput = await page.$('#phone');
    await phoneInput.type('+79000000000');
    console.log('Шаг 4: ввод в поле Subject');
    const subjectInput = await page.$('#subject');
    await subjectInput.type('Вопрос');
    console.log('Шаг 5: ввод в поле Message');
    const descriptionInput = await page.$('#description');
    await descriptionInput.type('Напишите мне на почту');
    console.log('Шаг 6: клик на кпоку');
    const btnSubmit = await page.$('#submitContact');
    await btnSubmit.click();
    await page.screenshot({path:'testResult.png'});
    console.log('Закрытие браузера');
    await browser.close();
}

testResult();
```
