<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced CTF Challenge</title>
    <style>
        /* CSS to hide elements creatively */
        #hidden-container {
            visibility: hidden;  /* Element is hidden but still takes space */
            opacity: 0;           /* Make it fully invisible */
            position: absolute;  /* Position it off-screen */
            left: -9999px;       /* Trick: Move it out of view */
            transition: opacity 0.5s; /* Subtle transition for any interaction */
        }
        
        #hidden-container:hover {
            opacity: 0.5;  /* Partial reveal on hover, but still not fully visible */
            visibility: visible; /* Make it inspectable on hover */
        }
        
        /* Use a pseudo-element for a hidden hint */
        .puzzle-element::before {
            content: "Hint: Check the JS for secrets..."; /* A misleading hint */
            color: transparent; /* Make the text invisible */
            text-shadow: 0 0 5px rgba(0,0,0,0.5); /* Subtle shadow that might show on inspection */
        }
        
        body {
            background-color: #f0f0f0; /* Muted background for misdirection */
        }
    </style>
</head>
<body>
    <h1>Advanced CTF Challenge: Dig Deeper!</h1>
    <p>Think you can find the flag? It's not as straightforward as before. Try inspecting elements, checking the console, or even editing the code.</p>
    
    <div class="puzzle-element">
        <!-- This element has a pseudo-element with a hint, but it's styled to be invisible -->
        Keep looking...
    </div>
    
    <div id="hidden-container" data-encoded-flag="UkxBR3tjdGZfY29tcGxleF9mbGFnX2V4YW1wbGV9"> <!-- Base64 encoded flag: FLAG{ctf_complex_flag_example} -->
        <!-- The actual flag is encoded in JavaScript, not here! -->
    </div>
    
    <script>
        // JavaScript for encoding and potential decoding
        const encodedFlag = "UkxBR3tjdGZfY29tcGxleF9mbGFnX2V4YW1wbGV9"; // This is Base64 for "FLAG{ctf_complex_flag_example}"
        
        function decodeFlag() {
            try {
                const decoded = atob(encodedFlag);  // Decode Base64
                console.log("Decoded flag: " + decoded);  // Logs to console if function is called
                document.getElementById('hidden-container').innerHTML = decoded;  // Sets the decoded flag in the hidden element
            } catch (error) {
                console.error("Decoding failed. Maybe the flag isn't meant to be found yet?");
            }
        }
        
        // The function isn't called automatically. Participants might need to:
        // 1. Open the console and run: decodeFlag();
        // 2. Inspect the code and notice the encoded string.
        // Misdirection: This script could be modified or triggered manually.
        
        console.log("Welcome back! Something's encoded... but where?");  // Vague hint
    </script>
</body>
</html>
