---
layout: home
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>👻 Find the Ghost Process</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <style>
        .process {
            background-color: #f3f4f6;
            padding: 1rem;
            border-radius: 0.5rem;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        .process:hover {
            background-color: #e5e7eb;
        }
        .ghost {
            color: orange;
            font-weight: bold;
        }
        #win-message {
            display: none;
        }
    </style>
</head>
<body class="flex flex-col items-center min-h-screen bg-gray-900 text-white">

    <header class="bg-gray-800 text-center p-4 w-full flex flex-col items-center">
        <img src="logo.png" alt="Couchbase Logo" class="w-36 h-auto mb-4">
        <h1 class="text-2xl font-bold">👻 Find the Ghost Process</h1>
    </header>

    <main class="flex flex-col items-center flex-1 p-6 text-center">
        <p class="mb-4 text-lg">One of these processes is haunted! Click the ghost process to exorcise it.</p>
        <div id="process-list" class="grid grid-cols-2 gap-4 md:grid-cols-4">
            <!-- Processes will be injected here -->
        </div>
        <div id="win-message" class="mt-6 p-4 bg-green-500 rounded-md">
            <p>🎉 You’ve exorcised the ghost process and restored harmony to the data realm! <br> Curious about taming real-world “ghosts” in your data? <a href="https://www.couchbase.com/products/sync-gateway/" class="underline">Click here to learn more!</a></p>
        </div>
    </main>

    <footer class="bg-gray-800 text-center p-4 w-full mt-auto">
        <p>&copy; Couchbase</p>
    </footer>

    <script>
        const processes = [
            "Process 101", "Process 102", "Process 103", "Process 104",
            "Process 105", "Process 106", "Process 107", "Process 108"
        ];
        const ghostIndex = Math.floor(Math.random() * processes.length);

        const processList = document.getElementById('process-list');
        const winMessage = document.getElementById('win-message');

        processes.forEach((process, index) => {
            const processElement = document.createElement('div');
            processElement.classList.add('process');
            processElement.innerText = process;
            if (index === ghostIndex) {
                processElement.classList.add('ghost'); 
                processElement.addEventListener('click', () => {
                    winMessage.style.display = 'block';
                    processList.style.display = 'none';
                });
            } else {
                processElement.addEventListener('click', () => {
                    alert("Not the ghost! Try another process.");
                });
            }
            processList.appendChild(processElement);
        });
    </script>
</body>
</html>
