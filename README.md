<div align="center" style="display: flex; align-items: center;">
  <a href="https://webtap.ai?utm_source=github" target="_blank">
    <picture>
      <source srcset="https://webtap.ai/images/webtap-logo-text-transparent-bg-with-shadow.png" media="(prefers-color-scheme: light)">
      <img alt="Webtap Logo" src="https://webtap.ai/images/webtap-logo-text-nobg.png" width="280" style="height: auto;">
    </picture>
  </a>
</div>

<p align="center">
  <a href="https://pypi.org/project/webtap/">
    <img src="https://img.shields.io/pypi/v/webtap" alt="PIP Version">
  </a>
  <a href="https://github.com/webtap-ai/webtap/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/webtap-ai/webtap" alt="MIT License">
  </a>
  <a href="https://github.com/webtap-ai/webtap/pulls">
    <img src="https://img.shields.io/badge/PRs-welcome-brightgreen" alt="Send PR">
  </a>
</p>

<h1 align="center">
  Try the beta for free on webtap.ai
</h1>

<p align="center">
  <br />
  <a href="https://webtap.ai" rel="dofollow">Test drive ready-to-go beta app</a>
<br />


# Webtap: A novel approch to AI-based web scraping

Webtap is a Python library that enables reliable, AI-driven web scraping. It leverages Large Language Models (LLMs) to orchestrate established scraping libraries, such as Apify, for efficient data extraction from the web.

## The problem with traditional AI-Based Web Scraping

Majority of modern websites implement tough anti-scraping measures to prevent automated data extraction: Captchas, IP blocking, and dynamic content are just a few examples. In addition to these challenges, websites are constantly evolving, with changes in layout, structure, and content. As a resultg eneric AI-based web scraping tools most of the times struggle to navigate these obstacles, leading to unreliable and inefficient data extraction.

## How Webtap solves this problem

Webtap relies on existing scraping libraries, such as Apify, which implement tailored solutions for specific websites to successfully extract data. Webtap uses Large Language Models (LLMs) to orchestrate these libraries, enabling intelligent navigation of the web and adaptation to dynamic content.

## Python example use case

The following code demonstrates how to use the TapManager to scrape data from Project Gutenberg using the atg_epctex_gutenberg_scraper tap. The goal is to search for books related to 'history', with a maximum of 15 items, in the Italian language, using the Apify Proxy.

```python

  tap_manager = TapManager()
  tap = tap_manager.get_tap( "atg_epctex_gutenberg_scraper" ) # Project Gutenberg: a collection of 70,000 free ebooks
  print(tap.get_retriever_and_run("Search for 'history', maximum 15 items, in Italian language, using Apify Proxy"))

  # The above print statement will output real time scraped data from project gutenberg in the following format:
  # {
  #   'retriever_result': ApifyRetrieverResult(can_fulfill=True, explanation='...', retriever=...),
  #   'data': '[{"author": "Albertazzi, Adolfo, 1865-1924", "title": "Novelle umoristiche by Adolfo Albertazzi", ...}]'
  # }

```

# Try it now on webtap.ai

