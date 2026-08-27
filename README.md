# AlphaTide: a reinforcement learning workbench for markets

<div align="center">
<img align="center" src=https://github.com/example-org/AlphaTide/blob/main/figure/Logo.png width="25%"/> 

<div>&nbsp;</div>

[![Python 3.10](https://shields.io/badge/python-3.10-blue.svg)](https://www.python.org/downloads/)
[![Platform](https://img.shields.io/badge/platform-linux%20%7C%20windows%20%7C%20macos-lightgrey)](Platform)
[![License](https://img.shields.io/github/license/example-org/AlphaTide)](License)
[![Document](https://img.shields.io/badge/docs-latest-red)](https://alphatide.readthedocs.io/en/latest/)
[![GitHub stars](https://img.shields.io/github/stars/example-org/AlphaTide?color=orange)](https://github.com/example-org/AlphaTide/stargazers)

## :star: **Recent changes**   :alarm_clock: 

| Change | State |
|------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| Added three new agent families | :hammer: Feb 2025 |
| Added a second agent pair for order placement | :hammer: Oct 2024 |
| Refreshed the market-simulator front end | :hammer: Sep 2023 |
| Refreshed the dynamics modelling tool | :wrench: Jul 2023 |
| Automatic indicator screening | :hammer: tutorial published May 2023 |
| Published the python package | :whale: May 2023 |
| Published the website | :whale: live since April 2023 |
| Published the documentation | :speech_balloon: April 2023 |
| Hosted notebook version | :speech_balloon: March 2023 |
| Added two more market datasets | :compass: March 2023 |
| Support for a wider indicator set | :hammer: March 2023 |
| First tagged release | :octocat: March 2023 |

## Contents

- [AlphaTide: a reinforcement learning workbench for markets](#alphatide-a-reinforcement-learning-workbench-for-markets)
  - [Recent changes](#recent-changes)
  - [Contents](#contents)
  - [Architecture](#architecture)
  - [Setup](#setup)
  - [Worked notebooks](#worked-notebooks)
  - [Helper scripts](#helper-scripts)
  - [Sandbox](#sandbox)
  - [Market data](#market-data)
  - [Agent catalogue](#agent-catalogue)
  - [Plotting tools](#plotting-tools)

## Architecture
<div align="center">
<img align="center" src=https://github.com/example-org/AlphaTide/blob/main/figure/architecture.jpg width="97%"/>
</div>
<br>

The project is built from six parts: market snapshots at several granularities across asset classes; a data pipeline that cleans and aligns them; a family of simulators faithful enough for mainstream trading tasks; implementations of a dozen-plus learning agents; an evaluation suite organised around six axes and seventeen measures; and separate entry points for people arriving from different disciplines.

## Setup
Two paths, pick whichever suits the machine you have:
- Install on Linux/Windows/MacOS following the requirements file in the repository
- Run it from a container using the supplied docker recipe

## Worked notebooks

Each notebook pairs one agent with one market so you can see the whole loop end to end.

|  Agent  | Data |   Venue |                                                  Goal                                                 |                     Notebook                      |
| :---------: | :-----: | :-----: | :---------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------: |
| EIIE | index basket | US equities | Portfolio Management | [notebook](https://github.com/example-org/AlphaTide/blob/1.0.0/tutorial/EIIE.ipynb)|
| RapidScalp  |   BTC | Crypto | Intraday Trading | [notebook](https://github.com/example-org/AlphaTide/blob/1.0.0/tutorial/RapidScalp.ipynb) | 
| SARL | index basket | US equities | Portfolio Management | [notebook](https://github.com/example-org/AlphaTide/blob/1.0.0/tutorial/SARL.ipynb)| 
| PPO  |  mainland index  | Mainland equities | Portfolio Management | [notebook](https://github.com/example-org/AlphaTide/blob/1.0.0/tutorial/PPO.ipynb)|
| ETEO | BTC | Crypto | Order Execution | [notebook](https://github.com/example-org/AlphaTide/blob/1.0.0/tutorial/ETEO.ipynb)|
| Double DQN | BTC | Crypto | High Frequency Trading | [notebook](https://github.com/example-org/AlphaTide/blob/1.0.0/tutorial/DDQN.ipynb)|

A hosted version of the same notebooks also exists, so nothing has to be installed to follow along.

## Helper scripts
- Hyperparameter search
- Indicator construction
- Filling gaps in market series with a diffusion model
- Training against a wide technical-indicator set

## Sandbox
- A white paper describing the design
- The dynamics-modelling guide
- A hosted service offering three things:
  1. a training demo
  2. the dynamics tool
  3. a simulator endpoint

## Market data

| Dataset |                    Source                     |     Class      |           Span            | Fields | Notes |
|:-------:| :------------------------------------------------: | :-----------: | :--------------------------------------: | :------: | :---: |
| broad US index  | Yahoo finance wrapper |   US equities    |       2000-2022, daily        |  OHLCV   | bundled sheet |
| blue-chip index   | Yahoo finance wrapper |   US equities    |       2012-2021, daily        |  OHLCV   | bundled sheet |
| FX basket   |    Kaggle    |      FX       |     2000-2019, daily        |  OHLCV   | bundled sheet |
| crypto pair  |    Kaggle    |    Crypto     |       2013-2021, daily        |  OHLCV   | bundled sheet |
| mainland index  | Yahoo finance wrapper | Mainland equities |       2009-2021, daily        |  OHLCV   | bundled sheet |
| BTC order flow |                     exchange export                     |    Crypto     | 2021, one-minute bars |   LOB    | bundled sheet |
| futures strip |                     akshare                     |    Futures     | 2023, five-minute bars |   OHLCV    | bundled sheet |
| HK tech basket |                     akshare                     |    HK equities     | 1988-2023, daily |   OHLCV    | bundled sheet |


Dates follow YY/MM/DD.

OHLCV stands for open, high, low, close and volume; LOB is a limit order book snapshot.

Every dataset above can be pulled from a shared cloud folder, with a mirror on a Chinese host.

## Agent catalogue

Implemented agents, each with the paper it comes from:

[DeepScalper (Sun et al, CIKM 22)](https://arxiv.org/abs/2201.09058)

[OPD (Fang et al, AAAI 21)](https://ojs.aaai.org/index.php/AAAI/article/view/16083)

[DeepTrader (Wang et al, AAAI 21)](https://ojs.aaai.org/index.php/AAAI/article/view/16144) 

[SARL (Ye et al, AAAI 20)](https://arxiv.org/abs/2002.05780)

[ETEO (Lin et al, 20)](https://www.ijcai.org/Proceedings/2020/627)

[Investor-Imitator (Ding et al, KDD 18)](https://www.kdd.org/kdd2018/accepted-papers/view/investor-imitator-a-framework-for-trading-knowledge-extraction)

[EIIE (Jiang et al, 17)](https://arxiv.org/abs/1706.10059)

Plus the standard gym-style set, wired through a distributed RL runtime:
PPO · A2C · Rainbow · SAC · DDPG · DQN · PG · TD3

## Plotting tools