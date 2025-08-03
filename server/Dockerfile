FROM python:3.12.0-slim-bookworm

ENV PYTHONBUFFERED 1
ENV PYTHONWRITEBYTECODE 1
ENV APP=/app

WORKDIR $APP

# Install dependencies
COPY requirements.txt $APP
RUN pip install --upgrade pip && pip install -r requirements.txt

# Copy app source
COPY . $APP

# Expose the port your app runs on
EXPOSE 8000

# Ensure entrypoint is executable
RUN chmod +x /app/entrypoint.sh

# Run migrations and static file collection before app starts
ENTRYPOINT ["/bin/bash", "/app/entrypoint.sh"]

# Gunicorn to serve Django app
CMD ["gunicorn", "--bind", ":8000", "--workers", "3", "djangoproj]()