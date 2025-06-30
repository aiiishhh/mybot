from tasks import add_task, list_tasks
from weather import get_weather
from email_sender import send_email
from calendar_integration import create_event
from ai_response import chat_with_ai

print("🤖 Hello Aysha! I’m your Personal AI Assistant.")

while True:
    cmd = input("\n💬 What can I help you with? (type 'exit' to quit)\n> ").lower()

    if "remind me" in cmd:
        task = cmd.replace("remind me to", "").strip()
        add_task(task)
        print("📝 Task added!")

    elif "show tasks" in cmd:
        print("📋 Your Tasks:")
        for t in list_tasks(): print(f"- {t}")

    elif "weather in" in cmd:
        city = cmd.split("in")[-1].strip()
        print("🌦️", get_weather(city))

    elif "send email" in cmd:
        to = input("📧 Recipient Email: ")
        subject = input("✉️ Subject: ")
        body = input("💬 Message: ")
        send_email(to, subject, body)

    elif "schedule" in cmd or "event" in cmd:
        title = input("📌 Event Title: ")
        time = input("🕒 Time (YYYY-MM-DD HH:MM): ")
        create_event(title, time)

    elif "chat" in cmd:
        user_input = input("🧠 Ask something:\n> ")
        print(chat_with_ai(user_input))

    elif cmd == "exit":
        print("👋 Goodbye, Aysha!")
        break

    else:
        print("❓ Sorry, I didn’t understand that.")
