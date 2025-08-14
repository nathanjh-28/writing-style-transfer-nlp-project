# Writing Style Transfer Project
Research Project focused on Writing Style Transfer

## Files and Folders
**data** folder contains the txt files and python formatted data files used to convert in to hugging face dataset.

**hugging-face-datasets** are the hugging face formatted datasets used for fine tuning if you want to skip creating one from an author's corpus.

**Colab Notebooks** are where the implementation of the project exists.  The first notebook Neutralize will take an author's text and process it with the last step as saving the Hugging Face Dataset to google drive.  The Style Imitation notebook will take the hugging face dataset and fine tune GPT2-Medium to generate stylized text.  At the end it will run evaluation over a list of input and output strings.

**result-snippets.txt** The results can be non deterministic therefore I copied and pasted some of the more noteworthy results in to this file.  Some of the snippets include the evaluation metrics.

**Documents** These are the PDF documents for submission requirements with the project.

## Usage

### Neutralize Text Pipeline
This project was created and implemented using Google Colab with a T4 GPU.  You can view it on Google Colab [here](https://colab.research.google.com/drive/1eZqYlT0aShOmAzMXZsXjOp3Mh14C5SV1?usp=sharing)

The Jupyter Notebook titled **Neutralize-Text-Pipeline** will read a text file from google drive and chunk it in to paragraph chunks with the author associated.  The text files I used are in the data folder.  

Once you have the chunks in python format, copy and paste in to a Custom GPT, [Neutralize Text Writing Style](https://chatgpt.com/g/g-6894b4229dc88191823a53602b992001-neutralize-text-writing-style), for converting the stylized text in to a neutral text.  

Once you have your new python formatted neutral stylized texts, sync it up with your original texts (ChatGPT randomly decides to truncate the original text).

Also in the data folder are my converted neutralized texts.

Finally, convert to Hugging Face Dataset and save to Google Drive.

### Style Imitation Notebook

You can view this notebook on Google Colab [here](https://colab.research.google.com/drive/16O0PhlF-b4O6cMsE2vGvjUWB4WLy2EHu?usp=sharing)

The next Jupyter notebook, Style-imititation-notebook pulls the hugging face dataset from google drive, format, tokenize, and readys the model for fine tuning.  Trains and Saves the model.  If you are using a few hundred chunks it should only take a few minutes.  Run test cases using the evaluation metrics function.  For convenience I included the hugging face datasets I created in the folder hugging-face-datasets.

Here are the test cases I used.

```Python
test_cases = [
    # excerpts from moby dick neutralized
    ("Manhattan is surrounded by docks, similar to how coral reefs surround islands. Business activity covers it like waves. The streets lead toward the water. At the southern tip is the Battery, where the pier is hit by ocean waves and cooled by sea breezes that were far from land not long ago. Many people are gathered there, watching the water.", "Herman Melville"),
    ("More people are walking straight toward the water, as if preparing to jump in. They do not stop near the buildings for shade. They want to get as close to the water as they can without entering it. Many people stand there, stretching for miles. They come from all directions and different parts of the city. Yet they all gather at the water. Is there something drawing them there, like a magnet attracts a compass needle?","Herman Melville"),
    ("If you are in an area with lakes, most paths eventually lead downhill to a pool of water. Even someone lost in thought will unknowingly walk toward water if it is nearby. If you are ever thirsty in a desert and traveling with a philosopher, try this as a method to find water. Thought and water are closely connected.","Herman Melville"),
    ("An artist wants to paint a peaceful and beautiful scene in the Saco valley. He includes trees, fields, animals, a cottage with smoke, and distant mountains. But the image only feels complete if the shepherd in the scene is looking at a stream. In the prairies during June, despite many flowers, something feels missing—there is no water. If Niagara Falls were only sand, people would not visit. A poor poet once had to decide whether to buy a needed coat or spend his money on a trip to the beach. Many healthy boys want to go to sea at some point. On your first sea trip, you may have felt something special when told the ship was out of sight of land. The Persians respected the sea, and the Greeks gave it a god. These reactions suggest something important. The story of Narcissus, who drowned while trying to reach his reflection, symbolizes how we are drawn to an unreachable idea of life, which we also see in bodies of water.","Herman Melville"),
    ("When I say I go to sea when I feel physically or mentally unwell, I do not mean I travel as a passenger. Passengers need money, and they often get sick and uncomfortable. I also do not go as a high-ranking officer or a cook. I avoid positions of responsibility and prefer not to work hard or take on duties. While I respect good cooking, I do not enjoy doing it myself. Ancient Egyptians preserved animals they cooked, such as ibises and hippopotamuses, which were later found as mummies.","Herman Melville"),
     
     # Simple Tests
    ("The sky is blue","Herman Melville"),
    ("I'm hungry","Herman Melville"),
    
    # excerpt from frankenstein neutralized
     ("Margaret, I believe I should achieve an important goal. I could have lived a life of comfort and wealth, but I chose to pursue recognition instead. I wish someone would confirm that I have made the right choice. My determination is strong, but my expectations change and I sometimes feel discouraged. I am preparing for a long and difficult journey that will require me to remain strong. I must encourage others and also maintain my own resolve when they are struggling.","Herman Melville"),
    # excerpt from Siddhartha neutralized
     ("After an hour without sleeping, the Brahman got up, walked back and forth, went outside, and saw the moon had risen. He looked into the room through the window and saw Siddhartha standing in the same place with his arms folded and moonlight on his lower legs. The father, feeling concerned, returned to bed.","Herman Melville"),
    # Sports paragraph on the dodgers
     ("Shohei Ohtani, a player for the Los Angeles Dodgers, hit his 40th home run of the season on Saturday in a game against the Toronto Blue Jays, giving the Dodgers a 3-0 lead. The Dodgers won the game 9-1. It was their first consecutive home wins since they defeated the Chicago White Sox in three games from July 1 to July 3. Ohtani’s home run traveled 417 feet to center field.","Herman Melville")
]
```