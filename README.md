<div class="max-w-4xl mx-auto p-4 md:p-8">
    <header class="text-center mb-10">
        <h1 class="text-3xl md:text-4xl font-extrabold text-blue-700 mb-2">اتحقق واتأكد</h1>
        <p class="text-gray-600">أداة للتحقق من مصداقية المحتوى الرقمي المتمثل في الأخبار، الروابط، وتحليل التزييف العميق للصور.</p>
    </header>

    <!-- --- Introductory Section (المقدمة) --- -->
    <div class="bg-blue-50 p-6 md:p-8 rounded-xl border-l-4 border-blue-400 mb-8">
        <h2 class="text-xl font-bold text-blue-800 mb-3">مرحباً بك في اتحقق واتأكد!</h2>
        <p class="text-gray-700 leading-relaxed mb-3">
            هذه الأداة هي إحدى محاولات الباحثة **سهيله شمسو** لمكافحة التزييف العميق (Deepfake) باستخدام سلاح الذكاء الاصطناعي نفسه في كشف الحقائق.
            في عصر المعلومات، أصبح التمييز بين الحقيقي والمزيف تحدياً كبيراً. هذه الأداة تستخدم قوة الذكاء الاصطناعي (نموذج Gemini) وخاصية البحث الفوري على الويب لمساعدتك في فحص المحتوى وتقديم تحليل واضح ونسبة مئوية لتقييم المصداقية.
        </p>
        <p class="text-sm text-blue-600 font-semibold">
            تم إعداد هذه الأداة في نوفمبر ٢٠٢٥.
        </p>
    </div>
    <!-- --- End Introductory Section --- -->

    <!-- Main Card for Inputs -->
    <div class="bg-white p-6 md:p-8 rounded-xl shadow-custom border border-gray-100">

        <div class="mb-6">
            <label for="inputType" class="block text-lg font-medium text-gray-700 mb-2">نوع المحتوى المراد التحقق منه:</label>
            <select id="inputType" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500 bg-gray-50">
                <option value="text">خبر أو نص أو رابط موقع (لتحليل الحقائق)</option>
                <option value="image">صورة (لتحليل التزييف العميق/التلاعب)</option>
            </select>
        </div>

        <!-- Text/Link Input Area -->
        <div id="textInputGroup" class="mb-6">
            <label for="textInput" class="block text-lg font-medium text-gray-700 mb-2">أدخل الخبر، النص، أو رابط الموقع هنا:</label>
            <textarea id="textInput" rows="4" class="w-full p-4 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500 placeholder-gray-400" placeholder="مثال: رابط لموقع إخباري، أو نص خبر كامل..."></textarea>
        </div>

        <!-- Image Input Area (Hidden by default) -->
        <div id="imageInputGroup" class="mb-6 hidden">
            <label for="imageUpload" class="block text-lg font-medium text-gray-700 mb-2">اختر صورة للتحليل (Deepfake):</label>
            <input type="file" id="imageUpload" accept="image/*" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500 bg-white">
            <div id="imagePreview" class="mt-4 hidden max-w-full h-auto rounded-lg overflow-hidden border border-gray-200">
                <img id="previewImg" class="w-full h-auto object-cover">
            </div>
        </div>
        
        <button id="checkButton" onclick="checkAuthenticity()" class="w-full py-3 px-6 bg-blue-600 text-white font-bold rounded-lg shadow-md hover:bg-blue-700 transition duration-300 ease-in-out transform hover:scale-[1.01] disabled:bg-gray-400">
            تحقق من المصداقية
        </button>

        <!-- Loading Indicator -->
        <div id="loadingIndicator" class="mt-6 text-center hidden">
            <svg class="animate-spin h-5 w-5 text-blue-500 mx-auto" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
            </svg>
            <p class="text-sm text-gray-500 mt-2">جاري تحليل المحتوى والبحث في المصادر الموثوقة...</p>
        </div>
    </div>

    <!-- Result Section -->
    <div id="resultContainer" class="mt-8">
        <h2 class="text-2xl font-semibold text-gray-800 mb-4 border-b pb-2">نتيجة التحقق</h2>
        <div id="resultBox" class="result-box p-6 rounded-xl text-center font-bold text-xl flex flex-col items-center justify-center bg-gray-100 text-gray-600">
            النتيجة ستظهر هنا بعد التحقق.
        </div>
        <div id="explanationBox" class="mt-4 p-4 bg-white rounded-lg shadow-inner border hidden">
            <p class="text-gray-700 font-medium mb-2">شرح التحليل:</p>
            <p id="explanationText" class="text-gray-600 leading-relaxed"></p>
            <div id="sourcesBox" class="mt-3 pt-3 border-t border-gray-100 text-sm hidden">
                <p class="font-semibold text-gray-500 mb-1">المصادر المعتمدة للبحث:</p>
                <ul id="sourcesList" class="list-disc list-inside text-left text-gray-500 space-y-1"></ul>
            </div>
        </div>
    </div>

</div>

<script>
    // Set API key placeholder
    const apiKey = "// Set API key placeholder (تعيين المفتاح الاحتياطي لـ API)
