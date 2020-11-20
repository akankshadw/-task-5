{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 129,
   "metadata": {},
   "outputs": [],
   "source": [
    "#importing libraries\n",
    "\n",
    "import pandas as pd\n",
    "import numpy as np\n",
    "import matplotlib.pyplot as plt\n",
    "import seaborn as sns\n",
    "%matplotlib inline"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 130,
   "metadata": {},
   "outputs": [],
   "source": [
    "deliveries = pd.read_csv(\"deliveries.csv\")\n",
    "matches = pd.read_csv(\"matches.csv\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 131,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 179078 entries, 0 to 179077\n",
      "Data columns (total 21 columns):\n",
      " #   Column            Non-Null Count   Dtype \n",
      "---  ------            --------------   ----- \n",
      " 0   match_id          179078 non-null  int64 \n",
      " 1   inning            179078 non-null  int64 \n",
      " 2   batting_team      179078 non-null  object\n",
      " 3   bowling_team      179078 non-null  object\n",
      " 4   over              179078 non-null  int64 \n",
      " 5   ball              179078 non-null  int64 \n",
      " 6   batsman           179078 non-null  object\n",
      " 7   non_striker       179078 non-null  object\n",
      " 8   bowler            179078 non-null  object\n",
      " 9   is_super_over     179078 non-null  int64 \n",
      " 10  wide_runs         179078 non-null  int64 \n",
      " 11  bye_runs          179078 non-null  int64 \n",
      " 12  legbye_runs       179078 non-null  int64 \n",
      " 13  noball_runs       179078 non-null  int64 \n",
      " 14  penalty_runs      179078 non-null  int64 \n",
      " 15  batsman_runs      179078 non-null  int64 \n",
      " 16  extra_runs        179078 non-null  int64 \n",
      " 17  total_runs        179078 non-null  int64 \n",
      " 18  player_dismissed  8834 non-null    object\n",
      " 19  dismissal_kind    8834 non-null    object\n",
      " 20  fielder           6448 non-null    object\n",
      "dtypes: int64(13), object(8)\n",
      "memory usage: 28.7+ MB\n"
     ]
    }
   ],
   "source": [
    "deliveries.info()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 132,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 756 entries, 0 to 755\n",
      "Data columns (total 18 columns):\n",
      " #   Column           Non-Null Count  Dtype \n",
      "---  ------           --------------  ----- \n",
      " 0   id               756 non-null    int64 \n",
      " 1   season           756 non-null    int64 \n",
      " 2   city             749 non-null    object\n",
      " 3   date             756 non-null    object\n",
      " 4   team1            756 non-null    object\n",
      " 5   team2            756 non-null    object\n",
      " 6   toss_winner      756 non-null    object\n",
      " 7   toss_decision    756 non-null    object\n",
      " 8   result           756 non-null    object\n",
      " 9   dl_applied       756 non-null    int64 \n",
      " 10  winner           752 non-null    object\n",
      " 11  win_by_runs      756 non-null    int64 \n",
      " 12  win_by_wickets   756 non-null    int64 \n",
      " 13  player_of_match  752 non-null    object\n",
      " 14  venue            756 non-null    object\n",
      " 15  umpire1          754 non-null    object\n",
      " 16  umpire2          754 non-null    object\n",
      " 17  umpire3          119 non-null    object\n",
      "dtypes: int64(5), object(13)\n",
      "memory usage: 106.4+ KB\n"
     ]
    }
   ],
   "source": [
    "matches.info()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 133,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>id</th>\n",
       "      <th>season</th>\n",
       "      <th>city</th>\n",
       "      <th>date</th>\n",
       "      <th>team1</th>\n",
       "      <th>team2</th>\n",
       "      <th>toss_winner</th>\n",
       "      <th>toss_decision</th>\n",
       "      <th>result</th>\n",
       "      <th>dl_applied</th>\n",
       "      <th>winner</th>\n",
       "      <th>win_by_runs</th>\n",
       "      <th>win_by_wickets</th>\n",
       "      <th>player_of_match</th>\n",
       "      <th>venue</th>\n",
       "      <th>umpire1</th>\n",
       "      <th>umpire2</th>\n",
       "      <th>umpire3</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>1</td>\n",
       "      <td>2017</td>\n",
       "      <td>Hyderabad</td>\n",
       "      <td>2017-04-05</td>\n",
       "      <td>Sunrisers Hyderabad</td>\n",
       "      <td>Royal Challengers Bangalore</td>\n",
       "      <td>Royal Challengers Bangalore</td>\n",
       "      <td>field</td>\n",
       "      <td>normal</td>\n",
       "      <td>0</td>\n",
       "      <td>Sunrisers Hyderabad</td>\n",
       "      <td>35</td>\n",
       "      <td>0</td>\n",
       "      <td>Yuvraj Singh</td>\n",
       "      <td>Rajiv Gandhi International Stadium, Uppal</td>\n",
       "      <td>AY Dandekar</td>\n",
       "      <td>NJ Llong</td>\n",
       "      <td>NaN</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>2</td>\n",
       "      <td>2017</td>\n",
       "      <td>Pune</td>\n",
       "      <td>2017-04-06</td>\n",
       "      <td>Mumbai Indians</td>\n",
       "      <td>Rising Pune Supergiant</td>\n",
       "      <td>Rising Pune Supergiant</td>\n",
       "      <td>field</td>\n",
       "      <td>normal</td>\n",
       "      <td>0</td>\n",
       "      <td>Rising Pune Supergiant</td>\n",
       "      <td>0</td>\n",
       "      <td>7</td>\n",
       "      <td>SPD Smith</td>\n",
       "      <td>Maharashtra Cricket Association Stadium</td>\n",
       "      <td>A Nand Kishore</td>\n",
       "      <td>S Ravi</td>\n",
       "      <td>NaN</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>3</td>\n",
       "      <td>2017</td>\n",
       "      <td>Rajkot</td>\n",
       "      <td>2017-04-07</td>\n",
       "      <td>Gujarat Lions</td>\n",
       "      <td>Kolkata Knight Riders</td>\n",
       "      <td>Kolkata Knight Riders</td>\n",
       "      <td>field</td>\n",
       "      <td>normal</td>\n",
       "      <td>0</td>\n",
       "      <td>Kolkata Knight Riders</td>\n",
       "      <td>0</td>\n",
       "      <td>10</td>\n",
       "      <td>CA Lynn</td>\n",
       "      <td>Saurashtra Cricket Association Stadium</td>\n",
       "      <td>Nitin Menon</td>\n",
       "      <td>CK Nandan</td>\n",
       "      <td>NaN</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>4</td>\n",
       "      <td>2017</td>\n",
       "      <td>Indore</td>\n",
       "      <td>2017-04-08</td>\n",
       "      <td>Rising Pune Supergiant</td>\n",
       "      <td>Kings XI Punjab</td>\n",
       "      <td>Kings XI Punjab</td>\n",
       "      <td>field</td>\n",
       "      <td>normal</td>\n",
       "      <td>0</td>\n",
       "      <td>Kings XI Punjab</td>\n",
       "      <td>0</td>\n",
       "      <td>6</td>\n",
       "      <td>GJ Maxwell</td>\n",
       "      <td>Holkar Cricket Stadium</td>\n",
       "      <td>AK Chaudhary</td>\n",
       "      <td>C Shamshuddin</td>\n",
       "      <td>NaN</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>5</td>\n",
       "      <td>2017</td>\n",
       "      <td>Bangalore</td>\n",
       "      <td>2017-04-08</td>\n",
       "      <td>Royal Challengers Bangalore</td>\n",
       "      <td>Delhi Daredevils</td>\n",
       "      <td>Royal Challengers Bangalore</td>\n",
       "      <td>bat</td>\n",
       "      <td>normal</td>\n",
       "      <td>0</td>\n",
       "      <td>Royal Challengers Bangalore</td>\n",
       "      <td>15</td>\n",
       "      <td>0</td>\n",
       "      <td>KM Jadhav</td>\n",
       "      <td>M Chinnaswamy Stadium</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   id  season       city        date                        team1  \\\n",
       "0   1    2017  Hyderabad  2017-04-05          Sunrisers Hyderabad   \n",
       "1   2    2017       Pune  2017-04-06               Mumbai Indians   \n",
       "2   3    2017     Rajkot  2017-04-07                Gujarat Lions   \n",
       "3   4    2017     Indore  2017-04-08       Rising Pune Supergiant   \n",
       "4   5    2017  Bangalore  2017-04-08  Royal Challengers Bangalore   \n",
       "\n",
       "                         team2                  toss_winner toss_decision  \\\n",
       "0  Royal Challengers Bangalore  Royal Challengers Bangalore         field   \n",
       "1       Rising Pune Supergiant       Rising Pune Supergiant         field   \n",
       "2        Kolkata Knight Riders        Kolkata Knight Riders         field   \n",
       "3              Kings XI Punjab              Kings XI Punjab         field   \n",
       "4             Delhi Daredevils  Royal Challengers Bangalore           bat   \n",
       "\n",
       "   result  dl_applied                       winner  win_by_runs  \\\n",
       "0  normal           0          Sunrisers Hyderabad           35   \n",
       "1  normal           0       Rising Pune Supergiant            0   \n",
       "2  normal           0        Kolkata Knight Riders            0   \n",
       "3  normal           0              Kings XI Punjab            0   \n",
       "4  normal           0  Royal Challengers Bangalore           15   \n",
       "\n",
       "   win_by_wickets player_of_match                                      venue  \\\n",
       "0               0    Yuvraj Singh  Rajiv Gandhi International Stadium, Uppal   \n",
       "1               7       SPD Smith    Maharashtra Cricket Association Stadium   \n",
       "2              10         CA Lynn     Saurashtra Cricket Association Stadium   \n",
       "3               6      GJ Maxwell                     Holkar Cricket Stadium   \n",
       "4               0       KM Jadhav                      M Chinnaswamy Stadium   \n",
       "\n",
       "          umpire1        umpire2 umpire3  \n",
       "0     AY Dandekar       NJ Llong     NaN  \n",
       "1  A Nand Kishore         S Ravi     NaN  \n",
       "2     Nitin Menon      CK Nandan     NaN  \n",
       "3    AK Chaudhary  C Shamshuddin     NaN  \n",
       "4             NaN            NaN     NaN  "
      ]
     },
     "execution_count": 133,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "matches.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 134,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>match_id</th>\n",
       "      <th>inning</th>\n",
       "      <th>batting_team</th>\n",
       "      <th>bowling_team</th>\n",
       "      <th>over</th>\n",
       "      <th>ball</th>\n",
       "      <th>batsman</th>\n",
       "      <th>non_striker</th>\n",
       "      <th>bowler</th>\n",
       "      <th>is_super_over</th>\n",
       "      <th>...</th>\n",
       "      <th>bye_runs</th>\n",
       "      <th>legbye_runs</th>\n",
       "      <th>noball_runs</th>\n",
       "      <th>penalty_runs</th>\n",
       "      <th>batsman_runs</th>\n",
       "      <th>extra_runs</th>\n",
       "      <th>total_runs</th>\n",
       "      <th>player_dismissed</th>\n",
       "      <th>dismissal_kind</th>\n",
       "      <th>fielder</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>Sunrisers Hyderabad</td>\n",
       "      <td>Royal Challengers Bangalore</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>DA Warner</td>\n",
       "      <td>S Dhawan</td>\n",
       "      <td>TS Mills</td>\n",
       "      <td>0</td>\n",
       "      <td>...</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>Sunrisers Hyderabad</td>\n",
       "      <td>Royal Challengers Bangalore</td>\n",
       "      <td>1</td>\n",
       "      <td>2</td>\n",
       "      <td>DA Warner</td>\n",
       "      <td>S Dhawan</td>\n",
       "      <td>TS Mills</td>\n",
       "      <td>0</td>\n",
       "      <td>...</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>Sunrisers Hyderabad</td>\n",
       "      <td>Royal Challengers Bangalore</td>\n",
       "      <td>1</td>\n",
       "      <td>3</td>\n",
       "      <td>DA Warner</td>\n",
       "      <td>S Dhawan</td>\n",
       "      <td>TS Mills</td>\n",
       "      <td>0</td>\n",
       "      <td>...</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>4</td>\n",
       "      <td>0</td>\n",
       "      <td>4</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>Sunrisers Hyderabad</td>\n",
       "      <td>Royal Challengers Bangalore</td>\n",
       "      <td>1</td>\n",
       "      <td>4</td>\n",
       "      <td>DA Warner</td>\n",
       "      <td>S Dhawan</td>\n",
       "      <td>TS Mills</td>\n",
       "      <td>0</td>\n",
       "      <td>...</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>Sunrisers Hyderabad</td>\n",
       "      <td>Royal Challengers Bangalore</td>\n",
       "      <td>1</td>\n",
       "      <td>5</td>\n",
       "      <td>DA Warner</td>\n",
       "      <td>S Dhawan</td>\n",
       "      <td>TS Mills</td>\n",
       "      <td>0</td>\n",
       "      <td>...</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>2</td>\n",
       "      <td>2</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>5 rows × 21 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "   match_id  inning         batting_team                 bowling_team  over  \\\n",
       "0         1       1  Sunrisers Hyderabad  Royal Challengers Bangalore     1   \n",
       "1         1       1  Sunrisers Hyderabad  Royal Challengers Bangalore     1   \n",
       "2         1       1  Sunrisers Hyderabad  Royal Challengers Bangalore     1   \n",
       "3         1       1  Sunrisers Hyderabad  Royal Challengers Bangalore     1   \n",
       "4         1       1  Sunrisers Hyderabad  Royal Challengers Bangalore     1   \n",
       "\n",
       "   ball    batsman non_striker    bowler  is_super_over  ...  bye_runs  \\\n",
       "0     1  DA Warner    S Dhawan  TS Mills              0  ...         0   \n",
       "1     2  DA Warner    S Dhawan  TS Mills              0  ...         0   \n",
       "2     3  DA Warner    S Dhawan  TS Mills              0  ...         0   \n",
       "3     4  DA Warner    S Dhawan  TS Mills              0  ...         0   \n",
       "4     5  DA Warner    S Dhawan  TS Mills              0  ...         0   \n",
       "\n",
       "   legbye_runs  noball_runs  penalty_runs  batsman_runs  extra_runs  \\\n",
       "0            0            0             0             0           0   \n",
       "1            0            0             0             0           0   \n",
       "2            0            0             0             4           0   \n",
       "3            0            0             0             0           0   \n",
       "4            0            0             0             0           2   \n",
       "\n",
       "   total_runs  player_dismissed dismissal_kind fielder  \n",
       "0           0               NaN            NaN     NaN  \n",
       "1           0               NaN            NaN     NaN  \n",
       "2           4               NaN            NaN     NaN  \n",
       "3           0               NaN            NaN     NaN  \n",
       "4           2               NaN            NaN     NaN  \n",
       "\n",
       "[5 rows x 21 columns]"
      ]
     },
     "execution_count": 134,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "deliveries.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 135,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "(756, 18)"
      ]
     },
     "execution_count": 135,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "matches.shape"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 136,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Index(['id', 'season', 'city', 'date', 'team1', 'team2', 'toss_winner',\n",
       "       'toss_decision', 'result', 'dl_applied', 'winner', 'win_by_runs',\n",
       "       'win_by_wickets', 'player_of_match', 'venue', 'umpire1', 'umpire2',\n",
       "       'umpire3'],\n",
       "      dtype='object')"
      ]
     },
     "execution_count": 136,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "matches.columns"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 137,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "id                   0\n",
       "season               0\n",
       "city                 7\n",
       "date                 0\n",
       "team1                0\n",
       "team2                0\n",
       "toss_winner          0\n",
       "toss_decision        0\n",
       "result               0\n",
       "dl_applied           0\n",
       "winner               4\n",
       "win_by_runs          0\n",
       "win_by_wickets       0\n",
       "player_of_match      4\n",
       "venue                0\n",
       "umpire1              2\n",
       "umpire2              2\n",
       "umpire3            637\n",
       "dtype: int64"
      ]
     },
     "execution_count": 137,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "matches.isnull().sum()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 138,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>match_id</th>\n",
       "      <th>inning</th>\n",
       "      <th>over</th>\n",
       "      <th>ball</th>\n",
       "      <th>is_super_over</th>\n",
       "      <th>wide_runs</th>\n",
       "      <th>bye_runs</th>\n",
       "      <th>legbye_runs</th>\n",
       "      <th>noball_runs</th>\n",
       "      <th>penalty_runs</th>\n",
       "      <th>batsman_runs</th>\n",
       "      <th>extra_runs</th>\n",
       "      <th>total_runs</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>count</th>\n",
       "      <td>179078.000000</td>\n",
       "      <td>179078.000000</td>\n",
       "      <td>179078.000000</td>\n",
       "      <td>179078.000000</td>\n",
       "      <td>179078.000000</td>\n",
       "      <td>179078.000000</td>\n",
       "      <td>179078.000000</td>\n",
       "      <td>179078.000000</td>\n",
       "      <td>179078.000000</td>\n",
       "      <td>179078.000000</td>\n",
       "      <td>179078.000000</td>\n",
       "      <td>179078.000000</td>\n",
       "      <td>179078.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>mean</th>\n",
       "      <td>1802.252957</td>\n",
       "      <td>1.482952</td>\n",
       "      <td>10.162488</td>\n",
       "      <td>3.615587</td>\n",
       "      <td>0.000452</td>\n",
       "      <td>0.036721</td>\n",
       "      <td>0.004936</td>\n",
       "      <td>0.021136</td>\n",
       "      <td>0.004183</td>\n",
       "      <td>0.000056</td>\n",
       "      <td>1.246864</td>\n",
       "      <td>0.067032</td>\n",
       "      <td>1.313897</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>std</th>\n",
       "      <td>3472.322805</td>\n",
       "      <td>0.502074</td>\n",
       "      <td>5.677684</td>\n",
       "      <td>1.806966</td>\n",
       "      <td>0.021263</td>\n",
       "      <td>0.251161</td>\n",
       "      <td>0.116480</td>\n",
       "      <td>0.194908</td>\n",
       "      <td>0.070492</td>\n",
       "      <td>0.016709</td>\n",
       "      <td>1.608270</td>\n",
       "      <td>0.342553</td>\n",
       "      <td>1.605422</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>min</th>\n",
       "      <td>1.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>25%</th>\n",
       "      <td>190.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>5.000000</td>\n",
       "      <td>2.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>50%</th>\n",
       "      <td>379.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>10.000000</td>\n",
       "      <td>4.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>1.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>75%</th>\n",
       "      <td>567.000000</td>\n",
       "      <td>2.000000</td>\n",
       "      <td>15.000000</td>\n",
       "      <td>5.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>1.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>max</th>\n",
       "      <td>11415.000000</td>\n",
       "      <td>5.000000</td>\n",
       "      <td>20.000000</td>\n",
       "      <td>9.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>5.000000</td>\n",
       "      <td>4.000000</td>\n",
       "      <td>5.000000</td>\n",
       "      <td>5.000000</td>\n",
       "      <td>5.000000</td>\n",
       "      <td>7.000000</td>\n",
       "      <td>7.000000</td>\n",
       "      <td>10.000000</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "            match_id         inning           over           ball  \\\n",
       "count  179078.000000  179078.000000  179078.000000  179078.000000   \n",
       "mean     1802.252957       1.482952      10.162488       3.615587   \n",
       "std      3472.322805       0.502074       5.677684       1.806966   \n",
       "min         1.000000       1.000000       1.000000       1.000000   \n",
       "25%       190.000000       1.000000       5.000000       2.000000   \n",
       "50%       379.000000       1.000000      10.000000       4.000000   \n",
       "75%       567.000000       2.000000      15.000000       5.000000   \n",
       "max     11415.000000       5.000000      20.000000       9.000000   \n",
       "\n",
       "       is_super_over      wide_runs       bye_runs    legbye_runs  \\\n",
       "count  179078.000000  179078.000000  179078.000000  179078.000000   \n",
       "mean        0.000452       0.036721       0.004936       0.021136   \n",
       "std         0.021263       0.251161       0.116480       0.194908   \n",
       "min         0.000000       0.000000       0.000000       0.000000   \n",
       "25%         0.000000       0.000000       0.000000       0.000000   \n",
       "50%         0.000000       0.000000       0.000000       0.000000   \n",
       "75%         0.000000       0.000000       0.000000       0.000000   \n",
       "max         1.000000       5.000000       4.000000       5.000000   \n",
       "\n",
       "         noball_runs   penalty_runs   batsman_runs     extra_runs  \\\n",
       "count  179078.000000  179078.000000  179078.000000  179078.000000   \n",
       "mean        0.004183       0.000056       1.246864       0.067032   \n",
       "std         0.070492       0.016709       1.608270       0.342553   \n",
       "min         0.000000       0.000000       0.000000       0.000000   \n",
       "25%         0.000000       0.000000       0.000000       0.000000   \n",
       "50%         0.000000       0.000000       1.000000       0.000000   \n",
       "75%         0.000000       0.000000       1.000000       0.000000   \n",
       "max         5.000000       5.000000       7.000000       7.000000   \n",
       "\n",
       "          total_runs  \n",
       "count  179078.000000  \n",
       "mean        1.313897  \n",
       "std         1.605422  \n",
       "min         0.000000  \n",
       "25%         0.000000  \n",
       "50%         1.000000  \n",
       "75%         1.000000  \n",
       "max        10.000000  "
      ]
     },
     "execution_count": 138,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "deliveries.describe()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 139,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>id</th>\n",
       "      <th>season</th>\n",
       "      <th>dl_applied</th>\n",
       "      <th>win_by_runs</th>\n",
       "      <th>win_by_wickets</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>count</th>\n",
       "      <td>756.000000</td>\n",
       "      <td>756.000000</td>\n",
       "      <td>756.000000</td>\n",
       "      <td>756.000000</td>\n",
       "      <td>756.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>mean</th>\n",
       "      <td>1792.178571</td>\n",
       "      <td>2013.444444</td>\n",
       "      <td>0.025132</td>\n",
       "      <td>13.283069</td>\n",
       "      <td>3.350529</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>std</th>\n",
       "      <td>3464.478148</td>\n",
       "      <td>3.366895</td>\n",
       "      <td>0.156630</td>\n",
       "      <td>23.471144</td>\n",
       "      <td>3.387963</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>min</th>\n",
       "      <td>1.000000</td>\n",
       "      <td>2008.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>25%</th>\n",
       "      <td>189.750000</td>\n",
       "      <td>2011.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>50%</th>\n",
       "      <td>378.500000</td>\n",
       "      <td>2013.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>4.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>75%</th>\n",
       "      <td>567.250000</td>\n",
       "      <td>2016.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>19.000000</td>\n",
       "      <td>6.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>max</th>\n",
       "      <td>11415.000000</td>\n",
       "      <td>2019.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>146.000000</td>\n",
       "      <td>10.000000</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                 id       season  dl_applied  win_by_runs  win_by_wickets\n",
       "count    756.000000   756.000000  756.000000   756.000000      756.000000\n",
       "mean    1792.178571  2013.444444    0.025132    13.283069        3.350529\n",
       "std     3464.478148     3.366895    0.156630    23.471144        3.387963\n",
       "min        1.000000  2008.000000    0.000000     0.000000        0.000000\n",
       "25%      189.750000  2011.000000    0.000000     0.000000        0.000000\n",
       "50%      378.500000  2013.000000    0.000000     0.000000        4.000000\n",
       "75%      567.250000  2016.000000    0.000000    19.000000        6.000000\n",
       "max    11415.000000  2019.000000    1.000000   146.000000       10.000000"
      ]
     },
     "execution_count": 139,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "matches.describe()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 140,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "array([2017, 2008, 2009, 2010, 2011, 2012, 2013, 2014, 2015, 2016, 2018,\n",
       "       2019], dtype=int64)"
      ]
     },
     "execution_count": 140,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "matches['season'].unique()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 141,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0    737\n",
       "1     19\n",
       "Name: dl_applied, dtype: int64"
      ]
     },
     "execution_count": 141,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "matches['dl_applied'].value_counts()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 142,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "array(['Yuvraj Singh', 'SPD Smith', 'CA Lynn', 'GJ Maxwell', 'KM Jadhav',\n",
       "       'Rashid Khan', 'N Rana', 'AR Patel', 'SV Samson', 'JJ Bumrah',\n",
       "       'SP Narine', 'KA Pollard', 'AJ Tye', 'RV Uthappa', 'CJ Anderson',\n",
       "       'BA Stokes', 'NM Coulter-Nile', 'B Kumar', 'CH Gayle',\n",
       "       'KS Williamson', 'JC Buttler', 'SK Raina', 'MJ McClenaghan',\n",
       "       'MS Dhoni', 'HM Amla', 'G Gambhir', 'LH Ferguson', 'KH Pandya',\n",
       "       'Sandeep Sharma', 'DA Warner', 'RG Sharma', 'Mohammed Shami',\n",
       "       'RA Tripathi', 'RR Pant', 'JD Unadkat', 'LMP Simmons', 'DR Smith',\n",
       "       'S Dhawan', 'MM Sharma', 'SS Iyer', 'WP Saha', 'KK Nair',\n",
       "       'Mohammed Siraj', 'AT Rayudu', 'HV Patel', 'Washington Sundar',\n",
       "       'KV Sharma', 'BB McCullum', 'MEK Hussey', 'MF Maharoof',\n",
       "       'MV Boucher', 'DJ Hussey', 'SR Watson', 'V Sehwag', 'ML Hayden',\n",
       "       'YK Pathan', 'KC Sangakkara', 'JDP Oram', 'AC Gilchrist',\n",
       "       'SM Katich', 'ST Jayasuriya', 'GD McGrath', 'SE Marsh',\n",
       "       'SA Asnodkar', 'R Vinay Kumar', 'IK Pathan', 'SM Pollock',\n",
       "       'Sohail Tanvir', 'S Sreesanth', 'A Nehra', 'SC Ganguly',\n",
       "       'CRD Fernando', 'L Balaji', 'Shoaib Akhtar', 'A Mishra',\n",
       "       'DPMD Jayawardene', 'GC Smith', 'DJ Bravo', 'M Ntini',\n",
       "       'SP Goswami', 'A Kumble', 'KD Karthik', 'JA Morkel', 'P Kumar',\n",
       "       'Umar Gul', 'SR Tendulkar', 'R Dravid', 'DL Vettori', 'RP Singh',\n",
       "       'M Muralitharan', 'AB de Villiers', 'RS Bopara', 'PP Ojha',\n",
       "       'TM Dilshan', 'HH Gibbs', 'DP Nannes', 'JP Duminy', 'SB Jakati',\n",
       "       'JH Kallis', 'A Singh', 'S Badrinath', 'LRPL Taylor',\n",
       "       'Harbhajan Singh', 'R Bhatia', 'SK Warne', 'B Lee', 'BJ Hodge',\n",
       "       'LR Shukla', 'MK Pandey', 'AD Mathews', 'MK Tiwary', 'WPUJC Vaas',\n",
       "       'A Symonds', 'AA Jhunjhunwala', 'J Theron', 'AC Voges', 'NV Ojha',\n",
       "       'SL Malinga', 'M Vijay', 'KP Pietersen', 'PD Collingwood',\n",
       "       'MJ Lumb', 'TL Suman', 'RJ Harris', 'PP Chawla', 'Harmeet Singh',\n",
       "       'R Ashwin', 'R McLaren', 'M Kartik', 'DE Bollinger', 'S Anirudha',\n",
       "       'SK Trivedi', 'SB Wagh', 'PC Valthaty', 'MD Mishra', 'DW Steyn',\n",
       "       'S Sohal', 'MM Patel', 'V Kohli', 'I Sharma', 'J Botha',\n",
       "       'Iqbal Abdulla', 'P Parameswaran', 'R Sharma', 'MR Marsh',\n",
       "       'BA Bhatt', 'S Aravind', nan, 'JEC Franklin', 'RE Levi',\n",
       "       'AM Rahane', 'RA Jadeja', 'MN Samuels', 'M Morkel', 'F du Plessis',\n",
       "       'AD Mascarenhas', 'Shakib Al Hasan', 'JD Ryder', 'S Nadeem',\n",
       "       'KMDN Kulasekara', 'CL White', 'Mandeep Singh', 'P Negi',\n",
       "       'Azhar Mahmood', 'BW Hilfenhaus', 'A Chandila', 'UT Yadav',\n",
       "       'MS Bisla', 'M Vohra', 'GH Vihari', 'AJ Finch', 'JP Faulkner',\n",
       "       'MS Gony', 'DA Miller', 'DJG Sammy', 'MG Johnson', 'KK Cooper',\n",
       "       'PA Patel', 'AP Tare', 'LJ Wright', 'YS Chahal', 'PV Tambe',\n",
       "       'DJ Hooda', 'GJ Bailey', 'AD Russell', 'MA Agarwal', 'MA Starc',\n",
       "       'VR Aaron', 'TA Boult', 'EJG Morgan', 'HH Pandya', 'MC Henriques',\n",
       "       'Z Khan', 'Q de Kock', 'Mustafizur Rahman', 'SA Yadav', 'AB Dinda',\n",
       "       'CH Morris', 'CR Brathwaite', 'MP Stoinis', 'A Zampa',\n",
       "       'BCJ Cutting', 'KL Rahul', 'SW Billings', 'JJ Roy', 'B Stanlake',\n",
       "       'J Archer', 'AS Rajpoot', 'TG Southee', 'AS Yadav', 'M Ur Rahman',\n",
       "       'Ishan Kishan', 'Kuldeep Yadav', 'S Gopal', 'L Ngidi', 'P Shaw',\n",
       "       'J Bairstow', 'S Curran', 'A Joseph', 'K Rabada', 'H Gurney',\n",
       "       'DL Chahar', 'Imran Tahir', 'K Paul', 'K Ahmed', 'S Gill',\n",
       "       'S Hetmyer'], dtype=object)"
      ]
     },
     "execution_count": 142,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "matches['player_of_match'].unique()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 143,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "CH Gayle          21\n",
       "AB de Villiers    20\n",
       "DA Warner         17\n",
       "RG Sharma         17\n",
       "MS Dhoni          17\n",
       "                  ..\n",
       "MF Maharoof        1\n",
       "MJ Lumb            1\n",
       "LH Ferguson        1\n",
       "J Archer           1\n",
       "MN Samuels         1\n",
       "Name: player_of_match, Length: 226, dtype: int64"
      ]
     },
     "execution_count": 143,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "matches['player_of_match'].value_counts()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 144,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 864x360 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "#visualising the data\n",
    "\n",
    "top10 = matches.player_of_match.value_counts()[:10]\n",
    "fig, ax = plt.subplots(figsize = (12,5))\n",
    "ax.set_ylabel(\"Number of times won\")\n",
    "ax.set_xlabel(\"Number of player\")\n",
    "ax.set_title(\"Top 10 'player_of_match' winners\")\n",
    "sns.barplot(x = top10.index, y = top10)\n",
    "plt.show()\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 145,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "id                               44\n",
       "season                         2017\n",
       "city                          Delhi\n",
       "date                     2017-05-06\n",
       "team1                Mumbai Indians\n",
       "team2              Delhi Daredevils\n",
       "toss_winner        Delhi Daredevils\n",
       "toss_decision                 field\n",
       "result                       normal\n",
       "dl_applied                        0\n",
       "winner               Mumbai Indians\n",
       "win_by_runs                     146\n",
       "win_by_wickets                    0\n",
       "player_of_match         LMP Simmons\n",
       "venue              Feroz Shah Kotla\n",
       "umpire1                 Nitin Menon\n",
       "umpire2                   CK Nandan\n",
       "umpire3                         NaN\n",
       "Name: 43, dtype: object"
      ]
     },
     "execution_count": 145,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "matches.iloc[matches['win_by_runs'].idxmax()]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 146,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "id                                                      3\n",
       "season                                               2017\n",
       "city                                               Rajkot\n",
       "date                                           2017-04-07\n",
       "team1                                       Gujarat Lions\n",
       "team2                               Kolkata Knight Riders\n",
       "toss_winner                         Kolkata Knight Riders\n",
       "toss_decision                                       field\n",
       "result                                             normal\n",
       "dl_applied                                              0\n",
       "winner                              Kolkata Knight Riders\n",
       "win_by_runs                                             0\n",
       "win_by_wickets                                         10\n",
       "player_of_match                                   CA Lynn\n",
       "venue              Saurashtra Cricket Association Stadium\n",
       "umpire1                                       Nitin Menon\n",
       "umpire2                                         CK Nandan\n",
       "umpire3                                               NaN\n",
       "Name: 2, dtype: object"
      ]
     },
     "execution_count": 146,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "matches.iloc[matches['win_by_wickets'].idxmax()]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 147,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "iVBORw0KGgoAAAANSUhEUgAAAX4AAAEWCAYAAABhffzLAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4yLjIsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy+WH4yJAAAfEUlEQVR4nO3de7xVdZ3/8ddbLpaIcTswoCJWqJmTipRaVhqZd6GS1NRBo6h+M5M+sino4thYk2X1K7tYTGaUZZKXQKckYsIuOioU5gUVRREE4UAamJOm85k/vt9Ty8Pe5+zDOWsfDuv9fDz2Y6/1XWt9P9+19t6fvfZ3rb2WIgIzM6uOnXq7AWZm1lxO/GZmFePEb2ZWMU78ZmYV48RvZlYxTvxmZhXjxG8vIOnFkm6Q9EdJP+rt9hRJCkkv78X443Ib+jc57oWSrmxmzO2JpKckvbS327EjceLvAyQ9Imm9pEGFsndLWlxCuFOAUcDwiJhaQv1/JelISWvKjGF9X0TsGhEre7sdOxIn/r6jP3BuE+LsBTwQEc81IZaZ9QIn/r7jEuBDkobUmijptZLuyF00d0h6bb2KJL1C0mJJT0q6R9LJufyTwAXAqfnn9fQay14o6UeSrpS0RdJdkvaRNEvSBkmrJb2lMP85kpbneVdKem8uHwT8FBiTYz0laYykfpI+KumhvMxSSXsWmvBmSSskPSHpa5JUiPWuHOsJSQsk7ZXLJen/5/b9UdLvJR1QZ9sslvQZSbfneedJGlZn3prrlqfdLemkwvgASRslHZTHD5N0S34N7pR0ZGHevSXdnOtdCIzo4LUcIenGXM8fJP1K0k552hhJ10pqlfSwpA8UlnuNpFvzcuskfVXSwM62l6SXSPpurnOVpI8X4p0t6deSPp9fg4clHdfBtruhMP6gpLmF8dWFbfXXLj5Jx0u6N2+bxyR9qLDMiZKW5XW6RdKr6m23yosIP7bzB/AI8GbgOuBTuezdwOI8PAx4AjiL9Mvg9Dw+vEZdA4AHgY8CA4E3AVuAffP0C4ErO2jLhcCfgWNyrO8CDwMfy3W/B3i4MP8JwMsAAW8EngYm5GlHAmva1f8vwF3AvnmZA9vWAwjgRmAIMBZoBY7N06bk9XpFbtfHgVvytGOApXk55XlG11m/xcBjwAHAIODatu0BjMtt6N/Aun0YuLpQ72Tgrjy8O7AJOJ6083V0Hm/J028FvgjsDLwhvz41XxPgM8A38rYfALw+t2envM4X5Nf5pcBK4Ji83CHAYXlbjQOWA+d1tr3y6z0PGJyXewCYnqedDfwlvwf6Ae8H1gKq0e6XAk/mdo4GVgGPFaY9AexUeN1fnofXAa/Pw0ML23sCsAE4NMeeRvrc7Nzbn9/t8dHrDfCjgRfpb4n/AOCPQAsvTPxnAbe3W+ZW4Owadb0eeLztQ5XLrgIuzMMX1ksyhekLC+MnAU8B/fL44PxBHVJn+R8D5+bhI9k68d8PTK6zbABHFMbnAjPz8E/bElAe34mUiPcifbk9kBPdTvXWLS+3GLi4ML4/8GxOJuMoJP5O1m0MKWHvlsevAT6chz8CfK/dsgtyshoLPAcMKkz7Qb3XBPg3UiJ+ebvyQ4FH25XNAq6oU895wPV5uOb2ytvgGWD/Qtl7C+/Ds4EHC9N2ydvr7+rEXE1K2KcBs4Hbgf2Ac4D57V73tsT/aI65W7u6LgMuqvFeemMzP6t95eGunj4kIu4m7fHObDdpDGmPqWgVac+yvTHA6oj43wbmrWd9Yfh/gI0R8XxhHGBXAEnHSfrv3A3xJGkvt27XBbAn8FAH0x8vDD/dFoeU4L+cf+Y/CfyBtLe6e0T8F/BV4GvAekmzJe3WQYzVheFVpD3prdrc0bpFxFrgN8DblbrnjgO+X2jr1La25mWPIO35jgGeiIg/tWtDPZeQfun8LHc3tb039iJ1oxVjfJR04B6l7rkbJT0uaTPw74W219teI0i/Hortaf/e+evrExFP58Fdqe1m0pf/G/LwYtIvpzfm8VreTtrOq3J32OGF9T2/3fruSdqe1o4Tf9/zr6Sf0sUP21rSG79oLKnLor21wJ5t/bKdzNstknYmdZV8HhgVEUOAn5ASMqQ9ufZWk7pPumo18N6IGFJ4vDgibgGIiEsj4hDglcA+pC6leorHFMaSui82FmdoYN0A5gBnAlOBWyOibRuvJu3xF9s6KCIuJnVlDFXhDK7chpoiYktEnB8RLyX9+vqgpEk5xsPtYgyOiOPzopcB9wHjI2I30peCCvXW2l4b87Yovte6895pS/yvz8M300nij4g7ImIyMJL0C6vtuMBq4NPt1neXiLhqG9u2Q3Pi72Mi4kHgauADheKfAPtIeqek/pJOJXVR3FijituAPwEfzgccjyQljB+W0NyBpH7qVuC5fKDvLYXp64Hhkl5SKPsWcJGk8fkg46skDW8g1jeAWZJeCX89CDk1D79a0qGSBpDW/c/A8/Wr4kxJ+0vahdSVck3hF02j6wYpMU0gnY313UL5lcBJko5ROpj9IqVTW/eIiFXAEuCTkgZKOoL0+tSUD2i+XJKAzXm9nid1m2yW9BGl/2b0k3SApFfnRQfn+Z+StB+pP76tzprbK2+DucCnJQ1WOnj+wbw+2+Jm4CjgxRGxBvgVcCwwHPhdjXUdKOkMSS+JiL8U1hfgP4D35XZL0iBJJ0gavI1t26E58fdN/0Y68AhARGwCTgTOJx0k/DBwYkRsbL9gRDwLnEzqetgIfB34h4i4r6cbGRFbSF9Qc0kH694JzC9Mv490fGFl/nk+hnRQcy7wM9IH+3LgxQ3Euh74LPDD3HVxN2kdAXYjJYYnSF0Tm0h76vV8D/gOqdviRbzwS7ahdcvz/A/pV8HepAPzbeWrSQd7P0r64lhN2qNu+zy+k9RH/wfSL7zil0Z744Gfk46z3Ap8PSIW5yR9EnAQ6eD7RtKXatuX7IdynC2kbXN1oc6Ottc/k74MVgK/Jh1/+HYH7asrIh7I7f5VHt+c6/1NjS/aNmcBj+TX+H2kX1RExBLSL+Gv5nY/SDrmYDUowjdiMWuj9Ke4KyPiWz1U3wXAPhFxZk/UZ9YTmvrXc7MqUTr/fzppL9Vsu+GuHrMSSHoPqQvnpxHxy95uj1mRu3rMzCrGe/xmZhXTJ/r4R4wYEePGjevtZpiZ9SlLly7dGBEt7cv7ROIfN24cS5Ys6e1mmJn1KZJq/uvbXT1mZhXjxG9mVjFO/GZmFePEb2ZWMU78ZmYV48RvZlYxTvxmZhXjxG9mVjFO/GZmFdMn/rlrti1OuP6S0ur+z7d2dOdGs+2b9/jNzCrGid/MrGKc+M3MKsaJ38ysYnxw15rmnOuPLa3uK956U2l1m+1ovMdvZlYxTvxmZhXjrp4K++b3jimt7veetaC0us2se7zHb2ZWMU78ZmYV48RvZlYxTvxmZhVTWuKXtK+kZYXHZknnSRomaaGkFfl5aFltMDOzrZWW+CPi/og4KCIOAg4BngauB2YCiyJiPLAoj5uZWZM0q6tnEvBQRKwCJgNzcvkcYEqT2mBmZjQv8Z8GXJWHR0XEOoD8PLLWApJmSFoiaUlra2uTmmlmtuMrPfFLGgicDPyoK8tFxOyImBgRE1taWsppnJlZBTVjj/844LcRsT6Pr5c0GiA/b2hCG8zMLGtG4j+dv3XzAMwHpuXhacC8JrTBzMyyUhO/pF2Ao4HrCsUXA0dLWpGnXVxmG8zM7IVKvUhbRDwNDG9Xtol0lo+ZmfUC/3PXzKxinPjNzCrGid/MrGKc+M3MKsaJ38ysYpz4zcwqxonfzKxinPjNzCrGid/MrGKc+M3MKsaJ38ysYpz4zcwqxonfzKxinPjNzCrGid/MrGKc+M3MKsaJ38ysYpz4zcwqpux77g6RdI2k+yQtl3S4pGGSFkpakZ+HltkGMzN7obL3+L8M3BQR+wEHAsuBmcCiiBgPLMrjZmbWJKUlfkm7AW8ALgeIiGcj4klgMjAnzzYHmFJWG8zMbGv9S6z7pUArcIWkA4GlwLnAqIhYBxAR6ySNrLWwpBnADICxY8eW2Mzty4LLjy+l3mOm/6SUeu1vTrzm+6XUe+MpZ5RSb1d94PrVpdR76Vv3LKXernrkS4+XUu+48/6uZvn6L99aSrxR5x7e6TxldvX0ByYAl0XEwcCf6EK3TkTMjoiJETGxpaWlrDaamVVOmYl/DbAmIm7L49eQvgjWSxoNkJ83lNgGMzNrp7Sunoh4XNJqSftGxP3AJODe/JgGXJyf55XVBrMd2ZRrFpVS749PmVRKvV3106s3llLvcaeOKKXevqTMPn6Afwa+L2kgsBI4h/QrY66k6cCjwNSS22BmZgWlJv6IWAZMrDFp+9ilMDOroLL3+Htc62VXllJvy/vPLKVeM7PtjS/ZYGZWMX1uj7/ZHr30lFLqHfuBa0qp18ysM97jNzOrGCd+M7OKceI3M6sYJ34zs4px4jczqxgnfjOzinHiNzOrGCd+M7OKceI3M6sYJ34zs4px4jczqxgnfjOziuk08UuaKmlwHv64pOskTSi/aWZmVoZG9vg/ERFbJB0BHAPMAS4rt1lmZlaWRhL/8/n5BOCyiJgHDCyvSWZmVqZGEv9jkr4JvAP4iaSdG1wOSY9IukvSMklLctkwSQslrcjPQ7e9+WZm1lWNJPB3AAuAYyPiSWAY8C9diHFURBwUEW333p0JLIqI8cCiPG5mZk3SaeKPiKeBDcARueg5YEU3Yk4mHScgP0/pRl1mZtZFjZzV86/AR4BZuWgA0OgdzwP4maSlkmbkslERsQ4gP4/sWpPNzKw7Grnn7luBg4HfAkTE2rbTOxvwujz/SGChpPsabVj+opgBMHbs2EYXMzOzTjTSx/9sRARp7x1JgxqtPCLW5ucNwPXAa4D1kkbnukaTupFqLTs7IiZGxMSWlpZGQ5qZWScaSfxz81k9QyS9B/g58B+dLSRpUOGPX4OAtwB3A/OBaXm2acC8bWm4mZltm067eiLi85KOBjYD+wIXRMTCBuoeBVwvqS3ODyLiJkl3kL5MpgOPAlO3ufVmZtZljfTxkxN9I8m+uMxK4MAa5ZuASV2py8zMek4jZ/W8Lf/Z6o+SNkvaImlzMxpnZmY9r5E9/s8BJ0XE8rIbY2Zm5Wvk4O56J30zsx1H3T1+SW/Lg0skXQ38GHimbXpEXFdy28zMrAQddfWcVBh+mnQ6ZpsAnPjNzPqguok/Is5pZkPMzKw5GjmrZ46kIYXxoZK+XW6zzMysLI0c3H1VvhwzABHxBOnaPWZm1gc1kvh3Kt4sRdIwGvzjl5mZbX8aSeBfAG6RdA3poO47gH8vtVVmZlaaRq7V891828Q3AQLeFhH3lt4yMzMrRaeJX9L3IuIs4N4aZWZm1sc00sf/yuKIpH7AIeU0x8zMylY38UuaJWkL8KrCxdm2kG6c4mvom5n1UXUTf0R8JiIGA5dExG4RMTg/hkfErHrLmZnZ9q2Rg7uz8umc44EXFcp/WWbDzMysHI0c3H03cC6wB7AMOAy4lXSWj5mZ9TGNHNw9F3g1sCoijiL9a7e11FaZmVlpGkn8f46IPwNI2jki7iPde9fMzPqgRhL/mnyRth8DCyXNA9Y2GkBSP0m/k3RjHh8maWG+nePC4uUgzMysfJ0m/oh4a0Q8GREXAp8ALgemdCHGuUDxDl4zgUURMR5YlMfNzKxJGtnjb7sU86uALcAa4IAGl9sDOAH4VqF4MjAnD8+ha18iZmbWTY2c1XMRcDawEvjfXBw0dlbPl4APA4MLZaMiYh1ARKyTNLJO3BnADICxY8c2EMrMzBrRyNU53wG8LCKe7UrFkk4ENkTEUklHdrVhETEbmA0wceLE6OryZmZWWyOJ/25gCOlSDV3xOuBkSceT/vi1m6QrgfWSRue9/dHbUK+ZmXVDI338nwF+J2mBpPltj84WiohZEbFHRIwDTgP+KyLOBOYD0/Js0/B1f8zMmqqRPf45wGeBu/hbH393XAzMlTQdeBSY2gN1mplZgxpJ/Bsj4tLuBImIxcDiPLwJmNSd+szMbNs1kviXSvoMqYvmmbbCiPhtaa0yM7PSNJL4D87PhxXKGj2d08zMtjONXJb5qGY0xMzMmqOhf+6amdmOw4nfzKxiOrrn7tT8vHfzmmNmZmXraI+/7b661zajIWZm1hwdHdzdJOkXwN61/qkbESeX1ywzMytLR4n/BGAC8D3gC81pjpmZla1u4s9X4/xvSa+NiFZJg1NxPNW85pmZWU9r5KyeUZJ+R7pK572Slkpq6EYsZma2/Wkk8c8GPhgRe0XEWOD8XGZmZn1QI4l/UET8om0kX3BtUGktMjOzUjVyrZ6Vkj5BOsgLcCbwcHlNMjOzMjWyx/8uoAW4Lj9GAOeU2SgzMytPIxdpewL4QBPaYmZmTeBr9ZiZVYwTv5lZxZSW+CW9SNLtku6UdI+kT+byYZIWSlqRn4eW1QYzM9tap4lf0h6SrpfUKmm9pGsl7dFA3c8Ab4qIA4GDgGMlHQbMBBZFxHhgUR43M7MmaWSP/wrS/XZHA7sDN+SyDkXSdnmHAfkRwGRgTi6fA0zpYpvNzKwbGkn8LRFxRUQ8lx/fIZ3e2SlJ/SQtAzYACyPiNmBURKwDyM8j6yw7Q9ISSUtaW1sbWhkzM+tcI4l/o6QzcxLvJ+lMYFMjlUfE8xFxELAH8JquXOMnImZHxMSImNjS0tD3jJmZNaDRP3C9A3gcWAeckssaFhFPAouBY4H1kkYD5OcNXanLzMy6p9PEHxGPRsTJEdESESMjYkpErOpsOUktkobk4RcDbwbuIx0vmJZnmwbM2/bmm5lZV9X9566kCzpYLiLiok7qHg3MkdSP9AUzNyJulHQrMFfSdOBRYGpXG21mZtuuo0s2/KlG2SBgOjAc6DDxR8TvgYNrlG8CJnWhjWZm1oM6ugPXX2+3mO++dS7p4mw/xLdiNDPrszq8SJukYcAHgTNI59xPyBdtMzOzPqqjPv5LgLeR7rb1977XrpnZjqGjs3rOB8YAHwfWStqcH1skbW5O88zMrKd11MfvK3eame2AnNzNzCrGid/MrGKc+M3MKsaJ38ysYpz4zcwqxonfzKxinPjNzCrGid/MrGKc+M3MKsaJ38ysYpz4zcwqxonfzKxinPjNzCqmtMQvaU9Jv5C0XNI9ks7N5cMkLZS0Ij8PLasNZma2tTL3+J8Dzo+IVwCHAf8oaX9gJrAoIsYDi/K4mZk1SWmJPyLWRcRv8/AWYDmwOzCZdBtH8vOUstpgZmZba0ofv6RxwMHAbcCoiFgH6csBGFlnmRmSlkha0tra2oxmmplVQumJX9KuwLXAeRHR8C0bI2J2REyMiIktLS3lNdDMrGJKTfySBpCS/vcj4rpcvF7S6Dx9NLChzDaYmdkLlXlWj4DLgeUR8cXCpPnAtDw8DZhXVhvMzGxrdW+23gNeB5wF3CVpWS77KHAxMFfSdOBRYGqJbTAzs3ZKS/wR8WtAdSZPKiuumZl1zP/cNTOrGCd+M7OKceI3M6sYJ34zs4px4jczqxgnfjOzinHiNzOrGCd+M7OKceI3M6sYJ34zs4px4jczqxgnfjOzinHiNzOrGCd+M7OKceI3M6sYJ34zs4px4jczqxgnfjOziinzZuvflrRB0t2FsmGSFkpakZ+HlhXfzMxqK3OP/zvAse3KZgKLImI8sCiPm5lZE5WW+CPil8Af2hVPBubk4TnAlLLim5lZbc3u4x8VEesA8vPIJsc3M6u87fbgrqQZkpZIWtLa2trbzTEz22E0O/GvlzQaID9vqDdjRMyOiIkRMbGlpaVpDTQz29E1O/HPB6bl4WnAvCbHNzOrvDJP57wKuBXYV9IaSdOBi4GjJa0Ajs7jZmbWRP3LqjgiTq8zaVJZMc3MrHPb7cFdMzMrhxO/mVnFOPGbmVWME7+ZWcU48ZuZVYwTv5lZxTjxm5lVjBO/mVnFOPGbmVWME7+ZWcU48ZuZVYwTv5lZxTjxm5lVjBO/mVnFOPGbmVWME7+ZWcU48ZuZVYwTv5lZxTjxm5lVTK8kfknHSrpf0oOSZvZGG8zMqqrpiV9SP+BrwHHA/sDpkvZvdjvMzKqqN/b4XwM8GBErI+JZ4IfA5F5oh5lZJSkimhtQOgU4NiLencfPAg6NiH9qN98MYEYe3Re4fxvCjQA2dqO5jledeDvyujledePtFREt7Qv7d789XaYaZVt9+0TEbGB2twJJSyJiYnfqcLxqxNuR183xHK+93ujqWQPsWRjfA1jbC+0wM6uk3kj8dwDjJe0taSBwGjC/F9phZlZJTe/qiYjnJP0TsADoB3w7Iu4pKVy3uoocr1LxduR1czzHe4GmH9w1M7Pe5X/umplVjBO/mVnVRESfeZDOBvoFsBy4Bzg3lw8DFgIr8vPQwjKzgAdJ/wM4plB+OnAX8HvgJmBEyfFOzbHuAT7XE+sHDM/zPwV8tV1dh+T1exC4lNytV2K8TwOrgafKXDdgF+A/gftyPRc3YVveBNyZ6/kG0K/MeIU65wN3N2H9FpPer8vyY2TJ8QaS+qwfyK/j20t8vwwurNcy0rnwXyp5/Xo8t3QSr9PcslX8riTe3n4Ao4EJhRf0AdJlHz4HzMzlM4HP5uH9SR/YnYG9gYdIB5T7AxvaXpC8/IUlxhsOPAq05PnmAJN6IN4g4AjgfTXeDLcDh5P+N/FT4LiS4x2W66uX+HskFinxH1VIIL9qwrrtlp8FXAucVma8PP1twA+on/h7cv0WAxN7+LPXUbxPAp/KwztROzH26PYs1LsUeEOJ78+ycku9eA3llq3idzbD9vwA5gFHk/ZWRhc26P15eBYwqzD/AlIyHAC0AnuRPszfAGaUGO/VwM8L5WcBX+9uvMJ8Z7d7M4wG7iuMnw58s6x47abVTPxlxMrTvwy8p0nrNgC4ATi1zHjArsCvSYmgZuLv4XiL6STx93C81cCgZsUrTBufY2/167en4lFSbukg3jbllj7bxy9pHHAwcBswKiLWAeTnkXm23UkvdJs1wO4R8Rfg/aSfY2tJH7DLy4pH6m7ZT9I4Sf2BKbzwT2zbGq+e3XPs9u0oK16X9FQsSUOAk4BFZceTtIC0J7cFuKbkeBcBXwCebrBt3Y0HcIWkZZI+IanWv+t7JF5+zQAukvRbST+SNKqseO2cDlwdOUOWEa/E3FJPl3ML9NGDu5J2Jf3kPi8iNnc0a42ykDSA9OIcDIwh9Y/NKiteRDyR411N6pp4BHiuB+J1qR0lxmtYT8XKb/KrgEsjYmXZ8SLiGNIe2M7Am8qKJ+kg4OURcX2D8/fE+p0REX8PvD4/zioxXn/Sv/V/ExETgFuBz5cYr+g00numrh54/crKLTV1Nbe06XOJP2/Ya4HvR8R1uXi9pNF5+mjSnhnUvzzEQQAR8VD+9p8LvLbEeETEDRFxaEQcTvo5t6IH4tWzJsfeqh0lxWtID8eaDayIiC81KR4R8WfSAdeaV5PtoXiHA4dIeoTU3bOPpMUlxiMiHsvPW0jHFV5TYrxNpF8ybV9sPwImlLl+ed4Dgf4RsbSDeXoiXlm5pa5Gc0tRn0r8+Sfo5cDyiPhiYdJ8YFoenkbqL2srP03SzpL2JvXx3Q48Buwvqe2qdUeTjq6XFQ9JI/PzUOD/Ad/qgXg15Z+IWyQdluv8h1rL9FS8RvRkLEmfAl4CnFd2PEm7Fj6I/YHjSWeilBIvIi6LiDERMY50MO+BiDiyxPXrL2lEHh4AnAjcXeL6Bek4Sds6TQLuLStewel0sLffg/HKyi11NZJbttLZQYDt6UH6IATp51Pb6VnHk45sLyJ90y0ChhWW+Rjp7Jr7KZz9QTo6vjzXdQMwvOR4V5He4PdS46yQbsR7BPgD6TSvNcD+uXwi6QP8EPBVap/O2ZPxPpfH/zc/X1hGLNKvl8ivXVs97y5r3YBRpOtLtZ0u9xXSnmNp27IwfRz1z+rpqfUbRDrTpW39vkzt01V78r2yF/DLXNciYGzZ2xNYCezXw7ml3vqVlVvqxes0t7R/+JINZmYV06e6eszMrPuc+M3MKsaJ38ysYpz4zcwqxonfzKxinPit0iR9TNI9kn6fL1lwaG+3yaxsTb/1otn2QtLhpD8sTYiIZ/IfmQb2crPMSuc9fquy0cDGiHgGICI2RsRaSYdIulnSUkkLCv/cfY+kOyTdKelaSbvk8qmS7s7lv8xlL5J0haS7JP1O0lG5/GxJ10m6SdIKSZ/rpXW3CvMfuKyy8gWyfk26xv/PSRe6ugW4GZgcEa2STiXdUOddkoZHxKa87KeA9RHxFUl3AcdGxGOShkTEk5LOBw6IiHMk7Qf8DNiHdKGwC0gX8XqG9A/vIyJiNWZN4q4eq6yIeErSIaQrUh5FSvyfAg4AFqbLqdAPWJcXOSAn/CGka+YvyOW/Ab4jaS7QdrGtI0iXdyAi7pO0ipT4ARZFxB8BJN1LuoSBE781jRO/VVpEPE+6EcnivOf+j8A9ka502N53gCkRcaeks8kXGouI9+WDwicAy5QurdzRNe2fKQw/jz+H1mTu47fKkrSvpPGFooNIF9dqyQd+kTRA0ivz9MHAunwVyzMK9bwsIm6LiAtI93Tdk3QRsjPy9H2AsaRuHbNe5z0Nq7Jdga8o3RXqOdLdjGaQrvV/qaSXkD4jXyJdufITpLskrSLdYWlwrueS/AUi0hUV7yRduvkb+VfEc8DZ+cyhZq2bWV0+uGtmVjHu6jEzqxgnfjOzinHiNzOrGCd+M7OKceI3M6sYJ34zs4px4jczq5j/A/FMYEEyLPUvAAAAAElFTkSuQmCC\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "sns.countplot(x='season', data=matches)\n",
    "plt.xlabel(\"Season\")\n",
    "plt.ylabel(\"No of matches\")\n",
    "plt.title(\"No of matches played season wise\")\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 148,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0.5, 1.0, 'Toss winner')"
      ]
     },
     "execution_count": 148,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "toss = matches['toss_winner'] == matches['winner']\n",
    "toss.groupby(toss).size()\n",
    "sns.countplot(toss)\n",
    "plt.title(\"Toss winner\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 149,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 864x432 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "plt.figure(figsize = (12,6))\n",
    "matches = matches.winner.value_counts()\n",
    "sns.barplot(y = matches.index, x = matches)\n",
    "plt.xlabel(\"Number of wins\")\n",
    "plt.ylabel(\"Name of team\")\n",
    "plt.title(\"Most successful teams in IPL \")\n",
    "plt.show()\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "CONCLUSION - Most successful team in IPL is Mumbai Indians,followed by Chennai Super Kings and Kolkata Knight Riders\n",
    "             Factors contributing to team's win or loss majorly depends upon toss result.\n",
    "             Teams or players a company should endorse for its products are Mumbai Indians, Chennai Super Kings.\n",
    "             "
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.3"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
