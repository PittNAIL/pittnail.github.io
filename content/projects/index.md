+++
title = "Projects"
template = "page.html"
+++

<div class="section-intro fade-in">
    <p class="lead">Our research projects focus on developing and applying AI and NLP technologies to solve critical challenges in healthcare.</p>
</div>

<div class="topic-filters fade-in">
    <span class="filter-label">Filter by Topic:</span>
    <button class="topic-filter active" data-topic="all">All</button>
    <button class="topic-filter" data-topic="Clinical NLP">Clinical NLP</button>
    <button class="topic-filter" data-topic="LLM Application">LLM Application</button>
    <button class="topic-filter" data-topic="LLM Alignment">LLM Alignment</button>
    <button class="topic-filter" data-topic="Precision Nutrition">Precision Nutrition</button>
    <button class="topic-filter" data-topic="LLM Evaluation">LLM Evaluation</button>
    <button class="topic-filter" data-topic="Foundation Models">Foundation Models</button>
    <button class="topic-filter" data-topic="Cancer Informatics">Cancer Informatics</button>
</div>

<div class="projects-list fade-in">

<script>
// Initialize filtering when the page loads
function initializeFiltering() {
    const filters = document.querySelectorAll('.topic-filter');
    const projects = document.querySelectorAll('.project-card');
    const spacers = document.querySelectorAll('.project-spacer');

    function updateVisibility() {
        const activeTopic = document.querySelector('.topic-filter.active').getAttribute('data-topic');
        let lastVisibleIndex = -1;

        // First pass: determine visibility
        projects.forEach((project, index) => {
            if (activeTopic === 'all') {
                project.style.display = '';
                lastVisibleIndex = index;
                return;
            }

            const projectTopics = project.getAttribute('data-topics');
            const shouldShow = projectTopics && projectTopics.includes(activeTopic);
            project.style.display = shouldShow ? '' : 'none';
            if (shouldShow) {
                lastVisibleIndex = index;
            }
        });

        // Second pass: update spacers
        spacers.forEach((spacer, index) => {
            spacer.style.display = (index < lastVisibleIndex) ? '' : 'none';
        });
    }

    filters.forEach(filter => {
        filter.addEventListener('click', function(e) {
            e.preventDefault();
            filters.forEach(f => f.classList.remove('active'));
            this.classList.add('active');
            updateVisibility();
        });
    });

    // Initial visibility update
    updateVisibility();
}

// Try to initialize immediately
initializeFiltering();

// Also try after a short delay to ensure content is loaded
setTimeout(initializeFiltering, 100);

// Also initialize when the DOM is fully loaded
document.addEventListener('DOMContentLoaded', initializeFiltering);
</script>

{{ project(title="PittTron", description="A Large Language Model Trained on University of Pittsburgh Medical Center Electronic Health Records", project_lead="Jordan Hilsman", topic="Clinical NLP,LLM Application", last_entry=false) }}

{{ project(title="ENACT NLP", description="Development and Validation of Natural Language Processing Algorithms in the ENACT National Electronic Health Record Research Network", project_lead="Jordan Hilsman", topic="Clinical NLP", last_entry=false) }}

{{ project(title="Safety of Large Language Models in Healthcare Applications", description="Measuring the safety of LLMs in healthcare", project_lead="Hang Zhang", topic="LLM Alignment", last_entry=false) }}

{{ project(title="AI and Precision Nutrition", description="Investigate how AI has been used in precision nutrition", project_lead="Xizhi Wu", topic="Precision Nutrition", last_entry=false) }}

{{ project(title="Generative AI for Medical Education", description="Investigate how generative AI will impact and advance medical education?", project_lead="Mariano De Leon", topic="LLM Application", last_entry=false) }}

{{ project(title="Precision Rehabilitation", description="Use data-driven approach to identify the precision rehabilitation approaches that could result in optimal clinical outcomes", topic="LLM Application,Clinical NLP", last_entry=false) }}

{{ project(title="Generative AI for Assisting People with Disabilities", description="Investigate how generative AI will assist people with disabilities?", project_lead="Mariano De Leon", topic="LLM Application", last_entry=false) }}

{{ project(title="Generative AI for Pathology", description="Generative AI technologies to advance clinical pratice in pathology using pathology images and EHRs", topic="Foundation Models,LLM Application", last_entry=false) }}

{{ project(title="Evaluation Frameworks for Large Language Models in Healthcare Applications", description="Evaluation needs to be standardized and comprehensive before the adoption of LLMs in healthcare", project_lead="Thomas Tam, Sonish Sivarajkumar", topic="LLM Evaluation", last_entry=false) }}

{{ project(title="Large Language Models for Drug Discovery", description="Designing creative LLM-based approaches to facilitate drug discovery.", project_lead="", topic="LLM Application", last_entry=false) }}

{{ project(title="Generative Deep Patient", description="Foundational AI models and large language models for generative patient embeddings using EHRs", project_lead="Sonish Sivarajkumar", project_lead_website="https://sonishsivarajkumar.github.io/homepage/", topic="Foundation Models,LLM Application,Clinical NLP", last_entry=false) }}

{{ project(title="Precision Oncology", description="NLP and ML algorithms to predict immunotherapy response and metastases prediction on lung adenocarcinoma patients.", project_lead="Sonish Sivarajkumar", project_lead_website="https://sonishsivarajkumar.github.io/homepage/", topic="Cancer Informatics,Clinical NLP", last_entry=true) }}

{{ project(title="Cancer NLP", description="NLP to extract social determinants of health information from ontology progress notes.", project_lead="Xizhi Wu", topic="Clinical NLP,Cancer Informatics", last_entry=true) }}

</div>
