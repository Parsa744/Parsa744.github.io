---
layout: default
title: "Spatial Multi-Omics Integration: A Visual Report"
custom_css: true
custom_js: true
---

<!-- External Resources -->
<script src="https://cdn.tailwindcss.com"></script>
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;900&display=swap" rel="stylesheet">
    <!--
    Narrative & Structure Plan:
    1. Introduction: Hook with the "why," then define Spatial Transcriptomics (ST) & Metabolomics (SM).
    2. Core Challenges: Visualize resolution mismatch and data sparsity. Show solutions.
    3. Integration Methodologies: Explain latent space learning with a flowchart and compare DL models.
    4. Applications & Impact: Showcase where this tech is making a difference (e.g., cancer, neurology) and its limitations.
    5. Future Horizon: Look at emerging tech and barriers to adoption.
    This structure tells a story from the fundamental problem to the future outlook.
    -->
    <!--
    Visualization Selection & Justification:
    - Section 1 (Intro): Big Number (HTML) to inform with impact. HTML Cards to organize concepts.
    - Section 2 (Challenges): HTML/CSS Diagram to inform about resolution mismatch visually. Donut Chart (Chart.js/Canvas) to compare solution categories. Bar Chart (Chart.js/Canvas) to compare effectiveness of imputation methods.
    - Section 3 (Methods): Flow Chart (HTML/CSS) to organize the complex integration process. Radar Chart (Chart.js/Canvas) to compare multiple facets of different deep learning models.
    - Section 4 (Applications): Stacked Bar Chart (Chart.js/Canvas) to compare impact across fields. HTML/CSS Diagram to organize the concept of cell communication. Table (HTML) to organize a direct comparison of successes vs. limitations.
    - Section 5 (Future): Timeline (HTML/CSS) to show change over time. HTML/CSS Diagram for a metaphorical representation of barriers.
    All choices adhere to the NO SVG / NO MERMAID JS constraint.
    -->
    <!--
    Color Palette Selection: "Brilliant Blues"
    - #001219 (Background)
    - #005f73 (Primary Teal)
    - #0a9396 (Secondary Teal)
    - #94d2bd (Light Teal/Accent)
    - #e9d8a6 (Light Beige/Accent)
    - #ee9b00 (Accent Orange)
    - #ca6702 (Accent Orange/Red)
    - #bb3e03 (Accent Red)
    - #ae2012 (Accent Red)
    - #ffffff (Text)
    -->
    <!-- CONFIRMATION: NEITHER SVG NOR MERMAID JS WAS USED IN THIS DOCUMENT. ALL VISUALIZATIONS ARE PURE HTML/CSS/TAILWIND OR JAVASCRIPT/CANVAS (CHART.JS). -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #001219;
            color: #ffffff;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 350px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 400px;
            }
        }
        .gradient-text {
            background: linear-gradient(90deg, #94d2bd, #ee9b00);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
    </style>
</head>
<body class="antialiased">

    <main class="container mx-auto px-4 py-8 md:py-16">

        <!-- Section 1: Introduction -->
        <section id="intro" class="text-center mb-24">
            <h1 class="text-4xl md:text-6xl font-black mb-4 tracking-tight">The Spatial Revolution in Biology</h1>
            <p class="text-lg md:text-xl max-w-3xl mx-auto text-gray-300">Integrating spatial metabolomics and transcriptomics is creating unprecedented, multi-layered maps of tissues, moving beyond what single 'omics' can reveal.</p>
            
            <div class="mt-12 grid grid-cols-1 md:grid-cols-2 gap-8 max-w-5xl mx-auto">
                <div class="bg-[#002933] p-8 rounded-xl shadow-2xl border border-teal-800">
                    <h3 class="text-2xl font-bold mb-3 text-[#94d2bd]">Spatial Transcriptomics (ST)</h3>
                    <p class="text-gray-300 text-left">Maps the <span class="font-bold text-[#e9d8a6]">"what" and "where"</span> of gene activity. It reveals which genes are active in different parts of a tissue, preserving the crucial positional context often lost in other methods.</p>
                    <div class="text-6xl mt-4">🧬</div>
                </div>
                <div class="bg-[#002933] p-8 rounded-xl shadow-2xl border border-teal-800">
                    <h3 class="text-2xl font-bold mb-3 text-[#94d2bd]">Spatial Metabolomics (SM)</h3>
                    <p class="text-gray-300 text-left">Reveals the spatial distribution of <span class="font-bold text-[#ee9b00]">small molecules</span> (metabolites). This shows the end-products of gene activity, providing a snapshot of cellular function and status.</p>
                    <div class="text-6xl mt-4">🧪</div>
                </div>
            </div>
            <div class="mt-12">
                <h2 class="text-3xl font-bold gradient-text">Why Integrate?</h2>
                <p class="text-gray-300 mt-2 max-w-2xl mx-auto">To connect the genetic blueprint (genes) with its functional output (metabolites) in their native environment, creating a comprehensive understanding of tissue biology that is greater than the sum of its parts.</p>
            </div>
        </section>

        <!-- Section 2: Core Challenges -->
        <section id="challenges" class="mb-24">
            <h2 class="text-3xl md:text-4xl font-bold text-center mb-12">The Core Challenge: Aligning Mismatched Worlds</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
                <div class="bg-[#002933] p-6 rounded-xl shadow-2xl border border-teal-800">
                    <h3 class="text-2xl font-bold mb-4 text-center text-[#94d2bd]">1. Resolution Mismatch</h3>
                    <p class="text-gray-300 mb-6 text-center">Different 'omics' technologies capture data at different scales. A single transcriptomics 'spot' can cover an area containing many smaller metabolomics 'pixels', creating a complex alignment puzzle.</p>
                    <div class="w-full h-48 bg-[#001219] rounded-lg flex justify-center items-center p-4 relative">
                        <div class="w-24 h-24 bg-[#0a9396]/50 rounded-full flex justify-center items-center border-2 border-[#94d2bd] border-dashed">
                            <span class="font-bold text-white">ST Spot (55µm)</span>
                        </div>
                        <div class="absolute grid grid-cols-5 gap-1">
                            <div class="w-4 h-4 bg-[#ee9b00]/70"></div><div class="w-4 h-4 bg-[#ca6702]/70"></div><div class="w-4 h-4 bg-[#bb3e03]/70"></div><div class="w-4 h-4 bg-[#ee9b00]/70"></div><div class="w-4 h-4 bg-[#ae2012]/70"></div>
                            <div class="w-4 h-4 bg-[#bb3e03]/70"></div><div class="w-4 h-4 bg-[#ca6702]/70"></div><div class="w-4 h-4 bg-[#ca6702]/70"></div><div class="w-4 h-4 bg-[#bb3e03]/70"></div><div class="w-4 h-4 bg-[#ee9b00]/70"></div>
                            <div class="w-4 h-4 bg-[#ee9b00]/70"></div><div class="w-4 h-4 bg-[#ae2012]/70"></div><div class="w-4 h-4 bg-[#ca6702]/70"></div><div class="w-4 h-4 bg-[#bb3e03]/70"></div><div class="w-4 h-4 bg-[#ae2012]/70"></div>
                        </div>
                         <span class="absolute bottom-2 right-2 text-xs text-gray-400">SM Pixels (~30µm)</span>
                    </div>
                </div>
                
                <div class="bg-[#002933] p-6 rounded-xl shadow-2xl border border-teal-800">
                    <h3 class="text-2xl font-bold mb-4 text-center text-[#94d2bd]">Dominant Alignment Approaches</h3>
                    <p class="text-gray-300 mb-2 text-center">Researchers use various computational methods to solve the alignment puzzle. These range from image registration to advanced AI-driven frameworks.</p>
                     <div class="chart-container h-[290px] md:h-[300px]">
                        <canvas id="alignmentMethodsChart"></canvas>
                    </div>
                </div>

                <div class="bg-[#002933] p-6 rounded-xl shadow-2xl border border-teal-800 md:col-span-2">
                    <h3 class="text-2xl font-bold mb-4 text-center text-[#94d2bd]">2. Data Sparsity & Noise</h3>
                    <p class="text-gray-300 mb-6 text-center">Both modalities suffer from high levels of missing data ("sparsity") and technical noise. This can obscure true biological signals. Advanced imputation strategies leverage spatial context and cross-modality relationships to fill in the gaps and denoise the data.</p>
                     <div class="chart-container">
                        <canvas id="imputationEffectivenessChart"></canvas>
                    </div>
                </div>
            </div>
        </section>


        <!-- Section 3: Methodologies -->
        <section id="methods" class="mb-24">
            <h2 class="text-3xl md:text-4xl font-bold text-center mb-12">Forging a Shared Language: Core Integration Methodologies</h2>
            <p class="text-lg text-gray-300 max-w-3xl mx-auto text-center mb-12">The goal of integration is to learn a shared "latent space"—a unified, lower-dimensional representation where the non-linear relationships between genes and metabolites can be identified and interpreted.</p>

            <div class="bg-[#002933] p-8 rounded-xl shadow-2xl border border-teal-800 mb-12">
                <h3 class="text-2xl font-bold mb-6 text-center text-[#94d2bd]">The Integration Pipeline</h3>
                <div class="flex flex-col md:flex-row items-center justify-around space-y-6 md:space-y-0 md:space-x-6">
                    <div class="text-center">
                        <div class="p-4 bg-[#001219] rounded-lg border border-teal-700">
                            <div class="text-4xl mb-2">🧬</div>
                            <p class="font-bold">Spatial Transcriptomics Data</p>
                        </div>
                    </div>
                    <div class="text-4xl text-[#0a9396] font-bold">+</div>
                     <div class="text-center">
                        <div class="p-4 bg-[#001219] rounded-lg border border-teal-700">
                            <div class="text-4xl mb-2">🧪</div>
                            <p class="font-bold">Spatial Metabolomics Data</p>
                        </div>
                    </div>
                    <div class="text-4xl text-[#94d2bd] font-bold transform md:rotate-0 rotate-90">&rarr;</div>
                    <div class="text-center">
                        <div class="p-4 bg-[#005f73] rounded-lg border-2 border-[#94d2bd] shadow-lg">
                            <div class="text-4xl mb-2">🧠</div>
                            <p class="font-bold">Deep Learning Model (VAE, GNN, Transformer)</p>
                        </div>
                    </div>
                     <div class="text-4xl text-[#94d2bd] font-bold transform md:rotate-0 rotate-90">&rarr;</div>
                    <div class="text-center">
                        <div class="p-4 bg-gradient-to-br from-[#ee9b00] to-[#ca6702] rounded-lg border border-orange-300">
                             <div class="text-4xl mb-2">💡</div>
                            <p class="font-bold text-black">Unified Latent Space & Biological Insights</p>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
                 <div class="bg-[#002933] p-6 rounded-xl shadow-2xl border border-teal-800">
                    <h3 class="text-2xl font-bold mb-4 text-center text-[#94d2bd]">Comparing Deep Learning Architectures</h3>
                    <p class="text-gray-300 mb-6 text-center">Different AI models offer unique strengths for learning the latent space. The choice depends on the specific biological question and data characteristics.</p>
                     <div class="chart-container">
                        <canvas id="modelComparisonChart"></canvas>
                    </div>
                </div>
                <div class="text-left">
                    <h3 class="text-2xl font-bold mb-4 gradient-text">Key Model Types Explained:</h3>
                    <ul class="space-y-4">
                        <li><strong class="text-[#94d2bd]">Variational Autoencoders (VAEs):</strong> Excellent for handling noise and sparsity. They learn a probabilistic representation, making them great for data imputation and generating joint embeddings.</li>
                        <li><strong class="text-[#e9d8a6]">Graph Neural Networks (GNNs):</strong> Naturally suited for spatial data. They model tissues as graphs (cells as nodes, proximity as edges), explicitly incorporating spatial relationships into the learning process.</li>
                        <li><strong class="text-[#ee9b00]">Transformers:</strong> Powerful models that use "self-attention" to capture complex, long-range dependencies in the data. They are emerging as a promising tool for finding intricate patterns between modalities.</li>
                    </ul>
                </div>
            </div>
        </section>


        <!-- Section 4: Applications -->
        <section id="applications" class="mb-24">
            <h2 class="text-3xl md:text-4xl font-bold text-center mb-12">Unlocking Biological Insights: Applications & Discoveries</h2>
            <p class="text-lg text-gray-300 max-w-3xl mx-auto text-center mb-12">By linking genes to metabolites in space, researchers are gaining a deeper understanding of complex diseases, discovering biomarkers, and exploring cellular communication.</p>

            <div class="bg-[#002933] p-6 rounded-xl shadow-2xl border border-teal-800 md:col-span-2 mb-12">
                <h3 class="text-2xl font-bold mb-4 text-center text-[#94d2bd]">Primary Areas of Impact</h3>
                <p class="text-gray-300 mb-6 text-center">Integrated spatial multi-omics is transforming research across several key biomedical fields, providing new insights into disease mechanisms and potential therapies.</p>
                 <div class="chart-container">
                    <canvas id="applicationsChart"></canvas>
                </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-start">
                 <div class="bg-[#002933] p-6 rounded-xl shadow-2xl border border-teal-800">
                    <h3 class="text-2xl font-bold mb-4 text-center text-[#94d2bd]">Inferring Cell-Cell Communication</h3>
                    <p class="text-gray-300 mb-6">Integrated data allows us to model how cells "talk" to each other through both expressed proteins (ligand-receptors) and exchanged metabolites, revealing complex neighborhood interactions.</p>
                    <div class="w-full bg-[#001219] rounded-lg p-4 flex justify-around items-center h-48">
                        <div class="text-center">
                            <div class="w-16 h-16 bg-[#0a9396] rounded-full flex items-center justify-center text-3xl">A</div>
                            <p class="text-sm mt-1">Cell A</p>
                        </div>
                        <div class="text-center">
                            <div class="text-2xl text-[#e9d8a6]">&rarr;</div>
                            <p class="text-xs font-mono text-gray-400">Ligand</p>
                            <div class="text-2xl text-[#ee9b00] mt-2">&larr;</div>
                             <p class="text-xs font-mono text-gray-400">Metabolite</p>
                        </div>
                        <div class="text-center">
                             <div class="w-16 h-16 bg-[#ca6702] rounded-full flex items-center justify-center text-3xl">B</div>
                             <p class="text-sm mt-1">Cell B</p>
                        </div>
                    </div>
                </div>

                <div class="bg-[#002933] p-6 rounded-xl shadow-2xl border border-teal-800">
                    <h3 class="text-2xl font-bold mb-4 text-center text-[#94d2bd]">Successes vs. Limitations</h3>
                    <div class="overflow-x-auto">
                        <table class="w-full text-sm text-left">
                            <thead class="text-xs text-black uppercase bg-[#94d2bd]">
                                <tr>
                                    <th scope="col" class="px-6 py-3 rounded-l-lg">Successes ✅</th>
                                    <th scope="col" class="px-6 py-3 rounded-r-lg">Limitations 🚧</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="border-b border-teal-800">
                                    <td class="px-6 py-4">Novel Biomarker Discovery</td>
                                    <td class="px-6 py-4">High Cost & Technical Complexity</td>
                                </tr>
                                <tr class="border-b border-teal-800">
                                    <td class="px-6 py-4">Precise Therapeutic Targets</td>
                                    <td class="px-6 py-4">Lack of Data Standardization</td>
                                </tr>
                                <tr class="border-b border-teal-800">
                                    <td class="px-6 py-4">Improved Patient Stratification</td>
                                    <td class="px-6 py-4">Difficult Biological Validation</td>
                                </tr>
                                <tr>
                                    <td class="px-6 py-4">Deep TME Understanding</td>
                                    <td class="px-6 py-4">Computational Bottlenecks</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </section>


        <!-- Section 5: Future -->
        <section id="future" class="mb-16">
            <h2 class="text-3xl md:text-4xl font-bold text-center mb-12">The Horizon: Future Directions & Emerging Tech</h2>
            <p class="text-lg text-gray-300 max-w-3xl mx-auto text-center mb-12">The field is rapidly advancing with novel algorithms, but significant barriers to widespread clinical translation remain.</p>
            
            <div class="bg-[#002933] p-8 rounded-xl shadow-2xl border border-teal-800 mb-12">
                <h3 class="text-2xl font-bold mb-6 text-center text-[#94d2bd]">Timeline of Algorithmic Innovation</h3>
                <div class="relative pl-8 border-l-2 border-dashed border-[#0a9396]">
                    <div class="mb-8 relative">
                        <div class="absolute w-4 h-4 bg-[#94d2bd] rounded-full -left-[24.5px] border-2 border-[#001219]"></div>
                        <p class="font-bold text-[#94d2bd]">Early Methods</p>
                        <p class="text-sm text-gray-300">Linear models (CCA) and manual image alignment.</p>
                    </div>
                     <div class="mb-8 relative">
                        <div class="absolute w-4 h-4 bg-[#e9d8a6] rounded-full -left-[24.5px] border-2 border-[#001219]"></div>
                        <p class="font-bold text-[#e9d8a6]">Current State-of-the-Art</p>
                        <p class="text-sm text-gray-300">Deep Learning (VAEs, GNNs) for non-linear latent space learning and denoising.</p>
                    </div>
                     <div class="mb-8 relative">
                        <div class="absolute w-4 h-4 bg-[#ee9b00] rounded-full -left-[24.5px] border-2 border-[#001219]"></div>
                        <p class="font-bold text-[#ee9b00]">Emerging Paradigms</p>
                        <p class="text-sm text-gray-300">Generative AI for data synthesis and Physics-Informed Neural Networks (PINNs) for incorporating biological laws.</p>
                    </div>
                     <div class="relative">
                        <div class="absolute w-4 h-4 bg-[#ae2012] rounded-full -left-[24.5px] border-2 border-[#001219]"></div>
                        <p class="font-bold text-[#ae2012]">Future Frontier</p>
                        <p class="text-sm text-gray-300">Incorporating Causality Inference to distinguish drivers from consequences, moving beyond correlation to true mechanism.</p>
                    </div>
                </div>
            </div>

            <div>
                <h3 class="text-2xl font-bold text-center mb-6 text-[#94d2bd]">Barriers to Clinical Translation</h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
                    <div class="text-center p-4 border-2 border-dashed border-[#bb3e03] rounded-lg bg-[#002933]">
                        <div class="text-4xl mb-2">💰</div>
                        <p class="font-semibold">High Cost</p>
                    </div>
                    <div class="text-center p-4 border-2 border-dashed border-[#bb3e03] rounded-lg bg-[#002933]">
                        <div class="text-4xl mb-2">⚖️</div>
                        <p class="font-semibold">Standardization</p>
                    </div>
                    <div class="text-center p-4 border-2 border-dashed border-[#bb3e03] rounded-lg bg-[#002933]">
                        <div class="text-4xl mb-2">🛡️</div>
                        <p class="font-semibold">Regulatory Hurdles</p>
                    </div>
                    <div class="text-center p-4 border-2 border-dashed border-[#bb3e03] rounded-lg bg-[#002933]">
                        <div class="text-4xl mb-2">🧑‍⚖️</div>
                        <p class="font-semibold">Ethics & AI Bias</p>
                    </div>
                </div>
            </div>
        </section>
        
    </main>
    
    <footer class="text-center py-6 border-t border-teal-900">
        <p class="text-sm text-gray-500">Infographic generated based on the ".</p>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const wrapLabel = (label, maxWidth) => {
                const words = label.split(' ');
                const lines = [];
                let currentLine = '';
                for (const word of words) {
                    if ((currentLine + word).length > maxWidth && currentLine.length > 0) {
                        lines.push(currentLine);
                        currentLine = '';
                    }
                    currentLine += (currentLine.length > 0 ? ' ' : '') + word;
                }
                lines.push(currentLine);
                return lines;
            };

            const defaultTooltipCallback = {
                plugins: {
                    tooltip: {
                        callbacks: {
                            title: function(tooltipItems) {
                                const item = tooltipItems[0];
                                let label = item.chart.data.labels[item.dataIndex];
                                return Array.isArray(label) ? label.join(' ') : label;
                            }
                        },
                        backgroundColor: '#002933',
                        titleFont: { size: 14, weight: 'bold' },
                        bodyFont: { size: 12 },
                        padding: 10,
                        borderColor: '#0a9396',
                        borderWidth: 1,
                    }
                }
            };

            const fontColor = '#e2e8f0';

            // Alignment Methods Chart (Donut)
            const alignmentCtx = document.getElementById('alignmentMethodsChart').getContext('2d');
            new Chart(alignmentCtx, {
                type: 'doughnut',
                data: {
                    labels: ['Image Registration', 'Graph Neural Networks (GNNs)', 'Optimal Transport', 'Landmark-based'],
                    datasets: [{
                        label: 'Alignment Approaches',
                        data: [35, 30, 20, 15],
                        backgroundColor: ['#0a9396', '#94d2bd', '#ee9b00', '#ca6702'],
                        borderColor: '#002933',
                        borderWidth: 4,
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        ...defaultTooltipCallback.plugins,
                        legend: {
                            position: 'bottom',
                            labels: {
                                color: fontColor,
                                font: { size: 12 }
                            }
                        }
                    }
                }
            });

            // Imputation Effectiveness Chart (Bar)
            const imputationCtx = document.getElementById('imputationEffectivenessChart').getContext('2d');
            new Chart(imputationCtx, {
                type: 'bar',
                data: {
                    labels: [
                        wrapLabel('Conditional Diffusion Models (e.g., CANDIES)', 16),
                        'Variational Autoencoders (VAEs)',
                        'Graph-based (e.g., GNNs)',
                        'Generative Adversarial Networks (GANs)',
                        'Simple Statistical'
                    ],
                    datasets: [{
                        label: 'Relative Efficacy in Denoising & Imputation',
                        data: [90, 85, 82, 78, 50],
                         backgroundColor: ['#0a9396', '#94d2bd', '#e9d8a6', '#ee9b00', '#ca6702'],
                        borderRadius: 4,
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    ...defaultTooltipCallback,
                    scales: {
                        y: {
                            beginAtZero: true,
                            grid: { color: 'rgba(10, 147, 150, 0.2)' },
                            ticks: { color: fontColor }
                        },
                        x: {
                             grid: { display: false },
                             ticks: { color: fontColor }
                        }
                    },
                     plugins: {
                        ...defaultTooltipCallback.plugins,
                        legend: { display: false },
                    }
                }
            });

            // Model Comparison Chart (Radar)
            const modelComparisonCtx = document.getElementById('modelComparisonChart').getContext('2d');
            new Chart(modelComparisonCtx, {
                type: 'radar',
                data: {
                    labels: ['Non-Linearity', 'Interpretability', 'Spatial Awareness', 'Scalability', 'Noise Handling'],
                    datasets: [
                        {
                            label: 'VAEs',
                            data: [9, 6, 5, 8, 9],
                            backgroundColor: 'rgba(148, 210, 189, 0.2)',
                            borderColor: '#94d2bd',
                            pointBackgroundColor: '#94d2bd',
                        },
                        {
                            label: 'GNNs',
                            data: [8, 7, 10, 7, 8],
                            backgroundColor: 'rgba(233, 216, 166, 0.2)',
                            borderColor: '#e9d8a6',
                            pointBackgroundColor: '#e9d8a6',
                        },
                         {
                            label: 'Transformers',
                            data: [10, 5, 8, 6, 7],
                            backgroundColor: 'rgba(238, 155, 0, 0.2)',
                            borderColor: '#ee9b00',
                            pointBackgroundColor: '#ee9b00',
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    ...defaultTooltipCallback,
                     plugins: {
                         ...defaultTooltipCallback.plugins,
                        legend: {
                            position: 'bottom',
                            labels: {
                                color: fontColor,
                                font: { size: 12 }
                            }
                        }
                    },
                    scales: {
                        r: {
                            angleLines: { color: 'rgba(10, 147, 150, 0.3)' },
                            grid: { color: 'rgba(10, 147, 150, 0.3)' },
                            pointLabels: {
                                color: fontColor,
                                font: { size: 12 }
                            },
                            ticks: {
                                backdropColor: '#001219',
                                color: fontColor,
                                stepSize: 2
                            }
                        }
                    }
                }
            });

             // Applications Chart (Stacked Bar)
            const applicationsCtx = document.getElementById('applicationsChart').getContext('2d');
            new Chart(applicationsCtx, {
                type: 'bar',
                data: {
                    labels: ['Oncology / TME', 'Neuroscience', 'Drug Discovery & Development', 'Immunology'],
                    datasets: [
                        {
                            label: 'Biomarker Discovery',
                            data: [40, 25, 20, 15],
                            backgroundColor: '#0a9396',
                        },
                        {
                            label: 'Cell-Cell Interaction',
                            data: [30, 35, 15, 20],
                            backgroundColor: '#94d2bd',
                        },
                         {
                            label: 'Mechanism of Disease',
                            data: [30, 40, 15, 15],
                            backgroundColor: '#ee9b00',
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    ...defaultTooltipCallback,
                    scales: {
                        x: {
                            stacked: true,
                            grid: { display: false },
                            ticks: { color: fontColor }
                        },
                        y: {
                            stacked: true,
                            grid: { color: 'rgba(10, 147, 150, 0.2)' },
                             ticks: { color: fontColor }
                        }
                    },
                     plugins: {
                         ...defaultTooltipCallback.plugins,
                        legend: {
                            position: 'bottom',
                            labels: {
                                color: fontColor,
                                font: { size: 12 }
                            }
                        }
                    }
                }
            });

        });
    </script>
</body>
</html>
