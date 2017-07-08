# Deep Proverbs

This repository holds the code for training a character level RNN twitter bot.  If you're interested in learning
more about character level models checkout Andrej Karpathy's great
<a href=http://karpathy.github.io/2015/05/21/rnn-effectiveness/>blog post</a> on the subject.  We implement a slightly
different model here based on the architecture in this <a href=https://arxiv.org/pdf/1308.0850.pdf>paper</a>
by Alex Graves.  This model differs from that paper in a few ways, most noteably that only four layers were used instead
of 7 and dropout was applied at each layer. This project relies on TensorFlow, Keras, numpy, tweepy, and enchant so if
you want to run it make sure that you have those libraries installed.  Docker image coming soon : ).

# Running the project.
This project takes in raw text files and trains a character level model.  To start I would recommend running my
clean_text.py script to remove unnecessary characters and numbers by putting the following command in the shell:

`python clean_text.py --path /path/to/file/ --files file_name_1 file_name_2`

Now if that worked you should have some new files called file_name_1_clean you can now use these to train a model by
running:

`python train_model.py --file_path /path/to/file/filename --model_name my_model --context_size 100 --n_hidden 650 \
--dropout .4  --epochs 40 --batch_size 128`

This will train a model with a 100 character context window, 650 units in each hidden layer, and 40% dropout for 40
epochs with a batch size of 128.  It will save of the model state every time it finishes an epoch.

Once you've trained a model you can start generating text by running:

`python generate_text.py --model_path /path/to/model/file --model_spec /path/to/model/spec --n_chars 100`

Enjoy!
