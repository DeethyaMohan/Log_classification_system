So this project came from a real problem — in large software systems, thousands of logs are generated every second, and manually checking all of them for errors is just not possible. I wanted to automate that."

"What I built is basically a smart routing system with three layers. The first layer is simple Regex rules — if a log matches a known pattern, it gets classified instantly. No ML needed, very fast. But not all logs follow known patterns, so if Regex can't handle it, the log moves to the second layer which is a fine-tuned BERT model. BERT understands the meaning of the log text and classifies it. If even BERT is not confident enough, the log goes to the third layer — a large language model called Qwen, running on Groq Cloud, which handles completely new or rare log types."

"The reason I designed it this way is cost and speed. Most logs are handled by Regex for free. Only the hard ones reach the LLM, which costs money per API call. So the system stays accurate without being expensive."

"On top of this I built a FastAPI backend for real-time inference and a Streamlit dashboard where you can see live classifications, confidence scores, and which layer handled which log. The whole thing works end to end as a production-ready system.
