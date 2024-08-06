<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta http-equiv="x-ua-compatible" content="ie=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>FFXIV EN JP Glossary</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        .container {
            padding: 20px;
            max-width: 1200px;
            margin: auto;
        }
        textarea {
            width: 100%;
            height: 200px;
            margin-bottom: 20px;
            padding: 10px;
            font-size: 16px;
            border: 1px solid #ddd;
            border-radius: 4px;
            box-sizing: border-box;
        }
        #output {
            border: 1px solid #ddd;
            border-radius: 4px;
            padding: 10px;
            min-height: 100px;
            white-space: pre-wrap; /* Preserve line breaks */
        }
        .highlight {
            background-color: blue;
            cursor: pointer;
            border-radius: 3px;
        }
        .tooltip {
            position: absolute;
            background-color: #333;
            color: #fff;
            padding: 10px;
            border-radius: 3px;
            display: none;
            font-size: 14px;
            max-width: 300px;
            z-index: 1000;
        }
        .tooltip-description {
            font-size: 12px;
            color: #ccc;
        }
        .section {
            margin-top: 20px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 20px;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 8px;
            text-align: left;
        }
        a {
            color: #007bff;
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Text Translation Tool -->
        <h1>Macro Translator (BETA)</h1>
        It works, but it's missing a lot of words.    
        <hr>
        <textarea id="text-box" placeholder="Paste your text here..."></textarea>
        <div id="output"></div>
        <div class="tooltip" id="tooltip"></div>

        <!-- Glossary Section -->
        <hr>
        <h1>FFXIV EN JP Glossary</h1>
        <p>This is a list of Japanese phrases you might see in Final Fantasy XIV and their more accurate translation. The goal is for people to fully understand Party Finder descriptions and understand the main gist of communication. Romaji is provided in order to help people write it using IME. It does not always represent reading (example: Konnichiha).</p>
        <p>IF YOU WANT A TERM ADDED, DM ME ON DISCORD (nerilingonberry) OR CREATE AN ISSUE ON GITHUB. PROVIDE AN ENGLISH AND/OR JAPANESE TERM. It doesn't matter if you don't have the translation, I'll provide it.</p>
        <p>Bookmark the page, cause the URL is bad and I should feel bad.</p>
        <p>Game8 (JP) Strats can be found at <a href="https://game8.jp/ff14" target="_blank">Game8</a></p>
        <hr>
        <p>これは、英語圏のプレイヤーたちとパーティ募集でレイドをする際に役立つ英語のフレーズのリストです。パーティー募集で一般的な処理法を的確に理解するとともに、基本的な連携が取れるようになることを目標として作りました。元々は日本語の資料を英語に翻訳することで資料を作成していたため、現時点で解説は英語版しかありませんが正確な処理法等の翻訳をご覧いただけます。</p>
        <p>用語/フレーズを追加したい場合は、Discordで私にメッセージを送ってください（nerilingonberry）。追加したい用語、またはフレーズの翻訳が分からなくても構いません。</p>
        <p>URLが非常に長いため、サイトをブックマークしておくことをお勧めします。</p>
        <p><a href="https://tuufless.github.io/FFXIV-Elemental-Raid-Macros/" target="_blank">Tuufless GitHub (EN/英圏 攻略)</a> このサイトの管理人であるTuuflessは、サイトの運営を通じて、日本語圏のプレイヤーと英語圏のプレイヤーとの間にある隔たりをなくし、国際的な交流ができるコミュニティを形成するために尽力しています。</p>

        <div id="tables">
            <!-- Tables will be inserted here -->
        </div>
    </div>

    <script>
        const translations = {}; // Placeholder for translations

        // Fetch translations from the raw text file
        fetch('https://raw.githubusercontent.com/NiwaFairy/MacroTranslator/main/Test2.txt')
            .then(response => response.text())
            .then(text => {
                // Parse the text file content
                const lines = text.split('\n');
                lines.forEach(line => {
                    const [japanese, romaji, translation, comment, tag] = line.split('|').map(s => s.trim());
                    if (japanese && translation) {
                        translations[japanese] = {
                            romaji: romaji || '',
                            translation: translation || '',
                            comment: comment || '',
                            tag: tag || ''
                        };
                    }
                });
                console.log('Translations:', translations); // Debug log
            })
            .catch(error => console.error('Error fetching translations:', error));

        document.getElementById('text-box').addEventListener('input', function() {
            const inputText = this.value;
            const outputDiv = document.getElementById('output');
            outputDiv.innerHTML = '';

            let processedText = inputText;
            Object.keys(translations).forEach(key => {
                const regex = new RegExp(`(${key})`, 'g');
                processedText = processedText.replace(regex, '<span class="highlight">$1</span>');
            });

            outputDiv.innerHTML = processedText;
        });

        document.getElementById('output').addEventListener('mousemove', function(e) {
            const tooltip = document.getElementById('tooltip');
            const target = e.target;

            if (target.classList.contains('highlight')) {
                const mouseX = e.clientX;
                const mouseY = e.clientY;
                tooltip.style.left = `${mouseX + 15}px`;
                tooltip.style.top = `${mouseY + 15}px`;

                const word = target.textContent.trim();
                const entry = translations[word];
                if (entry) {
                    let tooltipText = '';
                    if (entry.romaji) tooltipText += `<strong>Romaji:</strong> ${entry.romaji}<br>`;
                    if (entry.translation) tooltipText += `<strong>Translation:</strong> ${entry.translation}<br>`;
                    if (entry.comment) tooltipText += `<strong>Comment:</strong> ${entry.comment}<br>`;
                    if (entry.tag) tooltipText += `<strong>Tag:</strong> ${entry.tag}`;

                    tooltip.innerHTML = tooltipText;
                    tooltip.style.display = 'block';
                } else {
                    tooltip.style.display = 'none';
                }
            } else {
                tooltip.style.display = 'none';
            }
        });

        document.getElementById('output').addEventListener('mouseleave', function() {
            const tooltip = document.getElementById('tooltip');
            tooltip.style.display = 'none';
        });

        document.addEventListener('DOMContentLoaded', () => {
            const url = 'https://raw.githubusercontent.com/NiwaFairy/MacroTranslator/main/Test2.txt';

            fetch(url)
                .then(response => {
                    if (!response.ok) {
                        throw new Error('Network response was not ok');
                    }
                    return response.text();
                })
                .then(data => {
                    console.log("Data fetched successfully");
                    console.log(data);  // Log data to check its content

                    const rows = data.split('\n');
                    const tablesContainer = document.querySelector('#tables');
                    tablesContainer.innerHTML = '';  // Clear the loading message

                    const tableData = {};
                    rows.forEach(row => {
                        if (row.trim() === '') return; 
                        const [japanese, romaji, english, description, tag] = row.split('|').map(s => s.trim());
                        if (tag) {
                            if (!tableData[tag]) {
                                tableData[tag] = [];
                            }
                            tableData[tag].push({ japanese, romaji, english, description });
                        }
                    });

                    for (const [tag, entries] of Object.entries(tableData)) {
                        const section = document.createElement('div');
                        section.classList.add('section');
                        section.innerHTML = `<h2>${tag}</h2>`;

                        const table = document.createElement('table');
                        const thead = document.createElement('thead');
                        const tbody = document.createElement('tbody');
                        table.appendChild(thead);
                        table.appendChild(tbody);

                        thead.innerHTML = `
                            <tr>
                                <th>Japanese</th>
                                <th>Romaji</th>
                                <th>English</th>
                                <th>Description</th>
                            </tr>
                        `;

                        entries.forEach(entry => {
                            const tr = document.createElement('tr');
                            tr.innerHTML = `
                                <td>${entry.japanese}</td>
                                <td>${entry.romaji}</td>
                                <td>${entry.english}</td>
                                <td>${entry.description}</td>
                            `;
                            tbody.appendChild(tr);
                        });

                        if (tbody.children.length === 0) {
                            const tr = document.createElement('tr');
                            tr.innerHTML = '<td colspan="4">No data available</td>';
                            tbody.appendChild(tr);
                        }

                        section.appendChild(table);
                        tablesContainer.appendChild(section);
                    }
                })
                .catch(error => {
                    console.error('Error fetching the file:', error);
                    const tablesContainer = document.querySelector('#tables');
                    tablesContainer.innerHTML = '<p>Error loading data.</p>';
                });
        });
    </script>
</body>
</html>
