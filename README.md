# ONLINE-CODE-EDITOR
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Online Code Editor</title>
    <link rel="icon" href="logo.png" type="image/png">
    <link rel="stylesheet" href="index.css">
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="headlogo">
                &lt;
            </div>
            <div class="heading">
                <div class="top-h"><h2>Online Code Editor</h2></div>
                <div class="top-h"><h4>HTML | CSS | JavaScript</h4></div>
            </div>
            <div class="headlogo">
                &#47;&gt;
            </div>
        </div>
        <div class="main">
            <div class="top">
                <div class="html-div">
                    <label id="html">
                        <div class="label-box">HTML</div>
                        <div class="labelbox2">
                            <button id="d1"><img class="down" src="download.png"></button>
                        </div>
                    </label>
                    <textarea id="htmlCode" onkeyup="run()" class="textbox"></textarea>
                </div>
                <div class="css-div">
                    <label id="css">
                        <div class="label-box">CSS</div>
                        <div class="labelbox2">
                            <button id="d2"><img class="down" src="download.png"></button>
                        </div>
                    </label>
                    <textarea id="cssCode" onkeyup="run()" class="textbox"></textarea>
                </div>
                <div class="js-div">
                    <label id="js">
                        <div class="label-box">JavaScript</div>
                        <div class="labelbox2">
                            <button id="d3"><img class="down" src="download.png"></button>
                        </div>
                    </label>
                    <textarea id="jsCode" onkeyup="run()" class="textbox"></textarea>
                </div>
            </div>
            <div class="bottom">
                <label id="out">
                    <div class="label-box">Output</div>
                    <div class="labelbox2">
                        <button id="shareBtn" onclick="share()">
                            <img class="down" src="share.png">
                        </button>
                        <button id="btn" onclick="goFullscreen('output'); return false">
                            <img class="down" src="full.png">
                        </button>
                        <button id="downloadOutputBtn">
                            <img class="down" src="download.png">
                        </button>
                    </div>
                </label>
                <iframe id="output"></iframe>
            </div>
        </div>
    </div>
    <script src="index.js"></script>
    <script>
        function run() {
            const htmlCode = document.getElementById('htmlCode').value;
            const cssCode = document.getElementById('cssCode').value;
            const jsCode = document.getElementById('jsCode').value;
            const output = document.getElementById('output');

            const source = `
                <html>
                <head>
                    <style>${cssCode}</style>
                </head>
                <body>
                    ${htmlCode}
                    <script>${jsCode}<\/script>
                </body>
                </html>
            `;

            output.srcdoc = source;
        }

        document.getElementById('downloadOutputBtn').addEventListener('click', function() {
            const htmlCode = document.getElementById('htmlCode').value;
            const cssCode = document.getElementById('cssCode').value;
            const jsCode = document.getElementById('jsCode').value;

            const source = `
                <html>
                <head>
                    <style>${cssCode}</style>
                </head>
                <body>
                    ${htmlCode}
                    <script>${jsCode}<\/script>
                </body>
                </html>
            `;

            const blob = new Blob([source], { type: 'text/html' });
            const link = document.createElement('a');
            link.href = URL.createObjectURL(blob);
            link.download = 'output.html';
            link.click();
        });
    </script>
</body>
</html>
