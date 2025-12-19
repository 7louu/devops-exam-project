# --- ÉTAPE 1: Build Stage (Compilation) ---
FROM gcc:11 AS build
WORKDIR /app
COPY . .
# Compilation du serveur
RUN gcc -o serveur serveur.c

# --- ÉTAPE 2: Final Stage (Image Légère) ---
FROM debian:bullseye-slim
WORKDIR /usr/local/bin
# Copie uniquement le binaire compilé
COPY --from=build /app/serveur .
# Port exposé
EXPOSE 5000
# Spécifiez la commande d'exécution
CMD ["./serveur"]