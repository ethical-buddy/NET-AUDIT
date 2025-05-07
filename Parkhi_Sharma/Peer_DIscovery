import socket
import threading
from zeroconf import Zeroconf, ServiceBrowser, ServiceInfo
import uuid

PORT = 12345
SERVICE_TYPE = "_chat._tcp.local."
UNIQUE_ID = uuid.uuid4().hex[:6]
SERVICE_NAME = f"ChatPeer-{UNIQUE_ID}.{SERVICE_TYPE}"
peer_sockets = {}  # key: peer_id (ip:port), value: socket
peer_lock = threading.Lock()
zeroconf = Zeroconf()

def get_ip():
    s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    try:
        s.connect(("8.8.8.8", 80))
        ip = s.getsockname()[0]
    finally:
        s.close()
    return ip

# 1. Announce this peer
def announce_service():
    ip = get_ip()
    desc = {'id': UNIQUE_ID}
    info = ServiceInfo(
        SERVICE_TYPE,
        SERVICE_NAME,
        addresses=[socket.inet_aton(ip)],
        port=PORT,
        properties=desc,
        server=f"chat-peer-{UNIQUE_ID}.local."
    )
    zeroconf.register_service(info)

# 2. Peer listener for mDNS
class PeerListener:
    def add_service(self, zeroconf, type, name):
        info = zeroconf.get_service_info(type, name)
        if info:
            ip = socket.inet_ntoa(info.addresses[0])
            port = info.port
            peer_id = f"{ip}:{port}"
            if ip == get_ip():
                return  # Don't connect to self
            with peer_lock:
                if peer_id in peer_sockets:
                    return
            print(f"[DISCOVERED] {ip}:{port}")
            connect_to_peer(ip, port)

    def remove_service(self, zeroconf, type, name):
        print(f"[REMOVED] {name}")

    def update_service(self, zeroconf, type, name):
        pass  # Optional

def discover_peers():
    ServiceBrowser(zeroconf, SERVICE_TYPE, PeerListener())

# 3. Listen for incoming connections
def listen_for_peers(port):
    server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server.bind(('', port))
    server.listen()
    print(f"[LISTENING] on port {port}")
    while True:
        conn, addr = server.accept()
        ip, port = addr
        peer_id = f"{ip}:{port}"
        with peer_lock:
            if peer_id in peer_sockets:
                conn.close()
                continue
            peer_sockets[peer_id] = conn
        print(f"[NEW CONNECTION] from {peer_id}")
        threading.Thread(target=handle_peer, args=(conn, peer_id), daemon=True).start()

# 4. Handle messages from one peer
def handle_peer(conn, peer_id):
    try:
        while True:
            msg = conn.recv(1024)
            if not msg:
                break
            print(f"[{peer_id}] {msg.decode()}")
    except Exception as e:
        print(f"[ERROR] {peer_id}: {e}")
    finally:
        print(f"[DISCONNECTED] {peer_id}")
        conn.close()
        with peer_lock:
            peer_sockets.pop(peer_id, None)

# 5. Outbound connect
def connect_to_peer(ip, port):
    peer_id = f"{ip}:{port}"
    with peer_lock:
        if peer_id in peer_sockets:
            return
    try:
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.connect((ip, port))
        with peer_lock:
            peer_sockets[peer_id] = s
        threading.Thread(target=handle_peer, args=(s, peer_id), daemon=True).start()
        print(f"[CONNECTED] to {peer_id}")
    except Exception as e:
        print(f"[ERROR] Could not connect to {peer_id}: {e}")

# 6. Chat interface
def send_messages():
    print("[CHAT MODE] Type messages to send to all peers. Ctrl+C to exit.")
    try:
        while True:
            msg = input()
            with peer_lock:
                for peer_id, s in list(peer_sockets.items()):
                    try:
                        s.send(msg.encode())
                    except:
                        print(f"[ERROR] Sending to {peer_id}")
                        peer_sockets.pop(peer_id, None)
                        s.close()
    except KeyboardInterrupt:
        print("\n[EXITING CHAT MODE]")

# MAIN
if __name__ == "__main__":
    threading.Thread(target=announce_service, daemon=True).start()
    threading.Thread(target=discover_peers, daemon=True).start()
    threading.Thread(target=listen_for_peers, args=(PORT,), daemon=True).start()

    while True:
        cmd = input("\nEnter 'chat' to start messaging: ").strip()
        if cmd.lower() == 'chat':
            send_messages()
