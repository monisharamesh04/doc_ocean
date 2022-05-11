# VirtualEnv commands

Dipping my toes into the Python ocean was purely out of curiosity. When I was still a Ruby developer, everyone talked about Python. I just had to understand what the hype was all about. So on one gloomy need-for-motivation day, I decided to pick up Python as I challenged myself with Codewars Katas.

The first thing that got on my nerves was the differences in the Python versions 2.7 and 3.*. Every time I tried to look up something and implement it into my solutions, the terminal would shriek at me. It was a struggle. Thanks to the millions of ways Python allows you to do one thing, my already-in-love-with-ruby brain almost hated it. I couldn't understand the appropriate and optimized way to solve a problem. But I wasn't ready to give up just yet. I had to know why everyone loved Python so much (maybe I just wanted to prove my love for ruby, meh!). It wasn't until much later I understood why Python had such a huge fan following.

Although I like the fully-object-oriented ways of Ruby, I have come to appreciate Python's not-mainly-focused-on-web ways and its humungous community that help me find solutions to problems so easily. Now when I think of it, it also probably had to do with the number of problems setting up a virtual environment has solved for me! 😅

## Creating a virtual environment
  
: `python3.9 -m venv <my_venv or /path/to/my_venv>`

: Creates a virtual environment called my_venv which is placed under the current directory.
: You can also pass the path to where you'd want to create your virtual environment instead of just its name.

## Activating a virtual environment 

: `$ source <my_venv or /path/to/my_venv>/bin/activate`

: Once you run this you will notice each line in the terminal  begins with `<my_venv>`, which means your virtual environment is active.

## Deactivate a virtual environment

: `$ deactivate`

: After you run this you will notice the `<ny_venv>` on terminal disappears, meaning your virtual environment has been turnned off.

## Remove/Delete a virtual environment

: `$ rm -rf <my_venv or /path/to/my_venv>`

: Deleting it through the UI could taake a bit of time.

## Clear out an existing virtual environment

: `$ python3 -m venv --clear <my_venv or /path/to/my_venv>`

: Sometimes, instead of completely deleting a virtual environment, you may instead want to clear all the packages that were previously installed.

## Update Python version

: `$ python3 -m venv <my_venv or /path/to/my_venv> --upgrade`

: Now if you want to instruct the environment to use the existing Python version, that it is assumed that it was upgraded in-place, then simply provide the --upgrade flag

## Give virtual environment access to system site-packages

: `$ python3 -m venv <my_venv or /path/to/my_venv> --system-site-packages`

: The dependencies installed in a virtual environment are isolated from the corresponding packages installed in the actual system or in any other environment, but by using the `--system-site-packages` flag you can access them.

: !!!caution
  This is not a recommended approach, use it only if there is no other way.

## Skip pip installation

: `$ python3 -m venv <my_venv or /path/to/my_venv> --without-pip`

:  You can skip the installation and/or upgrade of pip (which is the default package manager) then you can do so by passing the --without-pip flag.

## Help with venv commands

: `$ python3 -m venv -h`

: The `-h` flag usually has answers to most questions.
