<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Happy New Year</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
    margin: 0;
    height: 100vh;
    font-family: 'Segoe UI', sans-serif;
    background: linear-gradient(135deg, #ff69b4, #1e90ff);
    overflow: hidden;
}

/* COUNTDOWN */
#countdownPage {
    position: fixed;
    inset: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    z-index: 10;
}

.countBox {
    background: rgba(255,255,255,0.15);
    backdrop-filter: blur(12px);
    padding: 40px 60px;
    border-radius: 25px;
    text-align: center;
}

#countdown {
    font-size: 36px;
}

/* FRONT */
#frontPage {
    display: none;
    height: 100vh;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: white;
}

.card {
    background: rgba(255,255,255,0.15);
    backdrop-filter: blur(10px);
    border-radius: 20px;
    padding: 40px 60px;
    text-align: center;
    box-shadow: 0 0 30px rgba(255,105,180,0.6);
}

.year {
    font-size: 60px;
    font-weight: bold;
    background: linear-gradient(to right, #ffb6c1, #add8e6);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}

button {
    margin-top: 25px;
    padding: 12px 30px;
    font-size: 18px;
    border-radius: 30px;
    border: none;
    cursor: pointer;
    background: white;
}

/* MESSAGE SCREEN */
#messageBox {
    margin-top: 30px;
    max-width: 850px;
    text-align: center;
    line-height: 1.8;
    font-size: 18px;
    display: none;
}

/* HEART */
.heart {
    position: absolute;
    color: pink;
    animation: float 6s infinite ease-in;
}

@keyframes float {
    from { transform: translateY(100vh); opacity: 1; }
    to { transform: translateY(-10vh); opacity: 0; }
}
</style>
</head>

<body>

<!-- COUNTDOWN -->
<div id="countdownPage">
    <div class="countBox">
        <h1> New Year Countdown 👀🎉🫣</h1>
        <div id="countdown"></div>
    </div>
</div>

<!-- FRONT PAGE -->
<div id="frontPage">
    <div class="card">
    <h1>🎉 Happy New Year 🎉</h1>
    <div class="year">2025</div>
    <h2>Wishing You Joy & Happiness</h2>
    <p>
        May this new year bring you<br>
        love, success, and endless smiles 💖
    </p>
    </div>

    <button id="forYouBtn">For You</button>

    <div id="messageBox"></div>
</div>

<script>
/* COUNTDOWN */
const target = new Date("January 1, 2026 00:00:00").getTime();
const cd = setInterval(() => {
    const now = new Date().getTime();
    const diff = target - now;

    if (diff <= 0) {
        clearInterval(cd);
        countdownPage.style.display = "none";
        frontPage.style.display = "flex";
        startHearts();
        return;
    }

    const d = Math.floor(diff / (1000*60*60*24));
    const h = Math.floor((diff / (1000*60*60)) % 24);
    const m = Math.floor((diff / (1000*60)) % 60);
    const s = Math.floor((diff / 1000) % 60);

    countdown.innerText = `${d}d ${h}h ${m}m ${s}s`;
}, 1000);

/* HEARTS */
function startHearts(){
    for(let i=0;i<25;i++){
        let h=document.createElement("div");
        h.className="heart";
        h.innerHTML="💗";
        h.style.left=Math.random()*100+"vw";
        h.style.fontSize=(Math.random()*20+15)+"px";
        document.body.appendChild(h);
    }
}

/* MESSAGES */
const messages = [
`Before 2025 ends
I want to say something.
Sorry for being rude sometimes.
Sorry for the times I wasn't there for you.
Sorry for my mood swings.
Sorry for the misunderstandings.
Sorry for bothering you.
Sorry for the hurt I caused.
I’m grateful to have you.`,

`সময় নিজের নিয়মেই চলে,
যেমন নদীর স্রোত থেমে না থেকে এগিয়ে যায়।
নতুন এসেছে,
আর পুরোনো সবকিছু এবার ছেড়ে দেওয়ার সময়।
যা ছিল, তা স্মৃতি হয়ে থাকুক।
Happy New Year.`,

`লাইফের প্রথমবার,
তুমি আর আমি একসঙ্গে নতুন বছরে পা দিতে যাচ্ছি।
তোমাকে অনেক ধন্যবাদ,
তুমি আমাকে বুঝেছো,
হেল্প করেছো,
অসংখ্যভাবে পাশে থেকেছো।`,

`পুরোনো দিনের খারাপ স্মৃতি পেছনে ফেলে,
নতুন বছরের ভালো স্মৃতি আমাদের জন্য অপেক্ষা করুক।
আমার জীবনের প্রতিটি সময়,
প্রতিটি মুহূর্ত
আমি তোমার সঙ্গেই কাটাতে চাই—ইনশাআল্লাহ।`,

`নতুন বছর তোমার স্মৃতিগুলোকে
আরও মধুর, আরও মিষ্টি করে তুলুক।
আমাদের সম্পর্কটা যেন আরও গভীর হয়।
ইনশাআল্লাহ আমরা নতুন গল্প দেখবো,
নতুন স্বপ্ন দেখবো,
আর সেগুলো একসঙ্গে পূরণ করবো।
I pray the coming days will be as you wish.`
];

let index = 0;
forYouBtn.onclick = () => {
    forYouBtn.style.display = "none";
    messageBox.style.display = "block";

    const interval = setInterval(()=>{
        messageBox.innerText = messages[index];
        index++;
        if(index === messages.length) clearInterval(interval);
    },10000);
};
</script>

</body>
</html>
