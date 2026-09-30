# ✈️ TravelBrain — Multi-Agent AI Travel Planner

> **Plan your entire trip with AI — flights, hotels, weather, itinerary, and budget in one conversation.**

TravelBrain is a **multi-agent AI travel planning application** that turns a natural-language travel request into a complete, research-backed trip plan.

Instead of opening multiple tabs to search for flights, hotels, weather, and attractions, users simply describe their trip in plain English. TravelBrain delegates different parts of the research to specialized AI agents and combines their findings into a practical **day-by-day itinerary with estimated costs**.

---

## 🌍 What TravelBrain Does

For example, simply enter:

> **"Plan a 10-day Europe trip from India in April with a mid-range budget."**

TravelBrain researches and generates:

| ✈️ Flights                                 | 🏨 Hotels                                           | 🌤️ Weather                           | 🗺️ Itinerary                 | 💰 Budget               |
| ------------------------------------------ | --------------------------------------------------- | ------------------------------------- | ----------------------------- | ----------------------- |
| Airports, airlines, duration & fare ranges | Accommodation options based on destination & budget | Conditions, forecasts & travel advice | Realistic day-by-day schedule | Estimated trip expenses |

The generated plan is saved automatically, allowing users to **reopen previous trips and continue the conversation without starting from scratch.**

---

## 🤖 Multi-Agent Architecture

TravelBrain uses a **multi-agent approach**, where different AI-powered components focus on specific travel-planning tasks.

```text
                         User Request
                              │
                              ▼
                    ┌──────────────────┐
                    │   TravelBrain    │
                    │   AI Planner     │
                    └────────┬─────────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
        ✈️ Flight Agent  🏨 Hotel Agent  🌤️ Weather Agent
              │              │              │
              ▼              ▼              ▼
       AviationStack       Tavily       OpenWeather
              │              │              │
              └──────────────┼──────────────┘
                             ▼
                    🧠 AI Plan Synthesis
                             │
                             ▼
                ┌────────────────────────┐
                │  Complete Trip Plan    │
                ├────────────────────────┤
                │ • Itinerary            │
                │ • Flights              │
                │ • Hotels               │
                │ • Weather              │
                │ • Budget               │
                └────────────────────────┘
                             │
                             ▼
                     PostgreSQL Database
```

This separation allows each part of the trip to receive focused research before the information is combined into one coherent travel plan.

---

## ✨ Features

### 🧠 AI-Powered Trip Planning

Describe your trip naturally instead of filling out complicated forms.

```text
I want a relaxed 5-day trip to Rome and Florence
in September for two people.
```

TravelBrain interprets the request and builds a structured travel plan.

### ✈️ Flight Research

Provides information such as:

* Likely airports
* Airlines operating on the route
* Typical flight duration
* Fare ranges

Powered by **AviationStack**.

### 🏨 Hotel Research

Finds accommodation options based on:

* Destination
* Budget
* Trip requirements

Powered by **Tavily**.

### 🌤️ Weather Information

Provides:

* Current weather conditions
* Forecast information
* Travel-related weather advice

Powered by **OpenWeather**.

### 🗺️ Day-by-Day Itinerary

Generates a practical itinerary based on the destination, duration and travel preferences.

### 💰 Budget Estimation

Provides an estimated breakdown of major travel expenses to help users understand the expected trip cost.

### 💾 Persistent Trips

Trips are automatically stored in PostgreSQL.

Users can:

* Reopen previous trips
* Continue conversations
* Ask follow-up questions
* Maintain the context of an existing trip

### 🛠️ Trip Builder

Users who prefer structured input can use the trip builder to enter:

* Origin
* Destination
* Dates
* Duration
* Number of travellers
* Budget
* Travel interests

The application automatically converts these inputs into an AI-ready prompt.

### 📄 Export & Sharing

Generated plans can be:

* Copied
* Downloaded as Markdown
* Printed

### 🌙 Light & Dark Mode

Switch between light and dark themes directly from the application.

---

# 🧰 Tech Stack

| Technology        | Purpose                        |
| ----------------- | ------------------------------ |
| **Python 3.11**   | Application backend            |
| **Groq**          | LLM inference and AI planning  |
| **Tavily**        | Web and hotel research         |
| **AviationStack** | Flight and airport information |
| **OpenWeather**   | Weather information            |
| **PostgreSQL**    | Persistent trip storage        |
| **uv**            | Python dependency management   |

---

# 🚀 Getting Started

## Prerequisites

Before running TravelBrain locally, install:

