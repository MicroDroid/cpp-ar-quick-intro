# مدخل سريع

> 💥 يجب بشكل قطعي تجريب كل فكرة تعلمتها في هذا المستند لتترسخ الفكرة لديك. هذا الأسلوب مهم وبشدة في كل مرة تتعلم فيها شيئ عن البرمجة.

<!-- -->

> التجربة > القراءة

## نظرة عامة

بدلاً من استخدام الأرقام مثل `10110000 01100001` (Binary) للقيام بعملية معينة على الكمبيوتر, يمكن استخدام لغات برمجة مثل C++ والتي تسمح ب:
- برمجة برامج معقدة بشكل اسهل (بكثير)

لكن لغات البرمجة لا يستطيع المعالج أن يتعامل معها بشكل مباشر وبذلك:

> بعد كتابة الكود, نحتاج الى "تجميعه" (compile) وتحويله الى Binary ليصبح برنامج قابل للتشغيل.

## تجميع أول برنامج C++

يوجد الكثير من الطرق لتجميع برامج C++, أهمها:
- **[cpp.sh](http://cpp.sh/) (سهل جداً وينصح به بشدة, لكن يحتاج الى شبكة الأنترنت بشكل دائم)**
- [DevC++](https://sourceforge.net/projects/orwelldevcpp/) (سهل)
- [Visual Studio Code](https://code.visualstudio.com/) + [MinGW](https://osdn.net/projects/mingw/releases/) (مستخدمين متقدمين فقط)

> مستخدمي Linux: أسهل طريقة هي تنزيل `g++` بشكل مباشر واستعماله مع اي محرر كود.

- **في حال cpp.sh, بكل بساطة يمكن زيارة الموقع, كتابة أي كود والضغط على Run بالأسفل لشتغيل الكود ومشاهدة النتائج.**
- في حال DevC++, انا لم استخدمه مسبقاً
- في حال MinGW, استخدم `g++`, مثلاً لو كان اسم الملف الذي يحتوي الكود `main.cpp` يمكن الكتابة ضمن اي Terminal التالي:
	- `g++ main.cpp -o main`
	- بعد ذلك يصبح ملف اسمه `main.exe` موجود وقابل للتشغيل

استخدم الكود البسيط التالي لتجريب هذه العملية:

```c++
#include <iostream>
 
int main()
{
	std::cout << "Hello, world!";
}
```

> هذا الكود يكتب "Hello World" فقط.

## تحليل المثال السابق

سوف نحلل كل سطر في الكود.
```c++
#include <iostream>
```
هذا السطر يدل على أننا نريد استخدام محتويات المكتبة التي اسمها `iostream` في هذا البرنامج.
```c++
int main()
```
هذا السطر يقوم بتعريف **تابع** اسمه `main`. هذا التابع هو أول تابع يعمل في البرنامج. **هذا التابع يجب أن يكون مجود في كل برنامج.**
السطرين:
```c++
{
	...
}
```
يعبران على أن كل كود بينهما هو جزء من التابع `main`.

ضمن التابع يوجد سطر واحد:
```c++
std::cout << "Hello World";
```

في هذا السطر, `std::cout` و `<<` يسمحان بكتابة أحرف او أرقام كخرج للبرنامج. هذا البرنامج يقوم بكتابة `Hello World` عند تشغيله, نتيجة لذلك.

## هيكلية الكود

### الفرق بين التعليمات والتعابير

- التعليمات (statements): هي سطر كود يقوم بشيئ معين. مثلا `int x = 5;` تعليمة تقوم بتعريف متحول `x` بقيمة `5` (ويتم تخزين المتحول في ال RAM)
- التعبيرات (expressions): هو *شيئ* يعبر عن قيمة معينة. مثلا `x+5` او `x/2`
- مجموعة كود (block): هي مجموعة تعلميات بين اقواس من الشكل  `{}`

كل تعليمة تكون بسطر منفرد (عادة) وتنتهي بفاصلة منقوطة `;`

في المثال السابق:
- `"Hello World"` هو تعبير (قيمة وليس عملية)
- `std::cout` هو تعبير (قيمة وليس عملية)
- `std::cout <<  "Hello, world!";` هي تعليمة (عملية كاملة).
- `{ std::cout << "Hello, world!"; }` هي block

### وضع المسافات وترتيب الكود (مهم جداً 🚨)

ترتيب الكود:
- يجعل القراءة سهلة
- يسهل ايجاد الأخطاء في الكود

قواعد اساسية:
- يجب وضع كل تعلمية بسطر منفرد **(مهم جداً)**
- يجب وضع مسافة واحدة في معظم الحالات الممكنة فيها
	- مثلا `int x=5;` هي تعليمة صحيحة ولكن `int x = 5;` هي أيضا صحيحة ولذلك يتم تفضل الثانية على الأولى.
- يجب وضع Tab (مسافة طويلة, يوجد زر مخصص في آخر الكيبورد جهة اليسار) عند الدخول لكل block
	```c++
	int main()
	{
	int x = 5;
	}
	``` 
	هي صحيحة ولكن:
	```c++
	int main()
	{
		int x = 5;
	}
	```
	هي اصح (بكثير).

## التعليقات ضمن الكود 💬

يمكن كتابة تعليقات ضمن الكود من غير ان تأثر في الكود, حيث يقوم المجمع (compiler) بتجاهلها تماما عند التجميع.
التعليقات تفيد في:
- كتابة شروحات وتوضيحات ضمن الكود
- فوائد اخرى غير مهمة للمبتدئين 😜

يوجد نوعين للتعليقات:
- تعليقات تأخذ سطر واحد فقط من حيث كتابة `//` الى نهاية السطر (لاحظ اللون المختلف للتعليق)
	```c++
	int main() {
		std::cout << "Hello World"; // prints hello world
	}
	```
- تعليقات تأخذ أكثر من سطر, تبدأ ب `/*` وتنتهي ب `*/`:
	```c++
	int main() {
		/*
			هذا السطر يقوم بكتابة Hello World
			وبعد ذلك يتم اغلاق البرنامج بشكل مباشر.
		*/
		std::cout << "Hello World";
	}
	```

> 🚩 **سيتم استخدام التعليقات من الآن فصاعدة لتقديم بعض الشروحات ضمن هذا المستند.**

## المتغيرات / المتحولات

كل برنامج, بشكل أو بآخر, يقوم بمعالجة معلومات. مثلاً البرنامج السابق يقوم بمعالجة المعلومة `Hello World` ليتم طباعتها.

يتم تخزين المعلومات بما يسمى المتحولات (variables). مثال عن تعريف متحول اسمه `x`:
```c++
int x = 5;
```
هذا المتحول هو من نوع `int` وقيمته `5`.

### أنواع المتحولات

في لغة C++, للمتحولات انواع, بعضها لتخزين الأعداد الصحيحة, وبعضها للأعداد التي تحوي فواصل, وبعضها للأحرف, الخ.

الأنواع الأساسية:

| النوع		   | الأستخدام			   |
|-----------------|-------------------------|
| `int`			 | عدد صحيح				|
| `float` او `double` | عدد له فواصل			|
| `char`			| حرف واحد فقط			|
| `bool`			| يقبل `true` او `false` فقط. |

> لاحظ اننا كنا نستعمل "Hello World" في السابق, والذي هو اكثر من حرف واحد. هذا النوع هو حالة خاصة ونوعه هو `std::string`, والذي يستخدم `char` داخليا ويمكن التعرف عليه بشكل افضل لاحقا.

### أمثلة

نقوم بتعريف عدة متحولات:

```c++
int number_of_apples = 5;
float temperature = 24.22; // Celsius 
double battery_level; // هذا المتحول لا يحوي قيمة
```

يمكن تغيير قيمة المتحولات فيما بعد (من دون ذكر النوع مرة أخرى)

```c++
number_of_apples = 8;
temperature = 14.0; // Celsius
battery_level = 78.8; // الأن أصبح هذا المتحول له قيمة
```

## مكتبة `iostream`

مكتبة `iostream` توفر بعض الأدوات للتعامل مع الدخل والخرج للبرنامج. نهتم حاليا بثلاث متغيرات ضمنها:

- `std::cout`
- `std::cin`
- `std::endl`

### المتحول `std::cout`

كلمة `cout` هي اختصار ل "Character Output". يمكن استخدام هذا المتغير كالتالي:

```c++
std::cout << "Hello World";
```

هذا الكود يطبع "Hello World" على الشاشة عند تشغيله. يمكن تخيل هذا الكود على انه `<<` هي اسهم تنقل `"Hello World"` الى `std::cout`.

يمكن ايضا اخراج عدة قيم بتعليمة واحدة:

```c++
int temperature = 25;
std::cout << "The temperature is: " << temperature;
```

### المتحول `std::cin`

بشكل مماثل, `cin` هي اختصار ل "Character Input" ويمكن استخدامها كالتالي:

```c++
int x;
std::cin >> x;
```

عندما يبدأ البرنامج سينتظر لحين يقوم المستخدم بإدخال رقم والضغط على Enter, بعدها يقوم بتخزين الرقم المدخل في المتحول `x`.

> 🤔 ماذا يحدث لو كان الدخل يحتوي احرف؟ 

### المتحول `std::endl`

لو قمت بتشغيل الكود التالي:

```c++
std::cout << "drink";
std::cout << "water";
```

سيكون الناتج كالتالي:

```plaintext
drinkwater
```

وذلك لأنك لم تضف بالكود على انك تريد النزول الى سطر جديد بعد كلمة drink.

كلمة `endl` هي اختصار الى "End Line" وبكل بساطة هو متغير عادي يمكن اخراجه عن طريق `std::cout` ليسبب النزول الى سطر جديد:


```c++
std::cout << "drink" << std::endl;
std::cout << "water";
```

سيكون الناتج كالتالي:

```plaintext
drink
water
```

## التوابع

التوابع ببساطة هي وسيلة لتجميع كود معين بوحدات صغيرة يمكن اعادة استخدامها. مثال عن تابع:

```c++
int add(int a, int b) {
	return a + b;
}

int main() {
	std::cout << add(10, 5);
}
```

> من المهم ترتيب التوابع في الوقت الحالي.

ماذا تتوقع أن يكون الخرج؟ سيكون 15.

في السطر:

```c++
int add(int a, int b)
```

نقوم بتعريف تابع, اسمه `add` ويقوم بارجاع عدد صحيحة (لانه تم كتابة `int` قبل اسم التابع) ويأخذ متحولين كدخل للتابع (بين القوسين), من النوع `int` واسمهما `a` و `b`.

```c++
{
	...
}
```

القوسين يدلان على الblock الي تتبع للتابع

```c++
return a + b
```

كلمة `return` تقوم بالأشار الى اننا نريد ارجاع قيمة `a + b`.

عندما يعمل البرنامج:
- يبدأ في `main`
- ينتقل الى `add` مع العددين 10 و 5
- يقوم بحساب المجموع, 15
- يتم ارجاع العدد 15 للتابع `main`
- تتم تمرير القيمة ل `std::cout` لتظهر على الشاشة

يمكن أيضا تعريف التابع السابق كالتالي:

```c++
int add (int a = 5, int b = 8)
```

في هذه الحالة في حال استخدام هذا التابع بالشكل التالي:

```c++
add();
```

يكون الناتج `13` وذلك لأنه تم استخدام القيم الأفتراضية ل `a = 5` و `b = 8`, لانه لم يتم تحديد قيم أخرى اثناء استعمال التابع.

----

- بعض التوابع قد لا تقوم بارجاع قيمة, ولذلك تستعمل كلمة `void` لنوع خرج التابع عند تعريفه.

## الشروط

### الشروط باستخدام `if`

يمكن في لغات البرمجة القيام (او عدم) القيام بعمليات محددة بحسب اذا ما كان شرط معين محقق او لم يكن.

الصيغة العامة:

```c++
if (شرط) {
	// تنفيذ كود عندما الشرط محقق
}	
```

ويمكن وضع بعدا كلمة `else` والي تفيد في القيام بعملية مختلفة في حال كان الشرط غير محقق:

```c++
if (شرط) {
	// تنفيذ كود عندما الشرط محقق
} else {
	// تنفيذ كود عندما الشرط غير محقق
}
```

مثال:

```c++
int main() {
	// لنأخذ قيمة حرارة الجو من المستخدم
	float temperature;
	std::cout << "Please enter temperature: ";
	std::cin >> temperature;

	// هل الحرارة أكثر من 25؟
	if (temperature > 25) {
		std::cout << "It is hot today" << std::endl;
	} else {
		std::cout << "It is cold today" << std::endl;
	}
}
```

يمكن أيضا استخدام كلمة `else if` لتجريب شرط اخر في حال كان الأول غير محقق. كصيغة عامة:

```c++
if (شرط) {
	// تنفيذ كود عندما الشرط محقق
} else if (شرط اخر) {
	// تنفيذ كود عندما الشرط الآخر محقق
	// (والأول غير محقق)
} else {
	// تنفيذ كود عندما الشرطين غير محققين
}
```

مثال عن فائدة `else if`: لو كان عندك مستخدمين في البرنامج وكان منهم مديرين, ومنهم مشرفين, منهم مستخدمين عاديين, فيمكن كتابة شرط كالتالي:

```c++
if (المستخدم هو مدير) {
	// تنفيذ كود خاص بالمدراء للبرنامج
} else if (المستخدم هو مشرف) {
	// تنفيذ كود خاص بالمشرفين للبرنامج
} else {
	// تنفيذ كود للمستخدمين العاديين فقط
}
```

### الشروط باستخدام `switch`

احيانا يكون لدينا شرط يشبه الشكل التالي:

```c++
if (a == 0) {
	// ...
} else if (a == 1) {
	// ...
} else if (a == 2) {
	// ...
} else if (a == 3) {
	// ...
} else {
	// ...
}
```

لاحظ انه في هذا الشرط, نحن نقوم بتفقد نفس المتحول, `a` ونقارن قيمته مع مجموعة من قيم معلومة. يمكن كتابة هذا الشرط باستخدام تعليمة `switch` كالتالي:

```c++
switch (a) {
	case 0:
		// ...
		break;
	case 1:
		// ...
		break;
	case 2:
		// ...
		break;
	case 3:
		// ...
		break;
	default:
		// ...
		break;
}
```

الفكرة من ال `switch` بسيطة, نقوم بتعريف `switch` على تعبير معين (مثلا `a`) ونقوم بتعريف `case`s, تقوم لغة البرمجة بمقارنة كل `case` مع قيمة التعبير وفي حال التطابق, يتم تشغيل كل الكود الذي هو أسفل ال `case` **(حتى لو كان الكود في `case` مختلف!)** حتى يصل الى نهاية ال `switch ` او الى تعليمة `break;`

تعليمة `default` تشبه `else`, هي `case` افتراضي يتم تشغيله في حال عدم تطابق قيمة التعبير مع اي من الحالات الأخرى, وهي ايضا غير ضرورية اي يمكن عدم ذكرها.

لاحظ وضع `break;` في نهاية كل `case`, لانه بدونها لكان مثلا تم تشغيل الكود في كل ال`cases` لو كانت `a` هي `0`.

أمثلة اخرى:

```c++
int a = 5;

switch (a) {
	case 5:
		std::cout << "i like apples";
	case 8:
		std::cout << "i like oranges";
}
```

لاحظ الخرج:

```plaintext
i like apples
i like oranges
```

تم كتابة السطرين مع أنه ال `case 5` هو الوحيد المحقق, وذلك يعدم وجود `break` تمنع استكمال تشغيل الكود.

مثال اخر:

```c++
int a = 5;

switch (a) {
	case 1:
		std::cout << "i like apples";
		break;
	case 2:
		std::cout << "i like oranges";
		break;
	default:
		std::cout << "i like bananas";
		break;
}
```

في هذه الحالة يكون الخرج:

```plaintext
i like bananas
```

> ينصح بتجريب `switch` في وقت فراغك لأخذ فكرة أكثر رسوخا عن الية عملها.
## الحلقات

الحلقات تسمح بإعادة تنفيذ كود معين طالما شرط معين محقق.

### حلقات `for`

الصيغة العامة:

```c++
for (الخطوة; الشرط; التهيئة الأولية) {
	// تنفيذ كود طالما الشرط محقق
}
```

- التهئية الأولية هي تعليمة واحدة عادة يتم فيها تعريف متحول ليتم استخدامه كعداد للحلقة
- الشرط يستعمل فيه العداد المعرف مسبقا غالبا
- الخطوة هي تعليمة يتم تشغيلها عند نهاية كل حلقة

مثال:

```c++
for (int i = 0; i < 5; i = i + 1) {
	std::cout << "i = " << i << std::endl;
}
```

النتيجة ستكون:

```
i = 0
i = 1
i = 2
i = 3
i = 4
```

---

تعمل حلقة `for` السابقة بالشكل التالي:

- تبدأ بتعريف متحول `i` وله قيمة `0`
- تقوم بالتحقق من الشرط `i < 5`, هل هو محقق؟
- في حال كان محقق, يتم تشغيل الكود وكتابة الكلام على الشاشة
- يتم بعد ذلك تشغيل `i = i + 1`
- ثم تعود الحلقة للتحقق من الشرط, وهكذا

> عندا يصبح الشرط غير محقق, تنتهي الحلقة

### حلقات `while`

حلقات `while` بسيطة جداً:

```c++
while (شرط محقق) {
	// كود
}
```

مثال:

```c++
int age = 0;

while (age < 1 && age > 100) {
	std::cout << "Please enter your age: ";
	std::cin >> age;
}
```

هذا البرنامج يطلب من المستخدم ادخال عمره, لكن في حال قام بإدخال رقم غير صحيح مثلا 0 او 150 فيعود ويسأل المستخدم مجددا عن العمر.


### ملاحظات

- يمكن دائما, بشكل فعلي, التحويل بين `for` و `while`
- لكن `for` غالبا تستخدم عندا يتم عد شيئ معين, وغالبا يكون عدد مرات التكرار معروف بشكل مسبق
- في حين `while` يتم استخدامها في حال عدم وضوح عدد مرات التكرار من البداية
- في معظم الوقت يتم استعمال `for` بدلا من `while` بشكل عملي.

## ال namespaces

لاحظ اننا كنا نستعمل `std::` في كل مرة اردنا فيها استخدام اي شيئ من `iostream`:

```c++
#include <iostream>

int main() {
	std::cout << "hello world" << std::endl;
}
```

الهدف من وجود `std::` هو منع تضارب تسمية المتحولات. مثلاً تخيل لو أنك أردت تعريف متحول اسمه `cout`, في هذه الحالة لا يحصل تضارب لأنه `cout` حاليا هي ضمن `namespace` اسمه `std` ومنه تستطيع لغة البرمجة التفريق بين الأثنين.

لكن توجد تعليمة يمكن استعمالها بحيث يصبح بالأمكان استعمال `cout` وغيرها من مكونات `iostream` من غير ذكر ال `namespace` الذي هو `std` في كل مرة:

```c++
using namespace std;
```

هذه التعليمة يمكن وضعا ضمن التابع `main` (او اي تابع اخر):

```c++
int main() {
	using namespace std;
	cout << "hello world" << endl;
}
```

...ليكون تأثيرها فقط ضمن التابع

أو يمكن وضعها خارج أي تابع ليكون تأثيرها يشمل الملف بالكامل:

```c++
using namespace std;

int main() {
	cout << "hello world" << endl;
}
```

## اشياء اخرى

### الحرف `\n`

يمكن استعمال `\n` بدلا من `std::endl` للنزول لسطر جديد:

```c++
std::cout << "hello world\n";
```

لاحظ وضع `\n` ضمن `std::string` وذلك لأن `\n` هو حرف.

