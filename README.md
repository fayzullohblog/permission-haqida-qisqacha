# permission
PERMISSION
Bu document bizga standart konfiguratsiyadagi djangoning authenticationdan qanday foydalanishlikni tushuntiradi. Bu konfugratsiya xizmat kursatishga moslashtirilgan eng kotta kerakli loytxalarni rivojlantirish imkoni beradi,turli keng miqyosdagi vazifalarga oqilani boshqarish va password av permassion (parol va ruxsat) larni extiyotkorligini osherish, project ushun projectda mavjud bulgan authentication standart xolatdagindan o'zgartirish kerak buladi, Djnago kub qullab quvvotlaydi authenticationdi kingaytrishi va moslashtirishni. Django authenticationi authentication tizimiga umumiy nazaryabilan bergalikda authetication va authorizationdi qullab quvvotlaydi.

# USER objects
User objectlar authentication sestimasining asosyiy qismidir. Odatda sizning sitengiz bilan odamlarni qizig'ishini ifodalash mumkin va yaratuvchi tomanidan birlashtiruvchi tartibdan foydalanib kirish,user profilelar bilan ruyxatdan utish cheklanishlarni yoqish uchun User objectslar ishlatiladi. Djangoning authentication framworkeda mavjuda bulgan yagona class user yani " superuser " maxsus attributeslarni tartiblash user buladi, user objectsning classes turli xil bulamydi,

# STANDART USER ATRIBUTES larinig asosiylari

1-username
2-password
3-email,
4-first_name,
5-last_name,

# USERS yaratish, terminal yoki visual codesdan foydalnishiz mumkin.
1. yangi project yaratib olayabman va unga manage.py va config nomli project yarataman 
<img width="1440" alt="Screenshot 2022-09-27 at 15 07 16" src="https://user-images.githubusercontent.com/97334206/192498116-ec154279-25e2-4a72-916c-77c374f4a9e4.png">
2. quyidagi command orqali homeapp nomli app yaratamiz
<img width="1440" alt="Screenshot 2022-09-27 at 15 21 51" src="https://user-images.githubusercontent.com/97334206/192501278-83d4a5a1-2f1f-498e-90b8-3357893d9021.png">
3. code . command orqali visual studioni ochib olaman
<img width="1407" alt="Screenshot 2022-09-27 at 15 12 29" src="https://user-images.githubusercontent.com/97334206/192499586-ebe780e9-782d-44e0-8d1a-d32ac8e425a3.png">
4. app filni config/setting.py ichidagi INSTALL_APSS uzgaruvchiga qushamiz.
<img width="936" alt="Screenshot 2022-09-27 at 15 24 24" src="https://user-images.githubusercontent.com/97334206/192501711-7562e512-fa7b-46e1-904d-e3e083105ed5.png">
5. python3 manage.py runserver ishlayotganini tekshirib kuramiz 
<img width="1433" alt="Screenshot 2022-09-27 at 15 30 18" src="https://user-images.githubusercontent.com/97334206/192502991-0c320856-3bd1-42d5-8b79-017f21d2ab8f.png">
6. ishlaaybdi
<img width="807" alt="Screenshot 2022-09-27 at 15 32 37" src="https://user-images.githubusercontent.com/97334206/192503286-c22f9eea-22e5-4eac-afbe-e8491e8936cd.png">

7. makemigrations va migrate yani malumotlarimni basaga yaratib olishim kerak, bu command bajarilmasa createsuperuser yaratib bulmaydi
<img width="1386" alt="Screenshot 2022-09-27 at 15 37 02" src="https://user-images.githubusercontent.com/97334206/192504128-ae3a6dc9-fa37-4fbd-9feb-740dcf06b3f4.png">

8. asosiy admindi yarataman, local ishlayotganda hardoim asosiy admin compyuter projectni yaratayotgan kishi buladi va quyidagi command orqali admin va password yarataman
! islatma::::: superuser yaratayotganda password kurinmaydi,nima yozyotgizdi islab qoling agarda isdan chiqsa shu comandlar orqali yani boshqa createsuperuser yaratib olishingiz mumkin.

<img width="1432" alt="Screenshot 2022-09-27 at 15 38 48" src="https://user-images.githubusercontent.com/97334206/192504507-db46be35-c634-4136-91f7-14659ff42742.png">

9. endi site qayta ishlatib urlga http://127.0.0.1:8000/admin/ shunday yozamiz va bizga shunday oyna ochilish kerak

<img width="813" alt="Screenshot 2022-09-27 at 15 44 58" src="https://user-images.githubusercontent.com/97334206/192505710-7f00fd62-7f02-4614-817f-628f3e277b63.png">

10. username va passwordga biz azgina vaqt oldin yaratgan username va passwordlarni kiritaman.
manda username va password ( admin, 1) edi:
<img width="766" alt="Screenshot 2022-09-27 at 15 46 36" src="https://user-images.githubusercontent.com/97334206/192506104-0b03cc57-766b-4957-8485-1324a7f1cc94.png">

