<div class="page-shell">
  <header class="topbar">
    <div class="brand-block">
      <span class="dot"></span>
      <span>Lola's Daily 4</span>
    </div>
    <span class="badge">Year 3</span>
  </header>

  <main class="main-panel">
    <section class="hero">
      <p class="eyebrow">Little questions, big thinking</p>
      <h1>One tiny challenge a day for Lola.</h1>
      <p class="subtitle">Four age-appropriate questions to keep her curious, confident and learning.</p>
      <div id="today-date" class="date-chip">Today</div>
    </section>

    <section id="question-grid" class="question-grid" aria-live="polite"></section>
  </main>
</div>

<style>
  :root {
    --bg: #f8f4ff;
    --panel: #ffffff;
    --card: #fffdf9;
    --ink: #2c2540;
    --muted: #5f5572;
    --shadow: rgba(58, 35, 99, 0.12);
    --math: #7c6cf2;
    --science: #35b38d;
    --geo: #f39b45;
    --general: #ef5f8d;
    --line: #efe6ff;
    --button: #2b1d4d;
  }

  * { box-sizing: border-box; }

  body {
    margin: 0;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
    background: linear-gradient(180deg, #fdf8ff 0%, #f4f0ff 100%);
    color: var(--ink);
  }

  .page-shell {
    width: min(1100px, calc(100% - 32px));
    margin: 32px auto 60px;
  }

  .topbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 18px;
    padding: 10px 14px;
  }

  .brand-block {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    font-weight: 700;
    font-size: 1.08rem;
    letter-spacing: 0.02em;
  }

  .dot {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--math), var(--science));
    box-shadow: 0 0 12px rgba(124, 108, 242, 0.3);
  }

  .badge {
    background: #f0ebff;
    color: var(--button);
    border: 1px solid var(--line);
    border-radius: 999px;
    padding: 8px 14px;
    font-size: 0.76rem;
    font-weight: 700;
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }

  .main-panel {
    background: rgba(255, 255, 255, 0.72);
    border: 1px solid var(--line);
    border-radius: 26px;
    box-shadow: 0 20px 50px var(--shadow);
    backdrop-filter: blur(2px);
    padding: 30px 20px 28px;
  }

  .hero {
    text-align: center;
    margin-bottom: 26px;
  }

  .eyebrow {
    margin: 0 0 8px;
    font-size: 0.8rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
    font-weight: 700;
  }

  h1 {
    margin: 0;
    font-size: clamp(2.2rem, 4vw, 3.5rem);
    line-height: 1.05;
  }

  .subtitle {
    max-width: 700px;
    margin: 12px auto 0;
    color: var(--muted);
    font-size: 1.05rem;
    line-height: 1.6;
  }

  .date-chip {
    display: inline-block;
    margin-top: 18px;
    border-radius: 999px;
    background: #fffaf2;
    border: 1px solid #f4d8ab;
    color: #75541d;
    font-weight: 700;
    padding: 10px 18px;
  }

  .question-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
    gap: 18px;
    margin-top: 18px;
  }

  .question-card {
    background: var(--card);
    border: 1px solid #f1e5ff;
    border-radius: 22px;
    padding: 18px 16px 16px;
    box-shadow: 0 10px 20px rgba(41, 27, 61, 0.04);
    display: flex;
    flex-direction: column;
    min-height: 220px;
  }

  .category-pill {
    align-self: flex-start;
    border-radius: 999px;
    padding: 7px 12px;
    font-size: 0.72rem;
    font-weight: 800;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: white;
    margin-bottom: 12px;
  }

  .question-card.maths .category-pill { background: var(--math); }
  .question-card.science .category-pill { background: var(--science); }
  .question-card.geography .category-pill { background: var(--geo); }
  .question-card.general .category-pill { background: var(--general); }

  .question-card h2 {
    margin: 0 0 12px;
    font-size: 0.82rem;
    letter-spacing: 0.09em;
    text-transform: uppercase;
    color: var(--muted);
    font-weight: 800;
  }

  .question {
    margin: 0;
    font-size: clamp(1.1rem, 2vw, 1.38rem);
    line-height: 1.5;
    font-weight: 700;
    flex: 1;
  }

  .answer-box {
    display: none;
    margin-top: 14px;
    padding: 12px 12px 10px;
    border-radius: 14px;
    background: #f2fff9;
    border: 1px solid #cdebdc;
    color: #1e5d45;
  }

  .answer-box.visible {
    display: block;
  }

  .answer-label {
    display: block;
    font-size: 0.68rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    font-weight: 800;
    margin-bottom: 6px;
    color: #2c7a5c;
  }

  .answer {
    font-size: 1.1rem;
    font-weight: 800;
    margin: 0;
  }

  .explanation {
    margin-top: 6px;
    font-size: 0.9rem;
    line-height: 1.5;
    color: #335a4d;
  }

  .reveal-btn {
    margin-top: 14px;
    border: 0;
    background: var(--button);
    color: white;
    border-radius: 12px;
    padding: 11px 14px;
    font-size: 0.92rem;
    font-weight: 700;
    cursor: pointer;
    transition: transform 0.15s ease, opacity 0.15s ease;
  }

  .reveal-btn:hover {
    transform: translateY(-1px);
    opacity: 0.98;
  }

  .reveal-btn:active {
    transform: translateY(0);
  }

  @media (max-width: 640px) {
    .page-shell {
      width: min(100% - 16px, 1100px);
      margin-top: 18px;
    }

    .main-panel {
      padding: 20px 12px 18px;
    }

    .topbar {
      padding-left: 0;
      padding-right: 0;
    }
  }
