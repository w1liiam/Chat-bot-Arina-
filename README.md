# Chat-bot-Arina-



<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Vocabulary Helper – Key Words Chatbot</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f3f4f6;
      display: flex;
      justify-content: center;
      padding: 20px;
    }
    #page-container {
      width: 100%;
      max-width: 900px;
      background: #ffffff;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      padding: 20px;
      box-sizing: border-box;
    }
    h1 {
      margin-top: 0;
      color: #111827;
      font-size: 24px;
    }
    h2 {
      margin-top: 20px;
      color: #1f2933;
      font-size: 20px;
    }
    .word-item {
      margin-bottom: 14px;
      padding: 8px 10px;
      border-left: 3px solid #2563eb;
      background: #f9fafb;
    }
    .word-item strong {
      font-size: 16px;
    }
    .word-label {
      font-weight: bold;
    }
    ul {
      margin: 4px 0 0 18px;
    }

    /* Chat styles */
    #chat-container {
      margin-top: 24px;
      border-radius: 8px;
      border: 1px solid #e5e7eb;
      overflow: hidden;
      display: flex;
      flex-direction: column;
    }
    #chat-header {
      padding: 12px 16px;
      background: #2563eb;
      color: white;
      font-weight: bold;
    }
    #chat-box {
      height: 280px;
      padding: 10px 16px;
      overflow-y: auto;
      font-size: 15px;
      background: #f9fafb;
    }
    .message {
      margin: 8px 0;
      max-width: 90%;
      line-height: 1.4;
    }
    .user {
      text-align: right;
    }
    .user span {
      background: #e5e7eb;
      padding: 6px 10px;
      border-radius: 12px;
      display: inline-block;
    }
    .bot span {
      background: #dbeafe;
      padding: 6px 10px;
      border-radius: 12px;
      display: inline-block;
    }
    #input-area {
      display: flex;
      border-top: 1px solid #e5e7eb;
      background: #ffffff;
    }
    #user-input {
      flex: 1;
      border: none;
      padding: 10px;
      font-size: 15px;
    }
    #user-input:focus {
      outline: none;
    }
    #send-btn {
      border: none;
      background: #2563eb;
      color: white;
      padding: 0 18px;
      font-size: 15px;
      cursor: pointer;
    }
    #send-btn:hover {
      background: #1d4ed8;
    }
    .hint {
      font-size: 13px;
      color: #6b7280;
      margin-bottom: 6px;
    }
  </style>
</head>
<body>
<div id="page-container">
  <h1>Key words with simple explanations and synonyms</h1>

  <!-- Static list for students to read -->
  <div id="word-list">
    <div class="word-item">
      <strong>1. Reforms</strong><br />
      <span class="word-label">Sentence:</span> The government is planning major reforms in schools.<br />
      <span class="word-label">Meaning:</span> Big changes to make things better.<br />
      <span class="word-label">Synonyms:</span> changes, improvements, updates
    </div>

    <div class="word-item">
      <strong>2. Topics</strong><br />
      <span class="word-label">Sentence:</span> They will be taught broad topics in class.<br />
      <span class="word-label">Meaning:</span> Subjects or things to talk about or study.<br />
      <span class="word-label">Synonyms:</span> subjects, themes, ideas
    </div>

    <div class="word-item">
      <strong>3. Collaboration</strong><br />
      <span class="word-label">Sentence:</span> Pupils work in collaboration on projects.<br />
      <span class="word-label">Meaning:</span> Working together with others.<br />
      <span class="word-label">Synonyms:</span> cooperation, teamwork, partnership
    </div>

    <div class="word-item">
      <strong>4. Curriculum</strong><br />
      <span class="word-label">Sentence:</span> The new curriculum includes more science.<br />
      <span class="word-label">Meaning:</span> The list of subjects or lessons taught at school.<br />
      <span class="word-label">Synonyms:</span> course, syllabus, program
    </div>

    <div class="word-item">
      <strong>5. Innovative</strong><br />
      <span class="word-label">Sentence:</span> They use innovative methods to teach.<br />
      <span class="word-label">Meaning:</span> New and creative ways of doing something.<br />
      <span class="word-label">Synonyms:</span> creative, new, original
    </div>

    <div class="word-item">
      <strong>6. Evaluate</strong><br />
      <span class="word-label">Sentence:</span> Teachers evaluate students' progress.<br />
      <span class="word-label">Meaning:</span> To check or judge how well someone is doing.<br />
      <span class="word-label">Synonyms:</span> assess, judge, review
    </div>
  </div>

  <!-- Chatbot section -->
  <h2>Ask the chatbot about the words</h2>
  <p class="hint">
    Example questions: <em>"What does reforms mean in this context?"</em> or
    <em>"Give a simple synonym for collaboration."</em>
  </p>

  <div id="chat-container">
    <div id="chat-header">Vocabulary Helper Chatbot</div>
    <div id="chat-box"></div>
    <div id="input-area">
      <input id="user-input" type="text" placeholder="Type your question here..." />
      <button id="send-btn">Send</button>
    </div>
  </div>