Webtap is available as a beta on [webtap.ai](https://webtap.ai?utm_source=github). You can test drive the ready-to-go beta app for free. No need to install anything, just sign up and start scraping. [Get started now!](https://webtap.ai/signup)


# Use cases

 - Use one of the 40 supported Apify actors out of the box to scrape data from websites
 - Use the Universal Scraper to scrape any website with a generic LLM based scraper
 - Access yoyr own Apify actors with natural language queries
 - Write a tap for your own scraping needs using the Tap Generator (or manually)

## Current state and limitations

In its current state, Webtap python library currently only supports Apify as a scraping library. Some of the top 40 Apify actors are supported out of the box and can be used immediately. In addition a special Universal Scraper is available that is a generic LLM based scraper that can be used to scrape any website although not what with the same efficiency as a custom Apify actor.

## Roadmap

 - We plan to add support for the remaining public Apify actors (1500 in total)
 - We plan to add support for other scraping libraries such as Scrapy
 - We plan to improve the Universal Scraper to be more efficient and reliable

# Installation

## Requirements

Webtap has been developed and tested with Python 3.11
Make sure that your python version is >= 3.11

## Installing Webtap library

1. Clone the repo
```bash 
git clone https://github.com/webtap-ai/webtap.git
cd webtap
```
2. It is recommended, though not mandatory, to create a virtual environment for your project.
```bash
python3 -m venv venv
source venv/bin/activate
```
3. Setup openai key and Apify Key
You must have an openai key and a Apify key in order to use the project. You can get an openai key by signing up at https://platform.openai.com/ and an Apify key by signing up at https://apify.com/
Set the following environment variables in your shell ( Add these to your .bashrc or .bash_profile to make them permanent):
```bash
export OPENAI_API_KEY="{your api key}"
export APIFY_API_TOKEN="{your api key}"
```
Optionally setup LangSmith (signup at https://langsmith.com) environment variables if you want to use LangSmith for tracing:
```bash
export LANGCHAIN_TRACING_V2=true
export LANGCHAIN_PROJECT="{Your dev environment project}"
export LANGCHAIN_ENDPOINT=https://api.smith.langchain.com
export LANGCHAIN_API_KEY={your api_key}
```
4. Install requirements
```bash
python setup.py install
```

## Run examples

After installation you can run an example using the following command:
```bash
python -m examples.apify_tap_example
```
## Run tests
You can run tests by using the following command:
```bash
    python -m tests.apify_tap_test --apify_tap_id={actor_id} --model=gpt-3.5-turbo --test_num={test_num}
```
## Alternativelly you can install the library using pip

To use Webtap in your project, you can install it directly from the Python Package Index (PyPI) using pip:

```bash
pip install webtap
```

After installing the library, follow the steps to set up the environment variables and run the examples as described in "Setup openai key and Apify Key section (2), (3) and (4)".

## Managing dependencies with requirements.txt

If you are managing your project's dependencies through a `requirements.txt` file, you can add Webtap to it:
    
```bash
webtap
```

After adding the line to your `requirements.txt`, you can install all your dependencies with:
    
```bash
pip install -r requirements.txt
```

# Creating a new Apify Tap using AI based Tap Generator

Webtap also offers a tool to automatically generate a new Apify Tap. 
It often works; when it doesn't work, it provides a good starting point for manual editing.
To do so, you can use the following python code:
(This feature is exclusive to the full GitHub repository and is not included in the PyPI package distribution.)

```bash
# make sure you Webtap project is setup(venv is activated, requirements are installed, environment variables are set and you are in the webtap directory)
python -m examples.tap_generator_example epctex/gutenberg-scraper
```
Check out the code in the `examples/tap_generator_example.py` file to see how to use the Tap Generator and how to customize the generated Tap.

# Creating a new standard Apify Tap using json definition

In order to see how to create a standard new ApifyTap (using json definition) see [GUIDE.md](docs/taps_definition/GUIDE.md)

# Creating a new Custom Apify Tap by extending the ApifyTap class

In order to see how to create a standard new ApifyTap (using json definition) see [CUSTOM_GUIDE.md](docs/taps_definition/CUSTOM_GUIDE.md)

# Acknowledgments

This project gratefully makes use of the following libraries and services:


- [Apify SDK](https://sdk.apify.com/) for web crawling and automation.
- [LangChain](https://github.com/langchain-ai/langchain) for integrating language models into applications.
- [OpenAI](https://openai.com/) for providing access to powerful AI models.
- [LangSmith](https://smith.langchain.com/) for their tracing and debugging tools.
- [Pydantic](https://pydantic-docs.helpmanual.io/) for data validation and settings management using Python type annotations.
- [tiktoken](https://pypi.org/project/tiktoken/) for handling TikTok tokens.
- [apify-client](https://pypi.org/project/apify-client/) for interacting with the Apify API.
- [demjson](https://pypi.org/project/demjson3/) for encoding, decoding, and linting JSON.
- [black](https://black.readthedocs.io/en/stable/) for formatting Python code.
- [html2text](https://pypi.org/project/html2text/) for converting HTML into clean, easy-to-read plain ASCII text.

We are grateful to the developers of these libraries and services for their hard work and dedication!

## Ownership and Responsibility

This project was initially developed and is owned by **Webtap Technologies LLC**.

### Founding Contributors

- [stefanopochet Stefano](https://github.com/stefanopochet)
- [alpha8eta](https://github.com/alpha8eta)
- [klokt-valg H. H.](https://github.com/klokt-valg)

### Legal Disclaimer

All contributions to this project are made on a voluntary basis and do not imply any legal responsibility for individual contributors, including but not limited to founding contributors. Legal responsibility for this project and its use rests solpely with Webtap Technologies LLC, as stated in the license.

### Contact Information

**Webtap Technologies LLC**  
30 N Gould ST STE R  
Sheridan, WY 82801  
EIN: 32-0763057