* Python **3.11**
* [uv](https://docs.astral.sh/uv/)
* PostgreSQL database
* Groq API key
* Tavily API key
* AviationStack API key
* OpenWeather API key

A free PostgreSQL instance from **Render** can be used for development.

---

## 1. Clone the Repository

```bash
git clone https://github.com/KalyanM45/TravelBrain-Multi-Agent-AI-Travel-Planner.git

cd TravelBrain-Multi-Agent-AI-Travel-Planner
```

---

## 2. Install Dependencies

The project uses `uv` for dependency management.

```bash
uv sync
```

---

## 3. Configure Environment Variables

Create a `.env` file in the project root:

```env
# Required
GROQ_API_KEY=your_groq_key
DATABASE_URL=postgresql://user:password@host:5432/dbname

# Travel data services
TAVILY_API_KEY=your_tavily_key
AVIATIONSTACK_API_KEY=your_aviationstack_key
OPENWEATHER_API_KEY=your_openweather_key

# Optional
GROQ_MODEL=openai/gpt-oss-20b
```

### Environment Variables

| Variable                | Required | Purpose                            |
| ----------------------- | :------: | ---------------------------------- |
| `GROQ_API_KEY`          |     ✅    | Powers AI planning                 |
| `DATABASE_URL`          |     ✅    | Stores trips and conversation data |
| `TAVILY_API_KEY`        |     ✅    | Web and hotel research             |
| `AVIATIONSTACK_API_KEY` |     ✅    | Flight and airport information     |
| `OPENWEATHER_API_KEY`   |     ✅    | Weather and forecast data          |
| `GROQ_MODEL`            |     ❌    | Allows changing the AI model       |

> ⚠️ **Never commit your `.env` file or expose API keys publicly.**

---

## 4. Start the Application

```bash
uv run python app.py
```

Then open:

```text
http://127.0.0.1:8000
```

If the application shows the **green API Connected indicator**, the setup is ready.

---

# 💬 Usage

## Plan a Trip

Enter a natural-language request in the chat box:

```text
Plan a 10 day Europe trip from India in April,
mid-range budget.
```

Or:

```text
I want a relaxed 5 day trip to Rome and Florence
in September for two people.
```

The AI agents research the required information and generate the complete plan.

A typical plan takes approximately **30–90 seconds**, depending on external API response times and research requirements.

---

## 🧩 Use the Trip Builder

If you don't want to write a prompt manually:

1. Open the **Trip Builder**
2. Enter your origin
3. Select your destination
4. Enter travel dates
5. Select trip duration
6. Add number of travellers
7. Select your budget
8. Choose your interests
9. Click **Write my prompt**
10. Review or edit the generated prompt
11. Send it to TravelBrain

---

# 📋 Generated Plan

Travel results are organized into dedicated sections:

### Plan

Overall trip summary and recommendations.

### Itinerary

Detailed day-by-day travel schedule.

### Flights

Flight routes, airports, airlines and estimated fare information.

### Hotels

Accommodation recommendations based on destination and budget.

### Weather

Weather conditions, forecast information and travel advice.

---

# 💾 Trip Management

Every generated trip is automatically saved.

From the sidebar you can:

* Open previous trips
* Continue an existing conversation
* Ask follow-up questions
* Start a new trip

For example:

```text
User:
Plan a 7-day trip to Japan.

TravelBrain:
[Generates the trip plan]

User:
Can you make the itinerary less crowded?

TravelBrain:
[Updates the existing plan while maintaining trip context]
```

---

# 🔧 Troubleshooting

## The page loads but planning fails

Check:

* `GROQ_API_KEY`
* `TAVILY_API_KEY`
* `AVIATIONSTACK_API_KEY`
* `OPENWEATHER_API_KEY`
* Internet connection
* Terminal error messages

---

## Model Does Not Exist

If Groq reports that the configured model does not exist, check your `GROQ_MODEL` value.

You can change it in `.env`:

```env
GROQ_MODEL=your_supported_model
```

Then restart the application.

---

## DATABASE_URL Is Missing

Make sure `.env` contains:

```env
DATABASE_URL=postgresql://user:password@host:5432/dbname
```

Also verify that the PostgreSQL database is running and accessible.

---

## Plans Take a Long Time

TravelBrain depends on multiple external services.

Slow responses can be caused by:

* LLM inference
* Web research
* Flight API response time
* Weather API response time
* Database connectivity
* Network latency

---

# 🤝 Contributing

Contributions are welcome!

## 1. Fork the Repository

Create your own fork of the project.

## 2. Clone Your Fork

```bash
git clone <your-fork-url>

cd TravelBrain-Multi-Agent-AI-Travel-Planner
```

## 3. Create a Feature Branch

```bash
git checkout -b feature/your-feature-name
```

## 4. Make Your Changes

Keep pull requests:

* Focused on one feature or fix
* Consistent with the existing codebase
* Tested end-to-end

Never commit:

```text
.env
API keys
Passwords
Database credentials
```

## 5. Commit Your Changes

```bash
git add .

git commit -m "Add support for multi-city trips"
```

## 6. Push Your Branch

```bash
git push origin feature/your-feature-name
```

Then open a Pull Request against the `main` branch.

---

# 🐛 Reporting Issues

Found a bug?

Open a GitHub Issue and include:

* What you were trying to do
* Steps to reproduce the issue
* Expected behavior
* Actual behavior
* Terminal error/output
* Relevant screenshots if applicable

For feature requests, describe:

* The problem
* Proposed solution
* Why the feature would be useful

---

# 🔐 Security

Please **never share API keys or database credentials** publicly.

If you accidentally expose a key:

1. Revoke the exposed key
2. Generate a new key
3. Update your `.env`
4. Remove the secret from Git history if necessary

---

# 🗺️ Future Improvements

Potential areas for extending TravelBrain include:

* 🌍 Multi-city trip optimization
* ✈️ Real-time flight price comparison
* 🏨 Direct hotel booking integrations
* 🚆 Train and local transportation planning
* 📍 Interactive maps
* 💱 Multi-currency budget calculation
* 📱 Mobile-friendly experience
* 🔔 Price and weather alerts
* 👥 Collaborative trip planning
* 📊 More detailed expense tracking

---

# 🙌 Acknowledgements

TravelBrain is powered by several services that make the travel research workflow possible:

* **[Groq](https://groq.com/)** — Fast AI inference
* **[Tavily](https://tavily.com/)** — Web research
* **[AviationStack](https://aviationstack.com/)** — Flight and airport data
* **[OpenWeather](https://openweathermap.org/)** — Weather data
* **[PostgreSQL](https://www.postgresql.org/)** — Persistent data storage
* **[uv](https://docs.astral.sh/uv/)** — Python package and project management

---

## ⭐ If You Find TravelBrain Useful

Give the repository a ⭐ on GitHub and feel free to open an issue or contribute to the project.

---

**TravelBrain — Describe your trip. Let AI research the rest.** ✈️🌍
