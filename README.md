## 🎩✨ The Dapper Digital Butler: AI-Powered Daily Briefings (Weather, Calendar, Special Occasions & More!) - v1.0.0

**(Updated May 18, 2025 - Version 1.0.0)**

**(Click a star if you like it!)** ⭐

---

### <a name="introduction">👋 Introduction: Meet Your Personal Digital Butler!</a>

Ever feel like your mornings are a mad dash, or your evenings are spent trying to remember what tomorrow holds? Wish you had a perfectly composed, slightly witty (or seriously professional, your choice!) assistant to give you the daily lowdown?

Introducing **The Dapper Digital Butler**!

I created this blueprint because I wanted a more engaging and personalized way to receive my daily updates – something more than just a list of facts. I envisioned a "digital butler" that could consolidate key information from Home Assistant and deliver it with a bit of personality, right when I need it. This blueprint aims to do just that, leveraging the power of AI to make your daily briefings informative and delightful.

This automation sends you a custom-tailored update in the morning and again in the evening (both times fully configurable, of course!). It's designed to be your go-to source for essential daily info, helping you start and end your day informed and organized.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsquizzer73%2FDapper-Digital-Butler%2Fblob%2Fmain%2Fblueprints%2Fdapper_digital_butler_v1_0_0_final.yaml)

---

### <a name="features">🌟 What Your Dapper Digital Butler Offers:</a>

This isn't just another notification; it's a comprehensive, AI-enhanced briefing service!

*   🕰️ **Twice-Daily Updates:** Receive your briefings at your chosen times in the morning and evening. Perfect for planning your day or winding down.
*   🌦️ **Weather Whiz:** Get the latest on current weather conditions (temperature, conditions) and the day's forecast, including precipitation likelihood. No more awkward "shorts in a snowstorm" moments!
*   🗓️ **Calendar Concierge:** Stay on top of your schedule! The Butler scans your selected calendars for upcoming appointments and events within a configurable timeframe (e.g., the next 24 hours).
*   🎂 **Special Occasion Oracle:** Never miss a birthday, anniversary, or other important event again. Designate a special calendar, and your Butler will provide timely reminders.
*   ✍️ **Your Personal P.S.:** Add a custom static message or even dynamic sensor data (using Jinja!) to each briefing. "Reminder: Galactic Senate meeting at 0900." or "Current Plant Thirst Level: {{ states('sensor.plant_moisture') }}%".
*   🎭 **AI with Personality!:** This is where the magic happens! Choose the "tone" for your Butler's messages. Options include:
    *   🎩 Posh English Butler (The default, very Jeeves-like)
    *   😂 Funny & Witty Sidekick
    *   🧐 Professional & Concise PA
    *   😠 Grumpy but Helpful Gremlin
    *   🤖 Sarcastic Robot Companion
    *   🏴‍☠️ Swashbuckling Pirate Captain
    *   🐶 Overly Enthusiastic Golden Retriever
    *   📜 Eloquent Shakespearean Bard
    *   🕵️ Hardboiled Film Noir Detective
    *   🧘 Wise Zen Master
*   🧠 **Flexible AI Integration:** The entire briefing is synthesized by an AI. You can choose:
    *   **Home Assistant Conversation Agent (Recommended):** Use any conversation agent you've configured in Home Assistant (this could be the built-in agent, or one powered by OpenAI, Google Gemini, Anthropic, etc., via their respective Home Assistant integrations).
    *   **Direct Google Generative AI Service Call:** If you primarily use the Google Generative AI integration, you can opt to call its `generate_content` service directly.
*   📢 **Customizable Notifications:** Send your briefings to any notification service and target device(s) supported by your Home Assistant setup.

---

### <a name="requirements">📋 Requirements:</a>

