<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Study Guide: AWS Senior Account Manager</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Chosen Palette: Slate & Sage -->
    <!-- Application Structure Plan: The application transforms the linear source report into a four-part interactive dashboard: 'Playbook', 'Market Intel', 'Sales Strategy', and 'AWS Culture'. This non-linear, thematic structure is chosen for superior usability, allowing users to jump directly to topics of interest. It prioritizes exploration and synthesis over passive reading. Key interactions include dynamic charts for quantitative data, clickable diagrams for frameworks, and tabbed/collapsible sections for layered information, reducing cognitive load and improving knowledge retention. The user flow is designed to be self-guided, encouraging exploration from high-level concepts to granular details. -->
    <!-- Visualization & Content Choices: 
        - Report Info: Top 30 Swiss Companies by Revenue -> Goal: Compare & Organize -> Viz: Interactive Bar Chart (Chart.js) -> Interaction: Filter by industry, click bar for details. -> Justification: Transforms a static table into a dynamic tool for market analysis.
        - Report Info: Well-Architected Framework -> Goal: Inform & Organize -> Viz: HTML/CSS Diagram -> Interaction: Clickable pillars revealing details. -> Justification: Visually represents the framework's structure, making it more memorable than a list.
        - Report Info: Sales Methodologies (Challenger Sale) -> Goal: Inform & Organize -> Viz: HTML/CSS Process Flow Diagram -> Interaction: Clickable steps. -> Justification: Clarifies the sequence and makes the process easy to follow.
        - Report Info: Competitive Landscape -> Goal: Compare -> Viz: Interactive HTML Table -> Interaction: Buttons to switch competitor view. -> Justification: Allows for direct, side-by-side comparison, which is more effective than a large, multi-column static table.
        - Report Info: AWS Services & Leadership Principles -> Goal: Inform -> Viz: Click-to-reveal cards/tabs -> Interaction: Click to show details. -> Justification: Manages information density and allows users to self-pace their learning.
        - Library/Method: Chart.js for canvas-based charting; Vanilla JS and Tailwind CSS for all other interactions and diagrams.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 900px;
            margin-left: auto;
            margin-right: auto;
            height: 450px;
            max-height: 60vh;
        }
        .nav-link {
            transition: all 0.3s ease;
            border-bottom: 2px solid transparent;
        }
        .nav-link.active {
            border-bottom-color: #F9A825; /* Amber */
            color: #F9A825;
        }
        .content-section {
            display: none;
        }
        .content-section.active {
            display: block;
        }
        .pill-button {
            transition: all 0.3s ease;
        }
        .pill-button.active {
            background-color: #232F3E;
            color: #FFFFFF;
        }
        .pillar-card, .lp-card, .team-card {
            transition: transform 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
        }
        .pillar-card:hover, .lp-card:hover, .team-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
    </style>
