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
.header {
    position: sticky;
    top: 0;
    padding: 10px;
    background-color: #490da9;
    color: #f1f1f1;
    text-align: center;
}

.header button {
    padding: 10px 20px;
    background-color: #04AA6D;
    color: rgb(255, 255, 255);
}

.header button:hover {
    background-color: #45a049;
}

.vertical-menu {
    width: 200px;
    height: 100%;
    font-size: 20px;
    display: flex;
    flex-direction: column;
    position: fixed;
}

.vertical-menu a {
    color: black;
    background-color: #bcea94;
    display: block;
    padding: 12px;
    text-decoration: none;
}

.vertical-menu a:hover {
    background-color: #ccc;
}

.content {
    display: none;
}

.content.active {
    display: block;
}

#content {
    margin-left: 220px;
    padding: 20px;
}

table, th, td {
    border: 1px solid black;
    padding: 8px;
    text-align: center;
}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Basic Website</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="header">
        <button id="imageBtn">Image View</button>
        <button id="tableBtn">Table View</button>
    </div>

    <div class="vertical-menu" id="links">
        <a href="#" type="image" content="image1">a</a>
        <a href="#" type="image" content="image2">b</a>
        <a href="#" type="image" content="image3">c</a>
        <a href="#" type="table" content="table1">a</a>
        <a href="#" type="table" content="table2">b</a>
        <a href="#" type="table" content="table3">c</a>
    </div>

    <div id="content">
        <div id="image1" class="content">
            <img src="sun.jpg" alt="Image 1">
        </div>
        <div id="image2" class="content">
            <img src="earth.jpg" alt="Image 2">
        </div>
        <div id="image3" class="content">
            <img src="moon.jpg" alt="Image 3">
        </div>
        <div id="table1" class="content">
            <table>
                <tr>
                    <th>Firstname</th>
                    <th>Lastname</th>
                    <th>Age</th>
                </tr>
                <tr>
                    <td>Priya</td>
                    <td>Sharma</td>
                    <td></td>
                </tr>
            </table>
        </div>
    </div>
</body>
</html>

