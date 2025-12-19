# Persona-Tuned LLMs with Ollama

This repository contains **custom Ollama Modelfiles** that give base LLMs (like `llama3`, `mistral`, or `phi3`) distinct *writing voices* or *personas*.
Each Modelfile wraps a base model and applies prompt-tuning so you can interact with the model in different styles.

---

### 1. Install Ollama

Follow the [official Ollama install guide](https://ollama.com/download) for your OS.
After installation, verify:

```bash
ollama --version
ollama list
```

### 2. Clone this repository

```bash
git clone https://github.com/AbhinavRudra/Prompt-Tuned-Voices-using-Ollama
cd Prompt-Tuned-Voices-using-Ollama
```

### 3. Pull a base model

Choose any supported base model (e.g., `llama3.2`, `mistral`, `phi3`):

```bash
ollama pull llama3.2
```

### 4. Build a custom persona

Pick a Modelfile from the repo and build it:

```bash
# Example: build Taylor's voice
ollama create taylor-voice -f taylor.modelfile

# Another example
ollama create elon-voice -f elon.modelfile
```

### 5. Run it

```bash
ollama run taylor-voice
```

Or pass a one-off prompt:

```bash
ollama run elon-voice "Write a tweet about reusable rockets."
```

### Example 1: Trump Voice on Economy
**Question:** "What's your opinion on making America's economy stronger?"

**Response:**
```
Folks, let me tell you, nobody knows more about making America's economy stronger than I do. It's gonna be huge, just huge. We're talking about creating jobs, creating growth, creating wealth like never before.

First of all, we gotta cut the red tape, folks. We gotta get rid of those regulations that are holding us back. We need to unleash the American entrepreneurial spirit, let people build, create, innovate. That's what made America great in the first place.

And let me tell you, our trade deals? Forget about it. They were disasters. We're gonna make new deals, great deals, fantastic deals. We're gonna protect American workers, American manufacturers. Nobody's better at making deals than me.
```

---

## 🛠 Create Your Own Voice

1. Create a new file, e.g., `myvoice.modelfile`:

   ```text
   FROM llama3.2

   PARAMETER temperature 0.8
   PARAMETER top_p 0.9

   SYSTEM """
   You are an inspiring teacher who explains concepts with simple analogies.
   Stay encouraging and clear in all responses.
   """
   ```

2. Build & run:

   ```bash
   ollama create teacher-voice -f myvoice.modelfile
   ollama run teacher-voice
   ```

---
