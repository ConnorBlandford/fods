# fods
Repository for Foundations of Data Science Course work and Code 

Every create a notebook with your continent code prep in 1 cell.



Darman:
- Upload a notebook with correlation stuff

Ji:
- 

Connor:
import os
import sys
import seaborn as sns
from statsforecast import StatsForecast
from statsforecast.models import Holt, ARIMA # Possible source of errors
from hierarchicalforecast.utils import aggregate
from hierarchicalforecast.methods import BottomUp, MinTrace
from hierarchicalforecast.core import HierarchicalReconciliation
from sklearn.metrics import mean_squared_error

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.backends.backend_pdf import PdfPages
import matplotlib.dates as mdates
from statsmodels.tsa.arima_model import ARIMA # Possible source of errors

import datetime as dt

import pycountry
import country_converter as coco

rn_con_col_names = ['Country','Code','Year','Other','Solar','Wind','Hydro']
rn_cap_col_names = ['Country','Code','Year','Wind','Hydro','Solar','Other']

rn_con = pd.read_csv('data/modern-renewable-energy-consumption.csv',
                     header=0,
                     names=rn_con_col_names)
rn_cap = pd.read_csv('data/modern-renewable-prod.csv',
                     header=0,
                     names=rn_cap_col_names)

rn_con = rn_con[rn_cap_col_names]
rn_cap = rn_cap[rn_cap_col_names]

rn_con['Continents'] = np.nan
rn_cap['Continents'] = np.nan

rn_con.info()
rn_cap.info()
