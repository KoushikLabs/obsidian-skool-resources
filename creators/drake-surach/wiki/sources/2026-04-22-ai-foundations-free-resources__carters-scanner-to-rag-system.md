---
title: "Carter's Scanner to RAG System"
date: 2026-04-22
creator: drake-surach
course: AI Foundations Free Resources
source_url: https://aifoundations.io/resources/carters-scanner-to-rag-system
has_resource: true
type: source
concepts:
  - rag
  - workflow-automation
  - trading-bots
  - cloud-deployment
entities:
  - claude-code
  - n8n
---

# Carter's Scanner to RAG System

> Course: **AI Foundations Free Resources**

## Links
- Lesson: https://aifoundations.io/resources/carters-scanner-to-rag-system
- Creator: [[drake-surach-profile]]

## Cross-references
**Concepts:** [[rag]], [[workflow-automation]], [[trading-bots]], [[cloud-deployment]]
**Entities:** [[claude-code]], [[n8n]]

## External links
- [https://www.skool.com/ai-foundations](https://www.skool.com/ai-foundations) — `external`
- [https://skool.com/ai-foundations](https://skool.com/ai-foundations) — `external`
- [https://www.youtube.com/watch?v=EO_Me91xYdc](https://www.youtube.com/watch?v=EO_Me91xYdc) — `youtube.com`

## Files
- [`1768273144-16006313664077e7-Document_preprocessing_1_.json`](../../raw/ai-foundations-free-resources__carters-scanner-to-rag-system/1768273144-16006313664077e7-Document_preprocessing_1_.json) — direct.json, 16.2 KB
- [`1768273162-821316fa6ed6fa6f-Document_Chat_1_.json`](../../raw/ai-foundations-free-resources__carters-scanner-to-rag-system/1768273162-821316fa6ed6fa6f-Document_Chat_1_.json) — direct.json, 4.3 KB

## Page content

🔴 April Hackathon Live in Ai Foundations! ($350 cash prizes)
Learn more
Products
Resources
K
Koushik Raghavan
Back to Resources
PRODUCTIVITY
Carter's Scanner to RAG System
7 min read
Copy as Markdown
Be sure to watch the full video while following along, using this post to copy/paste the resources you need. Or copy the whole post and give it to Claude Code or another coding model to help you along the way.
Scroll all the way down to the resources to get the n8n workflows and copy/paste code examples! ⬇️
Here's the code I used. Keep in mind you'll also have to create your New and Sent folders in the source directory for your project, you'll also need to install the requirements.
config.py
python
Copy
# config.py
import os
# --- Configuration ---
# !! IMPORTANT !!
# Replace this with your actual webhook URL
WEBHOOK_URL = "YOUR_WEBHOOK_URL_HERE"
# Folders (relative to the script's location)
BASE_DIR = os.path.dirname(os.path.abspath(__file__))
NEW_FOLDER = os.path.join(BASE_DIR, "New")
SENT_FOLDER = os.path.join(BASE_DIR, "Sent")
# Time to wait before processing a file after detection (in seconds)
# This helps ensure the file is fully written before processing
PROCESSING_DELAY = 2
# --- End Configuration ---
# Basic validation
if WEBHOOK_URL == "YOUR_WEBHOOK_URL_HERE":
    print("-----------------------------------------------------")
    print(">>> Warning: WEBHOOK_URL in config.py is not set. <<<")
    print(">>> Please edit config.py and set your webhook URL. <<<")
    print("-----------------------------------------------------")
if not os.path.isdir(NEW_FOLDER):
    print(f"Warning: Directory not found: {NEW_FOLDER}")
    # Optionally create it: os.makedirs(NEW_FOLDER, exist_ok=True)
if not os.path.isdir(SENT_FOLDER):
    print(f"Warning: Directory not found: {SENT_FOLDER}")
    # Optionally create it: os.makedirs(SENT_FOLDER, exist_ok=True)
file_processor.py
python
Copy
import base64
import os
import time
import requests
import shutil
import mimetypes
import logging
from datetime import datetime
import config
# Setup basic logging
logging.basicConfig(level=logging.INFO, format='%(asctime)s - %(levelname)s - %(message)s')
class WebhookHandler:
    """Handles processing files, sending them to a webhook, and moving them."""
    def __init__(self, webhook_url, sent_folder):
        self.webhook_url = webhook_url
        self.sent_folder = sent_folder
    def _get_file_metadata(self, file_path):
        """Extracts metadata from a file."""
        try:
            stat_info = os.stat(file_path)
            mime_type, _ = mimetypes.guess_type(file_path)
            return {
                "filename": os.path.basename(file_path),
                "size_bytes": stat_info.st_size,
                "created_timestamp_utc": datetime.utcfromtimestamp(stat_info.st_ctime).isoformat() + 'Z',
                "modified_timestamp_utc": datetime.utcfromtimestamp(stat_info.st_mtime).isoformat() + 'Z',
                "mime_type": mime_type or "application/octet-stream"
            }
        except OSError as e:
            logging.error(f"Error getting metadata for {file_path}: {e}")
            return None
    def _encode_file_base64(self, file_path):
        """Reads a file and encodes its content to base64."""
        try:
            with open(file_path, "rb") as file_handle:
                return base64.b64encode(file_handle.read()).decode('utf-8')
        except IOError as e:
            logging.error(f"Error reading file {file_path} for encoding: {e}")
            return None
    def _send_to_webhook(self, data):
        """Sends data to the configured webhook once and logs timing."""
        filename = data.get('metadata', {}).get('filename', 'file')
        start_time = time.time()
        logging.info(f"Sending {filename} to webhook...")
        print(f"Processing for {filename}...")
        try:
            # Send the request with a 2-minute timeout
            response = requests.post(self.webhook_url, json=data, timeout=120)
            response.raise_for_status()  # Raise an exception for bad status codes
            # Check for specific success status in response body
            try:
                response_json = response.json()
                if response_json.get("status") == "success":
                    end_time = time.time()
                    duration = end_time - start_time
                    logging.info(f"Webhook received success status for {filename}. Duration: {duration:.2f}s")
                    print(f"Processed successfully in {duration:.2f}s")
                    return True, "Success status received."
                else:
                    status_detail = response_json.get("status", "N/A")
                    message = response_json.get("message", "No message provided.")
                    logging.warning(f"Webhook success status not found for {filename}. Status: {status_detail}, Message: {message}")
                    return False, f"Webhook did not return 'success' status. Status: {status_detail}, Message: {message}"
            except ValueError:  # Includes JSONDecodeError
                logging.error(f"Webhook response was not valid JSON for {filename}. Response: {response.text}")
                return False, "Webhook response not valid JSON."
        except requests.exceptions.Timeout:
            logging.error(f"Webhook request timed out after 120 seconds for {filename}.")
            print(f"Error: Webhook request timed out for {filename}.")
            return False, "Webhook request timed out after 120 seconds."
        except requests.exceptions.RequestException as e:
            logging.error(f"Error sending {filename} to webhook: {e}")
            print(f"Error sending {filename} to webhook: {e}")
            return False, f"Failed to send to webhook: {e}"
    def _move_file(self, source_path):
        """Moves the file to the sent folder, handling name conflicts with '(n)' suffix."""
        try:
            filename = os.path.basename(source_path)
            destination_path = os.path.join(self.sent_folder, filename)
            # Handle potential name conflicts in the destination
            counter = 1
            base, ext = os.path.splitext(filename)
            while os.path.exists(destination_path):
                # Generate new name with (n) suffix
                logging.warning(f"File {destination_path} already exists. Attempting to rename.")
                destination_path = os.path.join(self.sent_folder, f"{base} ({counter}){ext}")
                counter += 1
                if counter > 100: # Safety break to prevent infinite loops
                    logging.error(f"Could not find a unique name for {filename} in {self.sent_folder} after 100 attempts. Aborting move.")
                    return False
            # Move the file
            shutil.move(source_path, destination_path)
            # Use the final destination path in the log message
            logging.info(f"Successfully moved {os.path.basename(source_path)} to {destination_path}")
            return True
        except (OSError, shutil.Error) as e:
            logging.error(f"Error moving file {source_path} to {self.sent_folder}: {e}")
            return False
    def process_file(self, file_path):
        """Processes a single file: encode, get metadata, send, move."""
        logging.info(f"Processing file: {file_path}")
        # Brief delay to ensure file is fully written/released
        time.sleep(config.PROCESSING_DELAY)
        # Check if file still exists (it might have been moved/deleted quickly)
        if not os.path.exists(file_path):
            logging.warning(f"File {file_path} no longer exists. Skipping processing.")
            return
        metadata = self._get_file_metadata(file_path)
        encoded_content = self._encode_file_base64(file_path)
        if metadata and encoded_content:
            payload = {
                "metadata": metadata,
                "content_base64": encoded_content
           

_(truncated — see source URL for full content)_

## Notes

_Hand-editable. Preserved across re-runs._