# Reviewing tools
AI-powered tools to support the literature review process.

The [`ai_reviewing.ipynb`](./ai_reviewing.ipynb) implements *Retrieval-Augmented Generation* (RAG), i.e. a technique that grants a generative model to fetch information from (in this case) files in the local system.
Leveraging on the power of RAG, the notebook allows the user to query the paper and gather insights without having to read the full-text.

> [!IMPORTANT] 
> The power of the present tool is its flexibility, and thus the possibility to be run on a large collection of references without any human supervision. For similar analysis of a single paper, online tools with better performance are available. 
> See for example [Paper Digest](https://www.paperdigest.org/ask/) or [SciSpace](https://typeset.io/chat-pdf).

## How to install
* Clone the repo with
    ```
    git clone https://github.com/Luca-Pozzi/ai_reviewing.git
    ```
* [Optional]. Setup a virtual environment and activate it
    ```
    python3.12 -m venv gpt4all_venv
    <path_to_venv>\Scripts\activate # in Windows
    . <path_to_venv>/bin/activate   # in Linux
    ```
* Install the requirements
    ```
    pip install -r requirements.txt
    ```

## How to use
### Export the collection of papers from Zotero
* [Create a collection of references in Zotero](https://libguides.graduateinstitute.ch/zotero/collections#:~:text=To%20create%20a%20collection%3A%20click,collection%20in%20the%20left%20pane.).
* Ensure that each reference has an [associated local PDF file](https://www.zotero.org/support/adding_items_to_zotero).
* Export the collection from Zotero in BibTex format. To do so:
    * right-click on the collection in the left menu,
    * select _Export_,
    * from the pop-up menu, select BibTex in the _Format_ field,
    * tick the _Export file_ option (other options can be left unchecked),
    * click _OK_ and select the location for your file.

### Use RAG to summarize papers from the collection
Run the [`ai_reviewing.ipynb`](./ai_reviewing.ipynb) cell-by-cell. You might have to adapt the query strings to your specific use case.

## Troubleshooting
* Even if you have downloaded the models, instanciating a `GPT4All` object will try to access [gpt4all.io](gpt4all.io). This happens under the hood with any instanciation of GPT4All models, either LLMs or embeddings, with both the GPT4All SDK or via LangChain.<br>
    See [here](https://github.com/nomic-ai/gpt4all/wiki/Python-Bindings#without-online-connectivity-allow_download-parameter) how to turn off this functionality and how to reproduce the online behavior without Internet access.
* If you are running the [`ai_reviewing.ipynb`](./ai_reviewing.ipynb) tool from VS Code and you have installed the dependencies in a virtual environment, you might have a hard time setting the right interpreter.<br>
    To do so:
    * From inside VS Code, press <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> to open the control palette, and look for the _Python: Select Interpreter_ entry.
    * Click on _Python: Select Interpreter_ > _Enter interpreter path..._ > _Find..._ and browse to the _python_ executable inside your venv folder.
    Now your venv should be visible in the list of kernels to select when you try to run the first cell. If not, try to close and re-open VS Code and check the list again.
