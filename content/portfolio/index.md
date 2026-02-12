+++
title = "Applications"
template = "page.html"
+++

<script>
window.lightboxData = window.lightboxData || {};

function closeAllLightboxes() {
    var lightboxes = document.querySelectorAll('.lightbox');
    lightboxes.forEach(function(lb) {
        lb.style.display = 'none';
    });
}

function openLightbox(galleryId, index) {
    // Close any open lightbox first
    closeAllLightboxes();
    
    var data = window.lightboxData[galleryId];
    if (!data) {
        return;
    }
    data.currentIndex = index;
    var lightbox = document.getElementById('lightbox-' + galleryId);
    var img = document.getElementById('lightbox-img-' + galleryId);
    var counter = document.getElementById('lightbox-counter-' + galleryId);
    
    // Find the project card and position lightbox relative to it
    var card = document.querySelector('[data-gallery-id="' + galleryId + '"]');
    if (card) {
        var cardRect = card.getBoundingClientRect();
        var cardCenterY = cardRect.top + (cardRect.height / 2) + window.scrollY - (window.innerHeight * 0.15);
        lightbox.style.top = cardCenterY + 'px';
    }
    
    img.src = data.images[index];
    counter.textContent = (index + 1) + ' / ' + data.images.length;
    lightbox.style.display = 'block';
    document.body.style.overflow = 'hidden';
}

function closeLightbox(galleryId) {
    var lightbox = document.getElementById('lightbox-' + galleryId);
    lightbox.style.display = 'none';
    document.body.style.overflow = '';
}

function navigateLightbox(galleryId, direction) {
    var data = window.lightboxData[galleryId];
    if (!data) return;
    data.currentIndex += direction;
    if (data.currentIndex < 0) data.currentIndex = data.images.length - 1;
    if (data.currentIndex >= data.images.length) data.currentIndex = 0;
    var img = document.getElementById('lightbox-img-' + galleryId);
    var counter = document.getElementById('lightbox-counter-' + galleryId);
    img.src = data.images[data.currentIndex];
    counter.textContent = (data.currentIndex + 1) + ' / ' + data.images.length;
}

document.addEventListener('keydown', function(e) {
    var lightboxes = document.querySelectorAll('.lightbox');
    lightboxes.forEach(function(lb) {
        if (lb.style.display === 'block') {
            var galleryId = lb.id.replace('lightbox-', '');
            if (e.key === 'Escape') closeLightbox(galleryId);
            if (e.key === 'ArrowLeft') navigateLightbox(galleryId, -1);
            if (e.key === 'ArrowRight') navigateLightbox(galleryId, 1);
        }
    });
});
</script>

<div class="section-intro fade-in">
    <p class="lead">Our application portfolio showcases the innovative software applications and tools we have developed to advance clinical decision support and healthcare research evaluation.</p>
</div>

<div class="portfolio-list fade-in">

{{ portfolio(
    title="MERLIN",
    description="MERLIN is a generative AI clinical decision support system that uses a multi-agent architecture to identify dangerous secondary headache warning for primary care physicians. Built with LangGraph and powered by local LLMs, MERLIN provides transparent, explainable diagnostic assistance for urgent headache referrals.",
    developers="Yanshan Wang, Xizhi Wu",
    collaborators="Justin F Rousseau, MD Clinical Informatics Center, UT Southwestern Medical Center; Yifan Peng, PhD, Population Health Sciences, Weill Cornell Medicine",
    technology="LangGraph, LangChain, Python, Flask, HTML5, CSS3, Vanilla JavaScript",
    publication="Wu X, Garduno-Rapp NE, Rousseau JF, Thakkallapally M, Zhang H, Ji Y, Visweswaran S, Peng Y, Wang Y. Orchestrator Multi-Agent Clinical Decision Support System for Secondary Headache Diagnosis in Primary Care. arXiv preprint arXiv:2512.04207. 2025 Dec 3.",
    images=["MERLIN/MERLIN1.png", "MERLIN/MERLIN2.png", "MERLIN/MERLIN3.png", "MERLIN/MERLIN5.png", "MERLIN/MERLIN6.png"]
) }}

