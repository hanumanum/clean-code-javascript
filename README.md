# clean-code-javascript

 :heavy_exclamation_mark: թարգմանությունը ընթացքի մեջ է, սակայն դուք արդեն կարող եք կարդալ որոշ հատվածներ։ Նաև շատ բան կարելի է հասկանալ կոդի կտորների *Լավ/Վատ* համեմատականներից։
 
 :heavy_exclamation_mark: թարգմանությունը ունի թերություններ, սխալներ և վրիպակներ։ Խմբագրումները, ուղղումները և առաջարկները բնականաբար ընդունվում են ։)

## Բովանդակություն
  1. [Ներածություն](#Ներածություն)
  2. [Փոփոխականներ](#Փոփոխականներ)
  3. [Ֆունկցիաներ](#Ֆունկցիաներ)
  4. [Օբյեկտներ և տվյալների ստրուկտուրաներ](#Օբյեկտներ-և-տվյալների-ստրուկտուրաներ)
  5. [Կասներ](#Կլասներ)
  6. [SOLID](#solid)
  7. [Տեստավորում](#Տեստավորում)
  8. [Concurrency](#concurrency)
  9. [Սխալների մշակում](#Սխալների-մշակում)
  10. [Ֆորմատավորում](#Ֆորմատավորում)
  11. [Մեկնաբանություններ](#Մեկնաբանություններ)
  12. [Թարգմանություններ](#Թարգմանություններ)

## Ներածություն
![Humorous image of software quality estimation as a count of how many expletives
you shout when reading code](http://www.osnews.com/images/comics/wtfm.jpg)

Ծրագրային ապահովման սկզբունքները, Ռոբերտ Մարտինի [*Պարզ կոդ*](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882) գրքից,
հարմարեցված JavaScript լեզվի համար: Սա ոճի ուղեցույց չի։ Սա JavaScript֊ով [ընթեռնելի, վերաօգտագործելի և վերափոխելի](https://github.com/ryanmcdermott/3rs-of-software-architecture) ծրագրային ապահովում գրելու ուղեցույց է։

Ոչ բոլոր սկզբունքներին է պետք խիստ հետևել։ Ավելին, ոչ բոլորն են համընդհանուր ընդունված։ Այս ուղղեցույցը ոչ ավելին է, քան *Պարզ կոդ* գրքի հեղինակների տարիներով հավաքված կոլեկտիվ փորձի արտացոլումը։

ԾԱ արհեստը միայն 50 տարեկան է և մենք դեռ շատ բան ենք սովորում։ Հնարավոր է, որ երբ ծրագրային ապահովման ճարտարապետությունը նույնքան ծեր լինի, որքան սովորական ճարտարապետությունը, մենք ավելի խիստ կանոնների կհետևենք։ Իսկ հիմա, դարձրու այս ուղեցույցը անկյունաքար, որով կբարձրացնես քո և քո թիմի գրած Javascript կոդի որակը։

Մի բան էլ․ սրանց իմացությունը քեզ անմիջապես չի դարձնի ավելի լավ ԾԱ նախագծող և սրանցով տարիներ շարունակ աշխատելը չի նշանակում, որ դու սխալներ չէս անի։ Կոդի ամեն կտորը սկսվում է որպես փոքր նախագիծ․ այն ձևավորվում է խոնավ կավի պես հասնելով իր վերջնական ձևին։ Վերջապես մենք հեռացնում ենք անկատարությունը մեր ընկերների հետ այն վերանայելիս։ Մի՛ ինքնախարազանվիր սկզբնական և փոփոխության ենթակա
ծրագրերի համար։ Խարազանի՛ր ծրագրերը։


## **Փոփոխականներ**
###  Օգտագործիր իմաստալից և արտասանելի փոփոխականների անուններ

**Վատ:**
```javascript
const yyyymmdstr = moment().format('YYYY/MM/DD');
```

**Լավ:**
```javascript
const currentDate = moment().format('YYYY/MM/DD');
```
**[⬆ վեր](#Բովանդակություն)**

### Օգտագործիր նույն բառարանը նույն փոփոխականների տեսակի համար

**Վատ՝**
```javascript
getUserInfo();
getClientData();
getCustomerRecord();
```

**Լավ՝**
```javascript
getUser();
```
**[⬆ վեր](#Բովանդակություն)**

### Օգտագործիր որոնելի փոփոխականների անուններ
Մենք պիտի ավելի շատ կոդ կարդանք, քան գրենք։ Կարևոր է մեր կոդը այնպես գրել, որ
այն լինի ընթեռնելի և որոնելի։ Ծրագրում փոփոխականների լավ անունները կօգնեն հասկանալ
ծրագրի նշանակությունը այն մարդկանց, ովքեր կցանկանան ուսումնասիրել քո ծրագրիը։ 
Փոփոխականների անունները որոնելի գրիր։ Հետևյալ գործիքները՝ 
[buddy.js](https://github.com/danielstjules/buddy.js), 
[ESLint](https://github.com/eslint/eslint/blob/660e0918933e6e7fede26bc675a0763a6b357c94/docs/rules/no-magic-numbers.md)
կօգնեն հայտնաբերել չանվանված հաստատունները։

**Վատ՝**
```javascript
// Ինչ թիվ է 86400000֊ը?
setTimeout(blastOff, 86400000);

```

**Լավ՝**
```javascript
// Հայտարարիր դրանք որպես հաստատուններ
const MILLISECONDS_IN_A_DAY = 86400000;

setTimeout(blastOff, MILLISECONDS_IN_A_DAY);

```
**[⬆ վեր](#Բովանդակություն)**

### Օգտագործիր փոփոխականների "բացատրող" անուններ
**Վատ՝**
```javascript
const address = 'One Infinite Loop, Cupertino 95014';
const cityZipCodeRegex = /^[^,\\]+[,\\\s]+(.+?)\s*(\d{5})?$/;
saveCityZipCode(address.match(cityZipCodeRegex)[1], address.match(cityZipCodeRegex)[2]);
```

**Լավ՝**
```javascript
const address = 'One Infinite Loop, Cupertino 95014';
const cityZipCodeRegex = /^[^,\\]+[,\\\s]+(.+?)\s*(\d{5})?$/;
const [, city, zipCode] = address.match(cityZipCodeRegex) || [];
saveCityZipCode(city, zipCode);
```
**[⬆ վեր](#Բովանդակություն)**

### Խուսափիր մտավոր կապ ստեղծելուց (Avoid Mental Mapping)
Բացահայտը ավելի է քան թաքնվածը։

**Վատ՝**
```javascript
const locations = ['Austin', 'New York', 'San Francisco'];
locations.forEach((l) => {
  doStuff();
  doSomeOtherStuff();
  // ...
  // ...
  // ...
  // սպասիր, ի՞նչ է l-ը
  dispatch(l);
});
```

**Լավ՝**
```javascript
const locations = ['Austin', 'New York', 'San Francisco'];
locations.forEach((location) => {
  doStuff();
  doSomeOtherStuff();
  // ...
  // ...
  // ...
  dispatch(location);
});
```
**[⬆ վեր](#Բովանդակություն)**

### Խուսափիր ավելորդ բովանդակությունից
Եթե քո կլասը/օբյեկտը քեզ որևէ բան է ասում, մի կրկնիր նույնը փոփոխականների անուններում։

**Վատ՝**
```javascript
const Car = {
  carMake: 'Honda',
  carModel: 'Accord',
  carColor: 'Blue'
};

function paintCar(car) {
  car.carColor = 'Red';
}
```

**Լավ՝**
```javascript
const Car = {
  make: 'Honda',
  model: 'Accord',
  color: 'Blue'
};

function paintCar(car) {
  car.color = 'Red';
}
```
**[⬆ վեր](#Բովանդակություն)**

### Օգտագործիր արգումենտների սկզբնարժեքավորում, խուսափիր պայմանների միջոցով սկզբնական արժեքներ դնելուց
Սկզբնարժեքավորված արգումենտները հաճախ ավելի հասկանալի են քան մյուս տարբերակները կարճ արժեքավորումը։ Նաև 
Իմացիր, որ եթե կարճ արժեքավորում օգտագործես, ապա քո ֆունկցիան կտրամադրի լռությամբ արժեքներ միայն արգումենտի `undefined` արժեքի դեպքում։
Արգումենտների այլ "կեղծոտ" արժեքները, ինչպիսիք են `''`, `""`, `false`, `null`, `0`, և 
`NaN` , չեն փոխարինվի լռությամբ արժեքներով։

**Վատ՝**
```javascript
function createMicrobrewery(name) {
  const breweryName = name || 'Hipster Brew Co.';
  // ...
}

```

**Լավ՝**
```javascript
function createMicrobrewery(name = 'Hipster Brew Co.') {
  // ...
}

```
**[⬆ վեր](#Բովանդակություն)**

## **Ֆունկցիաներ**
### Ֆունկցիաների արգումենտներ (իդեալական տարբերակում 2 կամ պակաս)
Ֆունկցիայի արգումենտների քանակը սահմանափակելը շատ կարևոր է, որովհետև դա հեշտացնում է 
ֆունկցիայի աշխատանքի տեստավորումը։ Երեքից ավել արգումենտներ ունենալը բերում է այն  տարբերակների բազմացմանը
, որոնք պետք է ստուգել յուրաքանչյուր արգումենտի հետ։

Մեկ կամ երկու արգումենտ ունենալը իդեալական է իսկ երեք արգումենտից հնարավորության դեպքում պետք է խուսափել։
Դրանցից ավելը պետք է խմբավորել։ Հաճախակի, եթե ունես երկու արգումենտից ավել, դա նշանակում է, 
որ ֆունկցիադ հավանաբար ավելի շատ բան է անում, քան անհրաժեշտ է։ Եթե ոչ, ապա օբյեկտը որպես արգումենտ փոխանցելը 
ավելի ճիշտ տարբերակ է։

Քանի որ, JavaScript֊ը թույլատրում է ընթացքից օբյեկտներ ստեղծել (առանց նախապես class-ով նախագծելու), կարող ես 
օգտագործել օբյեկտ եթե ունես շատ արգումենտների կարիք։

Ֆունկցիայի պահանջած հատկանիշները ակնհայտ սարքելու համար, կարող ես օգտագործել ES2015/ES6֊ից
դեստրուկտուրիզացիայի սինտաքսը (destructuring syntax) , այն ունի որոշակի առավելություններ՝

1. Երբ մեկը նայում է ֆունկցիայի սիգնատուրային , միանգամից ակնհայտ է դառնում թե ինչ արգումենտներ են օգտագործվում
2. Դեստրուկտուրիզացիան կլոնավորում է ֆունկցիային փոխանցված արգումենտի պրիմիտիվ արժեքները։ Սա օգնում է խուսափել կողմնակի էֆեկտներից։
ՀԻՇԻՐ։ Դեստրուկտուրացված արժեքների օբյեկտները և զանգվածները չէն կլոնավորվում։

3. Լինթերները կարող են նախազգուշացնել չօգտագործված հատկանիշների մասին, ինչը անհնար կլինի առանց դեստրուկտուրիզացիայի։



**Վատ՝**
```javascript
function createMenu(title, body, buttonText, cancellable) {
  // ...
}
```

**Լավ՝**
```javascript
function createMenu({ title, body, buttonText, cancellable }) {
  // ...
}

createMenu({
  title: 'Foo',
  body: 'Bar',
  buttonText: 'Baz',
  cancellable: true
});
```
**[⬆ վեր](#Բովանդակություն)**


### Ֆունկցիան պիտի միայն մի բան անի
Սա ԾԱ նախագծման կարևորագույն սկզբունքն է։ Մեկից ավելի բան անող ֆունկցիաները դժվար են նախագծվում, տեստավորվում և նաև դրանց մասին մտածելը նույնպես դժվարանում է։ Եթե կարող ես յուրաքանչյուր գործողություն իզոլացնել մեկ ֆունկցիայի ներսում, ապա այդ ֆունկցիաները հեշտ փոփոխելի (refactoring) են դառնում և քո ծրագիրը ավելի հեշտ է կարդացվում։ Եթե այս ուղեցույցից վերցնես միայն այս կանոնը, դու արդեն առաջ կանցնես բազմաթիվ ծրագրավորողներից։
 


**Վատ՝**
```javascript
function emailClients(clients) {
  clients.forEach((client) => {
    const clientRecord = database.lookup(client);
    if (clientRecord.isActive()) {
      email(client);
    }
  });
}
```

**Լավ՝**
```javascript
function emailActiveClients(clients) {
  clients
    .filter(isActiveClient)
    .forEach(email);
}

function isActiveClient(client) {
  const clientRecord = database.lookup(client);
  return clientRecord.isActive();
}
```
**[⬆ վեր](#Բովանդակություն)**

### Ֆունկցիաների անունները պիտի ասեն, թե ինչ է ֆունկցիան անում
**Վատ՝**
```javascript
function addToDate(date, month) {
  // ...
}

const date = new Date();

// Դժվար է ֆունկցիայի անունից հասկանալ , թե ինչ է այն ավելացնում, օ՞ր, ամի՞ս, ի՜՞նչ ․․․
addToDate(date, 1);
```

**Լավ՝**
```javascript
function addMonthToDate(month, date) {
  // ...
}

const date = new Date();
addMonthToDate(1, date);
```
**[⬆ վեր](#Բովանդակություն)**

### Ֆունկցիան պիտի արտահայտի աբստրակցիայի միայն մեկ մակարդակ
Աբստրակցիայի մեկ մակարդակից ավելին ունեցող ֆունկցիան, հավանաբար, անում է ավելին քան պետք է։
Ֆունկցիան բաժանելը մի քանի ֆունկցիաների օգնում է ֆունկցիաների վերաօգտագործելիությանը և հեշտ տեստավորմանը։


**Վատ՝**
```javascript
function parseBetterJSAlternative(code) {
  const REGEXES = [
    // ...
  ];

  const statements = code.split(' ');
  const tokens = [];
  REGEXES.forEach((REGEX) => {
    statements.forEach((statement) => {
      // ...
    });
  });

  const ast = [];
  tokens.forEach((token) => {
    // lex...
  });

  ast.forEach((node) => {
    // parse...
  });
}
```

**Լավ՝**
```javascript
function parseBetterJSAlternative(code) {
  const tokens = tokenize(code);
  const ast = lexer(tokens);
  ast.forEach((node) => {
    // parse...
  });
}

function tokenize(code) {
  const REGEXES = [
    // ...
  ];

  const statements = code.split(' ');
  const tokens = [];
  REGEXES.forEach((REGEX) => {
    statements.forEach((statement) => {
      tokens.push( /* ... */ );
    });
  });

  return tokens;
}

function lexer(tokens) {
  const ast = [];
  tokens.forEach((token) => {
    ast.push( /* ... */ );
  });

  return ast;
}
```
**[⬆ վեր](#Բովանդակություն)**

### Հեռացրու կրկնվող կոդը
Արա առավելագույնը կրկնվող կոդից խուսափելու համար։ Կրկնվող կոդը վատ է, որովհետև անրհաժեշտության դեպքում, փոփոխությունները անհրաժեշտ կլինի անել մեկից ավել տեղերում։ 

Պատկերացրու դու ռեստորան ունես և պահում ես տվյալներ բոլոր մթերքների մասին, բոլոր պոմիդորների, սոխերի, սխտորների, համեմունքների և այլն ․․․ Եթե ունենաս մի քանի ցանկ, ապա 
բոլոր այդ ցանկերը պիտի թարմանացվեն, երբ պոմիդորով որևէ ճաշատեսակ սարքես։ Միայն մեկ ցանկ ունենալու դեպքում միայն մի տեղ պիտի թարմացնես տվյալները։

Հաճախակի կոդը կրկնապատկվում է, որովհետև ունես իրարից մի քիչ տարբերվող բաներ, որոնք հիմնականում նույնն են, բայց նաև տարբերություններ կան։ Տարբերությունենրը ստիպում են քեզ երկու կամ ավել առանձին ֆունկցիաներ սարքել այդ երկու բաների համար։ Կրկնվող կոդը հեռացնելը նշանակում է, որ պետք է ստեղծել աբստրակցիայի այնպիսի մակարդակ, որը կկարողանա աշխատել այդ բաների խմբի հետ միայն մեկ ֆունկցիայի (մոդուլի,կլասսի) միջոցով:

Ճիշտ աբստրակցիա նկարագրելը կրիտիկական է, այդ պատճառով պետք է  հետևես *Կլասներ* բաժնում նկարագրված SOLID սկզբունքներին։ Վատ աբստրակցիան ավելի վատ է, քան կրկնվող կոդը․ զգույշ եղիր։ Մի կրկնիր ինքդ քեզ, հակառակ դեպքում կհայտնվես այնպիսի վիճակում, որ մեկ փոփոխության համար մի քանի տեղ պիտի կոդը փոփոխես։ 
 
**Վատ՝**
```javascript
function showDeveloperList(developers) {
  developers.forEach((developer) => {
    const expectedSalary = developer.calculateExpectedSalary();
    const experience = developer.getExperience();
    const githubLink = developer.getGithubLink();
    const data = {
      expectedSalary,
      experience,
      githubLink
    };

    render(data);
  });
}

function showManagerList(managers) {
  managers.forEach((manager) => {
    const expectedSalary = manager.calculateExpectedSalary();
    const experience = manager.getExperience();
    const portfolio = manager.getMBAProjects();
    const data = {
      expectedSalary,
      experience,
      portfolio
    };

    render(data);
  });
}
```

**Լավ՝**
```javascript
function showEmployeeList(employees) {
  employees.forEach((employee) => {
    const expectedSalary = employee.calculateExpectedSalary();
    const experience = employee.getExperience();

    const data = {
      expectedSalary,
      experience
    };

    switch (employee.type) {
      case 'manager':
        data.portfolio = employee.getMBAProjects();
        break;
      case 'developer':
        data.githubLink = employee.getGithubLink();
        break;
    }

    render(data);
  });
}
```
**[⬆ վեր](#Բովանդակություն)**

### Օբյեկտները սկզբարժեքավորիր Object.assign֊ի միջոցով

**Վատ՝**
```javascript
const menuConfig = {
  title: null,
  body: 'Bar',
  buttonText: null,
  cancellable: true
};

function createMenu(config) {
  config.title = config.title || 'Foo';
  config.body = config.body || 'Bar';
  config.buttonText = config.buttonText || 'Baz';
  config.cancellable = config.cancellable !== undefined ? config.cancellable : true;
}

createMenu(menuConfig);
```

**Լավ՝**
```javascript
const menuConfig = {
  title: 'Order',
  // 'body' բանալին չի արժեքավորվել
  buttonText: 'Send',
  cancellable: true
};

function createMenu(config) {
  config = Object.assign({
    title: 'Foo',
    body: 'Bar',
    buttonText: 'Baz',
    cancellable: true
  }, config);

  // config֊ը հիմա հավասաար է {title: "Order", body: "Bar", buttonText: "Send", cancellable: true}
  // ...
}

createMenu(menuConfig);
```
**[⬆ վեր](#Բովանդակություն)**


### Խուսափեք որպես ֆունկցիայի արգումենտ օգտագործել տրամաբանական փոփոխականներ

Տրամաբանական փոփոխականը որպես արգումենտ, օգտագործողին հուշում է, որ ձեր ֆունկցիան մեկից ավելի բաներ է անում։ Բայց լավ ֆունկցիան պետք է կատարի միայն մեկ բան։ Նման ֆունկցիաները կարող եք բաժանել երկու մասի։

**Վատ՝**
```javascript
function createFile(name, temp) {
  if (temp) {
    fs.create(`./temp/${name}`);
  } else {
    fs.create(name);
  }
}
```

**Լավ՝**
```javascript
function createFile(name) {
  fs.create(name);
}

function createTempFile(name) {
  createFile(`./temp/${name}`);
}
```
**[⬆ վեր](#Բովանդակություն)**

### Խուսափիր կողմնակի էֆեկտներից (մաս 1)
Եթե ֆունկցիան բացի արժեք վերցնելուց և վերադարձնելուց այլ բան է անում, ապա ասում են, որ այն ունի կողմնակի էֆետներ։ Կողմնակի էֆեկտները կարող են լինել՝
* որևէ գլոբալ փոփոխականի արժեքը փոխելը 
* ֆայլի մեջ տեղեկություներ գրելը
* պատահականորեն ձեր ամբողջ փողը անծանոթ մեկին ուղարկելը ։)

Հաճախ կարիք է լինում օգտագործել կողմնակի ազդեցություններ, ինչպիսիք են վերոշարադրյալները, քանի որ երբեմն պետք է գրել ֆայլի մեջ։ Նման դեպքերում դուք պետք է առանձնացնեք և կենտրոնացնեք ծրագրի այն մասերը որոնք ունեն կողմնակի ազդեցություն ու մի տեղից կատարել ֆայլիերի մանիպուլիացիան։ Մի ստեղծեք մի քանի ֆունկցիա միևնույն ֆայլի վրա գրելու համար։ Գրեք մեկ և միայն մեկ service (ծառայություն) որն անում է այդ գորոծղությունը։

Հիմնական իմաստն այն է, որ չստեղծեք ընդհանուր օգտագործման օբյեկտներ առանց դրա վրա կառուցելու ձևափոխությունների կենտրոնացված կլաս կամ օբյեկտ։ Քանի որ նման դեպքում, ծրագրի տարբեր մասերում կարող է ձևափոխվել ձեր օբյեկտը և դուք ստանաք անկանխատեսելի արդյունքներ։ Եթե կարողանաք խուսափել այս տարածված խնդիրց, ապա շատ ավելի երջանիկ կլինեք, քան ծրագրավորողների մեծ մասը։

**Վատ՝**
```javascript
// Global variable referenced by following function.
// If we had another function that used this name, now it'd be an array and it could break it.
let name = 'Ryan McDermott';

function splitIntoFirstAndLastName() {
  name = name.split(' ');
}

splitIntoFirstAndLastName();

console.log(name); // ['Ryan', 'McDermott'];
```

**Լավ՝**
```javascript
function splitIntoFirstAndLastName(name) {
  return name.split(' ');
}

const name = 'Ryan McDermott';
const newName = splitIntoFirstAndLastName(name);

console.log(name); // 'Ryan McDermott';
console.log(newName); // ['Ryan', 'McDermott'];
```
**[⬆ վեր](#Բովանդակություն)**

### Խուսափիր կողմնակի էֆեկտներից (մաս 2)
JavaScript լեզվում տարրական տիպի տվյալները ֆունկցիաներին փոխանցվում են իրենց արժեքով, իսկ օբյեկտները/զանգվածները հղումով (by refreance)։ Օբյեկտների/զանգվածների դեպքում, եթե քո ֆունկցիան կատարում է փոփոխություն օրինակ զամբյուղում, ավելացնելով ապրանք, ապա մյուս ֆունկցիան որը կօգտագործի այդ զանգվածը կստանա փոփոխված տարբերակը։ Սա կարող է լավ լինել, սակայն կարող է նաև վատ լինել։ Պատկերացնենք վատ իրավիճակը։ 

Օգտատերը սեղում է "Գնել" կոճակը, որը կանչում է `purchase` ֆունկցիան, որը առաջացնում է ցանցային հարցում և ուղարկում է `cart` զանգվածը սերվերին։ Ցանցային վատ կապի պատճառով `purchase` ֆունկցիան շարունակում է փորձել ուղարկել հարցումը։ Ի՞նչ կլինի եթե օգտատերը միևնույն ժամանակ պատահաբար սեղմի "Ավելացնել զամբյուղին" կոճակը և ավելացնի ապրանք, որը նա չէր ցանկանում։ Եթե դա պատահի և ցանցային հարցումը սկսվի, գնելու ֆունկցիան կուղարկի նաև սխալմամբ ավելացված ապրանքը, որովհետև այն ունի հղում `cart` զանգվածին որը արդեն փոփոխված է `addItemToCart` ֆունկցիայի աշխատանքի պատճառով։

Լավագույն լուծումը կլինի այն, որ `addItemToCart` ֆունկցիան միշտ պատճենի `cart`֊ը, խմբագրի այն և վերադարձնի պատճենը։ Սա երաշխավորում է, որ ոչ մի այլ ֆունկցիա չի փոխի զամբյուղի արժեքը։ 

Երկու նախազգուշացում այս տեսանկյունի կապակցությամբ


  1. Կարող են լինել իրավիճակներ, երբ իրոք պետք կլինի փոփոխել մտնող օբյեկտը, սակայն եթե դու ընդունես վերընշված պրակտիկան, ապա կտեսնես, որ նմանատիպ իրավիճակները շատ հազվադեպ են։ Շատ բաներ կարելի է վերափոխել (refactoring) հեռացնելով կողմնակի էֆեկտները։
  
  2. Մեծ օբյեկտների պատճենումը կարող է շատ ծախսատար լինել արագագործության տեսանկյունից։ Բարեբախտաբար գործանականում դա մեծ խնդիր չի, որովհետև կան [լավ գրադարաններ](https://facebook.github.io/immutable-js/) որոնք այս տիպի ծրագրավորումը դարձում են ավելի արագ և ոչ այդքան ծախսատար (հիշողության տեսանկյունից) , քան ձեռքով օբյետները և զանգվածները պատճենելու ժամանակ։ 
  

**Վատ՝**
```javascript
const addItemToCart = (cart, item) => {
  cart.push({ item, date: Date.now() });
};
```

**Լավ՝**
```javascript
const addItemToCart = (cart, item) => {
  return [...cart, { item, date: Date.now() }];
};
```

**[⬆ վեր](#Բովանդակություն)**

### Մի գրիր գլոբալ ֆունկցիաներ
Գլոբալ փոփոխականները աղտոտելը վատ պրակտիկա է JavaScript֊ում, որովհետև դու կարող ես ունենալ բախում այլ գրադարանների հետ։ Եվ քո API֊ի օգտատերը ոչինչ չի իմանա, քանի դեռ իրական ծրագրում չի ստանա բացառություն (exeption in production): Արի մտածենք հետևյալ օրինակի վրա։ Ի՞նչ կլինի եթե դու ուզենաս ընդլայնել JavaScript-ի հարազատ(native) Array֊ը ստեղծելով `diff` մեթոդը, որը ցուցադրում է զանգվածների տարբերությունը։ Դու կարող ես գրել քո ֆունկցիան `Array.prototype`֊ի միջոցով, սակայն այն կարող է բախվել այլ գրադարանի նույնանուն ֆունկցիայի հետ, որը փորձում է անել նույն բանը։ Իսկ եթե մյուս գրադարանի `diff`֊ը որոնում է տարբերությունը զանգվածի առաջին և վերջին անդամների միջև։ Ահա թե ինչու է ավելի լավ ուղակի օգտագործել ES2015/ES6 կլասները և հեշտությամբ ընդլայնել `Array` օբյեկտը։

**Վատ՝**
```javascript
Array.prototype.diff = function diff(comparisonArray) {
  const hash = new Set(comparisonArray);
  return this.filter(elem => !hash.has(elem));
};
```

**Լավ՝**
```javascript
class SuperArray extends Array {
  diff(comparisonArray) {
    const hash = new Set(comparisonArray);
    return this.filter(elem => !hash.has(elem));
  }
}
```
**[⬆ վեր](#Բովանդակություն)**

### Նախընտրիր ֆունկցիոնալ ծրագրավորումը՝ ոչ իմպերատիվը
JavaScript֊ը ֆունկցիոնալ ծրագրավորման լեզու չի այն իմաստով, որով Haskell֊ն է, սակայն այն ունի ֆունկցիոնալ հատկանիշներ։ Ֆունկցիոնալ լեզուները կարող են լինել ավելի մաքուր և հեշտ տեստավորվող։ Նախընտրիր այս ոճը, երբ դա հնարավոր է։

**Վատ՝**
```javascript
const programmerOutput = [
  {
    name: 'Uncle Bobby',
    linesOfCode: 500
  }, {
    name: 'Suzie Q',
    linesOfCode: 1500
  }, {
    name: 'Jimmy Gosling',
    linesOfCode: 150
  }, {
    name: 'Gracie Hopper',
    linesOfCode: 1000
  }
];

let totalOutput = 0;

for (let i = 0; i < programmerOutput.length; i++) {
  totalOutput += programmerOutput[i].linesOfCode;
}
```

**Լավ՝**
```javascript
const programmerOutput = [
  {
    name: 'Uncle Bobby',
    linesOfCode: 500
  }, {
    name: 'Suzie Q',
    linesOfCode: 1500
  }, {
    name: 'Jimmy Gosling',
    linesOfCode: 150
  }, {
    name: 'Gracie Hopper',
    linesOfCode: 1000
  }
];

const totalOutput = programmerOutput
  .map(output => output.linesOfCode)
  .reduce((totalLines, lines) => totalLines + lines);
```
**[⬆ վեր](#Բովանդակություն)**

### Ինկապսուլացրու (Encapsulate) պայմանները

**Վատ՝**
```javascript
if (fsm.state === 'fetching' && isEmpty(listNode)) {
  // ...
}
```

**Լավ՝**
```javascript
function shouldShowSpinner(fsm, listNode) {
  return fsm.state === 'fetching' && isEmpty(listNode);
}

if (shouldShowSpinner(fsmInstance, listNodeInstance)) {
  // ...
}
```
**[⬆ վեր](#Բովանդակություն)**

### Խուսափիր բացասական պայմաններից

**Վատ՝**
```javascript
function isDOMNodeNotPresent(node) {
  // ...
}

if (!isDOMNodeNotPresent(node)) {
  // ...
}
```

**Լավ՝**
```javascript
function isDOMNodePresent(node) {
  // ...
}

if (isDOMNodePresent(node)) {
  // ...
}
```
**[⬆ վեր](#Բովանդակություն)**

### Խուսափիր պայմաններից
Սա կարծես անլուծելի մի բան լինի։ Առաջին անգամ սա լսելիս շատ մարդիկ ասում են․
"Ինպե՞ս կարող եմ անել որևէ բան առանց `if`֊ի"։ Պատասխանը այն է, որ շատ դեպքերում  
դու կարող ես օգտագործել բազմաձևությունը (պոլիմորֆիզմ) նույն խնդիրը լուծելու համար։
Հաճախ տրվող երկրորդ հարցն է՝ "լավ, բայց ինչի համար է դա պետք անել"։ Պատասխանը այն 
նախկինում սովորած մաքուր կոդի գաղափարներից մեկն է․ ֆունկցիան պիտի անի միայն մի բան։ 
Երբ քո ֆունկցիաները և կլասները ունեն `if`֊եր, դու ասում ես քո օգտատերերին, որ քո 
ֆունկցիան անում է մեկ բանից ավել։ Հիշիր ՝ ֆունկցիան պիտի անի միայն մեկ բան։

**Վատ՝**
```javascript
class Airplane {
  // ...
  getCruisingAltitude() {
    switch (this.type) {
      case '777':
        return this.getMaxAltitude() - this.getPassengerCount();
      case 'Air Force One':
        return this.getMaxAltitude();
      case 'Cessna':
        return this.getMaxAltitude() - this.getFuelExpenditure();
    }
  }
}
```

**Լավ՝**
```javascript
class Airplane {
  // ...
}

class Boeing777 extends Airplane {
  // ...
  getCruisingAltitude() {
    return this.getMaxAltitude() - this.getPassengerCount();
  }
}

class AirForceOne extends Airplane {
  // ...
  getCruisingAltitude() {
    return this.getMaxAltitude();
  }
}

class Cessna extends Airplane {
  // ...
  getCruisingAltitude() {
    return this.getMaxAltitude() - this.getFuelExpenditure();
  }
}
```
**[⬆ վեր](#Բովանդակություն)**

### Խուսափիր տիպերի ստուգումներից (մաս 1)
JavaScript֊ը տիպավորված չէ, ինչը նշանակում է, որ քո ֆունկցիաները կարող են ստանալ
ցանկացած տիպի արգումենտ։ Հաճախ դու տուժում ես այս ազատությունից և ստիպված ես լինում
ստուգել տիպերը ֆունկցիաների ներսում։ Կան շատ եղանակներ սրանից խուսափելու համար։
Առաջինը դիտարկիր հետևողական API֊ները։

**Վատ՝**
```javascript
function travelToTexas(vehicle) {
  if (vehicle instanceof Bicycle) {
    vehicle.pedal(this.currentLocation, new Location('texas'));
  } else if (vehicle instanceof Car) {
    vehicle.drive(this.currentLocation, new Location('texas'));
  }
}
```

**Լավ՝**
```javascript
function travelToTexas(vehicle) {
  vehicle.move(this.currentLocation, new Location('texas'));
}
```
**[⬆ վեր](#Բովանդակություն)**

### Խուսափիր տիպերի ստուգումներից (մաս 2)
Եթե աշխատում ես հիմնական տարրական արժեքների հետ (ինչպիսին են տողերը և ամբողջ թվերը),
և չէս կարող բազմաձևություն (պոլիմորֆիզմ) կիրառել, սակայն ունես տիպերի ստուգման 
անհրաժեշտություն, պիտի դիտարկես TypeScript֊ի կիրառությունը։ Այն նորմալ JavasSript-ի
գերազանց այլընտրանք է, որովհետև առաջարկում է ստատիկ տիպավորում ի հավելումն ստանդարտ 
JavaScript-ի  սիտնաքսին։ Նորմալ JavaScrpt-ում ձեռքով տիպերի ստուգման խնդիրը նրանում է, 
որ այն լավ անելու համար պահանջվում է շեղում կոդի ընթեռնելիությունից։ Պահիր քո JavaScript-ը
մաքուր, գրիր լավ տեստեր և ունեցիր լավ կոդ-վերանայումներ (code reviews): Հակառակ դեպքում արա 
նույնը, սակայն TypeScript֊ի օգտագործմամբ, որը ինչպես վերը նշվեց գերազանց այլընտրանք է։


**Վատ՝**
```javascript
function combine(val1, val2) {
  if (typeof val1 === 'number' && typeof val2 === 'number' ||
      typeof val1 === 'string' && typeof val2 === 'string') {
    return val1 + val2;
  }

  throw new Error('Must be of type String or Number');
}
```

**Լավ՝**
```javascript
function combine(val1, val2) {
  return val1 + val2;
}
```
**[⬆ վեր](#Բովանդակություն)**

### Մի արա գերօպտիմիզացիա
Ժամանակակից դիտարկիչները «տակից»(under-the-hood) կատարում են բազմապիսի օպտիմիզացիաներ։
Հիմնականում, դու ժամանակ ես վատնում, երբ օպտիմիզացնում ես ծրագիրը։ [Կան լավ աղբյուրներ](https://github.com/petkaantonov/bluebird/wiki/Optimization-killers) 
հասկանալու համար, թե երբ է օպտիմիզացիան բացակայում։ 

**Վատ՝**
```javascript

// On old browsers, each iteration with uncached `list.length` would be costly
// because of `list.length` recomputation. In modern browsers, this is optimized.
for (let i = 0, len = list.length; i < len; i++) {
  // ...
}
```

**Լավ՝**
```javascript
for (let i = 0; i < list.length; i++) {
  // ...
}
```
**[⬆ վեր](#Բովանդակություն)**

### Հեռացրու մեռած կոդը
Մեռած կոդը նույնքան վատ է, որքան կրկնվող կոդը։ Ոչ մի պատճառ չկա այն քո ծրագրում
պահելու համար։ Եթե այն չի աշխատելու, վերացրո՛ւ այն։ Այն կպահպանվի վարկածների
պատմության մեջ, եթե հանակարծ ապագայում անհրաժեշտ լինի։


**Վատ՝**
```javascript
function oldRequestModule(url) {
  // ...
}

function newRequestModule(url) {
  // ...
}

const req = newRequestModule;
inventoryTracker('apples', req, 'www.inventory-awesome.io');

```

**Լավ՝**
```javascript
function newRequestModule(url) {
  // ...
}

const req = newRequestModule;
inventoryTracker('apples', req, 'www.inventory-awesome.io');
```
**[⬆ վեր](#Բովանդակություն)**

## **Օբյեկտներ և տվյալների ստրուկտուրաներ**
### Օգտագործիր getter֊ներ և setter-ներ
Օբյեկնտերում տվյալներին հասնելու համար getter֊ներ և setter֊ներ օգտագործելը ավելի
լավ է, քան օբյեկտի հատկանիշներին անմիջապես դիմելը։ Ինչու՞։ Ահա պատճառների մի
մի չդասակարգված ցանկ՝
* եթե դու ուզում ես անել ավելին քան օբյեկտի հատկանիշից արժեքը ուղղակի վերցնելն է, 
քեզ պետք չի լինի փնտրել և փոփոխել այն ամեն ժառանգորդի մեջ։
* Կարող ես հեշտությամբ անել վավերացում (validation) երբ `set` կա
* Ինկապսուլացնում ես ներքին իրականացումը
* Հեշտանում է արժեքներ վերցնելու և փոխելու ժամանակ սխալների մշակումը և լոգավորումը
* Կարող ես ալարկոտ (հետաձգված) արժեքավորում անել, օրինակ եթե վերցնում ես արժեքը սերվերից


**Վատ՝**
```javascript
function makeBankAccount() {
  // ...

  return {
    balance: 0,
    // ...
  };
}

const account = makeBankAccount();
account.balance = 100;
```

**Լավ՝**
```javascript
function makeBankAccount() {
  // this one is private
  let balance = 0;

  // a "getter", made public via the returned object below
  function getBalance() {
    return balance;
  }

  // a "setter", made public via the returned object below
  function setBalance(amount) {
    // ... validate before updating the balance
    balance = amount;
  }

  return {
    // ...
    getBalance,
    setBalance,
  };
}

const account = makeBankAccount();
account.setBalance(100);
```
**[⬆ վեր](#Բովանդակություն)**


### Օբյեկտներում ունեցիր private անդամներ
Սա կարելի է իրականացնել closure֊ներով (ES5 և ցածր վարկածների համար)

**Վատ՝**
```javascript

const Employee = function(name) {
  this.name = name;
};

Employee.prototype.getName = function getName() {
  return this.name;
};

const employee = new Employee('John Doe');
console.log(`Employee name: ${employee.getName()}`); // Employee name: John Doe
delete employee.name;
console.log(`Employee name: ${employee.getName()}`); // Employee name: undefined
```

**Լավ՝**
```javascript
function makeEmployee(name) {
  return {
    getName() {
      return name;
    },
  };
}

const employee = makeEmployee('John Doe');
console.log(`Employee name: ${employee.getName()}`); // Employee name: John Doe
delete employee.name;
console.log(`Employee name: ${employee.getName()}`); // Employee name: John Doe
```
**[⬆ վեր](#Բովանդակություն)**


## **Կլասներ**
### Նախընտրիր ES2015/ES6 կլասները և ոչ ES5 ֆունկցիաները
Դասական ES5 կլասների համար շատ դժվար է գրել ընթեռնելի կլասների ժառանգում, 
կառուցում և մեթոդների հայտարարում։ Եթե քեզ անհրաժեշտ է ժառանգում՝ նախընտրիր ES2015/ES6 կլասները։ 
Հակառակ դեպքում նախընտրիր փոքր ֆունկցիաներ, քանի դեռ չունես ավելի մեծ և բարդ օբյեկտներ կիրառելու 
անհրաժեշտություն։Միշտ համոզվի՛ր ,որ իրոք ժառանգության անհրաժեշտություն ունես։


**Վատ՝**
```javascript
const Animal = function(age) {
  if (!(this instanceof Animal)) {
    throw new Error('Instantiate Animal with `new`');
  }

  this.age = age;
};

Animal.prototype.move = function move() {};

const Mammal = function(age, furColor) {
  if (!(this instanceof Mammal)) {
    throw new Error('Instantiate Mammal with `new`');
  }

  Animal.call(this, age);
  this.furColor = furColor;
};

Mammal.prototype = Object.create(Animal.prototype);
Mammal.prototype.constructor = Mammal;
Mammal.prototype.liveBirth = function liveBirth() {};

const Human = function(age, furColor, languageSpoken) {
  if (!(this instanceof Human)) {
    throw new Error('Instantiate Human with `new`');
  }

  Mammal.call(this, age, furColor);
  this.languageSpoken = languageSpoken;
};

Human.prototype = Object.create(Mammal.prototype);
Human.prototype.constructor = Human;
Human.prototype.speak = function speak() {};
```

**Լավ՝**
```javascript
class Animal {
  constructor(age) {
    this.age = age;
  }

  move() { /* ... */ }
}

class Mammal extends Animal {
  constructor(age, furColor) {
    super(age);
    this.furColor = furColor;
  }

  liveBirth() { /* ... */ }
}

class Human extends Mammal {
  constructor(age, furColor, languageSpoken) {
    super(age, furColor);
    this.languageSpoken = languageSpoken;
  }

  speak() { /* ... */ }
}
```
**[⬆ վեր](#Բովանդակություն)**


### Օգտագործիր մեթոդների շղթայավորում
Այս մոտեցումը շատ կիրառական է JavaScript֊ում և կարող ես տեսնել այն բազում 
գրադարաններում ինչպիսիք են jQuery֊ը և Lodash֊ը: Այն քո կոդը ավելի արտահայտիչ 
և սակավաբառ է դարձնում։ Այդ պատճառով օգտագործիր մեթոդների շղթայավորում և կտեսնես թե որքան 
ավելի մաքուր կդառնա կոդդ։ Քո կլասսի ֆունկցիաներում վերադարձրու `this`֊ը բոլոր 
ֆունկցիաների վերջում և հետագայում կարող ես շղթայավորել մեթոդները։


**Վատ՝**
```javascript
class Car {
  constructor(make, model, color) {
    this.make = make;
    this.model = model;
    this.color = color;
  }

  setMake(make) {
    this.make = make;
  }

  setModel(model) {
    this.model = model;
  }

  setColor(color) {
    this.color = color;
  }

  save() {
    console.log(this.make, this.model, this.color);
  }
}

const car = new Car('Ford','F-150','red');
car.setColor('pink');
car.save();
```

**Լավ՝**
```javascript
class Car {
  constructor(make, model, color) {
    this.make = make;
    this.model = model;
    this.color = color;
  }

  setMake(make) {
    this.make = make;
    // NOTE: Returning this for chaining
    return this;
  }

  setModel(model) {
    this.model = model;
    // NOTE: Returning this for chaining
    return this;
  }

  setColor(color) {
    this.color = color;
    // NOTE: Returning this for chaining
    return this;
  }

  save() {
    console.log(this.make, this.model, this.color);
    // NOTE: Returning this for chaining
    return this;
  }
}

const car = new Car('Ford','F-150','red')
  .setColor('pink')
  .save();
```
**[⬆ վեր](#Բովանդակություն)**

### Կոմպոզիցիան նախընտրելի է ժառանգությունից 
Ինչպես նշված է հայտնի  [*Design Patterns*](https://en.wikipedia.org/wiki/Design_Patterns) գրքում,
դու պիտի նախընտրես կոմպոզիցիան ժառանգմանը երբ կարող ես։ Կան բազում պատճառներ թե կոմպոզիցիան և թե ժառանգումը
նախընտրելու համար։ Այս մտքի հիմնական կետը այն է, որ երբ քո միտքը բնազդորեն գնում է ժառանգում անելու, մտածես,
որ գուցե կոմպոզիցիան կարող է ավելի լավ մոդելավորել քո խնդիրը։ Որոշ դեպքերում կարող է ․․․ 

Դու կարող ես զարմանալ․ «Ե՞րբ օգտագործեմ ժառանգում»։ Դա կախված է քո խնդիրց, բայց ահա մի համեստ ցանկ, 
թե երբ ժառանգումը ավելի իմաստալի է քան կոմպոզիցիան ՝

1. Քո ժառանգումը նկարագրում է "է" (is-a) հարաբերությունը այլ ոչ "պատկանում է" (has-a) հարաբերությունը
(Human->Animal vs. User->UserDetails)
2. Դու կարող ես վերօգտագործել հիմնական կլասի կոդը (մարդիկ շարժվում են բոլոր կենդանիների պես)
3. Դու ուզում ես կատարել գլոբալ փոփոխություններ ժառանգ կլասներում, փոխելով հիմնական կլասը։


**Վատ՝**
```javascript
class Employee {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }

  // ...
}

// Bad because Employees "have" tax data. EmployeeTaxData is not a type of Employee
class EmployeeTaxData extends Employee {
  constructor(ssn, salary) {
    super();
    this.ssn = ssn;
    this.salary = salary;
  }

  // ...
}
```

**Լավ՝**
```javascript
class EmployeeTaxData {
  constructor(ssn, salary) {
    this.ssn = ssn;
    this.salary = salary;
  }

  // ...
}

class Employee {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }

  setTaxData(ssn, salary) {
    this.taxData = new EmployeeTaxData(ssn, salary);
  }
  // ...
}
```
**[⬆ վեր](#Բովանդակություն)**

## **SOLID**
### Single Responsibility Principle (Միակ պատասխանատվության սկզբունք) (SRP)
Ինչպես ասված է «Մաքուր Կոդ»֊ում՝ "Կլասի փոփոխության համար պիտի լինի միայն մեկ պատճառ"։
Շատ գաւթակղիչ է մեկ կլասի մեջ շատ ֆունկցիաներ պահելը, կարծես այն թռիչքի համար միակ ճամպրուկը լինի։ 
Խնդիրը նրանում է, որ քո կլասը չի լինի կոնցեպտուալ կապված ու ամեն պատեհ ու անպատեհ առիթով ստիպված կլինես փոփոխալ այն։ Շատ կարևոր է կլասի ներսում փոփոխությունները հնարավորինս նվազեցնել։ Երբ դու փոփոխություններ
ես կատարում մեծ ֆունկիոնալով կասում, դժվար ա է վերահսկել այդ փոփոխությունների բոլոր հետևանքները։

**Վատ՝**
```javascript
class UserSettings {
  constructor(user) {
    this.user = user;
  }

  changeSettings(settings) {
    if (this.verifyCredentials()) {
      // ...
    }
  }

  verifyCredentials() {
    // ...
  }
}
```

**Լավ՝**
```javascript
class UserAuth {
  constructor(user) {
    this.user = user;
  }

  verifyCredentials() {
    // ...
  }
}


class UserSettings {
  constructor(user) {
    this.user = user;
    this.auth = new UserAuth(user);
  }

  changeSettings(settings) {
    if (this.auth.verifyCredentials()) {
      // ...
    }
  }
}
```
**[⬆ վեր](#Բովանդակություն)**

### Բացության/փակության սկզբունք (Open/Closed Principle (OCP))
Ինչպես նշել է Բերտրան Մեյերը․ «ծրագրային էությունները (կլասներ, մոդուլներ, ֆունկցիաներ, և այլն ․․․) պիտի բաց լինեն ընդլայնման համար, սակայն փակ՝ ձևափոխության համար»։ Ի՞նչ է սա նշանակում։ Այս սկզբունքը
պնդում է, որ դու պիտի թույլատերս քո կոդի օգտատերերին<sup>*</sup> ընդլայնել հնարավորությունները առանց եղած կոդի ձևափոխության։

<sup>*</sup> օգտատերերը այստեղ մյուս ծրագրավորողներն են, ովքեր օգտագործում են քո կոդային բազան։

**Վատ՝**
```javascript
class AjaxAdapter extends Adapter {
  constructor() {
    super();
    this.name = 'ajaxAdapter';
  }
}

class NodeAdapter extends Adapter {
  constructor() {
    super();
    this.name = 'nodeAdapter';
  }
}

class HttpRequester {
  constructor(adapter) {
    this.adapter = adapter;
  }

  fetch(url) {
    if (this.adapter.name === 'ajaxAdapter') {
      return makeAjaxCall(url).then((response) => {
        // տրանսֆորմացնել պատասխանը և վերադարձնել 
      });
    } else if (this.adapter.name === 'httpNodeAdapter') {
      return makeHttpCall(url).then((response) => {
        // տրանսֆորմացնել պատասխանը և վերադարձնել
      });
    }
  }
}

function makeAjaxCall(url) {
  // հարցում անել և վերադարձնել promise
}

function makeHttpCall(url) {
  // հարցում անել և վերադարձնել promise
}
```

**Լավ՝**
```javascript
class AjaxAdapter extends Adapter {
  constructor() {
    super();
    this.name = 'ajaxAdapter';
  }

  request(url) {
    // հարցում անել և վերադարձնել promise
  }
}

class NodeAdapter extends Adapter {
  constructor() {
    super();
    this.name = 'nodeAdapter';
  }

  request(url) {
    // հարցում անել և վերադարձնել promise
  }
}

class HttpRequester {
  constructor(adapter) {
    this.adapter = adapter;
  }

  fetch(url) {
    return this.adapter.request(url).then((response) => {
      // տրանսֆորմացնել պատասխանը և վերադարձնել
    });
  }
}
```
**[⬆ վեր](#Բովանդակություն)**

### Լիսկովի փոխարինման սկզբունքը (Liskov Substitution Principle (LSP))
Սա շատ վախենալու տերմին է, որը հասարակ գաղափար է նկարագրում։ Ֆորմալ ձևակերպումը հետևյալն է․ «Եթե S-ը հանդիսանում է T-ի ենթատիպը, ապա T տիպի
օբյեկտները կարող են փոխարինվել S տիպի օբյեկտներով» (այսինքն S տիպի
օբյեկտները փոխարինում են T տիպի օբյեկտներին) առանց ծրագրի կարևոր հատկանիշների փոփոխության (ճշգրտություն, կատարվող առաջադրանք և այլն ․․․)

Լավագույն բացատրությունը այն է, որ եթե դու ունես մայրական և ռառանգ կլասներ, ապա մայրական և ժառանգ կլասները փոխարինելի են և փոխարինումը չի բերի սխալ արդյունքների։ Սա գուցե դեռ անհասկանալի է․ արի նայենք դասական Քառակուսի֊ՈՒղղանկյուն օրինակը։ Մաթեմատիկայի տեսանկյունից քառակուսին ուղղանկյուն է, և եթե դու մոդելավորես դրանք "է" (is-a) հարաբերությամբ ժառանգման միջոցով, կընկնես անախորժությունների մեջ։
 
**Վատ՝**
```javascript
class Rectangle {
  constructor() {
    this.width = 0;
    this.height = 0;
  }

  setColor(color) {
    // ...
  }

  render(area) {
    // ...
  }

  setWidth(width) {
    this.width = width;
  }

  setHeight(height) {
    this.height = height;
  }

  getArea() {
    return this.width * this.height;
  }
}

class Square extends Rectangle {
  setWidth(width) {
    this.width = width;
    this.height = width;
  }

  setHeight(height) {
    this.width = height;
    this.height = height;
  }
}

function renderLargeRectangles(rectangles) {
  rectangles.forEach((rectangle) => {
    rectangle.setWidth(4);
    rectangle.setHeight(5);
    const area = rectangle.getArea(); // Վատ: Վերադարձնում է 25  քառակուսու համար (Square). պիտի լինի 20.
    rectangle.render(area);
  });
}

const rectangles = [new Rectangle(), new Rectangle(), new Square()];
renderLargeRectangles(rectangles);
```

**Լավ՝**
```javascript
class Shape {
  setColor(color) {
    // ...
  }

  render(area) {
    // ...
  }
}

class Rectangle extends Shape {
  constructor(width, height) {
    super();
    this.width = width;
    this.height = height;
  }

  getArea() {
    return this.width * this.height;
  }
}

class Square extends Shape {
  constructor(length) {
    super();
    this.length = length;
  }

  getArea() {
    return this.length * this.length;
  }
}

function renderLargeShapes(shapes) {
  shapes.forEach((shape) => {
    const area = shape.getArea();
    shape.render(area);
  });
}

const shapes = [new Rectangle(4, 5), new Rectangle(4, 5), new Square(5)];
renderLargeShapes(shapes);
```
**[⬆ վեր](#Բովանդակություն)**

### Ինտերֆեյսի բաժանման սկզբունք (Interface Segregation Principle (ISP))
JavaScript֊ը չունի ինտերֆեյսներ և այս սկզբունքը նույն խստությամբ չի կիրառվում։ Ամեն դեպքում այն կարևոր և էական է նույնիսկ JavaScript's֊ում տիպերի բացակայության իրավիճակում։

ԻԲՍ (ISP) նշում է որ «օգտատերերը չպետք է ստիպված լինեն կախված լինել այն ինտերֆեյսներից, որոնք նրանք չեն օգտագործում»: Ինտերֆեյսներն անուղղակի պայմանագրեր են JavaScript-ում տիպերի համակարգի պատճառով:

Այս սկզբունքը ցուցադրող լավ օրինակ է այն դեպքը, երբ կլասը պահանջում է
կարգավորումների մեծ օբյեկտ։ Օգտատերերին պետք է ազատել մեծաքանակ, այդ պահին իրենց համար ոչ անհրաժեշտ կարգավորումները գրելու անհրաժեշտությունից, քանի որ հաճախ, նրանք չունեն այդ բոլոր կարգավորումների կարիքը։ Այս կարգավորումները ընտրովի դարձնելը օգնում է խուսափել "չաղ ինտերֆեյս" ունենալուց։

**Վատ՝**
```javascript
class DOMTraverser {
  constructor(settings) {
    this.settings = settings;
    this.setup();
  }

  setup() {
    this.rootNode = this.settings.rootNode;
    this.animationModule.setup();
  }

  traverse() {
    // ...
  }
}

const $ = new DOMTraverser({
  rootNode: document.getElementsByTagName('body'),
  animationModule() {} // Most of the time, we won't need to animate when traversing.
  // ...
});

```

**Լավ՝**
```javascript
class DOMTraverser {
  constructor(settings) {
    this.settings = settings;
    this.options = settings.options;
    this.setup();
  }

  setup() {
    this.rootNode = this.settings.rootNode;
    this.setupOptions();
  }

  setupOptions() {
    if (this.options.animationModule) {
      // ...
    }
  }

  traverse() {
    // ...
  }
}

const $ = new DOMTraverser({
  rootNode: document.getElementsByTagName('body'),
  options: {
    animationModule() {}
  }
});
```
**[⬆ վեր](#Բովանդակություն)**

### Կախվածությունների շրջման սկզբունք (Dependency Inversion Principle (DIP))
Այս սյզբունքը հասմանում է երկու հիմնական բան՝
1. Բարձր կարգի մոդուլները չպիտի կախվածություն ունենան ցածր կարգի մոդուլներից։ Երկուսն էլ պիտի կախված կլինեն աբստրակցիաներից։
2. Աբստրակցիաները չպիտի կախված լինեն մանրամասնություններից, մանրամասնությունները պիտի կախված լինեն աբստրակցիաներից։

Սա սկզբից դժվար հասկանալի է, բայց եթե դու աշխատել ես AngularJS֊ով, ապա տեսել ես այս սկբունքի իրականացումը Կախվածության Ներարկման (Dependency Injection (DI)) տեսքով։ Չնայած որ DI֊ն և DIP-ը նույնական գաղափարներ չեն , DIP֊ը թաքցնում է ցածր կագի մոդուլների իրականացման մանրամասները բարձր կարգի մոդուլներից։ Դա կարող է արվել DI֊ի միջոցով։ Այս մեթոդի օգտագործումը թուլացնում է շղթայակցումը մոդուլների միջև։ Մոդուլների շղթայակցումը շատ վատ նախագծման եղանակ է,որովհետև այն դժվարեցնում է կոդի վերափոխումը (refactoring)։

Ինչպես նախկինում նշվեց JavaScript֊ը չուն ինտերֆեյսներ, հետևաբար աբստրակցիաները անուղակի պայմանագրերի վրա են հիմնվում։ Այսինքն մի կլասից/օբյեկտից մյուսին փոխանցվող մեթոդները և հատկանիշները։ Հաջորդ օրինակում անուղակի պայմանագիրը այն է, որ `InventoryTracker`֊ի համար Request մոդուլը պիտի ունենա `requestItems` մեթոդը։

**Վատ՝**
```javascript
class InventoryRequester {
  constructor() {
    this.REQ_METHODS = ['HTTP'];
  }

  requestItem(item) {
    // ...
  }
}

class InventoryTracker {
  constructor(items) {
    this.items = items;

    // BAD: We have created a dependency on a specific request implementation.
    // We should just have requestItems depend on a request method: `request`
    this.requester = new InventoryRequester();
  }

  requestItems() {
    this.items.forEach((item) => {
      this.requester.requestItem(item);
    });
  }
}

const inventoryTracker = new InventoryTracker(['apples', 'bananas']);
inventoryTracker.requestItems();
```

**Լավ՝**
```javascript
class InventoryTracker {
  constructor(items, requester) {
    this.items = items;
    this.requester = requester;
  }

  requestItems() {
    this.items.forEach((item) => {
      this.requester.requestItem(item);
    });
  }
}

class InventoryRequesterV1 {
  constructor() {
    this.REQ_METHODS = ['HTTP'];
  }

  requestItem(item) {
    // ...
  }
}

class InventoryRequesterV2 {
  constructor() {
    this.REQ_METHODS = ['WS'];
  }

  requestItem(item) {
    // ...
  }
}

// By constructing our dependencies externally and injecting them, we can easily
// substitute our request module for a fancy new one that uses WebSockets.
const inventoryTracker = new InventoryTracker(['apples', 'bananas'], new InventoryRequesterV2());
inventoryTracker.requestItems();
```
**[⬆ վեր](#Բովանդակություն)**

## **Տեստավորում**
Testing is more important than shipping. If you have no tests or an
inadequate amount, then every time you ship code you won't be sure that you
didn't break anything. Deciding on what constitutes an adequate amount is up
to your team, but having 100% coverage (all statements and branches) is how
you achieve very high confidence and developer peace of mind. This means that
in addition to having a great testing framework, you also need to use a
[good coverage tool](http://gotwarlost.github.io/istanbul/).

There's no excuse to not write tests. There are [plenty of good JS test frameworks](http://jstherightway.org/#testing-tools), so find one that your team prefers.
When you find one that works for your team, then aim to always write tests
for every new feature/module you introduce. If your preferred method is
Test Driven Development (TDD), that is great, but the main point is to just
make sure you are reaching your coverage goals before launching any feature,
or refactoring an existing one.

### Ամեն տեստին միակ պարզ գաղափար

**Վատ՝**
```javascript
import assert from 'assert';

describe('MakeMomentJSGreatAgain', () => {
  it('handles date boundaries', () => {
    let date;

    date = new MakeMomentJSGreatAgain('1/1/2015');
    date.addDays(30);
    assert.equal('1/31/2015', date);

    date = new MakeMomentJSGreatAgain('2/1/2016');
    date.addDays(28);
    assert.equal('02/29/2016', date);

    date = new MakeMomentJSGreatAgain('2/1/2015');
    date.addDays(28);
    assert.equal('03/01/2015', date);
  });
});
```

**Լավ՝**
```javascript
import assert from 'assert';

describe('MakeMomentJSGreatAgain', () => {
  it('handles 30-day months', () => {
    const date = new MakeMomentJSGreatAgain('1/1/2015');
    date.addDays(30);
    assert.equal('1/31/2015', date);
  });

  it('handles leap year', () => {
    const date = new MakeMomentJSGreatAgain('2/1/2016');
    date.addDays(28);
    assert.equal('02/29/2016', date);
  });

  it('handles non-leap year', () => {
    const date = new MakeMomentJSGreatAgain('2/1/2015');
    date.addDays(28);
    assert.equal('03/01/2015', date);
  });
});
```
**[⬆ վեր](#Բովանդակություն)**

## **Concurrency**
### Օգտագործիր փրոմիսներ(Promises), ոչ քալբեքներ(callback)
Callbacks aren't clean, and they cause excessive amounts of nesting. With ES2015/ES6,
Promises are a built-in global type. Use them!

**Վատ՝**
```javascript
import { get } from 'request';
import { writeFile } from 'fs';

get('https://en.wikipedia.org/wiki/Robert_Cecil_Martin', (requestErr, response) => {
  if (requestErr) {
    console.error(requestErr);
  } else {
    writeFile('article.html', response.body, (writeErr) => {
      if (writeErr) {
        console.error(writeErr);
      } else {
        console.log('File written');
      }
    });
  }
});

```

**Լավ՝**
```javascript
import { get } from 'request';
import { writeFile } from 'fs';

get('https://en.wikipedia.org/wiki/Robert_Cecil_Martin')
  .then((response) => {
    return writeFile('article.html', response);
  })
  .then(() => {
    console.log('File written');
  })
  .catch((err) => {
    console.error(err);
  });

```
**[⬆ վեր](#Բովանդակություն)**

### Async/Await փրոմիսներից ավելի հասկանալի է
Promises are a very clean alternative to callbacks, but ES2017/ES8 brings async and await
which offer an even cleaner solution. All you need is a function that is prefixed
in an `async` keyword, and then you can write your logic imperatively without
a `then` chain of functions. Use this if you can take advantage of ES2017/ES8 features
today!

**Վատ՝**
```javascript
import { get } from 'request-promise';
import { writeFile } from 'fs-promise';

get('https://en.wikipedia.org/wiki/Robert_Cecil_Martin')
  .then((response) => {
    return writeFile('article.html', response);
  })
  .then(() => {
    console.log('File written');
  })
  .catch((err) => {
    console.error(err);
  });

```

**Լավ՝**
```javascript
import { get } from 'request-promise';
import { writeFile } from 'fs-promise';

async function getCleanCodeArticle() {
  try {
    const response = await get('https://en.wikipedia.org/wiki/Robert_Cecil_Martin');
    await writeFile('article.html', response);
    console.log('File written');
  } catch(err) {
    console.error(err);
  }
}
```
**[⬆ վեր](#Բովանդակություն)**


## **Սխալների մշակում**
Thrown errors are a good thing! They mean the runtime has successfully
identified when something in your program has gone wrong and it's letting
you know by stopping function execution on the current stack, killing the
process (in Node), and notifying you in the console with a stack trace.

### Մի անտեսիր բռնված սխալները
Doing nothing with a caught error doesn't give you the ability to ever fix
or react to said error. Logging the error to the console (`console.log`)
isn't much better as often times it can get lost in a sea of things printed
to the console. If you wrap any bit of code in a `try/catch` it means you
think an error may occur there and therefore you should have a plan,
or create a code path, for when it occurs.

**Վատ՝**
```javascript
try {
  functionThatMightThrow();
} catch (error) {
  console.log(error);
}
```

**Լավ՝**
```javascript
try {
  functionThatMightThrow();
} catch (error) {
  // One option (more noisy than console.log):
  console.error(error);
  // Another option:
  notifyUserOfError(error);
  // Another option:
  reportErrorToService(error);
  // OR do all three!
}
```

### Մի անտեսիր մերժված փրոմիսները
For the same reason you shouldn't ignore caught errors
from `try/catch`.

**Վատ՝**
```javascript
getdata()
  .then((data) => {
    functionThatMightThrow(data);
  })
  .catch((error) => {
    console.log(error);
  });
```

**Լավ՝**
```javascript
getdata()
  .then((data) => {
    functionThatMightThrow(data);
  })
  .catch((error) => {
    // One option (more noisy than console.log):
    console.error(error);
    // Another option:
    notifyUserOfError(error);
    // Another option:
    reportErrorToService(error);
    // OR do all three!
  });
```

**[⬆ վեր](#Բովանդակություն)**


## **Ֆորմատավորում**
Formatting is subjective. Like many rules herein, there is no hard and fast
rule that you must follow. The main point is DO NOT ARGUE over formatting.
There are [tons of tools](http://standardjs.com/rules.html) to automate this.
Use one! It's a waste of time and money for engineers to argue over formatting.

For things that don't fall under the purview of automatic formatting
(indentation, tabs vs. spaces, double vs. single quotes, etc.) look here
for some guidance.

### Use consistent capitalization
JavaScript is untyped, so capitalization tells you a lot about your variables,
functions, etc. These rules are subjective, so your team can choose whatever
they want. The point is, no matter what you all choose, just be consistent.

**Վատ՝**
```javascript
const DAYS_IN_WEEK = 7;
const daysInMonth = 30;

const songs = ['Back In Black', 'Stairway to Heaven', 'Hey Jude'];
const Artists = ['ACDC', 'Led Zeppelin', 'The Beatles'];

function eraseDatabase() {}
function restore_database() {}

class animal {}
class Alpaca {}
```

**Լավ՝**
```javascript
const DAYS_IN_WEEK = 7;
const DAYS_IN_MONTH = 30;

const SONGS = ['Back In Black', 'Stairway to Heaven', 'Hey Jude'];
const ARTISTS = ['ACDC', 'Led Zeppelin', 'The Beatles'];

function eraseDatabase() {}
function restoreDatabase() {}

class Animal {}
class Alpaca {}
```
**[⬆ վեր](#Բովանդակություն)**


### Function callers and callees should be close
If a function calls another, keep those functions vertically close in the source
file. Ideally, keep the caller right above the callee. We tend to read code from
top-to-bottom, like a newspaper. Because of this, make your code read that way.

**Վատ՝**
```javascript
class PerformanceReview {
  constructor(employee) {
    this.employee = employee;
  }

  lookupPeers() {
    return db.lookup(this.employee, 'peers');
  }

  lookupManager() {
    return db.lookup(this.employee, 'manager');
  }

  getPeerReviews() {
    const peers = this.lookupPeers();
    // ...
  }

  perfReview() {
    this.getPeerReviews();
    this.getManagerReview();
    this.getSelfReview();
  }

  getManagerReview() {
    const manager = this.lookupManager();
  }

  getSelfReview() {
    // ...
  }
}

const review = new PerformanceReview(employee);
review.perfReview();
```

**Լավ՝**
```javascript
class PerformanceReview {
  constructor(employee) {
    this.employee = employee;
  }

  perfReview() {
    this.getPeerReviews();
    this.getManagerReview();
    this.getSelfReview();
  }

  getPeerReviews() {
    const peers = this.lookupPeers();
    // ...
  }

  lookupPeers() {
    return db.lookup(this.employee, 'peers');
  }

  getManagerReview() {
    const manager = this.lookupManager();
  }

  lookupManager() {
    return db.lookup(this.employee, 'manager');
  }

  getSelfReview() {
    // ...
  }
}

const review = new PerformanceReview(employee);
review.perfReview();
```

**[⬆ վեր](#Բովանդակություն)**

## **Մեկնաբանություններ**
### Only comment things that have business logic complexity.
Comments are an apology, not a requirement. Good code *mostly* documents itself.

**Վատ՝**
```javascript
function hashIt(data) {
  // The hash
  let hash = 0;

  // Length of string
  const length = data.length;

  // Loop through every character in data
  for (let i = 0; i < length; i++) {
    // Get character code.
    const char = data.charCodeAt(i);
    // Make the hash
    hash = ((hash << 5) - hash) + char;
    // Convert to 32-bit integer
    hash &= hash;
  }
}
```

**Լավ՝**
```javascript

function hashIt(data) {
  let hash = 0;
  const length = data.length;

  for (let i = 0; i < length; i++) {
    const char = data.charCodeAt(i);
    hash = ((hash << 5) - hash) + char;

    // Convert to 32-bit integer
    hash &= hash;
  }
}

```
**[⬆ վեր](#Բովանդակություն)**

### Don't leave commented out code in your codebase
Version control exists for a reason. Leave old code in your history.

**Վատ՝**
```javascript
doStuff();
// doOtherStuff();
// doSomeMoreStuff();
// doSoMuchStuff();
```

**Լավ՝**
```javascript
doStuff();
```
**[⬆ վեր](#Բովանդակություն)**

### Don't have journal comments
Remember, use version control! There's no need for dead code, commented code,
and especially journal comments. Use `git log` to get history!

**Վատ՝**
```javascript
/**
 * 2016-12-20: Removed monads, didn't understand them (RM)
 * 2016-10-01: Improved using special monads (JP)
 * 2016-02-03: Removed type-checking (LI)
 * 2015-03-14: Added combine with type-checking (JR)
 */
function combine(a, b) {
  return a + b;
}
```

**Լավ՝**
```javascript
function combine(a, b) {
  return a + b;
}
```
**[⬆ վեր](#Բովանդակություն)**

### Avoid positional markers
They usually just add noise. Let the functions and variable names along with the
proper indentation and formatting give the visual structure to your code.

**Վատ՝**
```javascript
////////////////////////////////////////////////////////////////////////////////
// Scope Model Instantiation
////////////////////////////////////////////////////////////////////////////////
$scope.model = {
  menu: 'foo',
  nav: 'bar'
};

////////////////////////////////////////////////////////////////////////////////
// Action setup
////////////////////////////////////////////////////////////////////////////////
const actions = function() {
  // ...
};
```

**Լավ՝**
```javascript
$scope.model = {
  menu: 'foo',
  nav: 'bar'
};

const actions = function() {
  // ...
};
```
**[⬆ վեր](#Բովանդակություն)**

## Թարգմանություններ

This is also available in other languages:

  - ![br](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Brazil.png) **Brazilian Portuguese**: [fesnt/clean-code-javascript](https://github.com/fesnt/clean-code-javascript)
  - ![es](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Uruguay.png) **Spanish**: [andersontr15/clean-code-javascript](https://github.com/andersontr15/clean-code-javascript-es)
  - ![cn](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/China.png) **Chinese**:
    - [alivebao/clean-code-js](https://github.com/alivebao/clean-code-js)
    - [beginor/clean-code-javascript](https://github.com/beginor/clean-code-javascript)
  - ![de](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Germany.png) **German**: [marcbruederlin/clean-code-javascript](https://github.com/marcbruederlin/clean-code-javascript)
  - ![kr](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/South-Korea.png) **Korean**: [qkraudghgh/clean-code-javascript-ko](https://github.com/qkraudghgh/clean-code-javascript-ko)
  - ![pl](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Poland.png) **Polish**: [greg-dev/clean-code-javascript-pl](https://github.com/greg-dev/clean-code-javascript-pl)
  - ![ru](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Russia.png) **Russian**:
    - [BoryaMogila/clean-code-javascript-ru/](https://github.com/BoryaMogila/clean-code-javascript-ru/)
    - [maksugr/clean-code-javascript](https://github.com/maksugr/clean-code-javascript)
  - ![vi](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Vietnam.png) **Vietnamese**: [hienvd/clean-code-javascript/](https://github.com/hienvd/clean-code-javascript/)
  - ![ja](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Japan.png) **Japanese**: [mitsuruog/clean-code-javascript/](https://github.com/mitsuruog/clean-code-javascript/)
  - ![id](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/Indonesia.png) **Indonesia**:
  [andirkh/clean-code-javascript/](https://github.com/andirkh/clean-code-javascript/)

**[⬆ վեր](#Բովանդակություն)**
