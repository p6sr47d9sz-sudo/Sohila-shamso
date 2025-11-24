# Sohila-shamso
هذه الاداة احدى محاولات الباحثة سهيله شمسو لمكافحة التزييف العميق
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>اتحقق واتأكد</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* تعريف خط Inter والتحسينات الجمالية */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f7f9fb;
            color: #1f2937;
        }
        .result-box {
            transition: all 0.3s ease-in-out;
            min-height: 120px; /* Increased height to accommodate percentage */
        }
        .shadow-custom {
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.05), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
        .confidence-percentage {
            font-size: 2.5rem; /* Larger font for percentage */
            line-height: 1;
            margin-bottom: 0.5rem;
            font-weight: 800; /* Extra bold */
        }
    </style>
</head>
<body>

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
const apiKey = ""; 
";
        // تحديد النموذج المستخدم للتحقق من الحقائق وتحليل الصور
        const factCheckModel = 'gemini-2.5-flash-preview-09-2025';
        const imageAnalysisModel = 'gemini-2.5-flash-preview-09-2025';
        
        // DOM elements (عناصر الواجهة)
        const inputType = document.getElementById('inputType');
        const textInputGroup = document.getElementById('textInputGroup');
        const imageInputGroup = document.getElementById('imageInputGroup');
        const textInput = document.getElementById('textInput');
        const imageUpload = document.getElementById('imageUpload');
        const previewImg = document.getElementById('previewImg');
        const imagePreview = document.getElementById('imagePreview');
        const checkButton = document.getElementById('checkButton');
        const loadingIndicator = document.getElementById('loadingIndicator');
        const resultBox = document.getElementById('resultBox');
        const explanationBox = document.getElementById('explanationBox');
        const explanationText = document.getElementById('explanationText');
        const sourcesBox = document.getElementById('sourcesBox');
        const sourcesList = document.getElementById('sourcesList');

        // --- UI Control Functions (وظائف التحكم في الواجهة) ---

        // Toggle visibility based on selected input type (تبديل الظهور حسب نوع الإدخال)
        inputType.addEventListener('change', () => {
            if (inputType.value === 'image') {
                textInputGroup.classList.add('hidden');
                imageInputGroup.classList.remove('hidden');
            } else {
                textInputGroup.classList.remove('hidden');
                imageInputGroup.classList.add('hidden');
                imagePreview.classList.add('hidden');
            }
            // Reset result display (إعادة تعيين عرض النتيجة)
            resetResult();
        });

        // Image file preview (معاينة ملف الصورة)
        imageUpload.addEventListener('change', (event) => {
            resetResult();
            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = (e) => {
                    previewImg.src = e.target.result;
                    imagePreview.classList.remove('hidden');
                };
                reader.readAsDataURL(file);
            } else {
                imagePreview.classList.add('hidden');
            }
        });

        function resetResult() {
            resultBox.className = 'result-box p-6 rounded-xl text-center font-bold text-xl flex flex-col items-center justify-center bg-gray-100 text-gray-600';
            resultBox.innerHTML = 'النتيجة ستظهر هنا بعد التحقق.';
            explanationBox.classList.add('hidden');
            sourcesBox.classList.add('hidden');
        }

        function setLoading(isLoading) {
            checkButton.disabled = isLoading;
            loadingIndicator.classList.toggle('hidden', !isLoading);
            if (isLoading) {
                resetResult();
            }
        }

        // --- Core Verification Logic (منطق التحقق الأساسي) ---

        async function checkAuthenticity() {
            setLoading(true);
            resetResult();

            const type = inputType.value;
            let resultData = { text: null, sources: [] };

            try {
                if (type === 'text') {
                    const text = textInput.value.trim();
                    if (!text) {
                        showError("الرجاء إدخال نص أو رابط موقع للتحقق.");
                        return;
                    }
                    resultData = await factCheckContent(text);

                } else if (type === 'image') {
                    const file = imageUpload.files[0];
                    if (!file) {
                        showError("الرجاء اختيار صورة للتحقق.");
                        return;
                    }
                    if (file.size > 5 * 1024 * 1024) { // Max 5MB
                        showError("حجم الصورة كبير جداً (الحد الأقصى 5 ميجابايت).");
                        return;
                    }
                    resultData = await deepfakeCheck(file);
                }

                // Process and display the final result (معالجة وعرض النتيجة النهائية)
                displayResult(resultData.text, resultData.sources);

            } catch (error) {
                console.error("Verification failed:", error);
                showError("حدث خطأ أثناء الاتصال بالخادم. حاول مرة أخرى.");
            } finally {
                setLoading(false);
            }
        }

        // Handles fact-checking for text and links using search grounding (تحقق الحقائق باستخدام البحث)
        async function factCheckContent(content) {
            // Updated system prompt to include percentage request (تحديث رسالة النظام لتشمل النسبة المئوية)
            const systemPrompt = `Act as a professional fact-checker. Your task is to analyze the provided content (text or a website summary/link description) using Google Search grounding. Based on verified sources, determine if the claim is 'REAL' (True/Safe) or 'FAKE' (False/Unsafe). Start your response with exactly one of the following structured labels: 'VERDICT: REAL|95%' or 'VERDICT: FAKE|88%'. The percentage must reflect your confidence in the verdict (ranging from 70% to 99%). Follow this with a brief explanation in Arabic that cites the sources.`;
            
            const userQuery = `تحقق من صحة الخبر/النص/الرابط التالي: ${content}`;
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/${factCheckModel}:generateContent?key=${apiKey}`;

            const payload = {
                contents: [{ parts: [{ text: userQuery }] }],
                tools: [{ "google_search": {} }], // Use Google Search for grounding (استخدام بحث جوجل كمصدر)
                systemInstruction: { parts: [{ text: systemPrompt }] },
            };

            return await fetchGeminiApi(apiUrl, payload);
        }

        // Handles image analysis for deepfake/manipulation (تحليل الصور للتزييف)
        async function deepfakeCheck(file) {
             // Updated system prompt to include percentage request
            const systemPrompt = `Act as an image forensic expert. Analyze the provided image for signs of digital manipulation, splicing, deepfake artifacts, or inconsistencies in lighting, shadows, or texture. Respond with a clear assessment. Start your response with exactly one of the following structured labels: 'VERDICT: REAL|95%' or 'VERDICT: FAKE|88%'. The percentage must reflect your confidence in the verdict (ranging from 70% to 99%). Follow this with a brief explanation in Arabic.`;
            
            const base64Data = await fileToBase64(file);
            const userPrompt = "قم بتحليل هذه الصورة بحثاً عن علامات التلاعب أو التزييف العميق (Deepfake).";
            
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/${imageAnalysisModel}:generateContent?key=${apiKey}`;

            const payload = {
                contents: [
                    {
                        role: "user",
                        parts: [
                            { text: userPrompt },
                            {
                                inlineData: {
                                    mimeType: file.type,
                                    data: base64Data
                                }
                            }
                        ]
                    }
                ],
                // No search tool for direct image analysis (لا حاجة لالبحث في تحليل الصور المباشر)
                systemInstruction: { parts: [{ text: systemPrompt }] },
            };

            return await fetchGeminiApi(apiUrl, payload);
        }

        // General function to handle API fetch with retries (وظيفة عامة للتعامل مع نداء API)
        async function fetchGeminiApi(apiUrl, payload, attempt = 1) {
            const MAX_RETRIES = 3;
            try {
                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                if (!response.ok) {
                    if (response.status === 429 && attempt < MAX_RETRIES) {
                        const delay = Math.pow(2, attempt) * 1000; // Exponential backoff (تأخير تصاعدي)
                        await new Promise(resolve => setTimeout(resolve, delay));
                        return fetchGeminiApi(apiUrl, payload, attempt + 1);
                    }
                    throw new Error(`API Request failed with status: ${response.status}`);
                }

                const result = await response.json();
                const candidate = result.candidates?.[0];

                if (!candidate || !candidate.content?.parts?.[0]?.text) {
                    throw new Error("Received an empty or malformed response from the model.");
                }

                // 1. Extract the generated text (استخراج النص المولد)
                const text = candidate.content.parts[0].text;

                // 2. Extract grounding sources (if available) (استخراج مصادر البحث إن وجدت)
                let sources = [];
                const groundingMetadata = candidate.groundingMetadata;
                if (groundingMetadata && groundingMetadata.groundingAttributions) {
                    sources = groundingMetadata.groundingAttributions
                        .map(attribution => ({
                            uri: attribution.web?.uri,
                            title: attribution.web?.title,
                        }))
                        .filter(source => source.uri && source.title);
                }

                return { text, sources };

            } catch (error) {
                console.error("API Call Error:", error);
                throw error;
            }
        }
        
        // Helper to convert File object to Base64 string (تحويل الملف إلى Base64)
        function fileToBase64(file) {
            return new Promise((resolve, reject) => {
                const reader = new FileReader();
                reader.onloadend = () => {
                    // Extract the base64 part (after the comma)
                    const base64String = reader.result.split(',')[1];
                    resolve(base64String);
                };
                reader.onerror = reject;
                reader.readAsDataURL(file);
            });
        }

        // --- Display Functions (وظائف العرض) ---

        function displayResult(rawText, sources) {
            // New Regex to capture VERDICT (REAL|FAKE) AND Percentage (e.g., |95%) (التعابير العادية لاستخلاص النتيجة والنسبة)
            const match = rawText.match(/VERDICT:\s*(REAL|FAKE)\|(\d{2,3})%/i); 

            const verdict = match ? match[1].toUpperCase() : 'UNKNOWN';
            let percentage = match ? parseInt(match[2], 10) : 0;
            
            // Fallback confidence percentage if parsing fails or model doesn't follow instructions (نسبة احتياطية في حالة الفشل)
            if (percentage < 70 || percentage > 99) {
                percentage = verdict === 'REAL' ? 95 : (verdict === 'FAKE' ? 88 : 0);
            }


            // Extract explanation (text after the VERDICT line) (استخراج الشرح)
            let explanation = rawText;
            if (match) {
                // Find the index right after the full matched string (e.g., "VERDICT: REAL|95%")
                explanation = rawText.substring(rawText.indexOf(match[0]) + match[0].length).trim();
                // Clean up any leading newline characters
                if (explanation.startsWith('\n')) explanation = explanation.substring(1).trim();
            }

            let resultTitle = 'غير معروف';
            let bgColor = 'bg-yellow-200';
            let textColor = 'text-yellow-800';
            let borderColor = 'border-yellow-300';
            // Formatting the percentage for display (تنسيق النسبة المئوية للعرض)
            let confidenceText = percentage > 0 ? `<div class="confidence-percentage">${percentage}%</div>` : '';


            if (verdict === 'REAL') {
                resultTitle = `${confidenceText} ✅ حقيقي / آمن`;
                bgColor = 'bg-green-100';
                textColor = 'text-green-700';
                borderColor = 'border-green-300';
            } else if (verdict === 'FAKE') {
                resultTitle = `${confidenceText} ❌ مزيف / غير آمن`;
                bgColor = 'bg-red-100';
                textColor = 'text-red-700';
                borderColor = 'border-red-300';
            }

            // Update Result Box: using innerHTML is necessary for the dynamic percentage styling (تحديث صندوق النتيجة)
            resultBox.className = `result-box p-6 rounded-xl text-center font-bold text-xl flex flex-col items-center justify-center ${bgColor} ${textColor} ${borderColor} border-2`;
            resultBox.innerHTML = resultTitle;

            // Update Explanation Box (تحديث صندوق الشرح)
            explanationText.textContent = explanation;
            explanationBox.classList.remove('hidden');

            // Update Sources (if available) (تحديث المصادر إن وجدت)
            sourcesList.innerHTML = '';
            if (sources && sources.length > 0) {
                sourcesBox.classList.remove('hidden');
                sources.forEach(source => {
                    const listItem = document.createElement('li');
                    const link = document.createElement('a');
                    link.href = source.uri;
                    link.textContent = source.title || source.uri;
                    link.target = '_blank';
                    link.className = 'hover:text-blue-600 transition duration-150';
                    listItem.appendChild(link);
                    sourcesList.appendChild(listItem);
                });
            } else {
                 sourcesBox.classList.add('hidden');
            }
        }

        function showError(message) {
            resultBox.className = 'result-box p-6 rounded-xl text-center font-bold text-xl flex flex-col items-center justify-center bg-red-500 text-white';
            resultBox.innerHTML = `⚠️ خطأ: ${message}`;
            explanationBox.classList.add('hidden');
        }

    </script>
</body>
</html>
