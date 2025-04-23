<script type="text/javascript">
        var gk_isXlsx = false;
        var gk_xlsxFileLookup = {};
        var gk_fileData = {};
        function filledCell(cell) {
          return cell !== '' && cell != null;
        }
        function loadFileData(filename) {
        if (gk_isXlsx && gk_xlsxFileLookup[filename]) {
            try {
                var workbook = XLSX.read(gk_fileData[filename], { type: 'base64' });
                var firstSheetName = workbook.SheetNames[0];
                var worksheet = workbook.Sheets[firstSheetName];

                // Convert sheet to JSON to filter blank rows
                var jsonData = XLSX.utils.sheet_to_json(worksheet, { header: 1, blankrows: false, defval: '' });
                // Filter out blank rows (rows where all cells are empty, null, or undefined)
                var filteredData = jsonData.filter(row => row.some(filledCell));

                // Heuristic to find the header row by ignoring rows with fewer filled cells than the next row
                var headerRowIndex = filteredData.findIndex((row, index) =>
                  row.filter(filledCell).length >= filteredData[index + 1]?.filter(filledCell).length
                );
                // Fallback
                if (headerRowIndex === -1 || headerRowIndex > 25) {
                  headerRowIndex = 0;
                }

                // Convert filtered JSON back to CSV
                var csv = XLSX.utils.aoa_to_sheet(filteredData.slice(headerRowIndex)); // Create a new sheet from filtered array of arrays
                csv = XLSX.utils.sheet_to_csv(csv, { header: 1 });
                return csv;
            } catch (e) {
                console.error(e);
                return "";
            }
        }
        return gk_fileData[filename] || "";
        }
        </script><!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Культура й повсякденне життя кінця 18 – початку 20 ст.</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body {
            font-family: 'Georgia', serif;
            background-color: #f8f1e9;
        }
    </style>
