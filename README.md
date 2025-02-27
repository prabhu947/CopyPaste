document.addEventListener('DOMContentLoaded', () => {
    const imageViewBtn = document.getElementById('imageBtn');
    const tableViewBtn = document.getElementById('tableBtn');
    const links = document.getElementById('links');
    const contentDivs = document.querySelectorAll('.content');
    let currentView = 'image';

    imageViewBtn.addEventListener('click', () => updateView('image'));
    tableViewBtn.addEventListener('click', () => updateView('table'));

    links.addEventListener('click', (event) => {
        if (event.target.tagName === 'A') {
            event.preventDefault();
            if (event.target.getAttribute('type') === currentView) {
                showContent(event.target.getAttribute('content'));
            }
        }
    });

    function updateView(view) {
        currentView = view;
        updateLinks();
    }

    function updateLinks() {
        links.querySelectorAll('a').forEach(link => {
            link.style.display = (link.getAttribute('type') === currentView) ? 'block' : 'none';
        });
    }

    function showContent(contentId) {
        contentDivs.forEach(div => {
            div.classList.toggle('active', div.id === contentId);
        });
    }

    updateLinks();
});
