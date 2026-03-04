# Практика 5
Осуществлено тестирование API карты. 

Написаны скрипты
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response time is less than 2000ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(2000);
});

const expectedName = pm.variables.get("NAME");
const expectedSurname = pm.variables.get("SURNAME");
const expectedBirthdate = pm.variables.get("BIRTHDATA");
const expectedPatronymic = pm.variables.get("PATRONYMIC");


const expectedPhone = pm.variables.get("PHONE");
const expectedPhoneCleaned = expectedPhone.replace(/[^\d+]/g,'');

pm.test(`Name is ${expectedName}`, function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.data.name).to.eql(expectedName);
});

pm.test(`Surname is ${expectedSurname}`, function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.data.surname).to.eql(expectedSurname);
});

pm.test(`Patronymic is ${expectedPatronymic}`, function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.data.patronymic).to.eql(expectedPatronymic);
});

pm.test(`Phone is ${expectedPhoneCleaned}`, function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.data.telephone).to.eql(expectedPhoneCleaned);
});

<img width="2880" height="1168" alt="image" src="https://github.com/user-attachments/assets/2a65c3ac-04bf-45c4-bb23-982b29b32c12" />



