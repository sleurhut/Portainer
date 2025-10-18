version: "3.9"

services:
  homeassistant:
    image: homeassistant/home-assistant:latest
    container_name: Home-Assistant
    mem_limit: 8g
    cpu_shares: 768
    security_opt:
      - no-new-privileges:true
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8123/"]
      interval: 1m
      retries: 5
    restart: unless-stopped
    network_mode: host
    volumes:
      - /volume1/docker/homeassistant:/config:rw
    environment:
      TZ: Europe/Amsterdam
    labels:
      - "com.centurylinklabs.watchtower.enable=true"
