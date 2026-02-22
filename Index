<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ultimate Mobile Trivia 2026</title>
    <style>
        :root { --p: #2563eb; --s: #059669; --bg: #f3f4f6; }
        body { font-family: sans-serif; background: var(--bg); margin: 0; padding: 15px; display: flex; justify-content: center; }
        #game-box { width: 100%; max-width: 450px; background: white; padding: 20px; border-radius: 20px; box-shadow: 0 10px 25px rgba(0,0,0,0.1); }
        .header { display: flex; justify-content: space-between; font-weight: bold; border-bottom: 2px solid #eee; margin-bottom: 15px; padding-bottom: 10px; }
        .q-text { font-size: 1.2rem; margin-bottom: 20px; min-height: 60px; }
        .options { display: grid; gap: 10px; }
        button { padding: 15px; border: 1px solid #ddd; border-radius: 10px; background: white; font-size: 1rem; text-align: left; transition: 0.2s; -webkit-tap-highlight-color: transparent; }
        button:active { background: #e0e7ff; border-color: var(--p); }
        .hidden { display: none; }
        .result-card { text-align: center; }
        .score { font-size: 2.5rem; color: var(--s); font-weight: 800; margin: 15px 0; }
        .insight-box { background: #fffbeb; padding: 15px; border-radius: 10px; font-size: 0.9rem; border-left: 4px solid #f59e0b; margin-top: 15px; }
        .next-btn { background: var(--p); color: white; border: none; width: 100%; text-align: center; margin-top: 20px; cursor: pointer; }
    </style>
</head>
<body>

<div id="game-box">
    <div id="quiz-ui">
        <div class="header">
            <span id="cat-title">Category</span>
            <span id="val-tag" style="color: var(--s)">$5</span>
        </div>
        <div class="q-text" id="q-text">Loading...</div>
        <div class="options" id="opt-box"></div>
    </div>

    <div id="result-ui" class="hidden result-card">
        <h2 id="res-title">Category Complete!</h2>
        <p>You won:</p>
        <div class="score" id="res-cash">$0</div>
        <p id="res-acc">Accuracy: 0%</p>
        <div class="insight-box" id="res-insight"></div>
        <button class="next-btn" onclick="nextCategory()">Next Challenge</button>
    </div>
</div>

<script>
const data = [
    {
        cat: "Disney & Pixar",
        questions: [
            { v: 5, q: "In Zootopia, what is Judy Hopps' official job title?", a: ["Meter Maid", "Police Officer", "Detective", "Mayor"], c: 1 },
            { v: 10, q: "Which 2024 Pixar sequel became the highest-grossing animated film of all time?", a: ["Inside Out 2", "Toy Story 5", "Moana 2", "Elio"], c: 0 },
            { v: 15, q: "What is the name of the 'savaging' flower in Zootopia?", a: ["Night Howlers", "Blue Violets", "Wolfsbane", "Moon Lilies"], c: 0 },
            { v: 20, q: "In Pixar's 'Coco', what is the name of Miguel's dog?", a: ["Dante", "Poco", "Hector", "Bruno"], c: 0 },
            { v: 25, q: "Which Disney park opened 'Zootopia: Better Zoogether' in 2025?", a: ["Disney World", "Disneyland Paris", "Animal Kingdom", "Shanghai Disneyland"], c: 2 },
            { v: 30, q: "What is the address P. Sherman's dentist office in Finding Nemo?", a: ["22 Sydney St", "42 Wallaby Way", "10 Coral Rd", "15 Shark Cove"], c: 1 },
            { v: 35, q: "In 'Turning Red', what animal does Mei Lee turn into?", a: ["Red Panda", "Tiger", "Fox", "Cat"], c: 0 },
            { v: 40, q: "What is the first name of the character 'Mr. Big' in Zootopia?", a: ["Tino", "Fru Fru", "Vito", "Guiseppe"], c: 0 },
            { v: 45, q: "Which Pixar movie features a robot named WALL-E?", a: ["WALL-E", "Robots", "Bolt", "Cars"], c: 0 },
            { v: 50, q: "Who was the voice of Nick Wilde in Zootopia?", a: ["Jason Bateman", "Bill Hader", "Chris Pratt", "Tom Hanks"], c: 0 }
        ],
        insight: "Valuation Tip: Disney 'Vault' items often appreciate. A 2025 'Inside Out 2' limited popcorn bucket can resell for $45, while a standard one is only $15."
    },
    {
        cat: "Taylor Swift (The Eras)",
        questions: [
            { v: 5, q: "What is Taylor's lucky number?", a: ["22", "1989", "13", "8"], c: 2 },
            { v: 10, q: "Which album features the 'Red Scarf'?", a: ["Speak Now", "Red", "Folklore", "Reputation"], c: 1 },
            { v: 15, q: "What city hosted the final show of The Eras Tour in Dec 2024?", a: ["Toronto", "Vancouver", "London", "Tokyo"], c: 1 },
            { v: 20, q: "Which vault track features Phoebe Bridgers?", a: ["Nothing New", "Better Man", "Castles Crumbling", "I Can See You"], c: 0 },
            { v: 25, q: "Taylor's 11th studio album released in 2024 is titled...?", a: ["The Anthology", "TTPD", "Midnights", "Evermore"], c: 1 },
            { v: 30, q: "Who is the 'Eras Tour' movie director?", a: ["Sam Wrench", "Greta Gerwig", "Taylor Swift", "Blake Lively"], c: 0 },
            { v: 35, q: "What was Taylor's first self-owned album (not a Taylor's Version)?", a: ["Lover", "Reputation", "1989", "Folklore"], c: 0 },
            { v: 40, q: "Which song was the first 'Taylor's Version' vault track ever released?", a: ["You All Over Me", "Mr. Perfectly Fine", "I Bet You Think About Me", "Slut!"], c: 0 },
            { v: 45, q: "What is the name of Taylor's cat with the highest 'net worth'?", a: ["Meredith Grey", "Olivia Benson", "Benjamin Button", "Karma"], c: 1 },
            { v: 50, q: "Which song did Taylor write entirely by herself at age 14?", a: ["Lucky You", "The Best Day", "Tim McGraw", "Our Song"], c: 0 }
        ],
        insight: "Resale Insight: Official Eras Tour hoodies (New: $75) maintain a used 'Floor Price' of $50 if in good condition. Fakes sell for <$20."
    },
    {
        cat: "Finance & Canadian History",
        questions: [
            { v: 5, q: "What is the tax-free account limit for most Canadians (TFSA)?", a: ["$7,000", "Varies by year", "$10,000", "$5,000"], c: 1 },
            { v: 10, q: "Who is the current Prime Minister of Canada (as of 2026)?", a: ["Justin Trudeau", "Pierre Poilievre", "Jagmeet Singh", "Stephen Harper"], c: 0 },
            { v: 15, q: "The 'Rule of 72' helps you calculate what?", a: ["Tax owing", "Time to double money", "Retirement age", "Credit score"], c: 1 },
            { v: 20, q: "Canada celebrates its 150th anniversary of the 'Indian Act' in which year?", a: ["2024", "2025", "2026", "2027"], c: 2 },
            { v: 25, q: "Which Canadian city hosted its 50th Olympic anniversary in 2026?", a: ["Montreal", "Calgary", "Vancouver", "Toronto"], c: 0 },
            { v: 30, q: "What is a 'Dividend'?", a: ["A loan", "Company profit share", "A tax penalty", "Stock price"], c: 1 },
            { v: 35, q: "Which province joined Confederation last (1949)?", a: ["PEI", "Newfoundland", "Alberta", "BC"], c: 1 },
            { v: 40, q: "What is the Bank of Canada's typical inflation target?", a: ["0%", "2%", "5%", "10%"], c: 1 },
            { v: 45, q: "In 2025, which Canadian space mission saw the first Canadian orbit the moon?", a: ["Artemis II", "Apollo 18", "STS-100", "Canadarm3"], c: 0 },
            { v: 50, q: "What does MER stand for in mutual funds?", a: ["Management Expense Ratio", "Market Equity Rate", "Monthly Earned Return", "Minimum Entry Requirement"], c: 0 }
        ],
        insight: "Savings Tip: Used financial textbooks from 2023-2024 are often a 'Steal' at $10-15. Basic principles don't change, even if tax numbers do!"
    }
];

let catIdx = 0, qIdx = 0, total = 0, catCorrect = 0;

function loadQ() {
    const q = data[catIdx].questions[qIdx];
    document.getElementById('cat-title').innerText = data[catIdx].cat;
    document.getElementById('val-tag').innerText = `$${q.v}`;
    document.getElementById('q-text').innerText = q.q;
    const box = document.getElementById('opt-box');
    box.innerHTML = '';
    q.a.forEach((opt, i) => {
        const b = document.createElement('button');
        b.innerText = opt;
        b.onclick = () => {
            if(i === q.c) { total += q.v; catCorrect++; }
            qIdx++;
            if(qIdx < 10) loadQ(); else showRes();
        };
        box.appendChild(b);
    });
}

function showRes() {
    document.getElementById('quiz-ui').classList.add('hidden');
    document.getElementById('result-ui').classList.remove('hidden');
    document.getElementById('res-cash').innerText = `$${total}`;
    document.getElementById('res-acc').innerText = `Accuracy: ${(catCorrect/10)*100}%`;
    document.getElementById('res-insight').innerText = data[catIdx].insight;
}

function nextCategory() {
    catIdx++;
    if(catIdx < data.length) {
        qIdx = 0; catCorrect = 0;
        document.getElementById('quiz-ui').classList.remove('hidden');
        document.getElementById('result-ui').classList.add('hidden');
        loadQ();
    } else {
        document.getElementById('res-title').innerText = "Grand Champion!";
        document.querySelector('.next-btn').style.display = 'none';
    }
}
loadQ();
</script>
</body>
</html>
