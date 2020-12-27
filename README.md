# Python Pandas examples

These are some examples of using pandas.

They are in Jupyter Notebooks; see the next section for now I setup Jupyter Notebooks.

* ibm_stock: Showing read of a csv file downloaded from yahoo.finance.com on IBM closing
  stock price.  It shows simple plotting with matplotlib and slicing of the data.
* home_oil: We take home oil consumption from a csv and fixup the data so that we can graph it.
  We then graph it using separate and combined graphs.
* us_property_and_income_tax: look at data from data.gov regarding US property and income
  taxes by state.
* plotting_examples: We use matplotlib and plot sin/cos/tan waves in a simple way.


## Notes On Setting up Jupyter Notebooks

These examples utilize Jupyter Notebooks.

My recipe for setting up a Jupyter Notebook server involves doing these:

* Set up a machine (it could be a (very secure, protected, restricted, and monitored)
  VM in the cloud or a separate BM in your basement); in my case it's a BM running Ubuntu 20.
  NOTE: Jupyter Notebooks allow execution of arbitrary python code by design.  As
  such, I high recommend running only on a high secured and isolated local machine --
  whether that machine be your local laptop or machine residing locally on your well
  secured network.
* Setup a virtualenv to avoid cluttering your machine.
* Run Jupyter Notebook server on that machine; save the token presented to you.
* Setup an ssh tunnel to the Jupyter Notebook server at 127.0.0.1:8888
* Browse locally to https://127.0.0.1:8899
* Enter the token presented earlier
* Run the Jupyter Notebooks.

NOTE: You can also just run Jupyter Notebook on your local machine.  I choose
to run it on a separate machine to conserve battery on my local laptop.

Here are the steps in more detail:

```
connect (i.e., ssh) to the machine you want to run your Jupyter Notebooks on
mkdir mygit
cd mygit
git clone https://github.com/dperique/pandas_examples.git
cd pandas_examples
python3 -m venv venv
source venv/bin/activate
pip3 install --upgrade pip
pip3 install jupyter
jupyter notebook --no-browser
<capture the token which you will use later>
control-z (to halt the jupyter process in the background)
bg (to put the jupyter process in the background)
```

On your local machine, setup an ssh tunnel (in the example below, my Jupyter Notebook
server's IP address is 192.168.1.9:

```
ssh -f -L 8899:127.0.0.1:8888 192.168.1.9 sleep 999999
```

The above sets up an ssh tunnel from your local machine's 127.0.0.1:8899 to the
Jupyter Notebooks's 127.0.0.1:8888. I purposely used 8899 instead of 8888 in case you
are also running a Jupyter Notebook locally.

NOTE: if you don't want to use an ssh tunnel, and you're Jupyter Notebook server is well
secured, you can start it like this `jupyter notebook --no-browser --ip <ipAddress>` where
`<ipAdress>` is an IP address reachable from your local machine.

On your local machine:

* If you used an ssh tunnel, browse to `127.0.0.1:8899`, and enter the token you saved earlier.
* If you used an IP address, browse to `<ipAddress>:8888`

If you want to setup password access, do this (as described in the text presented to
you when you first login):

```
See https://jupyter-notebook.readthedocs.io/en/stable/public_server.html
Do this if you don't already have a ~/.jupyter/jupyter_notebook_config.py file
  jupyter notebook --generate-config
Create a password like this:
  python3
  from notebook.auth import passwd
  passwd()
  <Enter a strong password>
  <Enter a strong password>
  exit()
  Paste the output in ~/.jupyter/jupyter_notebook_config.py at:
    c.NotebookApp.password = <outputFromAbove>

When you login, you can enter your password instead of a token.
```