</div>

<script>
  const chatBox = document.getElementById("chat-box");
  const userInput = document.getElementById("user-input");
  const sendBtn = document.getElementById("send-btn");

  // Vocabulary data based on your list
  const vocab = {
    "reforms": {
      sentence: "The government is planning major reforms in schools.",
      meaning: "Big changes to make things better.",
      synonyms: ["changes", "improvements", "updates"]
    },
    "topics": {
      sentence: "They will be taught broad topics in class.",
      meaning: "Subjects or things to talk about or study.",
      synonyms: ["subjects", "themes", "ideas"]
    },
    "collaboration": {
      sentence: "Pupils work in collaboration on projects.",
      meaning: "Working together with others.",
      synonyms: ["cooperation", "teamwork", "partnership"]
    },
    "curriculum": {
      sentence: "The new curriculum includes more science.",
      meaning: "The list of subjects or lessons taught at school.",
      synonyms: ["course", "syllabus", "program"]
    },
    "innovative": {
      sentence: "They use innovative methods to teach.",
      meaning: "New and creative ways of doing something.",
      synonyms: ["creative", "new", "original"]
    },
    "evaluate": {
      sentence: "Teachers evaluate students' progress.",
      meaning: "To check or judge how well someone is doing.",
      synonyms: ["assess", "judge", "review"]
    }
  };

  function addMessage(text, sender = "bot") {
    const msg = document.createElement("div");
    msg.classList.add("message", sender);
    const span = document.createElement("span");
    span.textContent = text;
    msg.appendChild(span);
    chatBox.appendChild(msg);
    chatBox.scrollTop = chatBox.scrollHeight;
  }

  // Try to detect which word the student is asking about
  function getWordFromQuestion(question) {
    const lower = question.toLowerCase();

    // Remove punctuation and asterisks (for questions like *reforms*)
    const cleaned = lower.replace(/[*?.!,]/g, " ");

    // 1) Direct substring match
    for (const word of Object.keys(vocab)) {
      if (cleaned.includes(word.toLowerCase())) {
        return word;
      }
    }

    // 2) Try last word as fallback (for "What does reforms mean?")
    const tokens = cleaned
      .split(/\s+/)
      .filter(Boolean);

    if (tokens.length > 0) {
      const last = tokens[tokens.length - 1];
      if (vocab[last]) return last;
    }

    return null;
  }

  function answerQuestion(question) {
    const word = getWordFromQuestion(question);

    if (!word) {
      addMessage(
        "Sorry, I don’t know this word yet. Please choose a word from the list above.",
        "bot"
      );
      return;
    }

    const entry = vocab[word];
    const lower = question.toLowerCase();

    // If student asks about synonyms
    if (lower.includes("synonym")) {
      addMessage(
        word + ": simple synonyms are: " + entry.synonyms.join(", ") + ".",
        "bot"
      );
    } else {
      // Explain meaning + show example sentence + synonyms
      const reply =
        word + " (from our text): " +
        "\nSentence: " + entry.sentence +
        "\nMeaning: " + entry.meaning +
        "\nSimple synonyms: " + entry.synonyms.join(", ") + ".";
      addMessage(reply, "bot");
    }
  }

  function handleSend() {
    const text = userInput.value.trim();
    if (!text) return;
    addMessage(text, "user");
    userInput.value = "";
    answerQuestion(text);
  }

  sendBtn.addEventListener("click", handleSend);
  userInput.addEventListener("keydown", (e) => {
    if (e.key === "Enter") {
      handleSend();
    }
  });

  // Welcome message
  window.addEventListener("load", () => {
    addMessage(
      'Hi! Ask me about a word from the list above. For example: "What does reforms mean in this context?" or "Give a simple synonym for collaboration."',
      "bot"
    );
  });
</script>
</body>
</html>


