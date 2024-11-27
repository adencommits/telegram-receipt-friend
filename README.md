# Telegram Receipt Processing Bot

## Overview

The **Telegram Receipt Processor Bot** is a Python-based tool that leverages the Telegram Bot API, OpenAI, and Google Sheets API to automate receipt processing. Users can interact with the bot to capture receipts, categorize expenses, and update data directly into a Google Sheets spreadsheet. The bot allows users to upload a receipt, categorize it, extract relevant details using OpenAI's API, and either confirm or correct the extracted data. This data is then stored in Google Sheets for tracking and analysis.

---

## Features

- **User Authentication**: The bot ensures only authenticated users can access the receipt processing features.
- **Receipt Categorization**: Users can select a category for their receipts, such as food, travel, groceries, etc.
- **Receipt Photo Upload**: Users can upload a photo of their receipt for processing.
- **Data Extraction**: The bot uses OpenAI's API to extract relevant information (store name, total price, taxes, and date) from the receipt image.
- **Google Sheets Integration**: The bot appends extracted data to a Google Sheet, allowing easy tracking and management.
- **Data Correction**: Users can review and correct extracted data if necessary.
- **Real-Time Interaction**: The bot engages in a conversation flow to guide the user through each step of the process.

---

## Requirements

1. **Python 3.x**  
   Ensure you have Python installed on your system.

2. **Telegram Bot Token**  
   Replace `TOKEN` in the `telegram_tool.py` with your bot's token, which can be obtained from [BotFather](https://core.telegram.org/bots#botfather) on Telegram.

3. **Google API Credentials**  
   You need to create and download a credentials file from Google Cloud for accessing Google Sheets and Drive APIs. Save it as `credentials.json` and place it in the project directory.

4. **OpenAI API Key**  
   You will need an OpenAI API key to process receipt images. Replace `OPENAI_API_KEY` in `telegram_tool.py` with your key.

---

## Setup

### 1. Install Dependencies

Install the necessary Python libraries using `pip`:

```bash
pip install telebot requests google-auth google-auth-oauthlib google-api-python-client
```

### 2. Google API Setup

- Create a Google Cloud project and enable the Google Sheets API and Google Drive API.
- Download the credentials file from Google Cloud Console and name it `credentials.json`. 
- Place `credentials.json` in the project directory.

### 3. Obtain OpenAI API Key

- Create an OpenAI account and obtain an API key.
- Replace the `OPENAI_API_KEY` variable in `telegram_tool.py` with your API key.

### 4. Set Up Google Sheets

- Create a Google Sheet and get the `SPREADSHEET_ID` from the URL (it’s the long string between `/d/` and `/edit`).
- Set the sheet name to "Sheet1" and define the range as `Sheet1!A:G`.

---

## Usage

1. **Start the Bot**:  
   Open Telegram and start a conversation with your bot. Send `/start` to initiate the welcome message.

2. **Authenticate**:  
   The bot will prompt for a password. Enter the correct password (default is `luna`) to proceed.

3. **Category Selection**:  
   After authentication, select a category for the receipt (e.g., Food, Travel, Groceries, etc.).

4. **Upload Receipt**:  
   Upload an image of the receipt. The bot will process the image and extract relevant data like store name, total price, taxes, and date.

5. **Data Review and Correction**:  
   The bot will show the extracted data. If there are any mistakes, you can correct individual fields (Store Name, Total Price, GST, HST, PST, Date).

6. **Data Submission**:  
   Once the data is correct, the bot will append it to the Google Sheet.

---

## Code Overview

### 1. **telegram_tool.py**

The core of the bot, which handles:

- Authentication and interaction with the Google Sheets API.
- Handling Telegram messages, including user authentication, category selection, and receipt processing.
- Image processing using OpenAI’s API for extracting receipt information.
- Integration with Google Sheets for storing receipt data.
- A flow for users to correct any errors in extracted data.

### 2. **google_auth_oauthlib & Google Sheets API**

- The bot uses `google-auth` and `google-auth-oauthlib` to authenticate and authorize Google Sheets API access.
- The data is appended to the sheet using `googleapiclient.discovery` for accessing Google Sheets.

---

## Security

- **Sensitive Information**: Ensure that `credentials.json` and your OpenAI API key are kept secure and not exposed in public repositories.
- **Password**: The bot requires a password for initial authentication. The default password is `luna`, but it can be changed for added security.

---

## Troubleshooting

- **Error in Processing Image**: If the bot fails to extract data from the image, ensure the receipt is clear and legible. Try re-uploading a better-quality image.
- **Google API Authorization Errors**: Ensure that `credentials.json` is correctly configured and the Google API client has the necessary permissions for your Google Sheets.

---

## Contributing

Feel free to fork this repository and submit pull requests. If you encounter any bugs or issues, please open an issue on the repository’s issue tracker.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

### Notes

- Remember to replace the placeholders (`TOKEN`, `OPENAI_API_KEY`, `SPREADSHEET_ID`) in the script with your actual credentials and IDs.
- For a smooth experience, ensure your bot's Telegram token is active, and the Google Sheets and OpenAI credentials are correctly set up.

