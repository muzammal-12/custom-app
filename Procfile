redis: redis-server
web: bench serve --port 8000
socketio: node apps/frappe/socketio.js --redis-url redis://127.0.0.1:6379
watch: bench watch
schedule: bench schedule
worker: bench worker --queue default