</style>

<script>
  const questionBank = {
    maths: [
      { question: "What is 9 + 7?", answer: "16", explanation: "9 and 7 make 16 when you add them together." },
      { question: "Half of 18 is what number?", answer: "9", explanation: "18 split into two equal groups is 9 and 9." },
      { question: "What is 5 × 4?", answer: "20", explanation: "Five groups of four make twenty." },
      { question: "Which is bigger: 34 or 43?", answer: "43", explanation: "43 has more tens, so it is larger." },
      { question: "A clock says 3:30. What time is it?", answer: "Half past three", explanation: "3:30 means thirty minutes past 3." },
      { question: "A cake has 8 slices and 3 are eaten. How many are left?", answer: "5", explanation: "8 minus 3 leaves 5 slices." },
      { question: "What is 12 - 6?", answer: "6", explanation: "Taking 6 away from 12 leaves 6." },
      { question: "What is double 7?", answer: "14", explanation: "7 plus 7 equals 14." },
      { question: "What is 25 + 10?", answer: "35", explanation: "25 and 10 more is 35." },
      { question: "What is 3 quarters of 8?", answer: "6", explanation: "One quarter of 8 is 2, so three quarters is 6." },
      { question: "What is 4 + 9 + 3?", answer: "16", explanation: "4 + 9 is 13, and 3 more makes 16." },
      { question: "How many sides does a triangle have?", answer: "3", explanation: "A triangle is made of three straight sides." },
      { question: "What is 7 + 8?", answer: "15", explanation: "7 plus 8 equals 15." },
      { question: "What is 20 - 9?", answer: "11", explanation: "20 minus 9 is 11." },
      { question: "What is half of 14?", answer: "7", explanation: "14 shared equally into 2 groups gives 7." },
      { question: "How many minutes are in half an hour?", answer: "30 minutes", explanation: "An hour has 60 minutes, so half is 30." },
      { question: "What is 6 × 3?", answer: "18", explanation: "6 groups of 3 equal 18." },
      { question: "What is 50 + 25?", answer: "75", explanation: "50 plus 25 makes 75." },
      { question: "If one apple costs 20p, how much do 2 apples cost?", answer: "40p", explanation: "20p doubled is 40p." },
      { question: "What number is 10 less than 27?", answer: "17", explanation: "27 take away 10 is 17." },
      { question: "What is 9 + 9?", answer: "18", explanation: "Double 9 is 18." },
      { question: "What is 14 + 6?", answer: "20", explanation: "14 and 6 more makes 20." },
      { question: "Which shape has 4 equal sides?", answer: "A square", explanation: "A square has four equal-length sides." },
      { question: "What is 100 - 25?", answer: "75", explanation: "Taking 25 away from 100 leaves 75." },
      { question: "What is 8 + 5?", answer: "13", explanation: "8 more than 5 is 13." }
    ],
    science: [
      { question: "Which part of a plant takes in water from the soil?", answer: "The roots", explanation: "Roots absorb water and minerals from the ground." },
      { question: "What do humans need to breathe?", answer: "Air", explanation: "Humans take in oxygen from the air when they breathe." },
      { question: "Which material is waterproof: paper or plastic?", answer: "Plastic", explanation: "Plastic does not soak up water as easily as paper." },
      { question: "What do we call an animal that eats other animals?", answer: "A predator", explanation: "Predators hunt and eat other animals." },
      { question: "Which sense do we use to hear?", answer: "Hearing", explanation: "Our ears help us hear sounds." },
      { question: "What force pulls things down to Earth?", answer: "Gravity", explanation: "Gravity is the force that keeps us on the ground." },
      { question: "What do plants need to make their food?", answer: "Sunlight, water and carbon dioxide", explanation: "Plants use sunlight to make food in their leaves." },
      { question: "Which part of the body pumps blood around the body?", answer: "The heart", explanation: "The heart beats and pushes blood through the body." },
      { question: "Do magnets attract or repel plastic?", answer: "Neither", explanation: "Plastic is not magnetic, so magnets do not attract it." },
      { question: "What is the name for a baby frog?", answer: "A tadpole", explanation: "A tadpole changes into a frog as it grows." },
      { question: "Which animal is known for laying eggs and having feathers?", answer: "A bird", explanation: "Birds have feathers and usually lay eggs." },
      { question: "What do we call the tiny living things that can make us ill?", answer: "Germs", explanation: "Germs are tiny organisms that can cause illness." },
      { question: "What kind of weather often follows rain clouds?", answer: "Rain", explanation: "Clouds can hold water that falls as rain." },
      { question: "What do leaves make for the plant?", answer: "Food", explanation: "Leaves use sunlight to make food for the plant." },
      { question: "What do we call the process when a liquid turns into a gas?", answer: "Evaporation", explanation: "When water warms up it can turn into a vapour and rise." },
      { question: "Which part of the body helps us to see?", answer: "The eyes", explanation: "Eyes let us detect light and shapes around us." },
      { question: "What do bees collect from flowers?", answer: "Nectar", explanation: "Bees collect nectar to make honey." },
      { question: "What do all living things need to grow?", answer: "Food, water and air", explanation: "Living things need these things to stay alive and grow." },
      { question: "Which season is usually coldest in the UK?", answer: "Winter", explanation: "Winter is usually the coldest season." },
      { question: "What is a habitat?", answer: "A place where an animal or plant lives", explanation: "A habitat gives living things what they need to survive." },
      { question: "What do we call the force that slows a toy car down on the floor?", answer: "Friction", explanation: "Friction happens when surfaces rub together." },
      { question: "Which sense helps us to taste food?", answer: "Taste", explanation: "Our tongue helps us taste sweet, salty, sour and bitter flavours." },
      { question: "What do birds use to keep warm?", answer: "Feathers", explanation: "Feathers help birds stay warm and dry." },
      { question: "What is the name for the way plants turn towards sunlight?", answer: "Phototropism", explanation: "Plants can grow toward the light they need." },
      { question: "Which planet is known as the Red Planet?", answer: "Mars", explanation: "Mars looks reddish because of iron-rich dust on its surface." }
    ],
    geography: [
      { question: "What is the capital city of England?", answer: "London", explanation: "London is the capital city of England and the UK." },
      { question: "Which sea is next to England?", answer: "The English Channel", explanation: "The English Channel lies to the south of England." },
      { question: "What is the name of the ocean that is next to the UK?", answer: "The Atlantic Ocean", explanation: "The Atlantic is to the west of the UK." },
      { question: "Which direction is opposite north?", answer: "South", explanation: "North and south are opposite directions." },
      { question: "What is the tallest mountain in the UK?", answer: "Ben Nevis", explanation: "Ben Nevis is the highest mountain in Scotland and the UK." },
      { question: "What country is famous for the Eiffel Tower?", answer: "France", explanation: "The Eiffel Tower is one of the most famous landmarks in France." },
      { question: "Which country is home to the pyramids of Giza?", answer: "Egypt", explanation: "The pyramids are ancient monuments in Egypt." },
      { question: "What is the capital city of Scotland?", answer: "Edinburgh", explanation: "Edinburgh is the capital of Scotland." },
      { question: "Which is larger: a river or a stream?", answer: "A river", explanation: "Rivers are usually wider and longer than streams." },
      { question: "What is the capital city of Wales?", answer: "Cardiff", explanation: "Cardiff is the capital city of Wales." },
      { question: "Which continent is the Sahara Desert in?", answer: "Africa", explanation: "The Sahara stretches across much of North Africa." },
      { question: "What is the name of the biggest ocean on Earth?", answer: "The Pacific Ocean", explanation: "The Pacific is the largest and deepest ocean." },
      { question: "What city is famous for the Statue of Liberty?", answer: "New York City", explanation: "The Statue of Liberty stands in New York Harbour." },
      { question: "Which country is home to the city of Rome?", answer: "Italy", explanation: "Rome is the capital city of Italy." },
      { question: "What do maps usually use to show north?", answer: "A compass rose", explanation: "The compass rose helps people know which direction they are facing." },
      { question: "What is the capital city of France?", answer: "Paris", explanation: "Paris is the capital city of France." },
      { question: "What do we call a very high landform that rises above the land?", answer: "A mountain", explanation: "Mountains are much higher than the surrounding land." },
      { question: "Which country is famous for the Great Wall?", answer: "China", explanation: "The Great Wall is one of China's most famous landmarks." },
      { question: "What word means the land next to the sea?", answer: "Coast", explanation: "The coast is the place where the land meets the sea." },
      { question: "What is the capital city of Northern Ireland?", answer: "Belfast", explanation: "Belfast is the capital city of Northern Ireland." },
      { question: "Which ocean is nearest to the UK?", answer: "The Atlantic Ocean", explanation: "The Atlantic lies to the west of the UK." },
      { question: "What do we call a place with lots of trees?", answer: "A forest", explanation: "Forests are large areas covered mainly by trees." },
      { question: "Which continent do we live on?", answer: "Europe", explanation: "The UK is in Europe." },
      { question: "What is the longest river in the world?", answer: "The Nile", explanation: "The Nile is often called the longest river in the world." }
    ],
    generalKnowledge: [
      { question: "Which animal is known as the fastest land animal?", answer: "The cheetah", explanation: "Cheetahs can run very fast in short bursts." },
      { question: "What colour do you get when you mix blue and yellow?", answer: "Green", explanation: "Blue and yellow combine to make green." },
      { question: "Who painted the Mona Lisa?", answer: "Leonardo da Vinci", explanation: "Leonardo da Vinci painted the Mona Lisa in the Renaissance." },
      { question: "Which planet is known as the Red Planet?", answer: "Mars", explanation: "Mars looks red because of iron in its soil." },
      { question: "Which is longer: a minute or an hour?", answer: "An hour", explanation: "An hour is 60 minutes long." },
      { question: "What do bees collect from flowers?", answer: "Nectar", explanation: "Bees collect nectar to help make honey." },
      { question: "How many days are there in a week?", answer: "7", explanation: "There are seven days in a week." },
      { question: "Who was the first person to walk on the Moon?", answer: "Neil Armstrong", explanation: "Neil Armstrong stepped onto the Moon in 1969." },
      { question: "What do we call a baby dog?", answer: "A puppy", explanation: "Puppies are the young of dogs." },
      { question: "Which sport uses a shuttlecock?", answer: "Badminton", explanation: "Badminton players hit a shuttlecock over the net." },
      { question: "What do birds use to fly?", answer: "Wings", explanation: "Birds flap their wings to move through the air." },
      { question: "What is the capital city of Italy?", answer: "Rome", explanation: "Rome is the capital city of Italy." },
      { question: "Which animal says 'moo'?", answer: "A cow", explanation: "Cows are famous for making a moo sound." },
      { question: "What do you call the shape that is round like a ball?", answer: "A sphere", explanation: "A sphere is a round 3D shape." },
      { question: "Which is heavier: a feather or a stone?", answer: "A stone", explanation: "A stone has much more mass than a feather." },
      { question: "What month comes after March?", answer: "April", explanation: "April comes after March in the calendar." },
      { question: "What is a baby cat called?", answer: "A kitten", explanation: "Kittens are young cats." },
      { question: "Which instrument has strings and is played with a bow?", answer: "A violin", explanation: "A violin is a string instrument played with a bow." },
      { question: "What colour is a banana when it is ripe?", answer: "Yellow", explanation: "Ripe bananas are usually yellow." },
      { question: "Which animal is famous for carrying its baby in a pouch?", answer: "A kangaroo", explanation: "Kangaroos carry their young in a pouch." },
      { question: "What do we use to tell the time?", answer: "A clock", explanation: "Clocks help us measure hours and minutes." },
      { question: "Which colour is made by mixing red and blue?", answer: "Purple", explanation: "Red and blue make purple." },
      { question: "Where do penguins live?", answer: "In cold places, especially Antarctica", explanation: "Penguins are adapted to live in cold environments." },
      { question: "What is the biggest mammal in the world?", answer: "The blue whale", explanation: "Blue whales are the largest animals known to have ever lived." }
    ]
  };

  const categoryOrder = [
    { key: 'maths', label: 'Maths', className: 'maths' },
    { key: 'science', label: 'Science', className: 'science' },
    { key: 'geography', label: 'Geography', className: 'geography' },
    { key: 'generalKnowledge', label: 'General Knowledge', className: 'general' }
  ];

  const categorySeed = {
    maths: 1,
    science: 5,
    geography: 9,
    generalKnowledge: 13
  };

  function getTodayDateText() {
    const today = new Date();
    return today.toLocaleDateString('en-GB', {
      weekday: 'long',
      day: 'numeric',
      month: 'long',
      year: 'numeric'
    });
  }

  function getDayNumber(date) {
    const start = new Date(date.getFullYear(), 0, 0);
    const diff = date - start;
    return Math.floor(diff / 86400000);
  }

  function selectQuestions() {
    const today = new Date();
    const dayNumber = getDayNumber(today);

    return categoryOrder.map((category, index) => {
      const list = questionBank[category.key];
      const offset = dayNumber + categorySeed[category.key] + index * 3;
      const chosen = list[offset % list.length];
      return { ...chosen, ...category };
    });
  }

  function renderQuestions() {
    const grid = document.getElementById('question-grid');
    const selected = selectQuestions();

    document.getElementById('today-date').textContent = getTodayDateText();

    grid.innerHTML = selected.map((item) => `
      <article class="question-card ${item.className}">
        <span class="category-pill">${item.label}</span>
        <h2>Today's challenge</h2>
        <p class="question">${item.question}</p>
        <div class="answer-box">
          <span class="answer-label">Answer</span>
          <p class="answer">${item.answer}</p>
          <p class="explanation">${item.explanation}</p>
        </div>
        <button class="reveal-btn" type="button">Reveal answer</button>
      </article>
    `).join('');

    document.querySelectorAll('.reveal-btn').forEach((button) => {
      button.addEventListener('click', () => {
        const box = button.parentElement.querySelector('.answer-box');
        const currentlyVisible = box.classList.contains('visible');
        box.classList.toggle('visible', !currentlyVisible);
        button.textContent = currentlyVisible ? 'Reveal answer' : 'Hide answer';
      });
    });
  }

  renderQuestions();
</script>