</head>
<body class="text-gray-800">
    <!-- Header -->
    <header class="bg-amber-800 text-white py-8 shadow-lg">
        <div class="container mx-auto px-4">
            <h1 class="text-4xl font-bold text-center">Культура й повсякденне життя кінця 18 – початку 20 ст.</h1>
            <nav class="mt-6">
                <ul class="flex justify-center space-x-10 text-lg">
                    <li><a href="#culture" class="hover:text-amber-300">Культура</a></li>
                    <li><a href="#daily-life" class="hover:text-amber-300">Повсякденне життя</a></li>
                    <li><a href="#art" class="hover:text-amber-300">Мистецтво</a></li>
                    <li><a href="#society" class="hover:text-amber-300">Суспільство</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="bg-cover bg-center h-[500px] flex items-center justify-center" style="background-image: url('https://images.unsplash.com/photo-1505664194779-8beaceb93744?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80')">
        <div class="text-center bg-black bg-opacity-60 p-8 rounded-lg">
            <h2 class="text-5xl font-bold text-white mb-4">Епоха змін</h2>
            <p class="text-xl text-white max-w-2xl">Пориньте в багатий світ культури, мистецтва та повсякденного життя кінця 18 – початку 20 століття, коли Європа та Україна переживали значні соціальні й культурні трансформації.</p>
        </div>
    </section>

    <!-- Culture Section -->
    <section id="culture" class="py-16">
        <div class="container mx-auto px-4">
            <h3 class="text-3xl font-bold text-center mb-10">Культура</h3>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="bg-white p-8 rounded-lg shadow-lg">
                    <h4 class="text-2xl font-semibold mb-4">Література</h4>
                    <p>Ця епоха подарувала світові романтизм, реалізм і початки модернізму. У Європі творили Йоганн Вольфганг фон Гете, Чарльз Діккенс, Лев Толстой, Федір Достоєвський, які досліджували людську душу та суспільні проблеми. В Україні Тарас Шевченко своєю поезією заклав фундамент національної літератури, а Іван Франко та Леся Українка підняли її на новий рівень, звертаючись до тем свободи, боротьби та людської гідності.</p>
                </div>
                <div class="bg-white p-8 rounded-lg shadow-lg">
                    <h4 class="text-2xl font-semibold mb-4">Музика</h4>
                    <p>Музика цього періоду відзначалася розмаїттям: від класицизму Людвіга ван Бетховена до романтизму Фридерика Шопена та національних мотивів Петра Чайковського. В Україні Микола Лисенко створив основу для національної класичної музики, використовуючи народні мелодії. Оперні театри у Львові та Києві ставали центрами культурного життя.</p>
                </div>
                <div class="bg-white p-8 rounded-lg shadow-lg">
                    <h4 class="text-2xl font-semibold mb-4">Театр</h4>
                    <p>Театр був популярною розвагою як для еліти, так і для простого люду. В Україні Іван Котляревський своєю п’єсою «Наталка Полтавка» започаткував національну драматургію. Марко Кропивницький та Михайло Старицький створювали професійні театральні трупи, які гастролювали містами, популяризуючи українську мову та культуру.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Daily Life Section -->
    <section id="daily-life" class="bg-amber-50 py-16">
        <div class="container mx-auto px-4">
            <h3 class="text-3xl font-bold text-center mb-10">Повсякденне життя</h3>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="bg-white p-8 rounded-lg shadow-lg">
                    <h4 class="text-2xl font-semibold mb-4">Побут і житло</h4>
                    <p>Селяни жили в хатах, збудованих із дерева, глини чи соломи, з печами для опалення та приготування їжі. У містах багатші верстви мешкали в кам’яних будинках із розкішним оздобленням. З початком індустріалізації з’явилися фабрики, залізниці, телеграф, а на початку 20 ст. – електричне освітлення та водопровід, що змінило міське життя.</p>
                </div>
                <div class="bg-white p-8 rounded-lg shadow-lg">
                    <h4 class="text-2xl font-semibold mb-4">Одяг</h4>
                    <p>Селянський одяг був практичним і відображав регіональні особливості: вишиванки, свитки, плахти. У містах європейська мода диктувала тренди: жінки носили корсети, пишні сукні, капелюшки, а чоловіки – сюртуки, фраки, циліндри. Наприкінці 19 ст. мода стала більш демократичною, з’явилися простіші силуети та фабричний одяг.</p>
                </div>
                <div class="bg-white p-8 rounded-lg shadow-lg">
                    <h4 class="text-2xl font-semibold mb-4">Харчування</h4>
                    <p>Селяни споживали просту їжу: борщ, каші, хліб, картоплю, квасолю. М’ясо було рідкістю, хіба на свята. У містах багатші верстви їли м’ясні страви, випічку, імпортні делікатеси. Чай і кава стали популярними напоями, а в шинках подавали горілку та медовуху. Наприкінці 19 ст. з’явилися перші ресторани.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Art Section -->
    <section id="art" class="py-16">
        <div class="container mx-auto px-4">
            <h3 class="text-3xl font-bold text-center mb-10">Мистецтво</h3>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="bg-white p-8 rounded-lg shadow-lg">
                    <img src="https://images.unsplash.com/photo-1576502200916-3808e07386a5?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Painting" class="h-48 w-full object-cover rounded-lg mb-4">
                    <h4 class="text-2xl font-semibold mb-4">Живопис</h4>
                    <p>Романтизм прославляв природу та почуття, реалізм зображав життя без прикрас. В Україні Ілля Рєпін створював епічні полотна, як-от «Запорожці пишуть листа турецькому султану», а Микола Ге та Олександр Мурашко зверталися до портретного жанру. Народні мотиви надихали на створення іконопису та декоративного мистецтва.</p>
                </div>
                <div class="bg-white p-8 rounded-lg shadow-lg">
                    <img src="https://images.unsplash.com/photo-1505664063603-35e4cc48c8e6?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Architecture" class="h-48 w-full object-cover rounded-lg mb-4">
                    <h4 class="text-2xl font-semibold mb-4">Архітектура</h4>
                    <p>Бароко і класицизм домінували на початку періоду, але в 19 ст. їх змінили еклектика та модерн. В Україні будували палаци (як-от Маріїнський у Києві), церкви з позолотою, а в містах з’явилися багатоповерхові будинки з ліпниною та кованими балконами. Модерн приніс асиметричні форми та рослинні орнаменти.</p>
                </div>
                <div class="bg-white p-8 rounded-lg shadow-lg">
                    <img src="https://images.unsplash.com/photo-1519671482749-fd09be7ccebf?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Sculpture" class="h-48 w-full object-cover rounded-lg mb-4">
                    <h4 class="text-2xl font-semibold mb-4">Скульптура</h4>
                    <p>Скульптура відображала класичні ідеали та історичні сюжети. У Європі Огюст Роден революціонізував мистецтво динамічними формами. В Україні скульптури прикрашали міські площі, церкви та садиби, часто зображуючи історичних діячів чи релігійні сцени. Наприкінці періоду з’явилися модерністські експерименти.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Society Section -->
    <section id="society" class="bg-amber-50 py-16">
        <div class="container mx-auto px-4">
            <h3 class="text-3xl font-bold text-center mb-10">Суспільство та зміни</h3>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div class="bg-white p-8 rounded-lg shadow-lg">
                    <h4 class="text-2xl font-semibold mb-4">Соціальна структура</h4>
                    <p>Суспільство було чітко поділене на стани: дворянство, селянство, міщанство. У 19 ст. скасування кріпацтва (1861 р. у Російській імперії) дало селянам свободу, але не землю, що призвело до бідності. Водночас зростала роль інтелігенції та робітничого класу, який формувався в містах завдяки індустріалізації.</p>
                </div>
                <div class="bg-white p-8 rounded-lg shadow-lg">
                    <h4 class="text-2xl font-semibold mb-4">Освіта і наука</h4>
                    <p>Освіта була доступною переважно для еліти, але в 19 ст. відкривалися народні школи. Університети в Харкові, Києві, Львові ставали осередками науки. Винаходи, як-от паровий двигун, електрика, телефон, змінили світ. В Україні Пирогов і Мечников зробили внесок у медицину, а Грушевський – в історію.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-amber-800 text-white py-8">
        <div class="container mx-auto px-4 text-center">
            <p class="text-lg">© 2025 Культура й повсякденне життя кінця 18 – початку 20 ст. Усі права захищено.</p>
            <p class="mt-2">Створено для тих, хто прагне пізнати історію.</p>
        </div>
    </footer>
</body>
</html>