</head>
<body class="bg-gray-50 text-gray-800">

    <header class="bg-white shadow-md sticky top-0 z-50">
        <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
            <h1 class="text-xl md:text-2xl font-bold text-gray-800">AWS Switzerland: Account Manager Playbook</h1>
            <div class="hidden md:flex space-x-8">
                <a href="#playbook" class="nav-link text-gray-600 hover:text-gray-900 font-semibold" data-section="playbook">The Playbook</a>
                <a href="#market" class="nav-link text-gray-600 hover:text-gray-900 font-semibold" data-section="market">Market Intel</a>
                <a href="#strategy" class="nav-link text-gray-600 hover:text-gray-900 font-semibold" data-section="strategy">Sales Strategy</a>
                <a href="#culture" class="nav-link text-gray-600 hover:text-gray-900 font-semibold" data-section="culture">AWS Culture</a>
            </div>
            <div class="md:hidden">
                <select id="mobile-nav" class="bg-gray-200 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5">
                    <option value="playbook">The Playbook</option>
                    <option value="market">Market Intel</option>
                    <option value="strategy">Sales Strategy</option>
                    <option value="culture">AWS Culture</option>
                </select>
            </div>
        </nav>
    </header>

    <main id="main-content" class="container mx-auto p-4 md:p-8">

        <!-- SECTION 1: The Playbook -->
        <section id="playbook" class="content-section">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-extrabold text-gray-900 mb-4">Mastering the AWS Value Proposition</h2>
                <p class="max-w-3xl mx-auto text-lg text-gray-600">This section provides the foundational knowledge to frame AWS not as an IT vendor, but as a strategic partner for agility, innovation, and global scale. Success begins with a C-suite-level comprehension of the platform, the ability to architect for excellence, and the skill to articulate quantifiable business value.</p>
            </div>

            <div class="space-y-12">
                <!-- AWS Cloud Platform -->
                <div>
                    <h3 class="text-2xl font-bold text-center mb-6">The AWS Cloud Platform: A C-Suite Perspective</h3>
                    <div id="aws-services-tabs" class="w-full max-w-4xl mx-auto">
                        <div class="flex border-b border-gray-300">
                            <button data-tab="foundational" class="tab-button flex-1 py-2 px-4 text-center font-semibold text-gray-500 hover:bg-gray-100 focus:outline-none active">Foundational Services</button>
                            <button data-tab="strategic" class="tab-button flex-1 py-2 px-4 text-center font-semibold text-gray-500 hover:bg-gray-100 focus:outline-none">Strategic Services</button>
                        </div>
                        <div id="aws-services-content" class="mt-6">
                            <!-- Content will be injected by JS -->
                        </div>
                    </div>
                </div>

                <!-- Well-Architected Framework -->
                <div>
                    <h3 class="text-2xl font-bold text-center mb-2">The Well-Architected Framework</h3>
                    <p class="text-center text-gray-600 mb-6 max-w-2xl mx-auto">A consultative tool to facilitate constructive conversations about architectural decisions. Click each pillar to reveal key conversation starters.</p>
                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 max-w-5xl mx-auto" id="waf-pillars">
                        <!-- Pillars will be injected by JS -->
                    </div>
                </div>

                <!-- Business Value -->
                <div>
                    <h3 class="text-2xl font-bold text-center mb-6">Articulating Business Value: TCO, ROI & Cost Optimization</h3>
                    <div class="max-w-4xl mx-auto bg-white p-6 rounded-lg shadow-lg">
                        <p class="text-gray-600 mb-6">An expert-level account manager must be fluent in the language of the CFO. This involves translating architectural improvements into quantifiable business value through Total Cost of Ownership (TCO), Return on Investment (ROI), and proactive cost optimization strategies.</p>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <div class="bg-blue-50 p-4 rounded-lg">
                                <h4 class="font-bold text-lg text-blue-800">TCO & ROI Calculation</h4>
                                <p class="text-blue-700 mt-2">The financial backbone of any proposal. It's not just about cost savings; it's about quantifying business value from increased productivity, resilience, and agility.</p>
                            </div>
                            <div class="bg-green-50 p-4 rounded-lg">
                                <h4 class="font-bold text-lg text-green-800">Continuous Cost Optimization</h4>
                                <p class="text-green-700 mt-2">An ongoing process to demonstrate value. Key strategies include Right Sizing, using appropriate Pricing Models (e.g., Savings Plans, Spot), Storage Tiering, and leveraging Elasticity.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- SECTION 2: Market Intel -->
        <section id="market" class="content-section">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-extrabold text-gray-900 mb-4">The Swiss Enterprise Landscape</h2>
                <p class="max-w-3xl mx-auto text-lg text-gray-600">A deep, data-driven understanding of the local market is essential. This section provides a nuanced analysis of Switzerland's key industries, a profile of strategic accounts, and an overview of the competitive cloud landscape to enable tailored, resonant value propositions.</p>
            </div>
            
            <div class="space-y-12">
                <!-- Strategic Accounts Chart -->
                <div>
                    <h3 class="text-2xl font-bold text-center mb-2">Top 30 Strategic Accounts in Switzerland by Revenue</h3>
                    <p class="text-center text-gray-600 mb-4">Filter by industry to analyze key sectors. Click on a company's bar for more details.</p>
                    <div class="flex justify-center flex-wrap gap-2 mb-6" id="industry-filters">
                        <!-- Filters will be injected by JS -->
                    </div>
                    <div class="chart-container bg-white p-4 rounded-lg shadow-lg">
                        <canvas id="companiesChart"></canvas>
                    </div>
                    <div id="company-details" class="mt-6 max-w-4xl mx-auto bg-white p-6 rounded-lg shadow-lg hidden"></div>
                </div>

                <!-- Competitive Landscape -->
                <div>
                    <h3 class="text-2xl font-bold text-center mb-6">Competitive Dynamics</h3>
                    <div class="max-w-6xl mx-auto">
                        <div class="text-center mb-4">
                            <button data-competitor="azure" class="competitor-btn bg-gray-200 py-2 px-4 rounded-l-lg pill-button active">vs. Azure</button>
                            <button data-competitor="gcp" class="competitor-btn bg-gray-200 py-2 px-4 rounded-r-lg pill-button">vs. GCP</button>
                        </div>
                        <div class="overflow-x-auto">
                            <table class="w-full text-sm text-left text-gray-500 bg-white shadow-md rounded-lg">
                                <thead class="text-xs text-gray-700 uppercase bg-gray-100">
                                    <tr>
                                        <th scope="col" class="px-6 py-3">Feature</th>
                                        <th scope="col" class="px-6 py-3">AWS</th>
                                        <th id="competitor-header" scope="col" class="px-6 py-3">Microsoft Azure</th>
                                    </tr>
                                </thead>
                                <tbody id="competitor-table-body">
                                    <!-- Rows will be injected by JS -->
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- SECTION 3: Sales Strategy -->
        <section id="strategy" class="content-section">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-extrabold text-gray-900 mb-4">The Enterprise Sales Playbook</h2>
                 <p class="max-w-3xl mx-auto text-lg text-gray-600">Execution is what drives results. This playbook details the practical sales methodologies required to engage C-suite executives, challenge their thinking, and connect technology solutions to quantifiable business imperatives, turning strategic knowledge into long-term partnerships.</p>
            </div>
            
            <div class="space-y-16">
                 <!-- Challenger Sale -->
                <div>
                    <h3 class="text-2xl font-bold text-center mb-2">The Challenger Sale: 6-Step Choreography</h3>
                    <p class="text-center text-gray-600 mb-8 max-w-2xl mx-auto">This isn't about being aggressive; it's about being assertive with insights. Follow this sequence to change the customer's perspective and lead them to your solution. Click each step for details.</p>
                    <div class="relative max-w-5xl mx-auto">
                        <div class="absolute left-1/2 top-0 bottom-0 w-0.5 bg-gray-300 hidden md:block"></div>
                        <div id="challenger-steps" class="space-y-8">
                            <!-- Steps will be injected by JS -->
                        </div>
                    </div>
                </div>
                
                 <!-- Value Selling -->
                <div>
                    <h3 class="text-2xl font-bold text-center mb-6">Value Selling Framework</h3>
                     <p class="text-center text-gray-600 mb-8 max-w-2xl mx-auto">After reframing the problem, quantify the "why". Connect solutions to the four key categories of business value to build a compelling case.</p>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6 max-w-4xl mx-auto" id="value-selling-quadrants">
                         <!-- Quadrants will be injected by JS -->
                    </div>
                </div>
            </div>
        </section>
        
        <!-- SECTION 4: Culture -->
        <section id="culture" class="content-section">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-extrabold text-gray-900 mb-4">Excelling Within AWS</h2>
                <p class="max-w-3xl mx-auto text-lg text-gray-600">Success at AWS is determined as much by navigating the internal landscape as by external sales skills. Mastering the company's culture and collaborating effectively with a vast internal team are critical for winning complex deals.</p>
            </div>

            <div class="space-y-12">
                 <!-- Leadership Principles -->
                <div>
                    <h3 class="text-2xl font-bold text-center mb-6">Key Amazon Leadership Principles</h3>
                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 max-w-5xl mx-auto" id="leadership-principles">
                        <!-- LPs will be injected by JS -->
                    </div>
                </div>

                 <!-- Internal Team -->
                <div>
                    <h3 class="text-2xl font-bold text-center mb-6">Your Internal Team: A Collaborative Approach</h3>
                    <p class="text-center text-gray-600 mb-8 max-w-2xl mx-auto">Enterprise sales at AWS is a team sport. The Account Manager acts as the 'quarterback', orchestrating a virtual team of specialists. Click each role to understand their function.</p>
                    <div class="max-w-5xl mx-auto p-6 bg-white rounded-lg shadow-lg">
                        <div class="flex flex-col items-center">
                            <div class="team-card bg-amber-400 text-white p-4 rounded-full shadow-lg z-10 cursor-pointer" data-role="am">
                                <h4 class="font-bold">You (Account Manager)</h4>
                            </div>
                            <div class="w-0.5 h-8 bg-gray-300"></div>
                            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-8 w-full text-center" id="team-roles">
                                <!-- Roles will be injected by JS -->
                            </div>
                        </div>
                         <div id="role-details" class="mt-6 p-4 bg-gray-100 rounded-lg hidden"></div>
                    </div>
                </div>
            </div>
        </section>
    </main>

