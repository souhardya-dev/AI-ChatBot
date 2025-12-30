from openai import OpenAI

client = OpenAI()

print(" AI Chatbot (type 'bye' to exit)")
print("-" * 40)

conversation = []

while True:
    user_input = input("You: ")

    if user_input.lower() == "bye":
        print("Bot: Goodbye! 👋")
        break

    conversation.append({
        "role": "user",
        "content": user_input
    })

    response = client.chat.completions.create(
        model="gpt-4o-mini",
        messages=conversation
    )

    bot_reply = response.choices[0].message.content
    print("Bot:", bot_reply)

    conversation.append({
        "role": "assistant",
        "content": bot_reply
    })
