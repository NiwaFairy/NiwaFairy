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
        h1 {
            font-size: 24px;
            margin-bottom: 20px;
        }
        pre {
            font-family: monospace;
            white-space: pre-wrap;
            border: 1px solid #ccc;
            padding: 10px;
            background-color: #f9f9f9;
            overflow-x: auto;
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
        <pre id="content">Loading...</pre>
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
                    let formattedText = '';

                    rows.forEach(row => {
                        const columns = row.split('|');
                        if (columns.length === 4) {
                            const [japanese, romaji, english, description] = columns;
                            formattedText += `${japanese.padEnd(30)}${romaji.padEnd(30)}${english.padEnd(30)}${description}\n`;
                        }
                    });

                    document.getElementById('content').textContent = formattedText || 'No data available';
                })
                .catch(error => {
                    console.error('Error fetching the file:', error);
                    document.getElementById('content').textContent = 'Error loading data.';
                });
        });
    </script>
</body>
</html>
