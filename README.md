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
        h1 {
            font-size: 24px;
            margin-bottom: 20px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            background-color: #f9f9f9;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 12px;
            text-align: left;
        }
        tr:hover {
            background-color: #e0e0e0;
        }
        a {
            color: #1a0dab;
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }
        hr {
            border: 0;
            border-top: 1px solid #ddd;
            margin: 20px 0;
        }
        .footer {
            margin-top: 20px;
            font-size: 14px;
        }
        .section {
            margin-bottom: 40px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>FFXIV EN JP Glossary</h1>
        <p>This is a list of Japanese phrases you might see in Final Fantasy XIV and their more accurate translation. The goal is for people to fully understand Party Finder descriptions and understand the main gist of communication. Romaji is provided in order to help people write it using IME. It does not always represent reading (example: Konnichiha).</p>
        <p>IF YOU WANT A TERM ADDED, DM ME ON DISCORD (niwafairy) OR CREATE AN ISSUE ON GITHUB. PROVIDE AN ENGLISH AND/OR JAPANESE TERM. It doesn't matter if you don't have the translation, I'll provide it.</p>
        <p>Bookmark the page, cause the URL is bad and I should feel bad.</p>
        <p>Game8 (JP) Strats can be found at <a href="https://game8.jp/ff14" target="_blank">Game8</a></p>
        <hr>
        <p>日本語</p>
        <p>これは、英語圏のプレイヤーたちとパーティ募集でレイドをする際に役立つ英語のフレーズのリストです。パーティー募集で一般的な処理法を的確に理解するとともに、基本的な連携が取れるようになることを目標として作りました。元々は日本語の資料を英語に翻訳することで資料を作成していたため、現時点で解説は英語版しかありませんが正確な処理法等の翻訳をご覧いただけます。</p>
        <p>用語/フレーズを追加したい場合は、Discordで私にメッセージを送ってください（niwafairy）。追加したい用語、またはフレーズの翻訳が分からなくても構いません。</p>
        <p>URLが非常に長いため、サイトをブックマークしておくことをお勧めします。</p>
        <p><a href="https://tuufless.github.io/FFXIV-Elemental-Raid-Macros/" target="_blank">Tuufless GitHub (EN/英圏 攻略)</a> このサイトの管理人であるTuuflessは、サイトの運営を通じて、日本語圏のプレイヤーと英語圏のプレイヤーとの間にある隔たりをなくし、国際的な交流ができるコミュニティを形成するために尽力しています。</p>

        <div id="tables">
            <!-- Tables will be inserted here -->
        </div>
    </div>
    <script>
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
                        const [japanese, romaji, english, description, tag] = row.split('|');
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
