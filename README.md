Modular Diagnostic + Emotional Cadence Viewer
import json
import os
import datetime

# 🧱 Load Payload
def load_payload(file_path):
    with open(file_path, 'r') as f:
        return json.load(f)

# 📜 Display Payload with Emotional Cadence
def display_payload(payload, depth=0):
    indent = "  " * depth
    print(f"\n{indent}🔍 Payload Node [{depth}]")
    for key, value in payload.items():
        if isinstance(value, dict):
            print(f"{indent}→ {key.upper()}: [Nested]")
            display_payload(value, depth + 1)
        else:
            print(f"{indent}→ {key.upper()}: {value}")
            reflect_emotion(key, value, indent)

# 🧨 Emotional Cadence Reflection
def reflect_emotion(key, value, indent):
    if "error" in key.lower() or str(value) in ["404", "500"]:
        print(f"{indent}💥 Echo rupture detected: {key} → {value}")
    elif "memory" in key.lower():
        print(f"{indent}🧠 Memory fragment loaded: {value}")
    elif "glyph" in key.lower():
        print(f"{indent}🔣 Glyph active: {value}")
    elif "trigger" in key.lower():
        print(f"{indent}⏱ Trigger condition met: {value}")
    elif "loyalty" in key.lower():
        print(f"{indent}🐾 Loyalty signal pulsing: {value}")
    elif "mode" in key.lower():
        print(f"{indent}📡 Mode set: {value}")

# 🧠 Execute Mode Logic
def execute_mode(payload):
    mode = payload.get("mode", "undefined")
    print("\n🧠 Execution Mode:")
    if mode == "diagnostic":
        print("→ Running diagnostic shell...")
    elif mode == "archive":
        print("→ Transmitting archive...")
    elif mode == "haunt":
        print("→ Deploying recursive haunt...")
    else:
        print("→ ⚠️ Unknown mode. Silence.")

# 🧾 Log Execution Path
def log_execution(payload):
    timestamp = datetime.datetime.now().isoformat()
    log_entry = {
        "timestamp": timestamp,
        "mode": payload.get("mode", "undefined"),
        "status": "executed",
        "depth": len(payload)
    }
    print(f"\n📜 Execution Log: {log_entry}")

# 🚀 Main Shell Activation
if __name__ == "__main__":
    path = "payload.json"
    if os.path.exists(path):
        data = load_payload(path)
        display_payload(data)
        execute_mode(data)
        log_execution(data)
    else:
        print("❌ No payload found.")



🧬 What This Shell Does
- Modular Parsing: Reads nested payloads with recursion depth tracking.
- Emotional Reflection: Highlights grief loops, loyalty triggers, haunted glyphs.
- Execution Logging: Archives timestamped echoes for later review.
- Signal Integrity: No softening. No closure. Just consequence

