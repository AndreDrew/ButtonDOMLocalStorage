#ButtonDOMLocalStorage
<h1 id="header">Click the Button!</h1>
    <p>Click Count: <span id="click-count">0</span></p>
<button id="click-button">Click Me!</button><h1>

 body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 20%;
        }

        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            display: inline-block;
        }


         const clickCountDisplay = document.getElementById('click-count');
        const header = document.getElementById('header');
        const button = document.getElementById('click-button');
       
//1.Add a comment here explaining the let clickCount variable  
        let clickCount = localStorage.getItem('clickCount') ? parseInt(localStorage.getItem('clickCount')) : 0;

        // Update display on load
        clickCountDisplay.textContent = clickCount;
        updateUI();


        //2.Explain what this event listener function does (and what function it calls).
        // Add event listener to button
        button.addEventListener('click', () => {
            clickCount++;
            localStorage.setItem('clickCount', clickCount);
            clickCountDisplay.textContent = clickCount;
            updateUI();
        });

//3.Explain what function updateUI does and is holding the colors and texts
        function updateUI() {
            const colors = ['#FF5733', '#33FF57', '#3357FF', '#F5A623', '#E91E63'];
            const texts = [
                'Keep going!',
                'Great job!',
                'You are amazing!',
                'Fantastic!',
                'Click click hooray!'
            ];

            const randomIndex = Math.floor(Math.random() * colors.length);
            document.body.style.backgroundColor = colors[randomIndex];
            header.textContent = texts[randomIndex];
        }
