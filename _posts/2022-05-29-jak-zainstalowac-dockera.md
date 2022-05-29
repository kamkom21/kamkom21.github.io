---
title: Jak zainstalować dockera
date: 2022-05-28 12:15:00 -500
categories: [homelab,docker]
tags: [cloud,selfhosted]
---
# W tym poście dowiesz jak zainstalować dockera na systemach Ubuntu/Debian
## Dodawanie repozytorium oraz wymaganych paczek
Na początku aktualizujemy nasze repozytoria
```bash
sudo apt update
```
Następnie instalujemy wymagane pakiety
```bash
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```
## Dodawanie klucza GPG
Aby dodać klucze wymagane do dodania repo wykonujemy następujące komendy:
```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
A następnie 
```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
## Instalowanie dockera
Po dodaniu kluczy do repo wykonujemy poniższą komendę aby zaktualizować repo w apt:
```bash
sudo apt-get update
```
A następnie instalujemy wymagane pakiety
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
## Sprawdzenie poprawności działania
Aby uruchomić jakikolwiek kontener dockerowy w celu sprawdzenia poprawności działania wykonaj poniższą komendę:
```bash
sudo docker run hello-world
```
Jeśli nie ma błędów gratulację udało się