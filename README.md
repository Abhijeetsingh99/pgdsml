document.getElementById('hamburger').addEventListener('click', function() {
    document.getElementById('menu').classList.toggle('show');
});


let slideIndex = 0;

function showSlides() {
    let slides = document.querySelectorAll(".slide");
    slides.forEach(slide => slide.style.display = "none");

    slideIndex++;
    if (slideIndex > slides.length) { slideIndex = 1; }
    
    slides[slideIndex - 1].style.display = "block";
    setTimeout(showSlides, 3000);
}

showSlides();


let topButton = document.getElementById("topBtn");

window.onscroll = function() {
    if (document.documentElement.scrollTop > 200) {
        topButton.classList.add("show");
    } else {
        topButton.classList.remove("show");
    }
};

topButton.onclick = function() {
    window.scrollTo({ top: 0, behavior: "smooth" });
};


const sections = document.querySelectorAll('.hidden');

const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.classList.add('show');
        }
    });
}, { threshold: 0.3 });

sections.forEach(section => observer.observe(section));