<script>
document.addEventListener('DOMContentLoaded', function () {
    const data = {
        services: {
            foundational: [
                { name: 'Compute', desc: 'Provides scalable virtual servers (EC2), serverless computing (Lambda), and hybrid solutions (Outposts) to run any workload, eliminating hardware capex.' },
                { name: 'Storage', desc: 'Offers a spectrum of services from highly durable object storage (S3) to high-performance block storage (EBS) and low-cost archival (Glacier).' },
                { name: 'Databases', desc: 'A portfolio of purpose-built databases, from managed relational DBs (RDS) to NoSQL (DynamoDB), optimizing for cost and performance.' },
                { name: 'Networking', desc: 'Fundamental services for secure infrastructure, including isolated cloud sections (VPC), private connections (Direct Connect), and content delivery (CloudFront).' },
            ],
            strategic: [
                { name: 'AI & Machine Learning', desc: 'Democratizes AI/ML with platforms to build, train, and deploy models (SageMaker) and access to generative AI foundation models (Bedrock).' },
                { name: 'Data & Analytics', desc: 'A comprehensive suite to turn data into a strategic asset, including real-time stream processing (Kinesis), data prep (Glue), and data warehousing (Redshift).' }
            ]
        },
        wafPillars: [
            { name: 'Operational Excellence', desc: "How do you manage changes and respond to events? Let's implement 'operations as code' to automate procedures and reduce human error.", icon: '⚙️' },
            { name: 'Security', desc: "How do you manage identity and detect threats? Let's review security at all layers to meet business and regulatory needs.", icon: '🛡️' },
            { name: 'Reliability', desc: "What are your RTO/RPO for critical apps? Let's design a resilient architecture that automatically recovers from failure.", icon: '🔄' },
            { name: 'Performance Efficiency', desc: "Are your resources sized correctly? Let's analyze utilization to ensure you can innovate rapidly without over-provisioning.", icon: '⚡' },
            { name: 'Cost Optimization', desc: "Do you have clear visibility into IT spending? Let's use cost management tools to adopt cost-effective models without overspending.", icon: '💰' },
            { name: 'Sustainability', desc: "What are your corporate sustainability goals? Let's discuss how migrating to AWS can help reduce your carbon footprint.", icon: '🌍' },
        ],
        companies: [
            { rank: 1, name: "Glencore", industry: "Commodity Trading", revenue: 230.94, hq: "Baar", use_cases: "Global supply chain optimization, risk management analytics, trading platforms, secure data management." },
            { rank: 2, name: "Nestlé", industry: "Food & Beverage", revenue: 101.54, hq: "Vevey", use_cases: "Supply chain visibility, consumer data analytics (360-degree view), e-commerce platforms, smart factory (IoT)." },
            { rank: 3, name: "Roche", industry: "Pharmaceuticals", revenue: 69.07, hq: "Basel", use_cases: "High-Performance Computing (HPC) for R&D, genomics data analysis, clinical trial data management, regulated GxP workloads." },
            { rank: 4, name: "Zurich Insurance", industry: "Insurance", revenue: 67.33, hq: "Zurich", use_cases: "Core policy system modernization, AI for claims processing & fraud detection, customer analytics, regulatory compliance (FINMA)." },
            { rank: 5, name: "Chubb", industry: "Insurance", revenue: 56.69, hq: "Zurich", use_cases: "Risk modeling (HPC), digital customer platforms, data analytics for underwriting, cybersecurity enhancement." },
            { rank: 6, name: "Novartis", industry: "Pharmaceuticals", revenue: 53.22, hq: "Basel", use_cases: "Drug discovery platforms (AI/ML), secure R&D data lakes, manufacturing process optimization (IoT), digital health solutions." },
            { rank: 7, name: "UBS", industry: "Banking", revenue: 45.76, hq: "Zurich", use_cases: "Mainframe modernization, wealth management personalization (AI), regulatory reporting, secure hybrid cloud, fraud detection." },
            { rank: 8, name: "Swiss Re", industry: "Reinsurance", revenue: 43.74, hq: "Zurich", use_cases: "Catastrophe modeling (HPC), big data analytics for risk assessment, modernizing legacy systems, digital partner ecosystems." },
            { rank: 9, name: "ABB", industry: "Engineering", revenue: 32.91, hq: "Zurich", use_cases: "Industrial IoT platforms (smart factories, robotics), predictive maintenance, connected product development, digital twin solutions." },
            { rank: 10, name: "SNB", industry: "Central Banking", revenue: 32.76, hq: "Bern", use_cases: "Secure data analytics, economic modeling, enhancing cybersecurity posture, resilient infrastructure." },
            { rank: 11, name: "Kühne + Nagel", industry: "Logistics", revenue: 29.03, hq: "Schindellegi", use_cases: "Global logistics and supply chain visibility, predictive analytics for shipping routes, warehouse automation, customer portals." },
            { rank: 12, name: "Holcim Group", industry: "Construction", revenue: 26.81, hq: "Jona", use_cases: "Supply chain optimization, IoT for plant efficiency, predictive maintenance on equipment, sustainability data tracking." },
            { rank: 13, name: "Adecco Group", industry: "Human Resources", revenue: 24.76, hq: "Opfikon", use_cases: "Global HR platform modernization, data analytics for talent matching, AI for resume screening, digital client portals." },
            { rank: 14, name: "Richemont", industry: "Luxury Goods", revenue: 23.15, hq: "Geneva", use_cases: "Global e-commerce platforms, personalized customer experience (CX), supply chain management, brand protection." },
            { rank: 15, name: "TE Connectivity", industry: "Manufacturing", revenue: 16.02, hq: "Schaffhausen", use_cases: "Smart factory initiatives (IoT), supply chain analytics, R&D collaboration platforms, connected sensor solutions." },
            { rank: 16, name: "Swiss Life", industry: "Insurance", revenue: 15.97, hq: "Zurich", use_cases: "Digital transformation of customer-facing applications, data analytics for actuarial modeling, compliance and risk management." },
            { rank: 17, name: "Swisscom", industry: "Telecommunications", revenue: 13.69, hq: "Bern", use_cases: "Network function virtualization (NFV), 5G support, big data analytics on network traffic, customer service modernization." },
            { rank: 18, name: "Amcor", industry: "Packaging", revenue: 13.46, hq: "Zurich", use_cases: "Supply chain optimization, smart packaging solutions (IoT), sustainability reporting, operational efficiency analytics." },
            { rank: 19, name: "DSM-Firmenich", industry: "Chemicals", revenue: 13.31, hq: "Kaiseraugst", use_cases: "R&D data platforms, supply chain management, AI for new ingredient discovery, production process optimization." },
            { rank: 20, name: "Sika", industry: "Chemicals", revenue: 13.02, hq: "Baar", use_cases: "R&D collaboration, global supply chain management, IoT for monitoring construction material performance, digital customer channels." },
            { rank: 21, name: "Schindler Group", industry: "Engineering", revenue: 12.79, hq: "Ebikon", use_cases: "Predictive maintenance for elevators (IoT), connected services platform, operational data analytics, smart building integration." },
            { rank: 22, name: "Helvetia Holding", industry: "Insurance", revenue: 12.42, hq: "St. Gallen", use_cases: "Digitalization of insurance processes, AI-driven underwriting, customer self-service portals, data analytics for risk assessment." },
            { rank: 23, name: "STMicroelectronics", industry: "Semiconductors", revenue: 12.32, hq: "Geneva", use_cases: "EDA workloads on the cloud (HPC), supply chain analytics, R&D data management." },
            { rank: 24, name: "DKSH Holding", industry: "Market Expansion", revenue: 12.28, hq: "Zurich", use_cases: "Supply chain and logistics optimization, data analytics for market trends, digital commerce platforms for B2B." },
            { rank: 25, name: "Barry Callebaut", industry: "Food & Beverage", revenue: 12.21, hq: "Zurich", use_cases: "Commodity sourcing analytics, supply chain traceability, production optimization, B2B customer platforms." },
            { rank: 26, name: "Sandoz Group", industry: "Pharmaceuticals", revenue: 10.38, hq: "Basel", use_cases: "Manufacturing execution systems, supply chain efficiency, regulatory compliance, data analytics for portfolio management." },
            { rank: 27, name: "Alcon", industry: "Medical Devices", revenue: 9.92, hq: "Geneva", use_cases: "Connected medical devices (IoT), R&D data platforms, supply chain management, digital health solutions." },
            { rank: 28, name: "Avolta AG", industry: "Retail", revenue: 8.98, hq: "Basel", use_cases: "Global retail analytics, passenger flow analysis, personalized marketing, inventory and supply chain management." },
            { rank: 29, name: "ALSO Holding", industry: "IT Distribution", revenue: 8.79, hq: "Emmen", use_cases: "Cloud marketplace platform development, supply chain logistics, partner ecosystem management, data analytics as a service." },
            { rank: 30, name: "Coca-Cola HBC", industry: "Food & Beverage", revenue: 8.50, hq: "Zug", use_cases: "Supply chain optimization, demand forecasting, consumer analytics, digital marketing platforms, IoT in bottling plants." }
        ],
        competitors: {
            azure: {
                name: 'Microsoft Azure',
                comparison: [
                    { feature: 'Swiss Data Centers', aws: 'Zurich, Geneva', other: 'Zurich, Geneva' },
                    { feature: 'Sovereignty Messaging', aws: 'Focus on customer control, encryption, and compliance.', other: 'Strong, explicit messaging on data remaining in Switzerland.' },
                    { feature: 'Key Strengths', aws: 'Mature platform, broadest services, largest community.', other: 'Deep enterprise relationships via M365, strong local investment story.' },
                    { feature: 'Key Weaknesses', aws: 'Must overcome competitor "local" narrative.', other: 'U.S. CLOUD Act is a concern, perceived as less open-source friendly.' }
                ]
            },
            gcp: {
                name: 'Google Cloud Platform',
                comparison: [
                    { feature: 'Swiss Data Centers', aws: 'Zurich, Geneva', other: 'Zurich' },
                    { feature: 'Sovereignty Messaging', aws: 'Focus on customer control, encryption, and compliance.', other: 'Emphasizes security, encryption by default, and local compliance.' },
                    { feature: 'Key Strengths', aws: 'Mature platform, broadest services, largest community.', other: 'Strong in Kubernetes (GKE), data analytics (BigQuery), and AI/ML.' },
                    { feature: 'Key Weaknesses', aws: 'Must overcome competitor "local" narrative.', other: 'Smaller market share and local enterprise footprint.' }
                ]
            }
        },
        challengerSteps: [
            { name: 'The Warmer', desc: 'Build credibility by demonstrating a deep understanding of the customer\'s world and their challenges.' },
            { name: 'The Reframe', desc: 'Introduce a disruptive insight. Connect their known problems to a larger, unrecognized issue or opportunity.' },
            { name: 'Rational Drowning', desc: 'Use data and logic to quantify the cost of the problem or the scale of the opportunity, making it tangible.' },
            { name: 'Emotional Impact', desc: 'Make the problem personal with stories and case studies, helping the customer feel the pain of inaction.' },
            { name: 'A New Way', desc: 'Sell the solution as a concept first. Describe the capabilities required to solve the problem and paint a picture of the ideal future state.' },
            { name: 'Your Solution', desc: 'Finally, demonstrate how AWS services are the best embodiment of that conceptual solution.' },
        ],
        valueQuadrants: [
            { name: 'Increase Revenue', desc: 'Example: "Using Amazon Personalize for e-commerce can lift conversion rates by 25%."', color: 'green' },
            { name: 'Decrease Costs', desc: 'Example: "Migrating SAP to AWS can reduce TCO by 35% through right-sizing and RIs."', color: 'blue' },
            { name: 'Improve Productivity', desc: 'Example: "Automating CI/CD pipelines can reduce manual deployment tasks by 80%."', color: 'purple' },
            { name: 'Mitigate Risk', desc: 'Example: "Leveraging AWS security services can avert a single major data breach, saving millions."', color: 'red' },
        ],
        leadershipPrinciples: [
            { name: 'Customer Obsession', desc: 'Start with the customer and work backward. Prioritize their long-term success over short-term targets.' },
            { name: 'Ownership', desc: 'Act on behalf of the entire company. Own your territory and the success of your customers. Never say, "that\'s not my job."' },
            { name: 'Earn Trust', desc: 'Listen attentively, speak candidly, and treat others with respect. It is the currency of collaboration.' },
            { name: 'Dive Deep', desc: 'Operate at all levels and stay connected to the details. Understand the business challenges, technical architecture, and deal specifics.' },
            { name: 'Have Backbone; Disagree and Commit', desc: 'Respectfully challenge decisions when you disagree, but once a decision is made, commit to it wholly.' },
            { name: 'Deliver Results', desc: 'Focus on the key inputs and deliver them with the right quality in a timely fashion. Rise to the occasion and never settle.' },
        ],
        teamRoles: [
            { id: 'sa', name: 'Solutions Architect (SA)', desc: 'Your primary technical partner. Designs architectures and ensures solutions align with best practices.' },
            { id: 'proserve', name: 'Professional Services', desc: 'A paid team of AWS experts who help execute large-scale projects like migrations and data platforms.' },
            { id: 'bd', name: 'Business Development', desc: 'Industry specialist (e.g., FinTech, HCLS) who provides insights and network connections.' },
            { id: 'tam', name: 'Technical Account Manager', desc: 'Post-sale technical resource for Enterprise Support customers, focusing on operational health.' },
            { id: 'apn', name: 'Partner Network (APN)', desc: 'The ecosystem of Systems Integrators (SIs) and Independent Software Vendors (ISVs).' }
        ]
    };

    let companiesChart;
    let currentSection = 'playbook';
    
    const sections = {
        playbook: document.getElementById('playbook'),
        market: document.getElementById('market'),
        strategy: document.getElementById('strategy'),
        culture: document.getElementById('culture'),
    };

    const navLinks = document.querySelectorAll('.nav-link');
    const mobileNav = document.getElementById('mobile-nav');

    function navigateToSection(sectionId) {
        currentSection = sectionId;

        Object.values(sections).forEach(section => {
            section.classList.remove('active');
        });
        sections[sectionId].classList.add('active');

        navLinks.forEach(link => {
            if (link.dataset.section === sectionId) {
                link.classList.add('active');
            } else {
                link.classList.remove('active');
            }
        });
        
        mobileNav.value = sectionId;

        // Lazy load initializers
        if (sectionId === 'market' && !companiesChart) {
            initMarketSection();
        }
        if (sectionId === 'strategy') {
            initStrategySection();
        }
        if (sectionId === 'culture') {
            initCultureSection();
        }

        window.location.hash = sectionId;
    }

    // Navigation handlers
    navLinks.forEach(link => {
        link.addEventListener('click', (e) => {
            e.preventDefault();
            navigateToSection(link.dataset.section);
        });
    });

    mobileNav.addEventListener('change', (e) => {
        navigateToSection(e.target.value);
    });
    
    function initPlaybookSection() {
        const servicesContent = document.getElementById('aws-services-content');
        const servicesTabs = document.getElementById('aws-services-tabs');
        const wafPillarsContainer = document.getElementById('waf-pillars');
        
        function renderServices(type) {
            const serviceData = data.services[type];
            servicesContent.innerHTML = serviceData.map(service => `
                <div class="mb-4 bg-white p-4 rounded-lg shadow">
                    <h4 class="font-bold text-gray-900">${service.name}</h4>
                    <p class="text-gray-600">${service.desc}</p>
                </div>
            `).join('');
        }

        servicesTabs.addEventListener('click', (e) => {
            if (e.target.matches('.tab-button')) {
                const tabType = e.target.dataset.tab;
                servicesTabs.querySelectorAll('.tab-button').forEach(btn => btn.classList.remove('active', 'bg-gray-200'));
                e.target.classList.add('active', 'bg-gray-200');
                renderServices(tabType);
            }
        });
        
        // Render WAF Pillars
        wafPillarsContainer.innerHTML = data.wafPillars.map(pillar => `
            <div class="pillar-card bg-white p-6 rounded-lg shadow-lg cursor-pointer border border-gray-200">
                <div class="text-3xl mb-3">${pillar.icon}</div>
                <h4 class="font-bold text-lg mb-2 text-gray-900">${pillar.name}</h4>
                <p class="text-gray-600 text-sm">${pillar.desc}</p>
            </div>
        `).join('');

        // Initial render
        renderServices('foundational');
        servicesTabs.querySelector('[data-tab="foundational"]').classList.add('active', 'bg-gray-200');
    }

    function initMarketSection() {
        const filtersContainer = document.getElementById('industry-filters');
        const companyDetailsContainer = document.getElementById('company-details');
        
        // Create industry filters
        const industries = ['All', ...new Set(data.companies.map(c => c.industry))];
        filtersContainer.innerHTML = industries.map(industry => `
            <button class="pill-button px-4 py-1 text-sm font-semibold rounded-full border ${industry === 'All' ? 'active bg-gray-800 text-white' : 'bg-white text-gray-700'}" data-industry="${industry}">
                ${industry}
            </button>
        `).join('');
        
        filtersContainer.addEventListener('click', e => {
            if (e.target.tagName === 'BUTTON') {
                const industry = e.target.dataset.industry;
                filtersContainer.querySelectorAll('button').forEach(btn => btn.classList.remove('active', 'bg-gray-800', 'text-white'));
                e.target.classList.add('active', 'bg-gray-800', 'text-white');
                updateChart(industry);
            }
        });

        const ctx = document.getElementById('companiesChart').getContext('2d');
        companiesChart = new Chart(ctx, {
            type: 'bar',
            data: {
                labels: [],
                datasets: [{
                    label: 'Revenue (USD B)',
                    data: [],
                    backgroundColor: 'rgba(35, 47, 62, 0.8)',
                    borderColor: 'rgba(35, 47, 62, 1)',
                    borderWidth: 1
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                indexAxis: 'y',
                scales: {
                    x: {
                        beginAtZero: true,
                        title: { display: true, text: 'Revenue (USD Billion)' }
                    },
                    y: {
                        ticks: {
                           autoSkip: false
                        }
                    }
                },
                plugins: {
                    legend: { display: false },
                    tooltip: {
                        callbacks: {
                            label: function(context) {
                                let label = context.dataset.label || '';
                                if (label) {
                                    label += ': ';
                                }
                                if (context.parsed.x !== null) {
                                    label += new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD' }).format(context.parsed.x) + ' B';
                                }
                                return label;
                            }
                        }
                    }
                },
                onClick: (event, elements) => {
                    if (elements.length > 0) {
                        const chartElement = elements[0];
                        const company = companiesChart.config.data.companiesData[chartElement.index];
                        showCompanyDetails(company);
                    }
                }
            }
        });

        function updateChart(industry = 'All') {
            const filteredData = (industry === 'All')
                ? data.companies
                : data.companies.filter(c => c.industry === industry);
            
            const sortedData = [...filteredData].sort((a, b) => b.revenue - a.revenue).slice(0, 15);
            
            companiesChart.config.data.companiesData = sortedData;
            companiesChart.data.labels = sortedData.map(c => c.name);
            companiesChart.data.datasets[0].data = sortedData.map(c => c.revenue);
            companiesChart.update();
            companyDetailsContainer.classList.add('hidden');
        }

        function showCompanyDetails(company) {
            companyDetailsContainer.innerHTML = `
                <h4 class="font-bold text-xl mb-2">${company.name}</h4>
                <p><strong>Industry:</strong> ${company.industry}</p>
                <p><strong>HQ:</strong> ${company.hq}</p>
                <p><strong>Revenue:</strong> $${company.revenue} Billion</p>
                <p class="mt-2"><strong>Potential Use Cases:</strong> ${company.use_cases}</p>
            `;
            companyDetailsContainer.classList.remove('hidden');
        }

        // Competitive Landscape
        const competitorBtns = document.querySelectorAll('.competitor-btn');
        const competitorHeader = document.getElementById('competitor-header');
        const competitorTableBody = document.getElementById('competitor-table-body');
        
        function renderCompetitorTable(competitorId) {
            const competitorData = data.competitors[competitorId];
            competitorHeader.textContent = competitorData.name;
            competitorTableBody.innerHTML = competitorData.comparison.map(row => `
                <tr class="border-b">
                    <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap">${row.feature}</th>
                    <td class="px-6 py-4">${row.aws}</td>
                    <td class="px-6 py-4">${row.other}</td>
                </tr>
            `).join('');
        }
        
        competitorBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                competitorBtns.forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                renderCompetitorTable(btn.dataset.competitor);
            });
        });
        
        // Initial render
        updateChart();
        renderCompetitorTable('azure');
    }

    function initStrategySection() {
        const challengerStepsContainer = document.getElementById('challenger-steps');
        challengerStepsContainer.innerHTML = data.challengerSteps.map((step, index) => `
            <div class="md:flex items-center ${index % 2 === 0 ? 'md:flex-row' : 'md:flex-row-reverse'}">
                <div class="md:w-5/12">
                    <div class="bg-white p-6 rounded-lg shadow-lg border border-gray-200 cursor-pointer">
                        <h4 class="font-bold text-lg text-gray-900">${index + 1}. ${step.name}</h4>
                        <p class="text-gray-600 mt-2">${step.desc}</p>
                    </div>
                </div>
                <div class="hidden md:flex md:w-2/12 justify-center">
                    <div class="bg-gray-800 text-white w-10 h-10 rounded-full flex items-center justify-center font-bold text-lg">${index + 1}</div>
                </div>
                <div class="md:w-5/12"></div>
            </div>
        `).join('');

        const valueQuadrantsContainer = document.getElementById('value-selling-quadrants');
        valueQuadrantsContainer.innerHTML = data.valueQuadrants.map(q => `
            <div class="bg-${q.color}-100 p-6 rounded-lg shadow-lg border border-${q.color}-200">
                <h4 class="font-bold text-xl text-${q.color}-800">${q.name}</h4>
                <p class="text-${q.color}-700 mt-2">${q.desc}</p>
            </div>
        `).join('');
    }

    function initCultureSection() {
        const lpContainer = document.getElementById('leadership-principles');
        lpContainer.innerHTML = data.leadershipPrinciples.map(lp => `
            <div class="lp-card bg-white p-6 rounded-lg shadow-lg cursor-pointer border border-gray-200">
                <h4 class="font-bold text-lg text-gray-900 mb-2">${lp.name}</h4>
                <p class="text-gray-600 text-sm">${lp.desc}</p>
            </div>
        `).join('');
        
        const teamRolesContainer = document.getElementById('team-roles');
        const roleDetailsContainer = document.getElementById('role-details');
        
        const amCard = document.querySelector('[data-role="am"]');
        amCard.addEventListener('click', () => {
             roleDetailsContainer.innerHTML = `
                <h5 class="font-bold">Account Manager (AM)</h5>
                <p>The "quarterback". Owns the "what" and "why"—the business relationship, value proposition, and commercial aspects of the deal.</p>
             `;
             roleDetailsContainer.classList.remove('hidden');
        });

        teamRolesContainer.innerHTML = data.teamRoles.map(role => `
            <div class="flex flex-col items-center">
                <div class="w-0.5 h-8 bg-gray-300"></div>
                <div class="team-card bg-gray-700 text-white p-3 rounded-lg shadow-md cursor-pointer" data-role-id="${role.id}">
                    <h5 class="font-semibold text-sm">${role.name}</h5>
                </div>
            </div>
        `).join('');
        
        teamRolesContainer.addEventListener('click', e => {
            const card = e.target.closest('.team-card');
            if (card) {
                const roleId = card.dataset.roleId;
                const roleData = data.teamRoles.find(r => r.id === roleId);
                if (roleData) {
                    roleDetailsContainer.innerHTML = `
                        <h5 class="font-bold">${roleData.name}</h5>
                        <p>${roleData.desc}</p>
                    `;
                    roleDetailsContainer.classList.remove('hidden');
                }
            }
        });
    }
    
    // Initial page load
    const initialHash = window.location.hash.replace('#', '');
    if (initialHash && sections[initialHash]) {
        navigateToSection(initialHash);
    } else {
        navigateToSection('playbook');
    }
    
    initPlaybookSection();

});
</script>
</body>
</html>
