# RB_salarycap_EPA
Runnings Backs in the NFL - Which Team Gets Best Bang for Buck? Scraping Spotrac and using nfl_data_py to find out.

Over the past summer, many have debated the value of running backs (RBs) in the NFL. Two sides persist in this case: the teams (who wish to get the most on-field production out of their RBs for the least money) and the players (who wish to earn the most money possible during their careers). As a fan, I'm interested in this debate as I believe these RBs should be given as much money as possible during their careers; however, I recognize there is a competitive advantage to ensuring that teams get good production out of their RBs while spending little money on the position. In an ideal world, teams would pay their RBs well, and RBs would produce on the field.

So, how do we determine which teams are getting the best production out of their RBs for the least amount of money, relative to their team and the league, during a given year? Well there are two keys variables we can look at: the percentage of a team’s salary cap going to the RBs (i.e., salary cap percentage) and how many points an RB contributes to the team each play they touch the ball (i.e., EPA or Expected Points Added).

To access these variables, I pulled data from two sources: Spotrac (for contract data) and nfl-data-py (for player EPA data).

I started by scraping the salary cap tables from each NFL team from 2020-2023. I chose to start at 2020 because the salary structures changed with the 2020 collective bargaining agreement, and have remained in place since. You can view Sections 1 to 3 to view the preparation and processing steps needed to return data frames containing the salary data for individual RBs and the total salary data given to RBs by each team from 2020-2023.

Next, I pulled EPA data from the nfl-data-py library. You can find the preparation and processing steps for this EPA data in Section 4, with the end result being a dataset with individual RB EPA for each year, and the sum of a team’s RB EPA for each year. This dataset was then merged with the RB salary data set, which is then used in analysis.

Now that I have my final dataset, I began the analysis and data visualization in Section 5. Heat maps were used to identify the teams that spent the most on RBs, and dedicated the greatest percentage of their respective salary caps to RBs. Scatter plots were used to visualize the relationship between receiving and rushing production from each team’s RBs, as well as their respective salary cap percentage dedicated to the position. Using these scatter pots, we can best identify which teams truly got the “best bang for their buck”. Section 6 is used to summarize the results.

Visiualizations that do not appear in github preview of RB_salarycap_EPA.ipynb:
![newplot](https://github.com/evmorg/RB_salarycap_EPA/assets/29820217/4f6899f9-68e3-498e-a1e5-7bd1ae086c0c)
![newplot(1)](https://github.com/evmorg/RB_salarycap_EPA/assets/29820217/67b358e5-5736-47c6-9031-ced6e1789d66)

Additional visualizations found in RB_salarycap_EPA.ipynb:
!![Untitled1](https://github.com/evmorg/RB_salarycap_EPA/assets/29820217/621c35e7-eef5-4e57-a39b-0f8de9de104d)
[Untitled](https://github.com/evmorg/RB_salarycap_EPA/assets/29820217/a19b686c-e606-4392-8a60-524444feb44d)
![Untitled3](https://github.com/evmorg/RB_salarycap_EPA/assets/29820217/fa0c77c2-4d74-45aa-8175-c1963a2792c5)

Modules, Libraries, etc. used:
- web-scraping:
  - from urllib.request import urlopen
  - from bs4 import BeautifulSoup

- data wrangling:
  - import pandas as pd
  - import numpy as np
  - import re
  - from functools import reduce

- nfl data:
  - %pip install nfl-data-py
  - import nfl_data_py as nfl

- data viz:
  - import plotly.express as px
  - import seaborn as sns
  - from matplotlib import pyplot as plt
  - import os
  - import urllib.request
  - from matplotlib.offsetbox import AnnotationBbox, OffsetImage
