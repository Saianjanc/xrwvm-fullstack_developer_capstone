    # Use official slim Python image
    FROM python:3.12.0-slim-bookworm

    # Set environment variables
    ENV PYTHONBUFFERED=1
    ENV PYTHONWRITEBYTECODE=1
    ENV APP=/app

    # Set working directory
    WORKDIR $APP

    # Install dependencies
    COPY requirements.txt $APP
    RUN pip install --upgrade pip && pip install -r requirements.txt

    # Copy app source code
    COPY . $APP

    # Expose the app port
    EXPOSE 8000

    # Ensure the entrypoint script is executable
    RUN chmod +x /app/entrypoint.sh

    # Entrypoint to run migrations, collectstatic, etc.
    ENTRYPOINT ["/bin/bash", "/app/entrypoint.sh"]

    # Start Django using Gunicorn (adjust 'djangoproj' to match your project name)
    CMD ["gunicorn", "--bind", ":8000", "--workers", "3", "djangoproj.wsgi:application"]