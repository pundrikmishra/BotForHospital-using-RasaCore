Note:-
    first install older version of python, I have latest python3.8.2 version, but in this rasa is not installing
    so I install python3.6 and then install rasa using command pip3 install rasa
    now rasa working fine.


sudo apt update
$sudo apt install python3-dev python3-pip
## pip3 install python3.6
## python3 -m venv ./venv        ## Create a new virtual environment by choosing a Python interpreter and making a ./venv directory to hold it:
## source ./venv/bin/activate    ## Activate the virtual environment:
pip3 install rasa

rasa init
rasa train nlu
rasa test nlu
rasa shell nlu


rasa train
rasa run actions & rasa shell
rasa train --agumentation 20
/stop   ## To stop bot
rasa run actions & rasa shell -m models --endpoints endpoints.yml

Tracker:- tracker keeps track what happens at each dialog state
Dispatcher:- dispatcher send response back to the user
Custom Action:- Custom action run on different server then the models,
                Rasa will call an endpoint you can specify, when a custom action is predicted.
                This endpoint should be a webserver that reacts to this call, runs the code and optionally
                returns information to modify the dialogue state.
                To specify, your action server use the endpoints.yml:
                        action_endpoint:
                          url: "http://localhost:5055/webhook"
                And pass it to the scripts using --endpoints endpoints.yml.

Data augmentation:- an amount of new stories to create from the existing stories. When you train a
                    model, by default Rasa Core will create longer stories by randomly gluing
                    together the ones in your stories files. You actually want to teach your policy
                    to ignore the dialogue history when it isn’t relevant and just respond with the
                    same action no matter what happened before.
                    By default augmentation is set to 20, resulting in a maximum of 200 augmented stories.



For more:
        https://www.youtube.com/watch?v=rlAQWbhwqLA&list=PL75e0qA87dlHQny7z43NduZHPo6qd-cRc
        https://rasa.com/docs/rasa/user-guide/installation/
        https://info.rasa.com/masterclass-ebook
        https://github.com/RasaHQ/rasa-masterclass


Building from Source
    If you want to use the development version of Rasa Open Source, you can get it from GitHub:
    $ curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python
    $ git clone https://github.com/RasaHQ/rasa.git
    $ cd rasa
    $ poetry install

    Just give me everything!
    If you don’t mind the additional dependencies lying around, you can use this to install everything.
    You’ll first need to clone the repository and then run the following command to install all the packages:
    $ poetry install --extras full