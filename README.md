<html lang="en" class="h-100">

<head>
  <meta charset="utf-8">
  <meta http-equiv="x-ua-compatible" content="ie=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>FFXIV EN JP Glossary</title>
</head>
<br>
English
<br>
<br>
This is a list of Japanese phrases you might see in Final Fantasy XIV and their more accurate translation.
The goal is for people to fully understand Party Finder descriptions and understand the main jist of communication. Romaji is provided in order to help people write it using IME. It does not always represent reading (example: Konnichiha).
<br>
<br> IF YOU WANT A TERM ADDED, DM ME ON DISCORD (niwafairy) OR CREATE AN ISSUE ON GITHUB. PROVIDE AN ENGLISH AND/OR JAPANESE TERM.
<br>It doesn't matter if you don't have the translation, I'll provide it.

<br>
<br>
Bookmark the page, cause the URL is bad and I should feel bad.
<br>
<br>
Game8 (JP) Strats can be found at
<a href="https://game8.jp/ff14"> Game8 </a>
<br>
<br>
-------------------------------------------------------------------------------------------
<br>
<br>
日本語
<br>
<br>
これは、英語圏のプレイヤーたちとパーティ募集でレイドをする際に役立つ英語のフレーズのリストです。
パーティー募集で一般的な処理法を的確に理解するとともに、基本的な連携が取れるようになることを目標として作りました。
元々は日本語の資料を英語に翻訳することで資料を作成していたため、現時点で解説は英語版しかありませんが正確な処理法等の翻訳をご覧いただけます。
<br>
<br> 用語/フレーズを追加したい場合は、Discordで私にメッセージを送ってください（niwafairy）。
<br> 追加したい用語、またはフレーズの翻訳が分からなくても構いません。

<br>
<br>
URLが非常に長いため、サイトをブックマークしておくことをお勧めします。
<br>
<br>
<a href="https://tuufless.github.io/FFXIV-Elemental-Raid-Macros/"> Tuufless GitHub (EN/英圏 攻略) </a>
<br>
このサイトの管理人であるTuuflessは、サイトの運営を通じて、日本語圏のプレイヤーと英語圏のプレイヤーとの間にある隔たりをなくし、国際的な交流ができるコミュニティを形成するために尽力しています。
<br>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formatted Text</title>
    <style>
        pre {
            font-family: monospace;
            white-space: pre-wrap;
        }
    </style>
</head>
<body>
    <h1>Formatted Text</h1>
    <pre id="content">Loading...</pre>
    <script>
        const url = 'https://raw.githubusercontent.com/NiwaFairy/MacroTranslator/main/Test2.txt';

        fetch(url)
            .then(response => {
                if (!response.ok) {
                    throw new Error('Network response was not ok');
                }
                return response.text();
            })
            .then(data => {
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
    </script>
</body>
</html>

