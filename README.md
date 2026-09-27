# Configuration-Management-System-
Using libraries like os and JSON for this task.

import json
import os


def load_config(file_name="config.json"):
    try:
        with open(file_name, "r") as file:
            return json.load(file)
    except FileNotFoundError:
        print("Configuration file not found.")
        return {}
    except json.JSONDecodeError:
        print("Invalid JSON format.")
        return {}


def display_config(config):
    print("\n===== APPLICATION CONFIGURATION =====")

    for key, value in config.items():
        print(f"{key}: {value}")

    print("====================================")


def get_environment_variables():
    print("\n===== ENVIRONMENT VARIABLES =====")

    app_env = os.getenv("APP_ENV", "Development")
    admin_email = os.getenv("ADMIN_EMAIL", "Not Set")
    api_key = os.getenv("API_KEY", "Not Set")

    print(f"APP_ENV    : {app_env}")
    print(f"ADMIN_EMAIL: {admin_email}")
    print(f"API_KEY    : {api_key}")

    print("==================================")


def main():
    print("Python Configuration Management System")

    config = load_config()

    if config:
        display_config(config)

    get_environment_variables()


if __name__ == "__main__":
    main()
