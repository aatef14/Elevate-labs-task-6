FROM nginx:alpine

# Set default environment variable or change during runtime
ENV FOOTER_TEXT="By Mohammed Aatef, Elevate-Labs Intern"

# Copy static files
COPY . /usr/share/nginx/html/

# Create nginx config template
RUN mkdir -p /etc/nginx/templates && \
    echo 'server { \
    listen 80; \
    location / { \
        root /usr/share/nginx/html; \
        index index.html; \
        try_files $uri $uri/ /index.html; \
        sub_filter "%%FOOTER_TEXT%%" "${FOOTER_TEXT}"; \
        sub_filter_once off; \
        sub_filter_types *; \
    } \
}' > /etc/nginx/templates/default.conf.template

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