11. shu xolda ochilish kerak, 
<img width="817" alt="Screenshot 2022-09-27 at 15 47 00" src="https://user-images.githubusercontent.com/97334206/192506174-40511825-6367-42dc-95ba-538d164d57c6.png">

# keling endi shu saxifadagi USUERS VA GROUP haqida azgina tanishsak
1. USERS buyerda asosiy admin va asosiy admin ruxsat bergan kichik admin lar buladi,
kichik adminlar asosiy admin ruxsat bergan buyruqlardan ortig'narsa bajara olmaydi, va sosiy admin xoxlagancha kichik adminlar yaratish mumkin va kotta yani uziga teng bulgan adminlar xam yaratish mumkin xammasi kotta admin qulida.
2. GROUP bulimida, bir nechta giuruhlar buladi va bu guruhlarni ustidan nazoratni kotta va kichik adminlar olib boradi, ammo kotta admin kichik adminga qanday ruxsat bergan bulsa shunday GROUP larni nazorat qiladi oladi, 

# demak bizning asosiy ishimiz kichik admin va guruhlarni nazorat qilish va kimlar bizning guruhimizdan foydalnayabdi boshqarish, xullas GROUP va KICHIK ADMIN lar ustidan authentication va permission( ruxsat)larni nazorat qiladi.
1. xozir biz mening uzim admin nomli userman asosiy kotta, endi qushimcha userlar qushishim kerak, buning 2 ta yuli bor: 1- admin panelga utib qushish, 2- terminal ochib shell ichiga kirib qushish, biz 2- usuldan foydalanib kurmiz. chunki bu usil kub projectlarda as qotadi: 
<img width="1353" alt="Screenshot 2022-09-27 at 16 04 01" src="https://user-images.githubusercontent.com/97334206/192509214-74af230d-432f-4d7b-b042-d45dd85a49fb.png">

2. quyidagi command orqali shelga kirib olamiz:
 <img width="1437" alt="Screenshot 2022-09-27 at 16 09 22" src="https://user-images.githubusercontent.com/97334206/192510217-29e0cec8-d8cd-4ab5-8ae0-fbf6ac5e148c.png">
3. userni chaqirib olamiz
 <img width="1439" alt="Screenshot 2022-09-27 at 16 13 01" src="https://user-images.githubusercontent.com/97334206/192510886-b050ef9e-ff7b-4a92-bb28-278d16d9b7f3.png">
4. user qushamiz
5. 2 ta user qushdim,
 <img width="1081" alt="Screenshot 2022-09-27 at 18 42 24" src="https://user-images.githubusercontent.com/97334206/192542940-c5f18042-5255-4d4c-aede-a9a034137a32.png">
<img width="1396" alt="Screenshot 2022-09-27 at 18 43 12" src="https://user-images.githubusercontent.com/97334206/192543143-e6deba90-24f3-4c6e-962d-76af25fbb03d.png">
6. qushilgan userlarni admin fileda kuramiz
                                          
<img width="853" alt="Screenshot 2022-09-27 at 18 55 03" src="https://user-images.githubusercontent.com/97334206/192546061-6ae9ee42-a68d-4a39-9dd0-847997993a38.png">

# Permission and Authorization
!! eslatma !! Django o'zining tayyor permission tizimi bilan birga  keladi. bu userlarning gruhlarda va userlarda maxsus aniqligini taminlaydi.
biz bunda django admi site orqali foydalanmiz ammo siz uzingizdi codingizni yozishingiz mumkin,
# Django admin siteni permissionlaridan quyidagi ruyxat buyicha foydalanamiz.
------------------------------------------------------------------------------------------------------
1--* objectlarni ko'rishga kirish uchun quyidagi object turidagi 'ko'rish'(view) va 'o'zgartirish'(change) bilan ruxsati bilan userlar cheklanadi
2--* formani ko'rish uchun kirish quyidagi object turi uchun 'qushish'(add) ruxsati bilan userlarga cheklanadi.
3--* listni o'zgartirishni ko'rishga kirish, shakilni 'o'zgartirish' (chanage), quyidagi object turi uchin 'o'zgartirish'(change) ruxsati bilan userlarga cheklov beriladi.
4--* objectni 'uchirish' uchun kirish quyidagi objectlar uchun 'delete' ruxsati bilan userlarga cheklov quyiladi.
------------------------------------------------------------------------------------------------------

!! islatma: Permissionlar objectning turiga qarab o'rnatilishi mumkin ammo muayyan object uchun bulishi mumkin.

has_view_permission(): ---> kurish
has_read_permission(): ---> uqish
has_add_permission():  ---> qushish
has_delete_permission(): ---> uchirish

ModelAdmin class ichida shu model orqali yuqorida taqdimm etilgam methodlar yordamida qullaniladi.

