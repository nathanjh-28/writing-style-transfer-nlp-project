# Writing Style Transfer Project
Research Project focused on Writing Style Transfer

### Neutralize Text Pipeline
This project was created and implemented using Google Colab with a T4 GPU.

The Jupyter Notebook titled **Neutralize-Text-Pipeline** will read a text file in your google drive, and chunk it in to paragraph chunks with the author associated.  The text files I used are in the data folder.  

Once you have the chunks in python format, copy and paste in to a Custom GPT, [Neutralize Text Writing Style](https://chatgpt.com/g/g-6894b4229dc88191823a53602b992001-neutralize-text-writing-style), for converting the stylized text in to a neutral text.  

Once you have your new python formatted neutral stylized texts, sync it up with your original texts (ChatGPT randomly decides to truncate the original text).

Also in the data folder are my converted neutralized texts.

Finally, convert to Hugging Face Dataset and save to Google Drive.

### Style Imitation Notebook

The next Jupyter notebook, Style-imititation-notebook will pull the hugging face dataset from google drive, format, tokenize, and ready the model for fine tuning.  Train and Save the model.  If you are using a few hundred chunks it should only take a few minutes.  Run test cases using the evaluation metric functions.  For convenience I included the hugging face datasets I created in the folder hugging-face-datasets.