{{ portfolio(
    title="QUEST",
    description="QUEST is a software tool designed to facilitate the human evaluation of large language models (LLMs) in healthcare. As the integration of generative AI into healthcare advances, it is crucial to ensure the safety and efficacy of these models through rigorous human assessments. QUEST provides a comprehensive evaluation framework organized into three main phases: Planning, Implementation and Adjudication, and Scoring and Review. This tool supports the evaluation process by guiding users through goal setting, task identification, stakeholder consideration, and success criteria definition, ultimately enhancing the reliability and effectiveness of LLMs in healthcare.",
    developers="Yanshan Wang, Yu-Chow Tam, Sonish Sivarajkumar",
    collaborators="Shyam Visweswaran, Department of Biomedical Informatics, University of Pittsburgh; Sunyang Fu, Department of Clinical and Health Informatics, Center for Translational AI Excellence and Applications in Medicine, University of Texas Health Science Center at Houston; Piyush Mathur, Department of Anesthesiology, Cleveland Clinic; Giovanni E. Cacciamani, Department of Urology, Keck School of Medicine, University of Southern California; Yifan Peng, Department of Population Health Sciences, Weill Cornell Medicine",
    technology="Next.js, Node.js, SQLite, Tailwind",
    publication="Tam TY, Sivarajkumar S, Kapoor S, Stolyar AV, Polanska K, McCarthy KR, Osterhoudt H, Wu X, Visweswaran S, Fu S, Mathur P. A framework for human evaluation of large language models in healthcare derived from literature review. NPJ digital medicine. 2024 Sep 28;7(1):258.",
    images=["QUEST/QUEST1.png", "QUEST/QUEST2.png", "QUEST/QUEST3.png", "QUEST/QUEST4.png", "QUEST/QUEST5.png", "QUEST/QUEST6.png", "QUEST/QUEST7.png", "QUEST/QUEST8.png"]
) }}

{{ portfolio(
    title="SmartBack",
    description="SmartBack is an intelligent web application that generates personalized exercise programs for individuals with low back pain. Built using advanced AI and Retrieval-Augmented Generation to provide tailored 7-day exercise plans that automatically adapt to patient progress. Features gamification mechanics including badges, levels, and streak tracking to promote long-term adherence, plus automated coordinator alerts for patients reporting worsening symptoms.",
    developers="Mariano De Leon, MS",
    collaborators="Yanshan Wang, PhD, University of Pittsburgh; Becky Zhou; Xu Yi",
    technology="React.js, Next.js, Node.js, Express.js, Claude API, Anthropic SDK, Bootstrap, Docker, AWS",
    publication="",
    link="http://smartback-alb-1910190298.us-east-1.elb.amazonaws.com",
    images=["SmartBack/SmartBack1.png", "SmartBack/SmartBack2.png", "SmartBack/SmartBack3.png"]
) }}

{{ portfolio(
    title="AIDA",
    description="AIDA is an intelligent chatbot that helps individuals find and access assistive technology funding programs in Pennsylvania Assistive Technology Foundation (PATF). The platform uses Retrieval-Augmented Generation to provide personalized program recommendations based on user needs, location, diagnosis, and insurance coverage. Users can interact via text or voice input in English or Spanish.",
    developers="Mariano De Leon, MS",
    collaborators="Yanshan Wang, PhD; Ding Dan, PhD; Adit Shah; Gina Novario; University of Pittsburgh",
    technology="Angular 19, TypeScript, Django 5.1.4, MongoDB, Azure OpenAI, Azure AI Search, Azure Cognitive Services, TailwindCSS",
    publication="",
    images=["AIDA/AIDA1.png", "AIDA/AIDA2.png", "AIDA/AIDA3.png"]
) }}

{{ portfolio(
    title="Anatomy Assistant",
    description="AnatomyAssistant is an intelligent AI-powered chatbot designed to enhance the learning experience for anatomy students. The application leverages advanced AI and Retrieval-Augmented Generation (RAG) to provide accurate, course-specific support by answering complex anatomical questions, generating customized quizzes to test knowledge retention, and precisely locating relevant content within video lectures with timestamp navigation. The system integrates with course materials to deliver contextually relevant responses, helping students master difficult concepts and prepare for examinations more effectively.",
    developers="Mariano De Leon, MS",
    collaborators="Yanshan Wang, PhD; Reivian Berrios Barillas, DPT; University of Pittsburgh",
    technology="React.js, Flask, OpenAI GPT-4, LangChain, Pinecone, AWS",
    publication="",
    link="http://anatomy-chatbot-alb-470813522.us-east-1.elb.amazonaws.com/",
    images=["AnatomyAssistant/AnatomyAssistant1.png", "AnatomyAssistant/AnatomyAssistant2.png", "AnatomyAssistant/AnatomyAssistant3.png"]
) }}

{{ portfolio(
    title="StudentFeedback",
    description="StudentFeedback is a comprehensive web-based application designed for managing and analyzing student feedback with AI-powered insights. The platform features secure Microsoft OAuth authentication, interactive data visualization dashboards, and automated feedback processing pipelines to support educational assessment and continuous improvement. Instructors can efficiently collect, organize, and analyze student responses while the AI system automatically identifies key themes, sentiment patterns, and actionable insights to enhance teaching effectiveness and student outcomes.",
    developers="Mariano De Leon",
    collaborators="Yanshan Wang, PhD; Reivian Berrios Barillas, DPT, PhD; University of Pittsburgh",
    technology="React.js, Flask, Python, OpenAI API, pandas, Microsoft OAuth, Docker, Nginx, Gunicorn",
    publication="",
    images=["StudentFeedback/StudentFeedback1.png", "StudentFeedback/StudentFeedback2.png", "StudentFeedback/StudentFeedback3.png"]
) }}

</div>
