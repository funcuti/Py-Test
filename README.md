## Error search in Py file
python -m py_compile main.py








# Py-Test
Test Twilio credentials in isolation


import os
from dotenv import load_dotenv
from twilio.rest import Client as TwilioClient

load_dotenv()

account_sid = os.environ.get("TWILIO_ACCOUNT_SID")
auth_token = os.environ.get("TWILIO_AUTH_TOKEN")
whatsapp_number = os.environ.get("TWILIO_WHATSAPP_NUMBER")

print(f"SID: {account_sid}")
print(f"Token: {auth_token}")
print(f"Number: {whatsapp_number}")
print(f"SID starts with AC: {str(account_sid).startswith('AC')}")
print(f"SID length: {len(str(account_sid))}")
print(f"Token length: {len(str(auth_token))}")

try:
    client = TwilioClient(account_sid, auth_token)
    # Try fetching account info — simplest possible API call
    account = client.api.accounts(account_sid).fetch()
    print(f"\nSuccess! Account status: {account.status}")
except Exception as e:
    print(f"\nError: {e}")

