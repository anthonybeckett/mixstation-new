# --- Build Stage ---
FROM node:20-alpine AS build
WORKDIR /app
COPY . .
RUN npm install && npm run build

# --- Serve Stage ---
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