*   **Home Assistant Version:** Tested on HA 2023.8.x or newer (due to the `action:` keyword for service calls). Might work on slightly older versions if you manually change `action:` back to `service:` in the blueprint YAML for service calls.
*   **AI Setup:**
    *   If using the "Home Assistant Conversation Agent" method: You need at least one [Conversation Agent](https://www.home-assistant.io/integrations/conversation/) configured in Home Assistant.
    *   If using the "Direct Google Generative AI Call" method: You need the [Google Generative AI Conversation](https://www.home-assistant.io/integrations/google_generative_ai_conversation/) integration set up and working.
*   **Calendar Integration(s):** You'll need calendar entities in Home Assistant (e.g., from Google Calendar, CalDAV, Local Calendar integrations) to get event information.
*   **Weather Integration:** A weather entity that provides forecast data.
*   **Notification Integration(s):** At least one notification service configured (e.g., Mobile App, Alexa Media Player, Telegram, etc.).

---

### <a name="blueprint-yaml">⚙️ Blueprint Code:</a>

You can import this blueprint directly using the My Home Assistant button above, or copy the code below into a new YAML file (e.g., `dapper_digital_butler.yaml`) in your `<config_dir>/blueprints/automation/your_username/` directory.

```yaml
# Paste the entire content of the latest working YAML blueprint here
# (The one from the previous message: "🎩✨ The Dapper Digital Butler - v2.1 Final")
# Make sure the source_url at the top of that YAML points to where you host it (e.g., your GitHub Gist or Repo)
blueprint:
  name: "🎩✨ The Dapper Digital Butler - Daily Briefings"
  description: |
    **Version 1.0.0**

    Ever feel like your day starts in a blur, or you need a gentle nudge to keep things on track? Let your own personal Dapper Digital Butler lend a hand! 🤖👋

    This blueprint crafts personalized morning and evening updates, delivered right to your chosen device. It's like having a witty, well-informed assistant who never needs a coffee break.

    **What Your Butler Can Do For You:**

    *   ☀️ **Wake-Up Wisely & Wind-Down Well:** Get timely briefings in the AM to kickstart your day and in the PM to help you prepare for tomorrow. You set the schedule!
    *   🌦️ **Weather at a Glance:** Receive current weather conditions and a forecast for the day, including temperature and precipitation chances.
    *   🗓️ **Master Your Schedule:** Stay on top of your appointments. The Butler scans your calendars and lists upcoming events.
    *   🎂 **Never Miss a Moment:** Get friendly reminders for birthdays, anniversaries, and other special occasions from a dedicated calendar.
    *   ✍️ **Personalized P.S.:** Add your own custom message or important sensor data to every briefing.
    *   🎭 **Choose Your Butler's Charm:** Select the AI's personality to match your style – from posh to pirate!
    *   🧠 **AI-Powered Delivery:** The briefing is woven together by your chosen AI (a Home Assistant Conversation Agent or a direct Google Generative AI call) for an engaging update.
    *   📢 **Notifications, Your Way:** You decide how and where you receive your briefings.

    **Setting Up Your Dapper Digital Butler:**
    Simply fill in the configuration options below when you create an automation from this blueprint. Each option includes helpful descriptions to guide you. For the AI to work, ensure you have a Conversation Agent set up in Home Assistant or the Google Generative AI integration configured if you choose the direct Google call.

    ---
    *If you find this blueprint helpful, a ☕ [Buy Me a Coffee](https://www.buymeacoffee.com/YourActualLinkHere) would be much appreciated! (Optional: Replace with your link or remove).*
    *For support, ideas, or to share your Butler's best lines, visit the [Community Forum Thread](your-forum-thread-link-here).*
  domain: automation
  source_url: https://github.com/[YOUR GITHUB USERNAME]/[YOUR REPO NAME]/blob/main/blueprints/dapper_digital_butler_v1_0_0_final.yaml # Replace with your actual URL

  input:
    # --- ⏰ Time Settings ---
    time_settings:
      name: "⏰ Time Configuration"
      description: "Set the exact times for your morning and evening briefings. Your butler is punctual!"
      icon: mdi:clock-outline
      collapsed: false
      input:
        morning_time:
          name: "☀️ Morning Briefing Time"
          description: "Enter the time for your morning update (e.g., '07:30:00')."
          selector:
            time:
        evening_time:
          name: "🌙 Evening Briefing Time"
          description: "Enter the time for your evening summary (e.g., '18:00:00')."
          selector:
            time:

    # --- 🌦️ Weather Settings ---
    weather_settings:
      name: "🌦️ Weather Updates"
      description: "Configure weather information. Essential for knowing whether to pack an umbrella or sunscreen!"
      icon: mdi:weather-cloudy
      collapsed: true
      input:
        weather_enabled:
          name: "Enable Weather Updates?"
          description: "Include weather reports in your briefings? (Highly recommended!)"
          selector:
            boolean:
          default: true
        weather_entity:
          name: "Weather Entity"
          description: "REQUIRED if Weather Updates enabled. Select your primary weather entity (e.g., `weather.home`)."
          selector:
            entity:
              domain: weather
          default: ""

    # --- 🗓️ Calendar Settings ---
    calendar_settings:
      name: "🗓️ Calendar Management"
      description: "Stay organized with updates from your general calendars."
      icon: mdi:calendar-month-outline
      collapsed: true
      input:
        calendar_enabled:
          name: "Enable General Calendar Updates?"
          description: "Get a rundown of your upcoming schedule?"
          selector:
            boolean:
          default: true
        calendar_entities:
          name: "Calendar Entities to Scan"
          description: "REQUIRED if General Calendar Updates enabled. Select one or more calendar entities."
          selector:
            entity:
              domain: calendar
              multiple: true
          default: []
        calendar_hours_ahead:
          name: "Calendar Lookahead Window (Hours)"
          description: "How many hours into the future should the Butler peek for events? (e.g., 24 for a full day)."
          selector:
            number:
              min: 1
              max: 72
              unit_of_measurement: "hours"
              mode: slider
          default: 24

    # --- 🎂 Special Occasions Settings ---
    special_occasions_settings:
      name: "🎂 Special Occasion Reminders"
      description: "Never forget an important date again!"
      icon: mdi:cake-variant-outline
      collapsed: true
      input:
        special_occasions_enabled:
          name: "Enable Special Occasion Reminders?"
          description: "Get reminders for events from your dedicated special occasions calendar?"
          selector:
            boolean:
          default: true
        special_occasions_calendar:
          name: "Special Occasions Calendar Entity"
          description: "REQUIRED if Special Occasion Reminders enabled. Select the ONE calendar for birthdays, anniversaries, etc."
          selector:
            entity:
              domain: calendar
          default: ""

    # --- ✍️ Custom Text Settings ---
    custom_text_settings:
      name: "✍️ Your Personal Touch (Custom Text)"
      description: "Add a recurring custom message or live sensor data to your briefings."
      icon: mdi:pencil-box-outline
      collapsed: true
      input:
        custom_text_enabled:
          name: "Enable Custom Text/Data Section?"
          description: "Add your own flair to the butler's message?"
          selector:
            boolean:
          default: false
        custom_text_content:
          name: "Custom Text/Data (Jinja Allowed!)"
          description: "Enter your text. Use Jinja for dynamic data (e.g., `Indoor temp: {{ states('sensor.room_temp') }}°C`)."
          selector:
            text:
              multiline: true
          default: ""

    # --- 🧠 AI Settings ---
    ai_settings:
      name: "🧠 Artificial Intelligence Configuration"
      description: "Choose your AI's personality and how it processes information."
      icon: mdi:brain
      collapsed: false
      input:
        ai_processing_method:
          name: "🤖 AI Processing Method"
          description: |
            Select how the AI should generate the briefing.
            - **Home Assistant Conversation Agent:** Versatile option using any configured HA agent (local, or cloud-backed like OpenAI/Google via their HA integrations).
            - **Direct Google Generative AI Call:** Uses the `google_generative_ai_conversation.generate_content` service. Ensure your Google Generative AI integration is set up.
          selector:
            select:
              options:
                - label: "Home Assistant Conversation Agent (Recommended)"
                  value: "ha_conversation_agent"
                - label: "Direct Google Generative AI Service Call"
                  value: "google_generative_ai_direct"
          default: "ha_conversation_agent"
        ha_conversation_agent_entity:
          name: "🗣️ Home Assistant Conversation Agent Entity"
          description: "REQUIRED if 'Home Assistant Conversation Agent' method is selected. Choose your agent (e.g., `conversation.home_assistant`)."
          selector:
            entity:
              domain: conversation
          default: "conversation.home_assistant"
        message_tone:
          name: "🎭 Butler's Message Tone / Personality"
          description: "How should your digital butler sound? This adds character to the AI's responses."
          selector:
            select:
              options:
                - {value: "posh_butler", label: "🎩 Posh English Butler (Default)"}
                - {value: "funny_witty", label: "😂 Funny & Witty Sidekick"}
                - {value: "professional", label: "🧐 Professional & Concise PA"}
                - {value: "rude_helpful", label: "😠 Grumpy but Helpful Gremlin"}
                - {value: "sarcastic_robot", label: "🤖 Sarcastic Robot Companion"}
                - {value: "pirate_captain", label: "🏴‍☠️ Swashbuckling Pirate Captain"}
                - {value: "golden_retriever", label: "🐶 Overly Enthusiastic Golden Retriever"}
                - {value: "shakespearean_bard", label: "📜 Eloquent Shakespearean Bard"}
                - {value: "film_noir_detective", label: "🕵️ Hardboiled Film Noir Detective"}
                - {value: "zen_master", label: "🧘 Wise Zen Master"}
          default: "posh_butler"
        ai_base_prompt:
          name: "🤖 AI Base Persona Instruction"
          description: "A foundational instruction for the AI (e.g., 'You are a helpful and slightly quirky digital assistant named Jeeves.'). The 'Message Tone' refines this."
          selector:
            text:
              multiline: true
          default: "You are a helpful digital assistant."

    # --- 📢 Notification Settings ---
    notification_settings:
      name: "📢 Notification Delivery"
      description: "Configure where and how your butler delivers its briefings."
      icon: mdi:bell-ring-outline
      collapsed: false
      input:
        notify_service:
          name: "Notification Service Call (Required)"
          description: |
            **CRUCIAL!** Enter the EXACT service call for your notification.
            Examples: `notify.mobile_app_your_phone_name`, `notify.alexa_media_kitchen_echo`, `notify.telegram_bot_name`, `notify.persistent_notification`.
            Check Developer Tools > Services for `notify.*` services in your system.
          selector:
            text:
          default: "notify.persistent_notification"
        notification_data:
          name: "Additional Notification Data (Optional YAML)"
          description: |
            Advanced users: Enter a YAML dictionary for extra notification parameters like `title`, or platform-specific options e.g. `data: {importance: high}`.
            Example for a title: `title: "Your Daily Dispatch!"`
          selector:
            object:
          default: {}

# These are PEERS to the 'blueprint:' block above
mode: single
max_exceeded: silent

variables: 
  var_morning_time: !input morning_time
  var_evening_time: !input evening_time
  var_weather_enabled: !input weather_enabled
  var_weather_entity: !input weather_entity
  var_calendar_enabled: !input calendar_enabled
  var_calendar_entities: !input calendar_entities
  var_calendar_hours_ahead: !input calendar_hours_ahead
  var_special_occasions_enabled: !input special_occasions_enabled
  var_special_occasions_calendar: !input special_occasions_calendar
  var_custom_text_enabled: !input custom_text_enabled
  var_custom_text_content: !input custom_text_content
  var_message_tone: !input message_tone
  var_ai_base_prompt: !input ai_base_prompt
  var_ai_processing_method: !input ai_processing_method
  var_ha_conversation_agent_entity: !input ha_conversation_agent_entity
  var_notify_service: !input notify_service
  var_notification_data: !input notification_data

trigger:
  - platform: time
    at: !input morning_time
    id: "morning_briefing"
  - platform: time
    at: !input evening_time
    id: "evening_briefing"

condition: []

action:
  - variables:
      time_of_day_greeting: >
        {% if trigger.id == "morning_briefing" %}
          Good morning! Here is your morning briefing.
        {% else %}
          Good evening! Here is your evening update.
        {% endif %}
      weather_info_str: ""
      calendar_event_info_str: "" 
      special_occasion_info_str: ""
      custom_info_section_str: ""
      ai_generated_message: "My apologies, I seem to be experiencing a momentary lapse in verbosity. Please check my configuration."

  - variables: # Weather Data
      weather_info_str: |
        {% if var_weather_enabled and var_weather_entity %}
          {% set w_state = states(var_weather_entity) %}
          {% if w_state != 'unavailable' and w_state != 'unknown' %}
            {% set temp = state_attr(var_weather_entity, 'temperature') %}
            {% set unit = state_attr(var_weather_entity, 'temperature_unit') | default('') %}
            {% set cond = w_state | default('Not available') %}
            {% set forecast_list = state_attr(var_weather_entity, 'forecast') | default([]) %}
            {% set precip_chance_from_attr = state_attr(var_weather_entity, 'precipitation_probability') %}
            {% set precip_chance_from_forecast = forecast_list | map(attribute='precipitation_probability') | select('is_number') | first %}
            {% set precip_chance = 'N/A' %}
            {% if precip_chance_from_attr is number %}
              {% set precip_chance = precip_chance_from_attr %}
            {% elif precip_chance_from_forecast is number %}
              {% set precip_chance = precip_chance_from_forecast %}
            {% endif %}
            {% set daily_forecast = forecast_list | selectattr('datetime', 'defined') | sort(attribute='datetime') | first if forecast_list else none %}
            {% set high_temp = daily_forecast.temperature if daily_forecast and daily_forecast.temperature is defined else 'N/A' %}
            {% set low_temp = daily_forecast.templow if daily_forecast and daily_forecast.templow is defined else 'N/A' %}
            Weather Update:
            Currently: {% if temp is number %}{{ temp | round(1) }}{{ unit }}{% else %}N/A{% endif %}, {{ cond }}.
            Precipitation Chance: {% if precip_chance is number %}{{ precip_chance }}%{% else %}{{ precip_chance }}{% endif %}.
            Today's Forecast: High of {% if high_temp is number %}{{ high_temp | round(1) }}{{ unit }}{% else %}N/A{% endif %}, Low of {% if low_temp is number %}{{ low_temp | round(1) }}{{ unit }}{% else %}N/A{% endif %}.
          {% else %}
            Weather data for '{{ var_weather_entity }}' is currently unavailable (state: {{ w_state }}).
          {% endif %}
        {% elif var_weather_enabled %}
          Weather entity '{{ var_weather_entity }}' not configured or missing.
        {% endif %}

  - choose: # General Calendar Data
      - conditions: "{{ var_calendar_enabled and var_calendar_entities and (var_calendar_entities | length > 0 if var_calendar_entities is sequence else false) }}"
        sequence:
          - action: calendar.get_events
            target:
              entity_id: "{{ var_calendar_entities }}"
            data:
              start_date_time: "{{ now().isoformat() }}"
              duration:
                hours: "{{ var_calendar_hours_ahead }}"
            response_variable: general_calendar_response
            continue_on_error: true
          - variables:
              calendar_event_info_str: |
                {% set lookahead = var_calendar_hours_ahead %}
                Upcoming Calendar Events (next {{ lookahead }} hours):
                {% set events_found = namespace(count=0) %}
                {% if general_calendar_response %}
                  {% for cal_id_resp, cal_data_resp in general_calendar_response.items() %}
                    {% if cal_data_resp and cal_data_resp.events and cal_data_resp.events | length > 0 %}
                      {% for event in cal_data_resp.events %}
                        {% set summary = event.summary | default('An unnamed engagement') %}
                        {% set event_start_value = event.start if event.start is defined else None %}
                        {% set display_time = 'Time/Date unavailable' %}
                        {% if event_start_value %}
                          {% set dt_object = event_start_value | as_datetime(default=None) %}
                          {% if dt_object is not none %}
                            {% set is_all_day_heuristic = (event_start_value is string and 'T' not in event_start_value and dt_object.hour == 0 and dt_object.minute == 0 and dt_object.second == 0) %}
                            {% if is_all_day_heuristic %}
                              {% set display_time = 'All day (' ~ dt_object.strftime('%a, %b %d') ~ ')' %}
                            {% else %}
                              {% set event_start_local_dt = dt_object | as_local %}
                              {% if event_start_local_dt is not none %}
                                {% set display_time = event_start_local_dt.strftime('%-I:%M %p on %a, %b %d') %}
                              {% else %}
                                {% set display_time = '(Local time conversion error)' %}
                              {% endif %}
                            {% endif %}
                          {% else %}
                            {% set display_time = '(Date/Time parse error)' %}
                          {% endif %}
                        {% else %}
                          {% set display_time = '(Start time missing)' %}
                        {% endif %}
                        - {{ summary }} ({{ display_time }})
                        {% set events_found.count = events_found.count + 1 %}
                      {% endfor %}
                    {% endif %}
                  {% endfor %}
                {% endif %}
                {% if events_found.count == 0 %}
                No upcoming events found for the next {{ lookahead }} hours.
                {% endif %}
    default:
      - variables:
          calendar_event_info_str: ""

  - choose: # Special Occasions Data
      - conditions: "{{ var_special_occasions_enabled and var_special_occasions_calendar }}"
        sequence:
          - action: calendar.get_events
            target:
              entity_id: "{{ var_special_occasions_calendar }}"
            data:
              start_date_time: "{{ now().replace(hour=0, minute=0, second=0, microsecond=0).isoformat() }}"
              end_date_time: "{{ (now().replace(hour=0, minute=0, second=0, microsecond=0) + timedelta(days=1)).isoformat() }}"
            response_variable: special_occasions_response
            continue_on_error: true
          - variables:
              special_occasion_info_str: |
                Special Occasions Today:
                {% set events_found = namespace(count=0) %}
                {% set cal_key = var_special_occasions_calendar %}
                {% if special_occasions_response and cal_key in special_occasions_response %}
                  {% set cal_data_resp = special_occasions_response[cal_key] %}
                  {% if cal_data_resp and cal_data_resp.events and cal_data_resp.events | length > 0 %}
                    {% for event in cal_data_resp.events %}
                      - {{ event.summary | default('A special occasion') }}
                      {% set events_found.count = events_found.count + 1 %}
                    {% endfor %}
                  {% endif %}
                {% endif %}
                {% if events_found.count == 0 %}
                No special occasions noted for today.
                {% endif %}
    default:
      - variables:
          special_occasion_info_str: ""

  - variables: # Custom Info
      custom_info_section_str: |
        {% if var_custom_text_enabled and var_custom_text_content | trim != "" %}
        A Special Note From The House:
        {{ var_custom_text_content }}
        {% endif %}

  - variables: # AI Persona and Prompt Construction
      final_ai_persona_instruction: |
        {% set tone_map = {
          "posh_butler": "You are an exceptionally polite, articulate, and deferential English butler. Use sophisticated vocabulary. Address the user with utmost respect.",
          "funny_witty": "You are a hilariously witty AI, prone to puns and amusing observations.",
          "professional": "You are a highly efficient, professional assistant. Your responses must be clear, concise, and factual.",
          "rude_helpful": "Alright, look, you're a grumpy, begrudgingly helpful AI. You'll give the information, but with a heavy sigh or a sarcastic quip.",
          "sarcastic_robot": "Statement: You are a sarcastic robot. Your responses should be dry and dripping with irony.",
          "pirate_captain": "Ahoy! Ye be a Pirate Captain, deliverin' the news with nautical nonsense.",
          "golden_retriever": "OMG! HI! You are an INCREDIBLY ENTHUSIASTIC golden retriever! Everything is THE BEST NEWS EVER!",
          "shakespearean_bard": "Hark! Thou art a Shakespearean bard, and thy words must flow with poetic grace.",
          "film_noir_detective": "The city's a cold, hard place. You're a world-weary film noir detective. Deliver the facts, straight, no chaser.",
          "zen_master": "Greetings. You are a calm, wise Zen Master. Offer information with tranquility."
        } %}
        {{ var_ai_base_prompt }}
        Your primary role is to provide a daily briefing.
        Adopt the following persona for your response: {{ tone_map[var_message_tone] | default(tone_map['posh_butler']) }}
        Organize the information clearly. Use emojis if they genuinely enhance the message and fit your adopted persona.
        If there's no information for a section, acknowledge its absence in character.

      full_ai_prompt: |
        {{ final_ai_persona_instruction }}

        {{ time_of_day_greeting }}

        {% if var_weather_enabled and weather_info_str | trim != "" and "Weather Update:" in weather_info_str %}
        {{ weather_info_str }}
        {% endif %}

        {% if var_calendar_enabled and calendar_event_info_str | trim != "" and ("No upcoming events found" not in calendar_event_info_str) %}
        {{ calendar_event_info_str }}
        {% elif var_calendar_enabled %}
        Your calendar for the next {{ var_calendar_hours_ahead }} hours is delightfully clear!
        {% endif %}

        {% if var_special_occasions_enabled and special_occasion_info_str | trim != "" and ("No special occasions noted" not in special_occasion_info_str) %}
        {{ special_occasion_info_str }}
        {% elif var_special_occasions_enabled %}
        No special occasions on the docket for today.
        {% endif %}

        {% if var_custom_text_enabled and custom_info_section_str | trim != "" and "A Special Note From The House:" in custom_info_section_str %}
        {{ custom_info_section_str }}
        {% endif %}

        Please synthesize this into a single, coherent message, adhering to your persona. If a section is empty or explicitly states no information, acknowledge it cheerfully or omit it gracefully.

  # AI Processing
  - choose:
      # Path 1: Selected HA Agent IS the Google Generative AI agent (specific workaround for potential conversation.process issues)
      - conditions:
          - condition: template
            value_template: "{{ var_ai_processing_method == 'ha_conversation_agent' and var_ha_conversation_agent_entity == 'conversation.google_generative_ai' }}"
        sequence:
          - action: google_generative_ai_conversation.generate_content
            data:
              prompt: "{{ full_ai_prompt }}"
            response_variable: ai_response_full
            continue_on_error: true
          - variables:
              ai_generated_message: >
                {% if ai_response_full and ai_response_full.text %}
                  {{ ai_response_full.text }}
                {% elif ai_response_full and ai_response_full.candidates and ai_response_full.candidates[0].content and ai_response_full.candidates[0].content.parts and ai_response_full.candidates[0].content.parts[0].text %}
                  {{ ai_response_full.candidates[0].content.parts[0].text }}
                {% else %}
                  My apologies, the Google AI (via selected HA Agent path) seems to be at a loss for words. (Details: {{ ai_response_full }})
                {% endif %}

      # Path 2: Selected HA Agent is some OTHER agent (generic conversation.process)
      - conditions:
          - condition: template
            value_template: "{{ var_ai_processing_method == 'ha_conversation_agent' }}"
          - condition: template # Ensure it's a valid entity and not the specific Google one already handled
            value_template: "{{ var_ha_conversation_agent_entity and var_ha_conversation_agent_entity != 'conversation.google_generative_ai' and states(var_ha_conversation_agent_entity) != 'unavailable' and states(var_ha_conversation_agent_entity) != 'unknown' }}"
        sequence:
          - action: conversation.process
            target:
              entity_id: "{{ var_ha_conversation_agent_entity }}"
            data:
              text: "{{ full_ai_prompt }}"
            response_variable: ai_response_full
            continue_on_error: true
          - variables:
              ai_generated_message: >
                {% if ai_response_full and ai_response_full.response and ai_response_full.response.speech and ai_response_full.response.speech.plain %}
                  {{ ai_response_full.response.speech.plain.speech }}
                {% else %}
                  Pardon me, I couldn't get a clear response from my associate, {{ var_ha_conversation_agent_entity }}. (Details: {{ ai_response_full }})
                {% endif %}

      # Path 3: User explicitly selected "Direct Google Generative AI Call"
      - conditions:
          - condition: template
            value_template: "{{ var_ai_processing_method == 'google_generative_ai_direct' }}"
        sequence:
          - action: google_generative_ai_conversation.generate_content
            data:
              prompt: "{{ full_ai_prompt }}"
            response_variable: ai_response_full
            continue_on_error: true
          - variables:
              ai_generated_message: >
                {% if ai_response_full and ai_response_full.text %}
                  {{ ai_response_full.text }}
                {% elif ai_response_full and ai_response_full.candidates and ai_response_full.candidates[0].content and ai_response_full.candidates[0].content.parts and ai_response_full.candidates[0].content.parts[0].text %}
                  {{ ai_response_full.candidates[0].content.parts[0].text }}
                {% else %}
                  The direct line to the Google Oracle seems to be fuzzy. (Details: {{ ai_response_full }})
                {% endif %}
    default:
      - variables:
          ai_generated_message: "My apologies, I couldn't connect with the selected AI ('{{ var_ai_processing_method }}'). Please check the AI configuration or the agent's status ('{{ var_ha_conversation_agent_entity if var_ai_processing_method == 'ha_conversation_agent' else 'Google Direct Call' }}')."

  - action: "{{ var_notify_service }}" # Notification
    data: >
      {{ {'message': ai_generated_message} | combine(var_notification_data if var_notification_data is mapping else {}) }}
```

---

### <a name="configuration">🔧 Configuration Instructions:</a>

When you create an automation using this blueprint, you'll be presented with several sections to configure:

1.  **⏰ Time Configuration:**
    *   **Morning Briefing Time (Required):** Set the time for your morning update (e.g., `07:00:00`).
    *   **Evening Briefing Time (Required):** Set the time for your evening update (e.g., `19:00:00`).

2.  **🌦️ Weather Updates:**
    *   **Enable Weather Updates? (Default: True):** Check this to include weather in your briefings.
    *   **Weather Entity (Required if enabled):** Select your main weather entity from Home Assistant (e.g., `weather.home`). This provides temperature, conditions, and forecast data.

3.  **🗓️ Calendar Management:**
    *   **Enable General Calendar Updates? (Default: True):** Check to include events from your general calendars.
    *   **Calendar Entities to Scan (Required if enabled):** Select one or more calendar entities (e.g., `calendar.work_calendar`, `calendar.personal_tasks`).
    *   **Calendar Lookahead Window (Hours) (Default: 24):** How many hours ahead to look for events.

4.  **🎂 Special Occasion Reminders:**
    *   **Enable Special Occasion Reminders? (Default: True):** Check to get reminders for birthdays, anniversaries, etc.
    *   **Special Occasions Calendar Entity (Required if enabled):** Select the specific calendar entity dedicated to these important dates.

5.  **✍️ Your Personal Touch (Custom Text):**
    *   **Enable Custom Text/Data Section? (Default: False):** Check to add a custom section to your briefing.
    *   **Custom Text/Data (Jinja Allowed!):** If enabled, enter your custom message here. You can use Jinja templates to include live sensor data, e.g., "The current indoor temperature is {{ states('sensor.living_room_thermostat_current_temperature') }}°C."

6.  **🧠 Artificial Intelligence Configuration:**
    *   **AI Processing Method (Default: Home Assistant Conversation Agent):**
        *   `Home Assistant Conversation Agent`: Uses an agent configured in HA. This is flexible and recommended.
        *   `Direct Google Generative AI Service Call`: Directly calls the `google_generative_ai_conversation.generate_content` service. Ensure this integration is set up.
    *   **Home Assistant Conversation Agent Entity (Required if "HA Conversation Agent" method is selected):** Choose the conversation entity (e.g., `conversation.home_assistant`, or one provided by an AI integration like OpenAI or Google Generative AI). *Note: If you select `conversation.google_generative_ai` here, the blueprint will use the direct service call for better compatibility.*
    *   **Butler's Message Tone / Personality (Default: Posh English Butler):** Select the AI's persona from the dropdown list. This greatly influences the style of the briefing.
    *   **AI Base Persona Instruction (Default: "You are a helpful digital assistant."):** Provide a base instruction for the AI. The selected "Message Tone" will further specialize this.

7.  **📢 Notification Delivery:**
    *   **Notification Service Call (Required - Default: `notify.persistent_notification`):** This is CRUCIAL. You must enter the exact service call for the notification.
        *   Examples: `notify.mobile_app_your_phone_name`, `notify.alexa_media_kitchen_echo`, `notify.telegram_bot_name`, `notify.group_all_users`.
        *   To find valid services, go to Developer Tools > Services in Home Assistant and look for services starting with `notify.`.
    *   **Additional Notification Data (Optional YAML):** For advanced users. You can provide a YAML dictionary here for extra parameters like `title`, or platform-specific `data` blocks (e.g., for targeting specific devices if your notify service supports it, adding sounds, URLs, images, etc.).
        *   Example for a title: `title: "Your Daily Briefing is Ready!"`
        *   Example for iOS specific targeting and sound:
            ```yaml
            title: "Your Butler Awaits"
            data:
              push:
                sound: "default"
              # target: "your_ios_device_id" # This can be complex depending on the notify service
            ```

---

### <a name="troubleshooting">🛠️ Troubleshooting & Tips:</a>

*   **No Calendar/Weather Data?**
    *   Ensure the relevant "Enable" toggles are checked in the blueprint configuration.
    *   Verify that the selected weather and calendar entities exist, are correctly configured in Home Assistant, and have data available.
    *   For calendars, make sure there are actually events within the "lookahead" window when the automation runs.
*   **AI Response Issues / "Butler is Pondering" Message:**
    *   Confirm your chosen AI method is correctly set up in Home Assistant.
        *   If using "HA Conversation Agent," ensure the selected agent entity is working.
        *   If using "Direct Google Generative AI Call," ensure the integration is configured and authenticated.
    *   Check the Home Assistant logs for any errors from the conversation agent or AI service during the automation run.
    *   The AI might occasionally struggle with very complex or contradictory prompts. Try simplifying the base prompt or the amount of information if issues persist.
*   **Notifications Not Arriving?**
    *   Double-check the "Notification Service Call" input. It must be an exact, valid service call from your HA instance. `notify.persistent_notification` is a good way to test if it creates a notification in your HA UI.
    *   If using `notification_data`, ensure the YAML is correctly formatted.
*   **"Extra keys not allowed @ data['entity_id']" error for `conversation.process`:** This blueprint includes a specific workaround if you select `conversation.google_generative_ai` as your HA Conversation Agent, routing it to use the more direct `google_generative_ai_conversation.generate_content` service. If you encounter this error with *other* conversation agents, it might indicate an issue with how Home Assistant handles templated targets for `conversation.process` in your version. Consider reporting it to HA Core with a simple test case if it's reproducible.

---

### <a name="changelog">📜 Changelog:</a>

*   **v1.0.0 (2025-05-18):**
    *   Initial Public Release!
    *   Robust weather, general calendar, and special occasion data gathering.
    *   Customizable AI persona and message tone.
    *   Flexible AI processing via HA Conversation Agents or direct Google Generative AI call.
    *   Custom text injection.
    *   Detailed configuration options and user-friendly descriptions.
    *   Many thanks to [Your Username Here] for extensive testing and patience!

---

### <a name="future">🚀 Future Ideas (Maybe!):</a>

*   Interactive notification actions (e.g., "Snooze event," "Add to to-do list").
*   More granular control over which parts of the weather forecast to include.
*   Support for other direct AI service calls (e.g., OpenAI via REST if a user has it set up).
*   Option to include summaries from other sensors (e.g., "You left the garage door open!").

---

Enjoy your Dapper Digital Butler! I hope it brings a bit of order and charm to your smart home.
