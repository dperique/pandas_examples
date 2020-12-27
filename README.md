# Python Pandas examples

Some examples of using pandas.

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

* Set up a machine (it could be a VM in the cloud or a separate BM in
  your basement); in my case it's a BM running Ubuntu 20.
* Run Jupyter Notebook server on that machine; save the token presented to you.
* Setup an ssh tunnel to the Jupyter Notebook server at 127.0.0.1:8899
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
pip3 install -r requirements.txt
pip3 install --upgrade pip
pip3 install jupyter
jupyter notebook
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
Jupyther Notebooks's 127.0.0.1:8888.

On your local machine, browse to 127.0.0.1:8899, and enter the token you saved earlier.
