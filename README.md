{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": [],
      "authorship_tag": "ABX9TyNic3dlOFk5W2byM/7xKBL0",
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/Sum-it07/Data_Analysis/blob/main/Project_1_Titanic_Data_Analysis.ipynb\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Project 1: Data Analysis Titanic**"
      ],
      "metadata": {
        "id": "wv7Gmo-8IKGm"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Import libraries required for data analysis**"
      ],
      "metadata": {
        "id": "PYUWR6y-NzQM"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "import matplotlib.pyplot as plt\n",
        "import seaborn as sns\n"
      ],
      "metadata": {
        "id": "gTZoYCORN5qT"
      },
      "execution_count": 2,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "# Display all example datasets from seaborn"
      ],
      "metadata": {
        "id": "65Txr3RdPGSz"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "sns.get_dataset_names()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "BwezPSRFPCiI",
        "outputId": "75970e9b-5e67-419d-dbd4-152f28bece9a"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "['anagrams',\n",
              " 'anscombe',\n",
              " 'attention',\n",
              " 'brain_networks',\n",
              " 'car_crashes',\n",
              " 'diamonds',\n",
              " 'dots',\n",
              " 'dowjones',\n",
              " 'exercise',\n",
              " 'flights',\n",
              " 'fmri',\n",
              " 'geyser',\n",
              " 'glue',\n",
              " 'healthexp',\n",
              " 'iris',\n",
              " 'mpg',\n",
              " 'penguins',\n",
              " 'planets',\n",
              " 'seaice',\n",
              " 'taxis',\n",
              " 'tips',\n",
              " 'titanic']"
            ]
          },
          "metadata": {},
          "execution_count": 6
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# Import 'titanic' dataset from seaborn"
      ],
      "metadata": {
        "id": "WPL_K_7HQDXU"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "df=sns.load_dataset('titanic')\n",
        "df.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 206
        },
        "id": "qxPKdaUzPSEp",
        "outputId": "19c3ab1c-4eaf-47dc-c17b-f59454ecf01a"
      },
      "execution_count": 4,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "   survived  pclass     sex   age  sibsp  parch     fare embarked  class  \\\n",
              "0         0       3    male  22.0      1      0   7.2500        S  Third   \n",
              "1         1       1  female  38.0      1      0  71.2833        C  First   \n",
              "2         1       3  female  26.0      0      0   7.9250        S  Third   \n",
              "3         1       1  female  35.0      1      0  53.1000        S  First   \n",
              "4         0       3    male  35.0      0      0   8.0500        S  Third   \n",
              "\n",
              "     who  adult_male deck  embark_town alive  alone  \n",
              "0    man        True  NaN  Southampton    no  False  \n",
              "1  woman       False    C    Cherbourg   yes  False  \n",
              "2  woman       False  NaN  Southampton   yes   True  \n",
              "3  woman       False    C  Southampton   yes  False  \n",
              "4    man        True  NaN  Southampton    no   True  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-319a9eeb-6745-4c1a-a536-31e0ce9a8d68\" class=\"colab-df-container\">\n",
              "    <div>\n",
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
              "      <th>survived</th>\n",
              "      <th>pclass</th>\n",
              "      <th>sex</th>\n",
              "      <th>age</th>\n",
              "      <th>sibsp</th>\n",
              "      <th>parch</th>\n",
              "      <th>fare</th>\n",
              "      <th>embarked</th>\n",
              "      <th>class</th>\n",
              "      <th>who</th>\n",
              "      <th>adult_male</th>\n",
              "      <th>deck</th>\n",
              "      <th>embark_town</th>\n",
              "      <th>alive</th>\n",
              "      <th>alone</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>0</td>\n",
              "      <td>3</td>\n",
              "      <td>male</td>\n",
              "      <td>22.0</td>\n",
              "      <td>1</td>\n",
              "      <td>0</td>\n",
              "      <td>7.2500</td>\n",
              "      <td>S</td>\n",
              "      <td>Third</td>\n",
              "      <td>man</td>\n",
              "      <td>True</td>\n",
              "      <td>NaN</td>\n",
              "      <td>Southampton</td>\n",
              "      <td>no</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>1</td>\n",
              "      <td>1</td>\n",
              "      <td>female</td>\n",
              "      <td>38.0</td>\n",
              "      <td>1</td>\n",
              "      <td>0</td>\n",
              "      <td>71.2833</td>\n",
              "      <td>C</td>\n",
              "      <td>First</td>\n",
              "      <td>woman</td>\n",
              "      <td>False</td>\n",
              "      <td>C</td>\n",
              "      <td>Cherbourg</td>\n",
              "      <td>yes</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>1</td>\n",
              "      <td>3</td>\n",
              "      <td>female</td>\n",
              "      <td>26.0</td>\n",
              "      <td>0</td>\n",
              "      <td>0</td>\n",
              "      <td>7.9250</td>\n",
              "      <td>S</td>\n",
              "      <td>Third</td>\n",
              "      <td>woman</td>\n",
              "      <td>False</td>\n",
              "      <td>NaN</td>\n",
              "      <td>Southampton</td>\n",
              "      <td>yes</td>\n",
              "      <td>True</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>1</td>\n",
              "      <td>1</td>\n",
              "      <td>female</td>\n",
              "      <td>35.0</td>\n",
              "      <td>1</td>\n",
              "      <td>0</td>\n",
              "      <td>53.1000</td>\n",
              "      <td>S</td>\n",
              "      <td>First</td>\n",
              "      <td>woman</td>\n",
              "      <td>False</td>\n",
              "      <td>C</td>\n",
              "      <td>Southampton</td>\n",
              "      <td>yes</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>0</td>\n",
              "      <td>3</td>\n",
              "      <td>male</td>\n",
              "      <td>35.0</td>\n",
              "      <td>0</td>\n",
              "      <td>0</td>\n",
              "      <td>8.0500</td>\n",
              "      <td>S</td>\n",
              "      <td>Third</td>\n",
              "      <td>man</td>\n",
              "      <td>True</td>\n",
              "      <td>NaN</td>\n",
              "      <td>Southampton</td>\n",
              "      <td>no</td>\n",
              "      <td>True</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-319a9eeb-6745-4c1a-a536-31e0ce9a8d68')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-319a9eeb-6745-4c1a-a536-31e0ce9a8d68 button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-319a9eeb-6745-4c1a-a536-31e0ce9a8d68');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "<div id=\"df-9358e6df-4e59-4ee0-870c-cda71ee7276a\">\n",
              "  <button class=\"colab-df-quickchart\" onclick=\"quickchart('df-9358e6df-4e59-4ee0-870c-cda71ee7276a')\"\n",
              "            title=\"Suggest charts\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "<svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "     width=\"24px\">\n",
              "    <g>\n",
              "        <path d=\"M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z\"/>\n",
              "    </g>\n",
              "</svg>\n",
              "  </button>\n",
              "\n",
              "<style>\n",
              "  .colab-df-quickchart {\n",
              "      --bg-color: #E8F0FE;\n",
              "      --fill-color: #1967D2;\n",
              "      --hover-bg-color: #E2EBFA;\n",
              "      --hover-fill-color: #174EA6;\n",
              "      --disabled-fill-color: #AAA;\n",
              "      --disabled-bg-color: #DDD;\n",
              "  }\n",
              "\n",
              "  [theme=dark] .colab-df-quickchart {\n",
              "      --bg-color: #3B4455;\n",
              "      --fill-color: #D2E3FC;\n",
              "      --hover-bg-color: #434B5C;\n",
              "      --hover-fill-color: #FFFFFF;\n",
              "      --disabled-bg-color: #3B4455;\n",
              "      --disabled-fill-color: #666;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart {\n",
              "    background-color: var(--bg-color);\n",
              "    border: none;\n",
              "    border-radius: 50%;\n",
              "    cursor: pointer;\n",
              "    display: none;\n",
              "    fill: var(--fill-color);\n",
              "    height: 32px;\n",
              "    padding: 0;\n",
              "    width: 32px;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart:hover {\n",
              "    background-color: var(--hover-bg-color);\n",
              "    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "    fill: var(--button-hover-fill-color);\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart-complete:disabled,\n",
              "  .colab-df-quickchart-complete:disabled:hover {\n",
              "    background-color: var(--disabled-bg-color);\n",
              "    fill: var(--disabled-fill-color);\n",
              "    box-shadow: none;\n",
              "  }\n",
              "\n",
              "  .colab-df-spinner {\n",
              "    border: 2px solid var(--fill-color);\n",
              "    border-color: transparent;\n",
              "    border-bottom-color: var(--fill-color);\n",
              "    animation:\n",
              "      spin 1s steps(1) infinite;\n",
              "  }\n",
              "\n",
              "  @keyframes spin {\n",
              "    0% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "      border-left-color: var(--fill-color);\n",
              "    }\n",
              "    20% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    30% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    40% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    60% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    80% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "    90% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "  }\n",
              "</style>\n",
              "\n",
              "  <script>\n",
              "    async function quickchart(key) {\n",
              "      const quickchartButtonEl =\n",
              "        document.querySelector('#' + key + ' button');\n",
              "      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.\n",
              "      quickchartButtonEl.classList.add('colab-df-spinner');\n",
              "      try {\n",
              "        const charts = await google.colab.kernel.invokeFunction(\n",
              "            'suggestCharts', [key], {});\n",
              "      } catch (error) {\n",
              "        console.error('Error during call to suggestCharts:', error);\n",
              "      }\n",
              "      quickchartButtonEl.classList.remove('colab-df-spinner');\n",
              "      quickchartButtonEl.classList.add('colab-df-quickchart-complete');\n",
              "    }\n",
              "    (() => {\n",
              "      let quickchartButtonEl =\n",
              "        document.querySelector('#df-9358e6df-4e59-4ee0-870c-cda71ee7276a button');\n",
              "      quickchartButtonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "    })();\n",
              "  </script>\n",
              "</div>\n",
              "\n",
              "    </div>\n",
              "  </div>\n"
            ],
            "application/vnd.google.colaboratory.intrinsic+json": {
              "type": "dataframe",
              "variable_name": "df",
              "summary": "{\n  \"name\": \"df\",\n  \"rows\": 891,\n  \"fields\": [\n    {\n      \"column\": \"survived\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 0,\n        \"min\": 0,\n        \"max\": 1,\n        \"num_unique_values\": 2,\n        \"samples\": [\n          1,\n          0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"pclass\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 0,\n        \"min\": 1,\n        \"max\": 3,\n        \"num_unique_values\": 3,\n        \"samples\": [\n          3,\n          1\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"sex\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          \"female\",\n          \"male\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"age\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 14.526497332334044,\n        \"min\": 0.42,\n        \"max\": 80.0,\n        \"num_unique_values\": 88,\n        \"samples\": [\n          0.75,\n          22.0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"sibsp\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 1,\n        \"min\": 0,\n        \"max\": 8,\n        \"num_unique_values\": 7,\n        \"samples\": [\n          1,\n          0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"parch\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 0,\n        \"min\": 0,\n        \"max\": 6,\n        \"num_unique_values\": 7,\n        \"samples\": [\n          0,\n          1\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"fare\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 49.693428597180905,\n        \"min\": 0.0,\n        \"max\": 512.3292,\n        \"num_unique_values\": 248,\n        \"samples\": [\n          11.2417,\n          51.8625\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"embarked\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 3,\n        \"samples\": [\n          \"S\",\n          \"C\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"class\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 3,\n        \"samples\": [\n          \"Third\",\n          \"First\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"who\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 3,\n        \"samples\": [\n          \"man\",\n          \"woman\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"adult_male\",\n      \"properties\": {\n        \"dtype\": \"boolean\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          false,\n          true\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"deck\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 7,\n        \"samples\": [\n          \"C\",\n          \"E\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"embark_town\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 3,\n        \"samples\": [\n          \"Southampton\",\n          \"Cherbourg\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"alive\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          \"yes\",\n          \"no\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"alone\",\n      \"properties\": {\n        \"dtype\": \"boolean\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          true,\n          false\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}"
            }
          },
          "metadata": {},
          "execution_count": 4
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# Display first five rows"
      ],
      "metadata": {
        "id": "tvGBuTFAQSiu"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "df.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 226
        },
        "id": "LGcVqQ4OPjUA",
        "outputId": "8f04f745-63aa-4430-c312-89e93ccea303"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "   survived  pclass     sex   age  sibsp  parch     fare embarked  class  \\\n",
              "0         0       3    male  22.0      1      0   7.2500        S  Third   \n",
              "1         1       1  female  38.0      1      0  71.2833        C  First   \n",
              "2         1       3  female  26.0      0      0   7.9250        S  Third   \n",
              "3         1       1  female  35.0      1      0  53.1000        S  First   \n",
              "4         0       3    male  35.0      0      0   8.0500        S  Third   \n",
              "\n",
              "     who  adult_male deck  embark_town alive  alone  \n",
              "0    man        True  NaN  Southampton    no  False  \n",
              "1  woman       False    C    Cherbourg   yes  False  \n",
              "2  woman       False  NaN  Southampton   yes   True  \n",
              "3  woman       False    C  Southampton   yes  False  \n",
              "4    man        True  NaN  Southampton    no   True  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-cc428fa1-0d42-4278-b883-98ed1491b691\" class=\"colab-df-container\">\n",
              "    <div>\n",
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
              "      <th>survived</th>\n",
              "      <th>pclass</th>\n",
              "      <th>sex</th>\n",
              "      <th>age</th>\n",
              "      <th>sibsp</th>\n",
              "      <th>parch</th>\n",
              "      <th>fare</th>\n",
              "      <th>embarked</th>\n",
              "      <th>class</th>\n",
              "      <th>who</th>\n",
              "      <th>adult_male</th>\n",
              "      <th>deck</th>\n",
              "      <th>embark_town</th>\n",
              "      <th>alive</th>\n",
              "      <th>alone</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>0</td>\n",
              "      <td>3</td>\n",
              "      <td>male</td>\n",
              "      <td>22.0</td>\n",
              "      <td>1</td>\n",
              "      <td>0</td>\n",
              "      <td>7.2500</td>\n",
              "      <td>S</td>\n",
              "      <td>Third</td>\n",
              "      <td>man</td>\n",
              "      <td>True</td>\n",
              "      <td>NaN</td>\n",
              "      <td>Southampton</td>\n",
              "      <td>no</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>1</td>\n",
              "      <td>1</td>\n",
              "      <td>female</td>\n",
              "      <td>38.0</td>\n",
              "      <td>1</td>\n",
              "      <td>0</td>\n",
              "      <td>71.2833</td>\n",
              "      <td>C</td>\n",
              "      <td>First</td>\n",
              "      <td>woman</td>\n",
              "      <td>False</td>\n",
              "      <td>C</td>\n",
              "      <td>Cherbourg</td>\n",
              "      <td>yes</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>1</td>\n",
              "      <td>3</td>\n",
              "      <td>female</td>\n",
              "      <td>26.0</td>\n",
              "      <td>0</td>\n",
              "      <td>0</td>\n",
              "      <td>7.9250</td>\n",
              "      <td>S</td>\n",
              "      <td>Third</td>\n",
              "      <td>woman</td>\n",
              "      <td>False</td>\n",
              "      <td>NaN</td>\n",
              "      <td>Southampton</td>\n",
              "      <td>yes</td>\n",
              "      <td>True</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>1</td>\n",
              "      <td>1</td>\n",
              "      <td>female</td>\n",
              "      <td>35.0</td>\n",
              "      <td>1</td>\n",
              "      <td>0</td>\n",
              "      <td>53.1000</td>\n",
              "      <td>S</td>\n",
              "      <td>First</td>\n",
              "      <td>woman</td>\n",
              "      <td>False</td>\n",
              "      <td>C</td>\n",
              "      <td>Southampton</td>\n",
              "      <td>yes</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>0</td>\n",
              "      <td>3</td>\n",
              "      <td>male</td>\n",
              "      <td>35.0</td>\n",
              "      <td>0</td>\n",
              "      <td>0</td>\n",
              "      <td>8.0500</td>\n",
              "      <td>S</td>\n",
              "      <td>Third</td>\n",
              "      <td>man</td>\n",
              "      <td>True</td>\n",
              "      <td>NaN</td>\n",
              "      <td>Southampton</td>\n",
              "      <td>no</td>\n",
              "      <td>True</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-cc428fa1-0d42-4278-b883-98ed1491b691')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-cc428fa1-0d42-4278-b883-98ed1491b691 button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-cc428fa1-0d42-4278-b883-98ed1491b691');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "<div id=\"df-d2f01342-6a69-4e99-b650-6686409aad2a\">\n",
              "  <button class=\"colab-df-quickchart\" onclick=\"quickchart('df-d2f01342-6a69-4e99-b650-6686409aad2a')\"\n",
              "            title=\"Suggest charts\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "<svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "     width=\"24px\">\n",
              "    <g>\n",
              "        <path d=\"M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z\"/>\n",
              "    </g>\n",
              "</svg>\n",
              "  </button>\n",
              "\n",
              "<style>\n",
              "  .colab-df-quickchart {\n",
              "      --bg-color: #E8F0FE;\n",
              "      --fill-color: #1967D2;\n",
              "      --hover-bg-color: #E2EBFA;\n",
              "      --hover-fill-color: #174EA6;\n",
              "      --disabled-fill-color: #AAA;\n",
              "      --disabled-bg-color: #DDD;\n",
              "  }\n",
              "\n",
              "  [theme=dark] .colab-df-quickchart {\n",
              "      --bg-color: #3B4455;\n",
              "      --fill-color: #D2E3FC;\n",
              "      --hover-bg-color: #434B5C;\n",
              "      --hover-fill-color: #FFFFFF;\n",
              "      --disabled-bg-color: #3B4455;\n",
              "      --disabled-fill-color: #666;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart {\n",
              "    background-color: var(--bg-color);\n",
              "    border: none;\n",
              "    border-radius: 50%;\n",
              "    cursor: pointer;\n",
              "    display: none;\n",
              "    fill: var(--fill-color);\n",
              "    height: 32px;\n",
              "    padding: 0;\n",
              "    width: 32px;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart:hover {\n",
              "    background-color: var(--hover-bg-color);\n",
              "    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "    fill: var(--button-hover-fill-color);\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart-complete:disabled,\n",
              "  .colab-df-quickchart-complete:disabled:hover {\n",
              "    background-color: var(--disabled-bg-color);\n",
              "    fill: var(--disabled-fill-color);\n",
              "    box-shadow: none;\n",
              "  }\n",
              "\n",
              "  .colab-df-spinner {\n",
              "    border: 2px solid var(--fill-color);\n",
              "    border-color: transparent;\n",
              "    border-bottom-color: var(--fill-color);\n",
              "    animation:\n",
              "      spin 1s steps(1) infinite;\n",
              "  }\n",
              "\n",
              "  @keyframes spin {\n",
              "    0% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "      border-left-color: var(--fill-color);\n",
              "    }\n",
              "    20% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    30% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    40% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    60% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    80% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "    90% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "  }\n",
              "</style>\n",
              "\n",
              "  <script>\n",
              "    async function quickchart(key) {\n",
              "      const quickchartButtonEl =\n",
              "        document.querySelector('#' + key + ' button');\n",
              "      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.\n",
              "      quickchartButtonEl.classList.add('colab-df-spinner');\n",
              "      try {\n",
              "        const charts = await google.colab.kernel.invokeFunction(\n",
              "            'suggestCharts', [key], {});\n",
              "      } catch (error) {\n",
              "        console.error('Error during call to suggestCharts:', error);\n",
              "      }\n",
              "      quickchartButtonEl.classList.remove('colab-df-spinner');\n",
              "      quickchartButtonEl.classList.add('colab-df-quickchart-complete');\n",
              "    }\n",
              "    (() => {\n",
              "      let quickchartButtonEl =\n",
              "        document.querySelector('#df-d2f01342-6a69-4e99-b650-6686409aad2a button');\n",
              "      quickchartButtonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "    })();\n",
              "  </script>\n",
              "</div>\n",
              "\n",
              "    </div>\n",
              "  </div>\n"
            ],
            "application/vnd.google.colaboratory.intrinsic+json": {
              "type": "dataframe",
              "variable_name": "df",
              "summary": "{\n  \"name\": \"df\",\n  \"rows\": 891,\n  \"fields\": [\n    {\n      \"column\": \"survived\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 0,\n        \"min\": 0,\n        \"max\": 1,\n        \"num_unique_values\": 2,\n        \"samples\": [\n          1,\n          0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"pclass\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 0,\n        \"min\": 1,\n        \"max\": 3,\n        \"num_unique_values\": 3,\n        \"samples\": [\n          3,\n          1\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"sex\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          \"female\",\n          \"male\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"age\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 14.526497332334044,\n        \"min\": 0.42,\n        \"max\": 80.0,\n        \"num_unique_values\": 88,\n        \"samples\": [\n          0.75,\n          22.0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"sibsp\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 1,\n        \"min\": 0,\n        \"max\": 8,\n        \"num_unique_values\": 7,\n        \"samples\": [\n          1,\n          0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"parch\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 0,\n        \"min\": 0,\n        \"max\": 6,\n        \"num_unique_values\": 7,\n        \"samples\": [\n          0,\n          1\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"fare\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 49.693428597180905,\n        \"min\": 0.0,\n        \"max\": 512.3292,\n        \"num_unique_values\": 248,\n        \"samples\": [\n          11.2417,\n          51.8625\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"embarked\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 3,\n        \"samples\": [\n          \"S\",\n          \"C\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"class\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 3,\n        \"samples\": [\n          \"Third\",\n          \"First\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"who\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 3,\n        \"samples\": [\n          \"man\",\n          \"woman\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"adult_male\",\n      \"properties\": {\n        \"dtype\": \"boolean\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          false,\n          true\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"deck\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 7,\n        \"samples\": [\n          \"C\",\n          \"E\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"embark_town\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 3,\n        \"samples\": [\n          \"Southampton\",\n          \"Cherbourg\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"alive\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          \"yes\",\n          \"no\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"alone\",\n      \"properties\": {\n        \"dtype\": \"boolean\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          true,\n          false\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}"
            }
          },
          "metadata": {},
          "execution_count": 9
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# Display last five rows"
      ],
      "metadata": {
        "id": "mhBZkus-QZri"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "df.tail()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 226
        },
        "id": "ycWd5hOzPrRq",
        "outputId": "d3b8e4ab-e07c-4fe9-9ad9-b010f3ba1b06"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "     survived  pclass     sex   age  sibsp  parch   fare embarked   class  \\\n",
              "886         0       2    male  27.0      0      0  13.00        S  Second   \n",
              "887         1       1  female  19.0      0      0  30.00        S   First   \n",
              "888         0       3  female   NaN      1      2  23.45        S   Third   \n",
              "889         1       1    male  26.0      0      0  30.00        C   First   \n",
              "890         0       3    male  32.0      0      0   7.75        Q   Third   \n",
              "\n",
              "       who  adult_male deck  embark_town alive  alone  \n",
              "886    man        True  NaN  Southampton    no   True  \n",
              "887  woman       False    B  Southampton   yes   True  \n",
              "888  woman       False  NaN  Southampton    no  False  \n",
              "889    man        True    C    Cherbourg   yes   True  \n",
              "890    man        True  NaN   Queenstown    no   True  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-c5fb5c4a-086a-4bbc-b8d2-acd2669b7ae6\" class=\"colab-df-container\">\n",
              "    <div>\n",
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
              "      <th>survived</th>\n",
              "      <th>pclass</th>\n",
              "      <th>sex</th>\n",
              "      <th>age</th>\n",
              "      <th>sibsp</th>\n",
              "      <th>parch</th>\n",
              "      <th>fare</th>\n",
              "      <th>embarked</th>\n",
              "      <th>class</th>\n",
              "      <th>who</th>\n",
              "      <th>adult_male</th>\n",
              "      <th>deck</th>\n",
              "      <th>embark_town</th>\n",
              "      <th>alive</th>\n",
              "      <th>alone</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>886</th>\n",
              "      <td>0</td>\n",
              "      <td>2</td>\n",
              "      <td>male</td>\n",
              "      <td>27.0</td>\n",
              "      <td>0</td>\n",
              "      <td>0</td>\n",
              "      <td>13.00</td>\n",
              "      <td>S</td>\n",
              "      <td>Second</td>\n",
              "      <td>man</td>\n",
              "      <td>True</td>\n",
              "      <td>NaN</td>\n",
              "      <td>Southampton</td>\n",
              "      <td>no</td>\n",
              "      <td>True</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>887</th>\n",
              "      <td>1</td>\n",
              "      <td>1</td>\n",
              "      <td>female</td>\n",
              "      <td>19.0</td>\n",
              "      <td>0</td>\n",
              "      <td>0</td>\n",
              "      <td>30.00</td>\n",
              "      <td>S</td>\n",
              "      <td>First</td>\n",
              "      <td>woman</td>\n",
              "      <td>False</td>\n",
              "      <td>B</td>\n",
              "      <td>Southampton</td>\n",
              "      <td>yes</td>\n",
              "      <td>True</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>888</th>\n",
              "      <td>0</td>\n",
              "      <td>3</td>\n",
              "      <td>female</td>\n",
              "      <td>NaN</td>\n",
              "      <td>1</td>\n",
              "      <td>2</td>\n",
              "      <td>23.45</td>\n",
              "      <td>S</td>\n",
              "      <td>Third</td>\n",
              "      <td>woman</td>\n",
              "      <td>False</td>\n",
              "      <td>NaN</td>\n",
              "      <td>Southampton</td>\n",
              "      <td>no</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>889</th>\n",
              "      <td>1</td>\n",
              "      <td>1</td>\n",
              "      <td>male</td>\n",
              "      <td>26.0</td>\n",
              "      <td>0</td>\n",
              "      <td>0</td>\n",
              "      <td>30.00</td>\n",
              "      <td>C</td>\n",
              "      <td>First</td>\n",
              "      <td>man</td>\n",
              "      <td>True</td>\n",
              "      <td>C</td>\n",
              "      <td>Cherbourg</td>\n",
              "      <td>yes</td>\n",
              "      <td>True</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>890</th>\n",
              "      <td>0</td>\n",
              "      <td>3</td>\n",
              "      <td>male</td>\n",
              "      <td>32.0</td>\n",
              "      <td>0</td>\n",
              "      <td>0</td>\n",
              "      <td>7.75</td>\n",
              "      <td>Q</td>\n",
              "      <td>Third</td>\n",
              "      <td>man</td>\n",
              "      <td>True</td>\n",
              "      <td>NaN</td>\n",
              "      <td>Queenstown</td>\n",
              "      <td>no</td>\n",
              "      <td>True</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-c5fb5c4a-086a-4bbc-b8d2-acd2669b7ae6')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-c5fb5c4a-086a-4bbc-b8d2-acd2669b7ae6 button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-c5fb5c4a-086a-4bbc-b8d2-acd2669b7ae6');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "<div id=\"df-e24ab854-1ace-4544-ad6e-d77adcca64e5\">\n",
              "  <button class=\"colab-df-quickchart\" onclick=\"quickchart('df-e24ab854-1ace-4544-ad6e-d77adcca64e5')\"\n",
              "            title=\"Suggest charts\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "<svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "     width=\"24px\">\n",
              "    <g>\n",
              "        <path d=\"M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z\"/>\n",
              "    </g>\n",
              "</svg>\n",
              "  </button>\n",
              "\n",
              "<style>\n",
              "  .colab-df-quickchart {\n",
              "      --bg-color: #E8F0FE;\n",
              "      --fill-color: #1967D2;\n",
              "      --hover-bg-color: #E2EBFA;\n",
              "      --hover-fill-color: #174EA6;\n",
              "      --disabled-fill-color: #AAA;\n",
              "      --disabled-bg-color: #DDD;\n",
              "  }\n",
              "\n",
              "  [theme=dark] .colab-df-quickchart {\n",
              "      --bg-color: #3B4455;\n",
              "      --fill-color: #D2E3FC;\n",
              "      --hover-bg-color: #434B5C;\n",
              "      --hover-fill-color: #FFFFFF;\n",
              "      --disabled-bg-color: #3B4455;\n",
              "      --disabled-fill-color: #666;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart {\n",
              "    background-color: var(--bg-color);\n",
              "    border: none;\n",
              "    border-radius: 50%;\n",
              "    cursor: pointer;\n",
              "    display: none;\n",
              "    fill: var(--fill-color);\n",
              "    height: 32px;\n",
              "    padding: 0;\n",
              "    width: 32px;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart:hover {\n",
              "    background-color: var(--hover-bg-color);\n",
              "    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "    fill: var(--button-hover-fill-color);\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart-complete:disabled,\n",
              "  .colab-df-quickchart-complete:disabled:hover {\n",
              "    background-color: var(--disabled-bg-color);\n",
              "    fill: var(--disabled-fill-color);\n",
              "    box-shadow: none;\n",
              "  }\n",
              "\n",
              "  .colab-df-spinner {\n",
              "    border: 2px solid var(--fill-color);\n",
              "    border-color: transparent;\n",
              "    border-bottom-color: var(--fill-color);\n",
              "    animation:\n",
              "      spin 1s steps(1) infinite;\n",
              "  }\n",
              "\n",
              "  @keyframes spin {\n",
              "    0% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "      border-left-color: var(--fill-color);\n",
              "    }\n",
              "    20% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    30% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    40% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    60% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    80% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "    90% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "  }\n",
              "</style>\n",
              "\n",
              "  <script>\n",
              "    async function quickchart(key) {\n",
              "      const quickchartButtonEl =\n",
              "        document.querySelector('#' + key + ' button');\n",
              "      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.\n",
              "      quickchartButtonEl.classList.add('colab-df-spinner');\n",
              "      try {\n",
              "        const charts = await google.colab.kernel.invokeFunction(\n",
              "            'suggestCharts', [key], {});\n",
              "      } catch (error) {\n",
              "        console.error('Error during call to suggestCharts:', error);\n",
              "      }\n",
              "      quickchartButtonEl.classList.remove('colab-df-spinner');\n",
              "      quickchartButtonEl.classList.add('colab-df-quickchart-complete');\n",
              "    }\n",
              "    (() => {\n",
              "      let quickchartButtonEl =\n",
              "        document.querySelector('#df-e24ab854-1ace-4544-ad6e-d77adcca64e5 button');\n",
              "      quickchartButtonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "    })();\n",
              "  </script>\n",
              "</div>\n",
              "\n",
              "    </div>\n",
              "  </div>\n"
            ],
            "application/vnd.google.colaboratory.intrinsic+json": {
              "type": "dataframe",
              "summary": "{\n  \"name\": \"df\",\n  \"rows\": 5,\n  \"fields\": [\n    {\n      \"column\": \"survived\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 0,\n        \"min\": 0,\n        \"max\": 1,\n        \"num_unique_values\": 2,\n        \"samples\": [\n          1,\n          0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"pclass\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 1,\n        \"min\": 1,\n        \"max\": 3,\n        \"num_unique_values\": 3,\n        \"samples\": [\n          2,\n          1\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"sex\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          \"female\",\n          \"male\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"age\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 5.354126134736337,\n        \"min\": 19.0,\n        \"max\": 32.0,\n        \"num_unique_values\": 4,\n        \"samples\": [\n          19.0,\n          32.0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"sibsp\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 0,\n        \"min\": 0,\n        \"max\": 1,\n        \"num_unique_values\": 2,\n        \"samples\": [\n          1,\n          0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"parch\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 0,\n        \"min\": 0,\n        \"max\": 2,\n        \"num_unique_values\": 2,\n        \"samples\": [\n          2,\n          0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"fare\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 10.09253436952285,\n        \"min\": 7.75,\n        \"max\": 30.0,\n        \"num_unique_values\": 4,\n        \"samples\": [\n          30.0,\n          7.75\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"embarked\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 3,\n        \"samples\": [\n          \"S\",\n          \"C\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"class\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 3,\n        \"samples\": [\n          \"Second\",\n          \"First\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"who\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          \"woman\",\n          \"man\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"adult_male\",\n      \"properties\": {\n        \"dtype\": \"boolean\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          false,\n          true\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"deck\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          \"C\",\n          \"B\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"embark_town\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 3,\n        \"samples\": [\n          \"Southampton\",\n          \"Cherbourg\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"alive\",\n      \"properties\": {\n        \"dtype\": \"category\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          \"yes\",\n          \"no\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"alone\",\n      \"properties\": {\n        \"dtype\": \"boolean\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          false,\n          true\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}"
            }
          },
          "metadata": {},
          "execution_count": 10
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# Display the shape of dataset"
      ],
      "metadata": {
        "id": "WV3M-oahQgcO"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "df.shape"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "MXgVKemlPtBZ",
        "outputId": "a3eb85dc-65d8-4735-a204-5236c44b5db2"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "(891, 15)"
            ]
          },
          "metadata": {},
          "execution_count": 12
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# Display information showing number of rows, column, dataset, null values, memory about dataset"
      ],
      "metadata": {
        "id": "93rfVXOSQm02"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "df.info()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "DMmwmNA8PvLQ",
        "outputId": "56f19263-36d3-454d-9eed-3e7750126178"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "<class 'pandas.core.frame.DataFrame'>\n",
            "RangeIndex: 891 entries, 0 to 890\n",
            "Data columns (total 15 columns):\n",
            " #   Column       Non-Null Count  Dtype   \n",
            "---  ------       --------------  -----   \n",
            " 0   survived     891 non-null    int64   \n",
            " 1   pclass       891 non-null    int64   \n",
            " 2   sex          891 non-null    object  \n",
            " 3   age          714 non-null    float64 \n",
            " 4   sibsp        891 non-null    int64   \n",
            " 5   parch        891 non-null    int64   \n",
            " 6   fare         891 non-null    float64 \n",
            " 7   embarked     889 non-null    object  \n",
            " 8   class        891 non-null    category\n",
            " 9   who          891 non-null    object  \n",
            " 10  adult_male   891 non-null    bool    \n",
            " 11  deck         203 non-null    category\n",
            " 12  embark_town  889 non-null    object  \n",
            " 13  alive        891 non-null    object  \n",
            " 14  alone        891 non-null    bool    \n",
            "dtypes: bool(2), category(2), float64(2), int64(4), object(5)\n",
            "memory usage: 80.7+ KB\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# Display statical summary"
      ],
      "metadata": {
        "id": "9Pn9FVJVQ3UQ"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "df.describe()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 300
        },
        "id": "YVJYtPGnPz4c",
        "outputId": "31ea7cba-6815-46ee-ec1c-fc70a7de11e1"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "         survived      pclass         age       sibsp       parch        fare\n",
              "count  891.000000  891.000000  714.000000  891.000000  891.000000  891.000000\n",
              "mean     0.383838    2.308642   29.699118    0.523008    0.381594   32.204208\n",
              "std      0.486592    0.836071   14.526497    1.102743    0.806057   49.693429\n",
              "min      0.000000    1.000000    0.420000    0.000000    0.000000    0.000000\n",
              "25%      0.000000    2.000000   20.125000    0.000000    0.000000    7.910400\n",
              "50%      0.000000    3.000000   28.000000    0.000000    0.000000   14.454200\n",
              "75%      1.000000    3.000000   38.000000    1.000000    0.000000   31.000000\n",
              "max      1.000000    3.000000   80.000000    8.000000    6.000000  512.329200"
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-a346de36-adc5-4ee2-91d2-61285a120f21\" class=\"colab-df-container\">\n",
              "    <div>\n",
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
              "      <th>survived</th>\n",
              "      <th>pclass</th>\n",
              "      <th>age</th>\n",
              "      <th>sibsp</th>\n",
              "      <th>parch</th>\n",
              "      <th>fare</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>count</th>\n",
              "      <td>891.000000</td>\n",
              "      <td>891.000000</td>\n",
              "      <td>714.000000</td>\n",
              "      <td>891.000000</td>\n",
              "      <td>891.000000</td>\n",
              "      <td>891.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>mean</th>\n",
              "      <td>0.383838</td>\n",
              "      <td>2.308642</td>\n",
              "      <td>29.699118</td>\n",
              "      <td>0.523008</td>\n",
              "      <td>0.381594</td>\n",
              "      <td>32.204208</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>std</th>\n",
              "      <td>0.486592</td>\n",
              "      <td>0.836071</td>\n",
              "      <td>14.526497</td>\n",
              "      <td>1.102743</td>\n",
              "      <td>0.806057</td>\n",
              "      <td>49.693429</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>min</th>\n",
              "      <td>0.000000</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.420000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>0.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>25%</th>\n",
              "      <td>0.000000</td>\n",
              "      <td>2.000000</td>\n",
              "      <td>20.125000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>7.910400</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>50%</th>\n",
              "      <td>0.000000</td>\n",
              "      <td>3.000000</td>\n",
              "      <td>28.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>14.454200</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>75%</th>\n",
              "      <td>1.000000</td>\n",
              "      <td>3.000000</td>\n",
              "      <td>38.000000</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>31.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>max</th>\n",
              "      <td>1.000000</td>\n",
              "      <td>3.000000</td>\n",
              "      <td>80.000000</td>\n",
              "      <td>8.000000</td>\n",
              "      <td>6.000000</td>\n",
              "      <td>512.329200</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-a346de36-adc5-4ee2-91d2-61285a120f21')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-a346de36-adc5-4ee2-91d2-61285a120f21 button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-a346de36-adc5-4ee2-91d2-61285a120f21');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "<div id=\"df-ca987e37-2753-45e0-b167-ae0ae20a8ce0\">\n",
              "  <button class=\"colab-df-quickchart\" onclick=\"quickchart('df-ca987e37-2753-45e0-b167-ae0ae20a8ce0')\"\n",
              "            title=\"Suggest charts\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "<svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "     width=\"24px\">\n",
              "    <g>\n",
              "        <path d=\"M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z\"/>\n",
              "    </g>\n",
              "</svg>\n",
              "  </button>\n",
              "\n",
              "<style>\n",
              "  .colab-df-quickchart {\n",
              "      --bg-color: #E8F0FE;\n",
              "      --fill-color: #1967D2;\n",
              "      --hover-bg-color: #E2EBFA;\n",
              "      --hover-fill-color: #174EA6;\n",
              "      --disabled-fill-color: #AAA;\n",
              "      --disabled-bg-color: #DDD;\n",
              "  }\n",
              "\n",
              "  [theme=dark] .colab-df-quickchart {\n",
              "      --bg-color: #3B4455;\n",
              "      --fill-color: #D2E3FC;\n",
              "      --hover-bg-color: #434B5C;\n",
              "      --hover-fill-color: #FFFFFF;\n",
              "      --disabled-bg-color: #3B4455;\n",
              "      --disabled-fill-color: #666;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart {\n",
              "    background-color: var(--bg-color);\n",
              "    border: none;\n",
              "    border-radius: 50%;\n",
              "    cursor: pointer;\n",
              "    display: none;\n",
              "    fill: var(--fill-color);\n",
              "    height: 32px;\n",
              "    padding: 0;\n",
              "    width: 32px;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart:hover {\n",
              "    background-color: var(--hover-bg-color);\n",
              "    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "    fill: var(--button-hover-fill-color);\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart-complete:disabled,\n",
              "  .colab-df-quickchart-complete:disabled:hover {\n",
              "    background-color: var(--disabled-bg-color);\n",
              "    fill: var(--disabled-fill-color);\n",
              "    box-shadow: none;\n",
              "  }\n",
              "\n",
              "  .colab-df-spinner {\n",
              "    border: 2px solid var(--fill-color);\n",
              "    border-color: transparent;\n",
              "    border-bottom-color: var(--fill-color);\n",
              "    animation:\n",
              "      spin 1s steps(1) infinite;\n",
              "  }\n",
              "\n",
              "  @keyframes spin {\n",
              "    0% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "      border-left-color: var(--fill-color);\n",
              "    }\n",
              "    20% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    30% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    40% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    60% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    80% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "    90% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "  }\n",
              "</style>\n",
              "\n",
              "  <script>\n",
              "    async function quickchart(key) {\n",
              "      const quickchartButtonEl =\n",
              "        document.querySelector('#' + key + ' button');\n",
              "      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.\n",
              "      quickchartButtonEl.classList.add('colab-df-spinner');\n",
              "      try {\n",
              "        const charts = await google.colab.kernel.invokeFunction(\n",
              "            'suggestCharts', [key], {});\n",
              "      } catch (error) {\n",
              "        console.error('Error during call to suggestCharts:', error);\n",
              "      }\n",
              "      quickchartButtonEl.classList.remove('colab-df-spinner');\n",
              "      quickchartButtonEl.classList.add('colab-df-quickchart-complete');\n",
              "    }\n",
              "    (() => {\n",
              "      let quickchartButtonEl =\n",
              "        document.querySelector('#df-ca987e37-2753-45e0-b167-ae0ae20a8ce0 button');\n",
              "      quickchartButtonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "    })();\n",
              "  </script>\n",
              "</div>\n",
              "\n",
              "    </div>\n",
              "  </div>\n"
            ],
            "application/vnd.google.colaboratory.intrinsic+json": {
              "type": "dataframe",
              "summary": "{\n  \"name\": \"df\",\n  \"rows\": 8,\n  \"fields\": [\n    {\n      \"column\": \"survived\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 314.8713661874558,\n        \"min\": 0.0,\n        \"max\": 891.0,\n        \"num_unique_values\": 5,\n        \"samples\": [\n          0.3838383838383838,\n          1.0,\n          0.4865924542648585\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"pclass\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 314.2523437079693,\n        \"min\": 0.8360712409770513,\n        \"max\": 891.0,\n        \"num_unique_values\": 6,\n        \"samples\": [\n          891.0,\n          2.308641975308642,\n          3.0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"age\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 242.9056731818781,\n        \"min\": 0.42,\n        \"max\": 714.0,\n        \"num_unique_values\": 8,\n        \"samples\": [\n          29.69911764705882,\n          28.0,\n          714.0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"sibsp\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 314.4908277465442,\n        \"min\": 0.0,\n        \"max\": 891.0,\n        \"num_unique_values\": 6,\n        \"samples\": [\n          891.0,\n          0.5230078563411896,\n          8.0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"parch\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 314.65971717879,\n        \"min\": 0.0,\n        \"max\": 891.0,\n        \"num_unique_values\": 5,\n        \"samples\": [\n          0.38159371492704824,\n          6.0,\n          0.8060572211299559\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"fare\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 330.6256632228577,\n        \"min\": 0.0,\n        \"max\": 891.0,\n        \"num_unique_values\": 8,\n        \"samples\": [\n          32.204207968574636,\n          14.4542,\n          891.0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}"
            }
          },
          "metadata": {},
          "execution_count": 14
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Univariate Analysis**"
      ],
      "metadata": {
        "id": "fICdn1PqRDu0"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "**1.Which gender had a greater presence among the passengers**"
      ],
      "metadata": {
        "id": "_EBMfpEmRSI6"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "sns.countplot(data=df,x='sex');"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 451
        },
        "id": "6ZGwwsJnP2Wy",
        "outputId": "c30c2917-c4f0-49f3-b5cb-a907a0553180"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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TwoAAKCxhNzMwf/7v//r+7m4uFgej8d3+/Lly8rLy9P3vve9xpsdAADALbqp2Ondu7dsNptsNts1364KDw/XkiVLGm1yAAAAt+qmYuf06dOyLEtdu3bVwYMH1bFjR99YaGioYmJiFBwc3OiTBAAAaKibip34+HhJUn19fZNMBgAAoLHdVOz8rRMnTmj37t2qqKi4Kn5ycnJueWIAAACNoUGxs2rVKk2cOFG33367XC6XbDabb8xmsxE7AACgxWhQ7Lz88st65ZVXNH369MaeDwAAQKNq0PfsfP3113r00Ucbey4AAACNrkGv7Dz66KPasWOHnnnmmcaeDwC0On2nrQ/0FIAWqei1sYGegqQGxs6dd96pmTNnav/+/UpKSlKbNm38xidPntwokwMAALhVDYqdlStXKiIiQnv37tXevXv9xmw2G7EDAABajAbFzunTpxt7HgAAAE2iQRcoAwAAtBYNemXn6aef/tbxt99++4buZ/ny5Vq+fLn+8pe/SJLuuece5eTkaNiwYZL++lfUn3vuOW3cuFE1NTVKTU3VsmXL5HQ6ffdRUlKiiRMnavfu3YqIiFB6erpyc3MVEtLg70sEAAAGaVARfP3113636+rq9Mknn6iysvKafyD0ejp37qxXX31V3bp1k2VZWrdunR5++GEdPnxY99xzj6ZOnapt27Zp06ZNcjgcyszM1MiRI1VQUCDpr39pffjw4XK5XNq3b5/Kyso0duxYtWnTRvPnz2/I0gAAgGEaFDvvvvvuVfvq6+s1ceJE/dM//dMN38+IESP8br/yyitavny59u/fr86dO2v16tXasGGDL6DWrFmjHj16aP/+/RowYIB27Nih4uJi7dq1S06nU71799a8efM0ffp0zZ49W6GhoQ1ZHgAAMEijXbMTFBSkrKwsLVy4sEHnX758WRs3blR1dbXcbreKiopUV1en5ORk3zHdu3dXly5dVFhYKEkqLCxUUlKS39taqamp8nq9Onr06HUfq6amRl6v128DAABmatQLlE+dOqVLly7d1DlHjhxRRESEwsLC9Mwzz+jdd99VYmKiPB6PQkNDFRUV5Xe80+mUx+ORJHk8Hr/QuTJ+Zex6cnNz5XA4fFtcXNxNzRkAALQeDXobKysry++2ZVkqKyvTtm3blJ6eflP3dffdd+vjjz9WVVWVNm/erPT09Ku+u6exZWdn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Zl31ViaA1o/nN67FZv2jz2sBAAC0Yq3+mh0AAIBvQ+wAAACjETsAAMBoxA7w/z355JN65JFHAj0N4DvBsixNmDBB0dHRstls+vjjjwMyj7/85S8BfXw0DyM+jQUAaF3y8vK0du1a7dmzR127dtXtt98e6CnBYMQOAKDZnTp1Sp06ddL9998f6KngO4C3sdAqDR48WJMmTdKUKVN02223yel0atWqVb4vk4yMjNSdd96p9957T5J0+fJljRs3TgkJCQoPD9fdd9+tN99881sfo76+Xrm5ub5z7r33Xm3evLk5lgcY7cknn9SkSZNUUlIim82mO+644x8+3/bs2SObzabt27erT58+Cg8P15AhQ1RRUaH33ntPPXr0kN1u149//GNduHDBd15eXp4GDRqkqKgodejQQf/6r/+qU6dOfev8PvnkEw0bNkwRERFyOp0aM2aMvvzyyyb774GmR+yg1Vq3bp1uv/12HTx4UJMmTdLEiRP16KOP6v7779dHH32klJQUjRkzRhcuXFB9fb06d+6sTZs2qbi4WDk5OXrppZf0m9/85rr3n5ubq/Xr12vFihU6evSopk6dqv/4j//Q3r17m3GVgHnefPNNzZ07V507d1ZZWZkOHTp0w8+32bNn65e//KX27dun0tJSPfbYY1q0aJE2bNigbdu2aceOHVqyZInv+OrqamVlZenDDz9Ufn6+goKC9G//9m+qr6+/5twqKys1ZMgQ9enTRx9++KHy8vJUXl6uxx57rEn/m6CJWUAr9MADD1iDBg3y3b506ZLVvn17a8yYMb59ZWVlliSrsLDwmveRkZFhpaWl+W6np6dbDz/8sGVZlnXx4kWrXbt21r59+/zOGTdunDVq1KhGXAnw3bRw4UIrPj7esqwbe77t3r3bkmTt2rXLN56bm2tJsk6dOuXb95Of/MRKTU297uOeOXPGkmQdOXLEsizLOn36tCXJOnz4sGVZljVv3jwrJSXF75zS0lJLknX8+PEGrxeBxTU7aLV69erl+zk4OFgdOnRQUlKSb9+VPxdSUVEhSVq6dKnefvttlZSU6JtvvlFtba169+59zfs+efKkLly4oB/96Ed++2tra9WnT59GXgnw3XYzz7e/fd47nU61a9dOXbt29dt38OBB3+0TJ04oJydHBw4c0Jdfful7RaekpEQ9e/a8ai5/+tOftHv3bkVERFw1durUKd11110NWyQCithBq9WmTRu/2zabzW+fzWaT9NdrbzZu3Kjnn39er7/+utxutyIjI/Xaa6/pwIED17zv8+fPS5K2bdum733ve35j/M0doHHdzPPt75/j1/p34G/fohoxYoTi4+O1atUqxcbGqr6+Xj179lRtbe115zJixAj9/Oc/v2qsU6dON7cwtBjEDr4TCgoKdP/99+vZZ5/17fu2ixQTExMVFhamkpISPfDAA80xReA7q6meb1999ZWOHz+uVatW6Qc/+IEk6Y9//OO3nnPffffpt7/9re644w6FhPAr0hT8n8R3Qrdu3bR+/Xpt375dCQkJ+s///E8dOnRICQkJ1zw+MjJSzz//vKZOnar6+noNGjRIVVVVKigokN1uV3p6ejOvADBXUz3fbrvtNnXo0EErV65Up06dVFJSohdffPFbz8nIyNCqVas0atQovfDCC4qOjtbJkye1ceNG/epXv1JwcHCD5oLAInbwnfCTn/xEhw8f1uOPPy6bzaZRo0bp2Wef9X00/VrmzZunjh07Kjc3V5999pmioqJ033336aWXXmrGmQPfDU3xfAsKCtLGjRs1efJk9ezZU3fffbcWL16swYMHX/ec2NhYFRQUaPr06UpJSVFNTY3i4+M1dOhQBQXxAebWymZZlhXoSQAAADQVMhUAABiN2AEAAEYjdgAAgNGIHQAAYDRiBwAAGI3YAQAARiN2AACA0YgdAABgNGIHAAAYjdgBAABGI3YAAIDRiB0ArdbmzZuVlJSk8PBwdejQQcnJyaqurpYk/epXv1KPHj3Utm1bde/eXcuWLfOd9/TTT6tXr16qqamRJNXW1qpPnz4aO3ZsQNYBoGkROwBapbKyMo0aNUpPP/20jh07pj179mjkyJGyLEvvvPOOcnJy9Morr+jYsWOaP3++Zs6cqXXr1kmSFi9erOrqar344ouSpJ/97GeqrKzUL3/5y0AuCUATCQn0BACgIcrKynTp0iWNHDlS8fHxkqSkpCRJ0qxZs/T6669r5MiRkqSEhAQVFxfrrbfeUnp6uiIiIvTrX/9aDzzwgCIjI7Vo0SLt3r1bdrs9YOsB0HRslmVZgZ4EANysy5cvKzU1VQcPHlRqaqpSUlL07//+7woNDVVERITCw8MVFPR/L15funRJDodD5eXlvn0vvfSScnNzNX36dL366quBWAaAZsArOwBapeDgYO3cuVP79u3Tjh07tGTJEv3sZz/Tli1bJEmrVq1S//79rzrnivr6ehUUFCg4OFgnT55s1rkDaF5cswOg1bLZbBo4cKDmzJmjw4cPKzQ0VAUFBYqNjdVnn32mO++8029LSEjwnfvaa6/p008/1d69e5WXl6c1a9YEcCUAmhKv7ABolQ4cOKD8/HylpKQoJiZGBw4c0JkzZ9SjRw/NmTNHkydPlsPh0NChQ1VTU6MPP/xQX3/9tbKysnT48GHl5ORo8+bNGjhwoN544w399Kc/1QMPPKCuXbsGemkAGhnX7ABolY4dO6apU6fqo48+ktfrVXx8vCZNmqTMzExJ0oYNG/Taa6+puLhY7du3V1JSkqZMmaJhw4apb9++GjRokN566y3f/T388MP68ssv9cEHH/i93QWg9SN2AACA0bhmBwAAGI3YAQAARiN2AACA0YgdAABgNGIHAAAYjdgBAABGI3YAAIDRiB0AAGA0YgcAABiN2AEAAEYjdgAAgNH+H8DWLShLpCJeAAAAAElFTkSuQmCC\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**2.which passenger class had the fewest number of paddengers?**"
      ],
      "metadata": {
        "id": "GO661-haIkaE"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "sns.countplot(data=df,x='class');"
      ],
      "metadata": {
        "id": "9pbC7ocPTg9V",
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 449
        },
        "outputId": "9b7ddb13-83eb-4f0e-dab5-309935f176cb"
      },
      "execution_count": 6,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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0Eg/K3Z69+4th8Mhh8Nx0ctVERERevnll302OQAAgMb6WbFz5MgRWZalq666Sjt27FBcXJy9LzQ0VG3btlVwcLDPJwkAANBQPyt2OnXqJEmqr69vkskAAAD4WoN/6/mhQ4f08ccfq7S09IL4mTFjRqMnBgAA4AsNip3XXntNEyZMUJs2bRQfHy+Hw2HvczgcxA4AAAgYDYqdP/3pT3rqqac0depUX88HAADApxr0PTvffPON7r77bl/PBQAAwOcaFDt333231q9f7+u5AAAA+FyDLmN16dJF06dP17Zt29SjRw+1aNHCa/8f/vAHn0wOAACgsRoUO3/5y18UGRmpzZs3a/PmzV77HA4HsQMAAAJGg2LnyJEjvp4HAABAk2jQPTsAAACXiwa9s/PAAw/84P433nijQZMBAADwtQbFzjfffOO1XlNTo3/+858qKyu76C8IBQAA8JcGxc7y5csv2FZfX68JEybo6quvbvSkAAAAfMVn9+wEBQUpKytL8+bN89VDAgAANJpPb1A+fPiwamtrffmQAAAAjdKgy1hZWVle65Zl6cSJE/rggw+UkZHhk4kBAAD4QoNiZ/fu3V7rQUFBiouL0/PPP/+jn9QCAABoTg2KnY8//tjX8wAAAGgSDYqd806ePKmioiJJUteuXRUXF+eTSQEAAPhKg25QPnfunB544AElJCRo4MCBGjhwoNq1a6dx48bp22+/9fUcAQAAGqxBsZOVlaXNmzdr1apVKisrU1lZmf7+979r8+bN+uMf/+jrOQIAADRYgy5j/e1vf9P777+vm2++2d522223KSIiQvfcc48WLlzoq/kBAAA0SoPe2fn222/lcrku2N62bVsuYwEAgIDSoNhxu92aOXOmKisr7W3fffednnzySbndbp9NDgAAoLEadBnrxRdf1JAhQ9S+fXv16tVLkrRnzx6FhYVp/fr1Pp0gAABAYzQodnr06KFDhw7prbfe0sGDByVJI0eO1KhRoxQREeHTCQIAADRGg2Jn7ty5crlcGj9+vNf2N954QydPntTUqVN9MjkAAIDGatA9O6+++qq6det2wfZf//rXWrRoUaMnBQAA4CsNih2Px6OEhIQLtsfFxenEiRONnhQAAICvNCh2OnTooC1btlywfcuWLWrXrl2jJwUAAOArDbpnZ/z48Zo8ebJqamqUnJwsScrLy9Pjjz/O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sizddtttqqmpscd8++23eu655/Tf//3f+uSTT1RcXKzHHnvM3v/8889r8eLFeuONN/TZZ5/p9OnTWr58eRP9V4EJnnjiCT3//PPatWuXQkJC9MADD/zg+Ly8PBUVFWnDhg1avXq1zp49q9tvv12JiYkqKCjQrFmzvF6T+Bks4BIyMjKs4OBgq1WrVvZy1113Wb/97W+tRx55xB7XqVMna/jw4V7HTpo0yUpOTrbq6+sv+tiSrOXLlzfh7HE5ef/9960rrrjCCg8Pt2688UYrOzvb2rNnj2VZlvXpp59aTqfTqqys9Drm6quvtl599VXLsizL7XZbo0aNuuhjf/HFF5Yka8uWLfa2r7/+2oqIiLDee+89y7IsKzc315Jkffnll/aYBQsWWC6Xy15PSEiwcnJy7PWamhqrffv21rBhwxp38rhs5ebmWlFRURds//jjjy1J1saNG+1tH3zwgSXJ+u677yzLsqyZM2davXr1svdnZGRYLpfLqqqqsre9+uqrVmxsrH2MZVnWwoULLUnW7t27fX4+JuOdHfygW265RYWFhfYyf/78i47r27ev1/rYsWNVWFiorl276g9/+IPWr1/fHNPFZSo9PV3Hjx/XypUrNWTIEG3atEl9+vTR4sWLtWfPHp09e1axsbH2u0CRkZE6cuSIDh8+LEkqLCzUoEGDLvrYBw4cUEhIiPr3729vi42NVdeuXXXgwAF7W8uWLXX11Vfb6wkJCSotLZUklZeX68SJE16PERIScsHrHvi+nj172n9OSEiQJPs1dTE9evTwuk/nwIED6tmzp8LDw+1t/ILrhuEGZfygVq1aqUuXLj9p3Pf16dNHR44c0dq1a7Vx40bdc889SklJ0fvvv99UU8VlLjw8XLfeeqtuvfVWTZ8+XQ8++KBmzpyphx9+WAkJCdq0adMFx0RHR0uSIiIiGv38LVq08Fp3OBzck4NG+f5ryuFwSJLq6+svOf5f/x6F7/DODpqM0+nUvffeq9dee03vvvuu/va3v9n3WLRo0UJ1dXV+niECWWJios6dO6c+ffrI4/EoJCREXbp08VratGkj6X//BX2pj/F2795dtbW12r59u73t1KlTKioqUmJi4k+aS1RUlBISErweo7a2VgUFBY04Q+CHde/eXZ9//rkqKyvtbdu2bfPjjC5fxA6axAsvvKC3335bBw8e1BdffKFly5YpPj7e/pf4lVdeqby8PHk8Hn3zzTf+nSz86tSpU0pOTtZf//pXff755zpy5IiWLVumnJwcDRs2TCkpKXK73Ro+fLjWr1+vo0ePauvWrXriiSfsj/jOnDlTb7/9tmbOnKkDBw5o7969euaZZyRJ11xzjYYNG6bx48frs88+0549e/Sf//mf+tWvfqVhw4b95Hk+8sgjevrpp7VixQodPHhQDz/88A9+aRzQWP/xH/8hh8Oh8ePHa//+/VqzZo2ee+45f0/rskTsoEm0bt1aOTk56tu3r/r166ejR49qzZo1Cgr635fc888/rw0bNqhDhw66/vrr/Txb+FNkZKT69++vefPmaeDAgbruuus0ffp0jR8/Xn/+85/lcDi0Zs0aDRw4UPfff7+uvfZa3Xffffrqq6/kcrkk/e+3ei9btkwrV65U7969lZycrB07dtjPkZubq6SkJN1+++1yu92yLEtr1qy54NLVD/njH/+o0aNHKyMjQ263W61bt/b6eDvga5GRkVq1apX27t2r66+/Xk888YQd8fh5HBYXpQEAgMF4ZwcAABiN2AEAAEYjdgAAgNGIHQAAYDRiBwAAGI3YAQAARiN2AACA0YgdAABgNGIHwGXr6NGjcjgcKiws9PdUAAQwYgcAABiN2AEAAEYjdgAEvPr6euXk5KhLly4KCwtTx44d9dRTT10wrq6uTuPGjVPnzp0VERGhrl276qWXXvIas2nTJt1www1q1aqVoqOj9Zvf/EZfffWVJGnPnj265ZZb1Lp1azmdTiUlJdm/WR3A5SvE3xMAgB+TnZ2t1157TfPmzdNNN92kEydO6ODBgxeMq6+vV/v27bVs2TLFxsZq69ateuihh5SQkKB77rlHtbW1Gj58uMaPH6+3335b1dXV2rFjhxwOhyRp1KhRuv7667Vw4UIFBwersLDwZ/1mdACBid96DiCgnTlzRnFxcfrzn/+sBx980Gvf0aNH1blzZ+3evVu9e/e+6PETJ06Ux+PR+++/r9OnTys2NlabNm3Sb3/72wvGOp1Ovfzyy8rIyGiKUwHgJ1zGAhDQDhw4oKqqKg0aNOgnjV+wYIGSkpIUFxenyMhI/eUvf1FxcbEkKSYmRmPHjlVqaqruuOMOvfTSSzpx4oR9bFZWlh588EGlpKTo6aef1uHDh5vknAA0L2IHQECLiIj4yWPfeecdPfbYYxo3bpzWr1+vwsJC3X///aqurrbH5ObmKj8/XzfeeKPeffddXXvttdq2bZskadasWdq3b5/S0tL00UcfKTExUcuXL/f5OQFoXlzGAhDQKisrFRMTo/nz5//oZaxJkyZp//79ysvLs8ekpKTo66+/vuR38bjdbvXr10/z58+/YN/IkSN17tw5rVy50qfnBKB58c4OgIAWHh6uqVOn6vHHH9ebb76pw4cPa9u2bXr99dcvGHvNNddo165d+vDDD/XFF19o+vTp2rlzp73/yJEjys7OVn5+vr766iutX79ehw4dUvfu3fXdd99p4sSJ2rRpk7766itt2bJFO3fuVPfu3ZvzdAE0AT6NBSDgTZ8+XSEhIZoxY4aOHz+uhIQE/f73v79g3O9+9zvt3r1b9957rxwOh0aOHKmHH35Ya9eulSS1bNlSBw8e1JIlS3Tq1CklJCQoMzNTv/vd71RbW6tTp05pzJgxKikpUZs2bTRixAg9+eSTzX26AHyMy1gAAMBoXMYCAABGI3YAAIDRiB0AAGA0YgcAABiN2AEAAEYjdgAAgNGIHQAAYDRiBwAAGI3YAQAARiN2AACA0YgdAABgtP8Hzv3esaRTIE8AAAAASUVORK5CYII=\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**3.Was the number of passengers who survived greater or less than the number of passenger who did not survive**"
      ],
      "metadata": {
        "id": "0mrQfHW8JWFK"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "sns.countplot(data=df,x='survived')"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 466
        },
        "id": "kxlNr1PjI8uE",
        "outputId": "d12072cc-777a-41b4-d7fd-dfee7c0b6509"
      },
      "execution_count": 7,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "<Axes: xlabel='survived', ylabel='count'>"
            ]
          },
          "metadata": {},
          "execution_count": 7
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**4.From which town most number of passengers embarked?**"
      ],
      "metadata": {
        "id": "8Utn2FjSJ5Mm"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "sns.countplot(data=df,x='embark_town')"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 467
        },
        "id": "2SDtBtYMJutl",
        "outputId": "fb0a9b25-0cb4-4d05-b964-0fed7aaf2876"
      },
      "execution_count": 8,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "<Axes: xlabel='embark_town', ylabel='count'>"
            ]
          },
          "metadata": {},
          "execution_count": 8
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAjsAAAGxCAYAAACEFXd4AAAAOnRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjEwLjAsIGh0dHBzOi8vbWF0cGxvdGxpYi5vcmcvlHJYcgAAAAlwSFlzAAAPYQAAD2EBqD+naQAAOEtJREFUeJzt3XtcVXW+//H3RgS5uDdiwJZE09ESCrWwdGcpGYpmpaM1XUypzE4eNG+Z4xwvZRca7XY0L+WUl5PWjNN009TMBCfFS5pmXhDJwhlBTQVEExG+vz/6saYdWoToxtXr+Xisx4P1/X7XWp+1WcCbtdZe22GMMQIAALApP18XAAAAcD4RdgAAgK0RdgAAgK0RdgAAgK0RdgAAgK0RdgAAgK0RdgAAgK0RdgAAgK35+7qA2qC8vFz79+9X/fr15XA4fF0OAACoAmOMjh07pujoaPn5nf38DWFH0v79+xUTE+PrMgAAQDXs27dPjRs3Pms/YUdS/fr1Jf3wYjmdTh9XAwAAqqKoqEgxMTHW3/GzIexI1qUrp9NJ2AEA4CLzS7egcIMyAACwNcIOAACwNcIOAACwNcIOAACwNcIOAACwNcIOAACwNcIOAACwNcIOAACwNcIOAACwNcIOAACwNcIOAACwNcIOAACwNcIOAACwNcIOAACwNcIOAACwNX9fF2AXCaPn+7oE1CKbpgzwdQkAgP+PMzsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWfB52/v3vf+u+++5Tw4YNFRQUpPj4eH3++edWvzFGEyZMUKNGjRQUFKSkpCRlZ2d7rePIkSPq16+fnE6nwsLCNHDgQBUXF1/oXQEAALWQT8PO0aNH1bFjR9WtW1dLly7Vjh079MILL6hBgwbWmMmTJ2vq1KmaNWuW1q9fr5CQECUnJ+vkyZPWmH79+mn79u1asWKFFi9erNWrV+vhhx/2xS4BAIBaxmGMMb7a+B//+EetWbNG//znP8/Yb4xRdHS0Ro0apccee0ySVFhYqKioKM2dO1d33323du7cqbi4OG3cuFHt2rWTJC1btky33HKL/vWvfyk6OvoX6ygqKpLL5VJhYaGcTme19iVh9PxqLQd72jRlgK9LAADbq+rfb5+e2fnggw/Url073XnnnYqMjNTVV1+t2bNnW/179+5Vfn6+kpKSrDaXy6X27dsrMzNTkpSZmamwsDAr6EhSUlKS/Pz8tH79+gu3MwAAoFbyadj5+uuvNXPmTLVs2VLLly/X4MGD9eijj2revHmSpPz8fElSVFSU13JRUVFWX35+viIjI736/f39FR4ebo35qZKSEhUVFXlNAADAnvx9ufHy8nK1a9dOzz77rCTp6quv1ldffaVZs2YpJSXlvG03LS1NTz755HlbPwAAqD18emanUaNGiouL82qLjY1Vbm6uJMntdkuSDhw44DXmwIEDVp/b7dbBgwe9+k+fPq0jR45YY35q7NixKiwstKZ9+/bVyP4AAIDax6dhp2PHjsrKyvJq2717t5o2bSpJatasmdxut1auXGn1FxUVaf369fJ4PJIkj8ejgoICbdq0yRrz6aefqry8XO3btz/jdgMDA+V0Or0mAABgTz69jDVixAhdf/31evbZZ/WHP/xBGzZs0GuvvabXXntNkuRwODR8+HA9/fTTatmypZo1a6bx48crOjpavXv3lvTDmaDu3btr0KBBmjVrlkpLSzVkyBDdfffdVXonFgAAsDefhp1rr71W7777rsaOHatJkyapWbNmevnll9WvXz9rzOOPP67jx4/r4YcfVkFBgW644QYtW7ZM9erVs8YsWLBAQ4YM0c033yw/Pz/17dtXU6dO9cUuAQCAWsanz9mpLXjODmoaz9kBgPPvonjODgAAwPlG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALZG2AEAALbm07DzxBNPyOFweE2tWrWy+k+ePKnU1FQ1bNhQoaGh6tu3rw4cOOC1jtzc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c6XlKgK4JK/AUpOq+jN0vraP6vmlsB0QEPCL69i6dav27Nnj9c+RJJ08eVI5OTk6fvy4cnJyNHDgQA0aNMjqP336dKVP4T7bP46tWrXSo48+qsGDB+vjjz9WUlKS+vbt6zX+p3JyclRaWqqOHTtabXXr1tV1111nBfkbb7xRx44d0xdffKG1a9eqc+fOSkxM1HPPPSdJysjI0OjRo89ao8PhkNvtttU/gpzZucjExcXp+PHjio2N1b59+7Rv3z6rb8eOHSooKFBcXJwkKSIiQnl5eV7Lb9myxWs+ICBAZWVlv7qONWvW6P7779fvf/97xcfHy+1265tvvvnV6zmT06dP6/PPP7fms7KyVFBQYP23dqaaq/J64MIJDw9XcnKypk+fruPHj1fqr+q7S6655hpt375dl112mVq0aOE1VSVgrFu3rtJ8xXEUGxurrVu3etW3Zs0a+fn56YorrpBU+WeorKxMX3311S9u94orrtDGjRu92n46j5rXokULORyOs54F3rlzpyIiIhQWFiaHw/GzQba4uFgJCQnasmWL17R7927de++9Ki4uliTNnj3bq/+rr76qdNz93D94Dz30kL7++mv1799f27ZtU7t27TRt2rRzeh3CwsLUpk0bpaenKyMjQ4mJierUqZO++OIL7d69W9nZ2ZXO7Nj9H0HCTi11+PBhdenSRW+++aa+/PJL7d27V4sWLdLkyZPVq1cvJSUlKT4+Xv369dPmzZu1YcMGDRgwQJ07d7ZOqXfp0kWff/655s+fr+zsbE2cOLHSL+rLLrtM69ev1zfffKPvvvuuygd3y5Yt9Y9//ENbtmzR1q1bde+999bYD0bdunU1dOhQrV+/Xps2bdL999+vDh06WJcBLrvsMu3du1dbtmzRd999p5KSkiq9Hriwpk+frrKyMl133XV65513lJ2drZ07d2rq1KmVLi+dTWpqqo4cOaJ77rlHGzduVE5OjpYvX64HHnigSiF90aJFeuONN7R7925NnDhRGzZssD4wuF+/fqpXr55SUlL01VdfadWqVRo6dKj69+9vXV7t0qWLlixZoiVLlmjXrl0aPHhwlYLa0KFD9dFHH+nFF19Udna2Xn31VS1dutT6Q4fzo2HDhuratatmzJih77//3qsvPz9fCxYs0P333y+pcpDNzs7WiRMnrPlrrrlG2dnZioyMrBS0XS6XoqKiFB0dra+//rpSf7NmzX5V3TExMXrkkUf0j3/8Q6NGjdLs2bMl/ecM1I+P9d/97ncKCAjwet5aaWmpNm7c6PWPXefOnbVq1SqtXr1aiYmJCg8PV2xsrJ555hk1atRIl19++a+q8WJH2KmlQkND1b59e7300kvq1KmTrrrqKo0fP16DBg3SK6+8IofDoffff18NGjRQp06dlJSUpObNm+uvf/2rtY7k5GSNHz9ejz/+uK699lodO3ZMAwYM8NrOY489pjp16iguLk4RERGV7rk5mxdffFENGjTQ9ddfr9tuu03Jycm65ppramTfg4ODNWbMGN17773q2LGjQkNDvfarb9++6t69u2666SZFRETorbfeqtLrgQurefPm2rx5s2666SaNGjVKV111lbp27aqVK1dq5syZVVpHdHS01qxZo7KyMnXr1k3x8fEaPny4wsLC5Of3y7++nnzySb399ttq3bq15s+fr7feesv6gxAcHKzly5fryJEjuvbaa3XHHXfo5ptv1iuvvGIt/+CDDyolJcUKzs2bN9dNN930i9vt2LGjZs2apRdffFFt2rTRsmXLNGLECNWrV69K+43qe+WVV1RSUqLk5GStXr1a+/bt07Jly9S1a1ddfvnlmjBhgqQfguwrr7yiL774Qp9//rkeeeQRr7Mb/fr10yWXXKJevXrpn//8p/bu3av09HQ9+uij+te//iXph+MrLS1NU6dO1e7du7Vt2zbNmTNHL774YpXrHT58uJYvX669e/dq8+bNWrVqlXX2sWnTpnI4HFq8eLEOHTqk4uJihYSEaPDgwRo9erSWLVumHTt2aNCgQTpx4oQGDhxorTcxMVHLly+Xv7+/dZ9bYmKiFixYUOmszm+CL++OBn6q4jk7gN089NBD5oYbbvB1Gb8Je/fuNSkpKSYqKso4HA4jyfTp08ccP37cGvPvf//bdOvWzYSEhJiWLVuajz76qNJbz/Py8syAAQPMJZdcYgIDA03z5s3NoEGDTGFhoTVmwYIFpm3btiYgIMA0aNDAdOrUyXoXYsW7sb744gtrfMUz1FatWmWMMWbIkCHmd7/7nQkMDDQRERGmf//+5rvvvrPGT5o0ybjdbuNwOKx3AX7//fdm6NChVl0/feu5Mf95Z9pdd91ltb377rtGkpk1a5bX2KZNm5qXXnrJq61NmzZm4sSJVX3Jaz2HMb/ibRPAeTZ37lwNHz6cJ4biovf888+ra9euCgkJ0dKlSzVq1CjNmDFDDz30kK9L+82ZOHGiXnzxRa1YsUIdOnTwdTnwAd6NBQDnwYYNGzR58mQdO3ZMzZs319SpUwk6PvLkk0/qsssu07p163TddddV6RIo7IUzOwAAwNaItwAAwNYIOwAAwNYIOwAAwNYIOwAAwNYIOwAAwNYIOwB8KjExUcOHDz8v637iiSfUtm3b87JuABcPwg4AnMHcuXMVFhbm6zIA1AAeKgjAdowxVfqgUAC/DZzZAVBl5eXlSktLU7NmzRQUFKQ2bdro73//uyQpPT1dDodDy5cv19VXX62goCB16dJFBw8e1NKlSxUbGyun06l7773X69OlJen06dMaMmSIXC6XLrnkEo0fP14/ft7p//3f/6ldu3aqX7++3G637r33Xh08eNDqr9j20qVLlZCQoMDAQH322WeV6s/JyVHz5s01ZMgQ/dzzVNPT0/XAAw+osLBQDodDDodDTzzxhCTp6NGjGjBggBo0aKDg4GD16NFD2dnZkn4IWREREdZrIklt27ZVo0aNrPnPPvtMgYGB1mvgcDj0l7/8Rb///e8VHBysli1b6oMPPqjqtwRAVfjuY7kAXGyefvpp06pVK7Ns2TKTk5Nj5syZYwIDA016erpZtWqVkWQ6dOhgPvvsM7N582bTokUL07lzZ9OtWzezefNms3r1atOwYUPz3HPPWevs3LmzCQ0NNcOGDTO7du0yb775pgkODjavvfaaNeb11183H330kcnJyTGZmZnG4/GYHj16WP0V227durX5+OOPzZ49e8zhw4fNxIkTTZs2bYwxxmzdutW43W7zP//zP7+4nyUlJebll182TqfT5OXlmby8PHPs2DFjjDG33367iY2NNatXrzZbtmwxycnJpkWLFubUqVPGGGP69OljUlNTjTHGHDlyxAQEBBiXy2V27txpvYYdO3a0tiXJNG7c2CxcuNBkZ2ebRx991ISGhprDhw9X87sE4KcIOwCq5OTJkyY4ONisXbvWq33gwIHmnnvusQLHJ598YvWlpaUZSSYnJ8dq+6//+i+TnJxszXfu3NnExsaa8vJyq23MmDEmNjb2rLVs3LjRSLICSMW233vvPa9xFWFnzZo1pkGDBub555+v8v7OmTPHuFwur7bdu3cbSWbNmjVW23fffWeCgoLM3/72N2OMMVOnTjVXXnmlMcaY9957z7Rv39706tXLzJw50xhjTFJSkvnTn/5kLS/JjBs3zpovLi42kszSpUurXCuAn8dlLABVsmfPHp04cUJdu3ZVaGioNc2fP185OTnWuNatW1tfR0VFKTg4WM2bN/dq+/ElKEnq0KGDHA6HNe/xeJSdnW3dd7Np0ybddtttatKkierXr6/OnTtLknJzc73W065du0p15+bmqmvXrpowYYJGjRp1Dq+AtHPnTvn7+6t9+/ZWW8OGDXXFFVdo586dkqTOnTtrx44dOnTokDIyMpSYmKjExESlp6ertLRUa9euVWJiotd6f/yahYSEyOl0VnqNAFQfNygDqJLi4mJJ0pIlS3TppZd69QUGBlqBp27dula7w+Hwmq9oKy8vr/J2jx8/ruTkZCUnJ2vBggWKiIhQbm6ukpOTderUKa+xISEhlZaPiIhQdHS03nrrLT344INyOp1V3nZ1xMfHKzw8XBkZGcrIyNAzzzwjt9utP//5z9q4caNKS0t1/fXXey1zrq8RgJ/HmR0AVRIXF6fAwEDl5uaqRYsWXlNMTMw5rXv9+vVe8+vWrVPLli1Vp04d7dq1S4cPH9Zzzz2nG2+8Ua1atfpVZz2CgoK0ePFi1atXT8nJyTp27FiVlgsICKj0jq7Y2FidPn3aq97Dhw8rKytLcXFxkn4IKjfeeKPef/99bd++XTfccINat26tkpISvfrqq2rXrt0ZQxmA84ewA6BK6tevr8cee0wjRozQvHnzlJOTo82bN2vatGmaN2/eOa07NzdXI0eOVFZWlt566y1NmzZNw4YNkyQ1adJEAQEBmjZtmr7++mt98MEHeuqpp37V+kNCQrRkyRL5+/urR48e1lmqn3PZZZepuLhYK1eu1HfffacTJ06oZcuW6tWrlwYNGqTPPvtMW7du1X333adLL71UvXr1spZNTEzUW2+9pbZt2yo0NFR+fn7q1KmTFixYYF2CA3DhEHYAVNlTTz2l8ePHKy0tTbGxserevbuWLFmiZs2andN6BwwYoO+//17XXXedUlNTNWzYMD388MOSfrgMNXfuXC1atEhxcXF67rnn9Pzzz//qbYSGhmrp0qUyxqhnz546fvz4z46//vrr9cgjj+iuu+5SRESEJk+eLEmaM2eOEhISdOutt8rj8cgYo48++sjrUlTnzp1VVlbmdW9OYmJipTYAF4bDmJ952AQAAMBFjjM7AADA1gg7AH6TevTo4fUW+h9Pzz77rK/LA1CDuIwF4Dfp3//+t77//vsz9oWHhys8PPwCVwTgfCHsAAAAW+MyFgAAsDXCDgAAsDXCDgAAsDXCDgAAsDXCDgAAsDXCDgAAsDXCDgAAsDXCDgAAsLX/B4kJ0C7JSu72AAAAAElFTkSuQmCC\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**5.How does the survival rate differ between males and females?**"
      ],
      "metadata": {
        "id": "4vakQ7r4Klte"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "sns.countplot(data=df,x='sex',hue='survived')"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 466
        },
        "id": "VaRHEhB7KLQT",
        "outputId": "be00d9ed-3485-4a84-d35c-041e96ef7539"
      },
      "execution_count": 9,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "<Axes: xlabel='sex', ylabel='count'>"
            ]
          },
          "metadata": {},
          "execution_count": 9
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAjsAAAGwCAYAAABPSaTdAAAAOnRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjEwLjAsIGh0dHBzOi8vbWF0cGxvdGxpYi5vcmcvlHJYcgAAAAlwSFlzAAAPYQAAD2EBqD+naQAAKVFJREFUeJzt3X14zHe+//HXJJLI3SRN5EYqIqqLHHFTtgy2VNOEag+lWLWk5bCroUu2arUVB9umZd2U1bL2qDqVS0/1sr3KCjZLbEmDoEfdnVJ7xXXJnW2TECuJZH5/nDW/zkFLTDKTj+fjuua6zPdm5v2dvaae+53vDIvdbrcLAADAUF7uHgAAAKAxETsAAMBoxA4AADAasQMAAIxG7AAAAKMROwAAwGjEDgAAMFoLdw/gCerr63XhwgUFBwfLYrG4exwAAHAb7Ha7Ll26pJiYGHl53fr8DbEj6cKFC4qNjXX3GAAAoAHOnz+vNm3a3HI9sSMpODhY0v++WFar1c3TAACA21FZWanY2FjH3+O3QuxIjo+urFYrsQMAQDPzQ5egcIEyAAAwGrEDAACMRuwAAACjcc0OAAAepK6uTrW1te4ewyP4+PjI29v7rh+H2AEAwAPY7XYVFxervLzc3aN4lNDQUEVHR9/V7+AROwAAeIDroRMZGamAgIB7/kdu7Xa7rly5otLSUklS69atG/xYxA4AAG5WV1fnCJ3w8HB3j+Mx/P39JUmlpaWKjIxs8EdaXKAMAICbXb9GJyAgwM2TeJ7rr8ndXMdE7AAA4CHu9Y+ubsYVrwmxAwAAjEbsAAAAoxE7AADgBu3atdPy5csb9Tn27Nkji8XS6F+359tYAADgBgcPHlRgYKC7x3AJYgcAgHtITU2NfH19f3C7iIiIJpimafAxFgAAHm7z5s1KTEyUv7+/wsPDlZSUpKqqKg0cOFAzZsxw2nb48OF67rnnHPfbtWunhQsXasKECbJarZoyZYr69u2r2bNnO+1XVlYmHx8f7d2717Hf9Y+xnn32WY0ZM8Zp+9raWrVq1UobNmyQJNXX1yszM1Px8fHy9/dXt27dtHnzZqd9/vSnP+lHP/qR/P399eijj+pvf/vb3b84t4EzO02k56wN7h4B31GweIK7RwCA21JUVKSxY8dq0aJFevrpp3Xp0iX99a9/ld1uv+3H+O1vf6uMjAzNmzdPkpSdna1FixbpzTffdHy1+8MPP1RMTIx+8pOf3LD/uHHjNGrUKF2+fFlBQUGSpB07dujKlSt6+umnJUmZmZn64IMPtHr1aj344IPau3evfvaznykiIkIDBgzQ+fPnNWLECKWlpWnKlCk6dOiQfvWrX93ty3NbiB0AADxYUVGRrl27phEjRiguLk6SlJiYeEePMWjQIKewGD16tGbMmKHPPvvMETdZWVkaO3bsTX/XJiUlRYGBgdqyZYvGjx/v2P5f//VfFRwcrOrqar3xxhv685//LJvNJklq3769PvvsM61Zs0YDBgzQu+++qwceeEBLliyRJHXs2FHHjh3TW2+9decvyh3iYywAADxYt27d9NhjjykxMVGjRo3S2rVr9e23397RY/Tq1cvpfkREhJKTk7Vx40ZJ0rlz55SXl6dx48bddP8WLVpo9OjRju2rqqr0ySefOLY/c+aMrly5oscff1xBQUGO24YNG3T27FlJ0smTJ9W7d2+nx70eRo2NMzsAAHgwb29v7dq1S/v379fOnTu1cuVKvfrqq8rPz5eXl9cNH2fd7J9VuNm3qsaNG6cXX3xRK1euVFZWlhITE7/3jNG4ceM0YMAAlZaWateuXfL399fgwYMlSZcvX5Ykbdu2Tffff7/Tfn5+fnd8zK7GmR0AADycxWJRv379NH/+fB05ckS+vr7asmWLIiIiVFRU5Niurq5OX3755W095rBhw3T16lVlZ2crKyvrlmd1ruvbt69iY2P14YcfauPGjRo1apR8fHwkSQkJCfLz81NhYaE6dOjgdIuNjZUkde7cWQcOHHB6zM8///xOXoYG48wOAAAeLD8/Xzk5OUpOTlZkZKTy8/NVVlamzp07KzAwUOnp6dq2bZseeOABLV269LZ/oC8wMFDDhw/X3LlzdfLkSY0dO/YH93n22We1evVq/c///I92797tWB4cHKyXXnpJM2fOVH19vfr376+Kigrt27dPVqtVqamp+sUvfqElS5Zo1qxZ+rd/+zcVFBRo/fr1DXxV7gyxAwCAB7Nardq7d6+WL1+uyspKxcXFacmSJRoyZIhqa2v1xRdfaMKECWrRooVmzpypRx999LYfe9y4cXriiSf0yCOPqG3btre1/euvv664uDj169fPad3ChQsVERGhzMxMff311woNDdVDDz2kV155RZLUtm1bffzxx5o5c6ZWrlyp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AAC4mRGxs3TpUk2ePFnPP/+8EhIStHr1agUEBGjdunXuHg0AALhZC3cPcLdqampUUFCgOXPmOJZ5eXkpKSlJeXl5N92nurpa1dXVjvsVFRWSpMrKykabs676H4322Lhzl3zq3D0C/qkx33dNhfe3Z+H97Tka+/19/fHtdvv3btfsY+fixYuqq6tTVFSU0/KoqCidOnXqpvtkZmZq/vz5NyyPjY1tlBnhebq4ewD8f5kh7p4AhuH97UGa6P196dIlhYTc+rmafew0xJw5c5Senu64X19fr2+++Ubh4eGyWCxunAxNobKyUrGxsTp//rysVqu7xwHgQry/7y12u12XLl1STEzM927X7GOnVatW8vb2VklJidPykpISRUdH33QfPz8/+fn5OS0LDQ1trBHhoaxWK/8xBAzF+/ve8X1ndK5r9hco+/r6qmfPnsrJyXEsq6+vV05Ojmw2mxsnAwAAnqDZn9mRpPT0dKWmpqpXr156+OGHtXz5clVVVen5559392gAAMDNjIidMWPGqKysTBkZGSouLlb37t2VnZ19w0XLgPS/H2POmzfvho8yATR/vL9xMxb7D31fCwAAoBlr9tfsAAAAfB9iBwAAGI3YAQAARiN2gH967rnnNHz4cHePAdwT7Ha7pkyZorCwMFksFh09etQtc/ztb39z6/OjaRjxbSwAQPOSnZ2t9evXa8+ePWrfvr1atWrl7pFgMGIHANDkzp49q9atW6tv377uHgX3AD7GQrM0cOBATZ8+XTNmzNB9992nqKgorV271vFjksHBwerQoYO2b98uSaqrq9OkSZMUHx8vf39/dezYUW+//fb3Pkd9fb0yMzMd+3Tr1k2bN29uisMDjPbcc89p+vTpKiwslMViUbt27X7w/bZnzx5ZLBbt2LFDPXr0kL+/vwYNGqTS0lJt375dnTt3ltVq1bPPPqsrV6449svOzlb//v0VGhqq8PBwPfnkkzp79uz3zvfll19qyJAhCgoKUlRUlMaPH6+LFy822uuBxkfsoNl6//331apVKx04cEDTp0/X1KlTNWrUKPXt21eHDx9WcnKyxo8frytXrqi+vl5t2rTRRx99pBMnTigjI0OvvPKK/uu//uuWj5+ZmakNGzZo9erVOn78uGbOnKmf/exnys3NbcKjBMzz9ttva8GCBWrTpo2Kiop08ODB236//fu//7t+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\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**6.which class passengers survived more in number**"
      ],
      "metadata": {
        "id": "WINTN5xXKzIt"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "sns.countplot(data=df,x='class',hue='survived')"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 466
        },
        "id": "FH3btHoLKxwh",
        "outputId": "56641bfc-3f14-476f-a9d1-3f7969883636"
      },
      "execution_count": 10,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "<Axes: xlabel='class', ylabel='count'>"
            ]
          },
          "metadata": {},
          "execution_count": 10
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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ODhYr7zyiu655x6FhoYqKytL99xzjyRp//796tq1q/Ly8nTjjTfq008/1e23364jR44oPDxckrRgwQJNmTJFR48elbe390Vts7KyUoGBgaqoqJDVam22fQOAX7uEyYtdXYJbyH9llKtLMIWL/f12m2t26uvr9cEHH6iqqko2m035+fmqq6tTYmKiMaZLly6KiYlRXl6eJCkvL0/x8fFG0JGkpKQkVVZWGkeHzqWmpkaVlZVOEwAAMCeXh53du3crICBAPj4+euyxx7RixQrFxcXJbrfL29tbQUFBTuPDw8Nlt9slSXa73SnonOk/03c+mZmZCgwMNKbo6Oim3SkAAOA2XB52OnfurIKCAm3ZskXjx49Xamqq9u7d26zbzMjIUEVFhTEdPny4WbcHAABcx+XvxvL29lbHjh0lSQkJCdq2bZveeOMN3X///aqtrVV5ebnT0Z3S0lLj7acRERHaunWr0/rO3K11oTek+vj4yMfHp4n3BAAAuCOXH9n5uYaGBtXU1CghIUFeXl7Kzs42+goLC1VcXCybzSZJstls2r17t8rKyowx69evl9VqVVxcXIvXDgAA3I9Lj+xkZGQoOTlZMTExOnHihLKyspSTk6O1a9cqMDBQY8aMUXp6uoKDg2W1WvXEE0/IZrPpxhtvlCQNGjRIcXFxeuihhzRr1izZ7XY9++yzSktL48gNAACQ5OKwU1ZWplGjRqmkpESBgYHq1q2b1q5dq9tuu02S9Prrr6tVq1YaMWKEampqlJSUpL/97W/G8h4eHlq1apXGjx8vm82m1q1bKzU1VTNnznTVLgEAADfjds/ZcQWeswMALYPn7PyI5+w0jSvuOTsAAADNgbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMjbADAABMzaVhJzMzU71791abNm0UFham4cOHq7Cw0GlMv379ZLFYnKbHHnvMaUxx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MV6S7rrrLlksFmMev07l5eX68ssv9fLLL6t///6KjY3VDTfcoIyMDN15553GmEcffVShoaGyWq0aMGCAdu7c6bSelStXqnfv3vL19VXbtm111113GX3ff/+9Ro0apd/85jfy9/dXcnKyvvnmG6N/0aJFCgoK0tq1a9W1a1cFBARo8ODBTj9s9fX1Sk9PV1BQkEJCQvT000//4puWYT4//bcwMDBQFovFqe2nASY/P1+9evWSv7+/brrpJqdQ9PPTWGdOib7wwguKiopS586dJUlbt25Vz5495evrq169emnHjh0ttq9mQthBk3j11VfVvXt37dixQ1OnTtWbb76pjz/+WP/85z9VWFioJUuWGKFm27ZtkqSFCxeqpKTEmMev05n/w/3www9VU1NzzjH33nuvysrK9Omnnyo/P1/XX3+9Bg4cqOPHj0uSPvnkE911110aMmSIduzYoezsbN1www3G8qNHj9b27dv18ccfKy8vTw6HQ0OGDFFdXZ0x5tSpU3r11Vf1P//zP9qwYYOKi4v11FNPGf2zZ8/WokWL9M4772jjxo06fvy4VqxY0UyfCszgmWee0ezZs7V9+3Z5enrqkUceueD47OxsFRYWav369Vq1apVOnjyp22+/XXFxccrPz9dzzz3n9J3EJXAA55Gamurw8PBwtG7d2pjuuecex6233ur405/+ZIyLjY11DB8+3GnZJ554wjFgwABHQ0PDOdctybFixYpmrB5XkuXLlzt+85vfOHx9fR033XSTIyMjw7Fz506Hw+FwfPnllw6r1eqorq52WqZDhw6Ot956y+FwOBw2m82RkpJyznV//fXXDkmOr776ymj77rvvHH5+fo5//vOfDofD4Vi4cKFDkuPAgQPGmHnz5jnCw8ON+cjISMesWbOM+bq6Oke7du0cw4YNu7ydxxVr4cKFjsDAwLPav/jiC4ckx2effWa0ffLJJw5Jjh9++MHhcDgc06dPd3Tv3t3oT01NdYSHhztqamqMtrfeessREhJiLONwOBzz5893SHLs2LGjyffHzDiygwvq37+/CgoKjOnNN98857hevXo5zY8ePVoFBQXq3Lmz/vjHP2rdunUtUS6uUCNGjNCRI0f08ccfa/DgwcrJydH111+vRYsWaefOnTp58qRCQkKMo0ABAQEqKirSwYMHJUkFBQUaOHDgOde9b98+eXp6qk+fPkZbSEiIOnfurH379hlt/v7+6tChgzEfGRmpsrIySVJFRYVKSkqc1uHp6XnW9x74qW7duhl/R0ZGSpLxnTqX+Ph4p+t09u3bp27dusnX19do4wXXjcMFyrig1q1bq2PHjhc17qeuv/56FRUV6dNPP9Vnn32m++67T4mJiVq+fHlzlYornK+vr2677Tbddtttmjp1qh599FFNnz5djz/+uCIjI5WTk3PWMkFBQZIkPz+/y96+l5eX07zFYuGaHFyWn36nLBaLJKmhoeG843/+7yiaDkd20GysVqvuv/9+vf3221q6dKn+9a9/GddYeHl5qb6+3sUVwp3FxcWpqqpK119/vex2uzw9PdWxY0enqW3btpJ+/D/o893G27VrV50+fVpbtmwx2o4dO6bCwkLFxcVdVC2BgYGKjIx0Wsfp06eVn59/GXsIXFjXrl21a9cuVVdXG22bN292YUVXLsIOmsVrr72m999/X/v379fXX3+tZcuWKSIiwvg/8auuukrZ2dmy2+36/vvvXVssXOrYsWMaMGCA3nvvPe3atUtFRUVatmyZZs2apWHDhikxMVE2m03Dhw/XunXrdOjQIW3atEnPPPOMcYvv9OnT9f7772v69Onat2+fdu/erZdfflmS1KlTJw0bNkxjx47Vxo0btXPnTv3+97/Xb3/7Ww0bNuyi6/zTn/6kl156SR9++KH279+vxx9//IIPjQMu14MPPiiLxaKxY8dq7969Wr16tV599VVXl3VFIuygWbRp00azZs1Sr1691Lt3bx06dEirV69Wq1Y/fuVmz56t9evXKzo6Wj179nRxtXClgIAA9enTR6+//rr69u2r6667TlOnTtXYsWP117/+VRaLRatXr1bfvn318MMP65prrtEDDzygb7/9VuHh4ZJ+fKr3smXL9PHHH6tHjx4aMGCAtm7damxj4cKFSkhI0O233y6bzSaHw6HVq1efderqQp588kk99NBDSk1Nlc1mU5s2bZxubweaWkBAgFauXKndu3erZ8+eeuaZZ4wQj0tjcXBSGgAAmBhHdgAAgKkRdgAAgKkRdgAAgKkRdgAAgKkRdgAAgKkRdgAAgKkRdgAAgKkRdgAAgKkRdgBcsQ4dOiSLxaKCggJXlwLAjRF2AACAqRF2AACAqRF2ALi9hoYGzZo1Sx07dpSPj49iYmL0wgsvnDWuvr5eY8aMUfv27eXn56fOnTvrjTfecBqTk5OjG264Qa1bt1ZQUJBuvvlmffvtt5KknTt3qn///mrTpo2sVqsSEhKMN6sDuHJ5uroAAPglGRkZevvtt/X666/rlltuUUlJifbv33/WuIaGBrVr107Lli1TSEiINm3apHHjxikyMlL33XefTp8+reHDh2vs2LF6//33VVtbq61bt8pisUiSUlJS1LNnT82fP18eHh4qKCi4pDejA3BPvPUcgFs7ceKEQkND9de//lWPPvqoU9+hQ4fUvn177dixQz169Djn8hMmTJDdbtfy5ct1/PhxhYSEKCcnR7feeutZY61Wq+bOnavU1NTm2BUALsJpLABubd++faqpqdHAgQMvavy8efOUkJCg0NBQBQQE6O9//7uKi4slScHBwRo9erSSkpJ0xx136I033lBJSYmxbHp6uh599FElJibqpZde0sGDB5tlnwC0LMIOALfm5+d30WM/+OADPfXUUxozZozWrVungoICPfzww6qtrTXGLFy4UHl5ebrpppu0dOlSXXPNNdq8ebMk6bnnntOePXs0dOhQff7554qLi9OKFSuafJ8AtCxOYwFwa9XV1QoODtabb775i6exnnjiCe3du1fZ2dnGmMTERH333XfnfRaPzWZT79699eabb57VN3LkSFVVVenjjz9u0n0C0LI4sgPArfn6+mrKlCl6+umntXjxYh08eFCbN2/WP/7xj7PGdurUSdu3b9fatWv19ddfa+rUqdq2bZvRX1RUpIyMDOXl5enbb7/VunXr9M0336hr16764YcfNGHCBOXk5Ojbb7/VV199pW3btqlr164tubsAmgF3YwFwe1OnTpWnp6emTZumI0eOKDIyUo899thZ4/7whz9ox44duv/++2WxWDRy5Eg9/vjj+vTTTyVJ/v7+2r9/v959910dO3ZMkZGRSktL0x/+8AedPn1ax44d06hRo1RaWqq2bdvq7rvv1owZM1p6dwE0MU5jAQAAU+M0FgAAMDXCDgAAMDXCDgAAMDXCDgAAMDXCDgAAMDXCDgAAMDXCDgAAMDXCDgAAMDXCDgAAMDXCDgAAMDXCDgAAMLX/D9oE9qrM5NkrAAAAAElFTkSuQmCC\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**7.Which town embarked passengers survived least in number?**"
      ],
      "metadata": {
        "id": "SjEHlqrsLcII"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "sns.countplot(data=df,x='embark_town',hue='survived');"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 450
        },
        "id": "eqjU4K8qLu54",
        "outputId": "b1dbe177-c86b-479b-843f-2b006f6932e5"
      },
      "execution_count": 11,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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2rdvn2JiYrRhwwZ16NBBS5cu1e9+9zt9++23Cg8PlyTNmjVLY8eO1dGjR+Xj41OldRYXFysoKEhFRUVyOp3Vqjt+zLxqLWc3W18c5O4SAAC/EVX9++0x9+xUVFTo3XffVWlpqRISErR161aVl5erW7duVptWrVqpcePG2rBhgyRpw4YNiouLs4KOJCUlJam4uNg6O3Q+ZWVlKi4udhkAAIA9uT3s7N69W4GBgfL19dXjjz+uhQsXKjY2VgUFBfLx8VFwcLBL+/DwcBUUFEiSCgoKXILO2fln511IRkaGgoKCrCEqKqpmNwoAAHgMt4edli1baseOHdq0aZOGDh2q1NRU7d2794quc9y4cSoqKrKGw4cPX9H1AQAA96nl7gJ8fHzUvHlzSVJ8fLw2b96s//zP/9T999+v06dP6/jx4y5nd44cOaKIiAhJUkREhL788kuX/s4+rXW2zfn4+vrK19e3hrcEAAB4Iref2fmlyspKlZWVKT4+XrVr19aqVauseTk5OcrLy1NCQoIkKSEhQbt371ZhYaHVZuXKlXI6nYqNjb3qtQMAAM/j1jM748aNU3Jysho3bqwTJ05owYIFyszM1PLlyxUUFKTBgwcrPT1dISEhcjqdGj58uBISEtShQwdJUo8ePRQbG6uBAwfqhRdeUEFBgcaPH6+0tDTO3AAAAEluDjuFhYUaNGiQ8vPzFRQUpNatW2v58uXq3r27JOmVV16Rl5eX+vfvr7KyMiUlJem1116zlvf29taiRYs0dOhQJSQkKCAgQKmpqXrmmWfctUkAAMDDeNx7dtyB9+zUHN6zAwC4Wq659+wAAABcCYQdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga4QdAABga24NOxkZGbr11ltVt25dhYWFqW/fvsrJyXFpk5iYKIfD4TI8/vjjLm3y8vLUq1cv+fv7KywsTGPGjNGZM2eu5qYAAAAPVcudK8/KylJaWppuvfVWnTlzRk899ZR69OihvXv3KiAgwGo3ZMgQPfPMM9a4v7+/9XVFRYV69eqliIgIrV+/Xvn5+Ro0aJBq166t55577qpuDwAA8DxuDTvLli1zGZ87d67CwsK0detWderUyZru7++viIiI8/axYsUK7d27V59//rnCw8PVtm1bTZkyRWPHjtXTTz8tHx+fK7oNAADAs3nUPTtFRUWSpJCQEJfp8+fPV4MGDXTTTTdp3LhxOnnypDVvw4YNiouLU3h4uDUtKSlJxcXF2rNnz3nXU1ZWpuLiYpcBAADYk1vP7PxcZWWlRo4cqY4dO+qmm26ypg8YMEDR0dGKjIzUrl27NHbsWOXk5Oijjz6SJBUUFLgEHUnWeEFBwXnXlZGRocmTJ1+hLQEAAJ7EY8JOWlqavvrqK61du9Zl+mOPPWZ9HRcXp4YNG+quu+5Sbm6urr/++mqta9y4cUpPT7fGi4uLFRUVVb3CAQCAR/OIy1jDhg3TokWLtHr1ajVq1Oiibdu3by9JOnjwoCQpIiJCR44ccWlzdvxC9/n4+vrK6XS6DAAAwJ7cGnaMMRo2bJgWLlyoL774Qk2bNv3VZXbs2CFJatiwoSQpISFBu3fvVmFhodVm5cqVcjqdio2NvSJ1AwCAa0e1wk7Xrl11/Pjxc6YXFxera9euVe4nLS1Nb7/9thYsWKC6deuqoKBABQUF+vHHHyVJubm5mjJlirZu3apvvvlGn376qQYNGqROnTqpdevWkqQePXooNjZWAwcO1M6dO7V8+XKNHz9eaWlp8vX1rc7mAQAAG6lW2MnMzNTp06fPmX7q1Cn94x//qHI/M2fOVFFRkRITE9WwYUNreO+99yRJPj4++vzzz9WjRw+1atVKo0ePVv/+/fXZZ59ZfXh7e2vRokXy9vZWQkKCHnzwQQ0aNMjlvTwAAOC365JuUN61a5f19d69e12edqqoqNCyZct03XXXVbk/Y8xF50dFRSkrK+tX+4mOjtaSJUuqvF4AAPDbcUlhp23bttZHNpzvcpWfn5+mT59eY8UBAABcrksKO4cOHZIxRs2aNdOXX36p0NBQa56Pj4/CwsLk7e1d40UCAABU1yWFnejoaEk/vQAQAADgWlDtlwoeOHBAq1evVmFh4TnhZ+LEiZddGAAAQE2oVtiZPXu2hg4dqgYNGigiIkIOh8Oa53A4CDsAAMBjVCvs/PnPf9azzz6rsWPH1nQ9AAAANapa79n54YcfdN9999V0LQAAADWuWmHnvvvu04oVK2q6FgAAgBpXrctYzZs314QJE7Rx40bFxcWpdu3aLvOfeOKJGikOAADgclUr7Pztb39TYGCgsrKyznnDscPhIOwAAACPUa2wc+jQoZquAwAA4Iqo1j07AAAA14pqndl55JFHLjr/zTffrFYxAAAANa1aYeeHH35wGS8vL9dXX32l48ePn/cDQgEAANylWmFn4cKF50yrrKzU0KFDdf311192UQAAADWlxu7Z8fLyUnp6ul555ZWa6hIAAOCy1egNyrm5uTpz5kxNdgkAAHBZqnUZKz093WXcGKP8/HwtXrxYqampNVIYAABATahW2Nm+fbvLuJeXl0JDQ/Xyyy//6pNaAAAAV1O1ws7q1atrug4AAIArolph56yjR48qJydHktSyZUuFhobWSFEAAAA1pVphp7S0VMOHD9e8efNUWVkpSfL29tagQYM0ffp0+fv712iRuHbkPRPn7hI8QuOJu91dAgDgf1Xraaz09HRlZWXps88+0/Hjx3X8+HF98sknysrK0ujRo2u6RgAAgGqr1pmdDz/8UB988IESExOtaXfffbf8/Pz0hz/8QTNnzqyp+gAAAC5Ltc7snDx5UuHh4edMDwsL08mTJy+7KAAAgJpSrbCTkJCgSZMm6dSpU9a0H3/8UZMnT1ZCQkKNFQcAAHC5qnUZa9q0aerZs6caNWqkNm3aSJJ27twpX19frVixokYLBAAAuBzVCjtxcXE6cOCA5s+fr3379kmSHnjgAaWkpMjPz69GCwQAALgc1Qo7GRkZCg8P15AhQ1ymv/nmmzp69KjGjh1bI8UBAABcrmrds/P666+rVatW50y/8cYbNWvWrMsuCgAAoKZUK+wUFBSoYcOG50wPDQ1Vfn5+lfvJyMjQrbfeqrp16yosLEx9+/a13sh81qlTp5SWlqb69esrMDBQ/fv315EjR1za5OXlqVevXvL391dYWJjGjBnDp68DAABJ1Qw7UVFRWrdu3TnT161bp8jIyCr3k5WVpbS0NG3cuFErV65UeXm5evToodLSUqvNqFGj9Nlnn+n9999XVlaWvv32W/Xr18+aX1FRoV69eun06dNav3693nrrLc2dO1cTJ06szqYBAACbqdY9O0OGDNHIkSNVXl6url27SpJWrVqlP/3pT5f0BuVly5a5jM+dO1dhYWHaunWrOnXqpKKiIr3xxhtasGCBtZ45c+YoJiZGGzduVIcOHbRixQrt3btXn3/+ucLDw9W2bVtNmTJFY8eO1dNPPy0fH5/qbCIAALCJaoWdMWPG6NixY/r3f/93nT59WpJUp04djR07VuPGjat2MUVFRZKkkJAQSdLWrVtVXl6ubt26WW1atWqlxo0ba8OGDerQoYM2bNiguLg4l5ccJiUlaejQodqzZ49uvvnmatcDAACufdUKOw6HQ3/5y180YcIEZWdny8/PTy1atJCvr2+1C6msrNTIkSPVsWNH3XTTTZJ+ujfIx8dHwcHBLm3Dw8NVUFBgtfnl25zPjp9t80tlZWUqKyuzxouLi6tdNwAA8GzVCjtnBQYG6tZbb62RQtLS0vTVV19p7dq1NdLfxWRkZGjy5MlXfD0AAMD9qnWDck0bNmyYFi1apNWrV6tRo0bW9IiICJ0+fVrHjx93aX/kyBFFRERYbX75dNbZ8bNtfmncuHEqKiqyhsOHD9fg1gAAAE/i1rBjjNGwYcO0cOFCffHFF2ratKnL/Pj4eNWuXVurVq2ypuXk5CgvL8/6DK6EhATt3r1bhYWFVpuVK1fK6XQqNjb2vOv19fWV0+l0GQAAgD1d1mWsy5WWlqYFCxbok08+Ud26da17bIKCguTn56egoCANHjxY6enpCgkJkdPp1PDhw5WQkKAOHTpIknr06KHY2FgNHDhQL7zwggoKCjR+/HilpaVd1j1EAADAHtwadmbOnClJSkxMdJk+Z84cPfTQQ5KkV155RV5eXurfv7/KysqUlJSk1157zWrr7e2tRYsWaejQoUpISFBAQIBSU1P1zDPPXK3NAAAAHsytYccY86tt6tSpoxkzZmjGjBkXbBMdHa0lS5bUZGkAAMAmPOIGZQAAgCuFsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGyNsAMAAGzNrWFnzZo16t27tyIjI+VwOPTxxx+7zH/ooYfkcDhchp49e7q0+f7775WSkiKn06ng4GANHjxYJSUlV3ErAACAJ3Nr2CktLVWbNm00Y8aMC7bp2bOn8vPzreGdd95xmZ+SkqI9e/Zo5cqVWrRokdasWaPHHnvsSpcOAACuEbXcufLk5GQlJydftI2vr68iIiLOOy87O1vLli3T5s2b1a5dO0nS9OnTdffdd+ull15SZGRkjdcMAACuLR5/z05mZqbCwsLUsmVLDR06VMeOHbPmbdiwQcHBwVbQkaRu3brJy8tLmzZtcke5AADAw7j1zM6v6dmzp/r166emTZsqNzdXTz31lJKTk7VhwwZ5e3uroKBAYWFhLsvUqlVLISEhKigouGC/ZWVlKisrs8aLi4uv2DYAAAD38uiw88c//tH6Oi4uTq1bt9b111+vzMxM3XXXXdXuNyMjQ5MnT66JEgEAgIfz+MtYP9esWTM1aNBABw8elCRFRESosLDQpc2ZM2f0/fffX/A+H0kaN26cioqKrOHw4cNXtG4AAOA+11TY+de//qVjx46pYcOGkqSEhAQdP35cW7dutdp88cUXqqysVPv27S/Yj6+vr5xOp8sAAADsya2XsUpKSqyzNJJ06NAh7dixQyEhIQoJCdHkyZPVv39/RUREKDc3V3/605/UvHlzJSUlSZJiYmLUs2dPDRkyRLNmzVJ5ebmGDRumP/7xjzyJBQAAJLn5zM6WLVt088036+abb5Ykpaen6+abb9bEiRPl7e2tXbt26Z577tENN9ygwYMHKz4+Xv/4xz/k6+tr9TF//ny1atVKd911l+6++27dcccd+tvf/uauTQIAAB7GrWd2EhMTZYy54Pzly5f/ah8hISFasGBBTZYFAABs5Jq6ZwcAAOBSEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtEXYAAICtuTXsrFmzRr1791ZkZKQcDoc+/vhjl/nGGE2cOFENGzaUn5+funXrpgMHDri0+f7775WSkiKn06ng4GANHjxYJSUlV3ErAACAJ3Nr2CktLVWbNm00Y8aM885/4YUX9Oqrr2rWrFnatGmTAgIClJSUpFOnTlltUlJStGfPHq1cuVKLFi3SmjVr9Nhjj12tTQAAAB6uljtXnpycrOTk5PPOM8Zo2rRpGj9+vPr06SNJmjdvnsLDw/Xxxx/rj3/8o7Kzs7Vs2TJt3rxZ7dq1kyRNnz5dd999t1566SVFRkZetW0BAACeyWPv2Tl06JAKCgrUrVs3a1pQUJDat2+vDRs2SJI2bNig4OBgK+hIUrdu3eTl5aVNmzZdsO+ysjIVFxe7DAAAwJ48NuwUFBRIksLDw12mh4eHW/MKCgoUFhbmMr9WrVoKCQmx2pxPRkaGgoKCrCEqKqqGqwcAAJ7CY8POlTRu3DgVFRVZw+HDh91dEgAAuEI8NuxERERIko4cOeIy/ciRI9a8iIgIFRYWusw/c+aMvv/+e6vN+fj6+srpdLoMAADAnjw27DRt2lQRERFatWqVNa24uFibNm1SQkKCJCkhIUHHjx/X1q1brTZffPGFKisr1b59+6teMwAA8DxufRqrpKREBw8etMYPHTqkHTt2KCQkRI0bN9bIkSP15z//WS1atFDTpk01YcIERUZGqm/fvpKkmJgY9ezZU0OGDNGsWbNUXl6uYcOG6Y9//CNPYgEAAEluDjtbtmxRly5drPH09HRJUmpqqubOnas//elPKi0t1WOPPabjx4/rjjvu0LJly1SnTh1rmfnz52vYsGG666675OXlpf79++vVV1+96tsCAAA8k8MYY9xdhLsVFxcrKChIRUVF1b5/J37MvBqu6tq0sO6L7i7BIzSeuNvdJeBn8p6Jc3cJHoHjEnZT1b/fHnvPDgAAQE0g7AAAAFsj7AAAAFsj7AAAAFsj7AAAAFsj7AAAAFsj7AAAAFsj7AAAAFsj7AAAAFsj7AAAAFsj7AAAAFsj7AAAAFsj7AAAAFsj7AAAAFur5e4CAFw58WPmubsEj7CwrrsrAOBOnNkBAAC2RtgBAAC2RtgBAAC2RtgBAAC2RtgBAAC2RtgBAAC2RtgBAAC2RtgBAAC2RtgBAAC2RtgBAAC2RtgBAAC2RtgBAAC2RtgBAAC2RtgBAAC2RtgBAAC25tFh5+mnn5bD4XAZWrVqZc0/deqU0tLSVL9+fQUGBqp///46cuSIGysGAACexqPDjiTdeOONys/Pt4a1a9da80aNGqXPPvtM77//vrKysvTtt9+qX79+bqwWAAB4mlruLuDX1KpVSxEREedMLyoq0htvvKEFCxaoa9eukqQ5c+YoJiZGGzduVIcOHa52qQAAwAN5/JmdAwcOKDIyUs2aNVNKSory8vIkSVu3blV5ebm6detmtW3VqpUaN26sDRs2XLTPsrIyFRcXuwwAAMCePDrstG/fXnPnztWyZcs0c+ZMHTp0SHfeeadOnDihgoIC+fj4KDg42GWZ8PBwFRQUXLTfjIwMBQUFWUNUVNQV3AoAAOBOHn0ZKzk52fq6devWat++vaKjo/X3v/9dfn5+1e533LhxSk9Pt8aLi4sJPAAA2JRHn9n5peDgYN1www06ePCgIiIidPr0aR0/ftylzZEjR857j8/P+fr6yul0ugwAAMCePPrMzi+VlJQoNzdXAwcOVHx8vGrXrq1Vq1apf//+kqScnBzl5eUpISHBzZUCAM4nfsw8d5fgEba+OMjdJfymeHTYefLJJ9W7d29FR0fr22+/1aRJk+Tt7a0HHnhAQUFBGjx4sNLT0xUSEiKn06nhw4crISGBJ7EAAIDFo8POv/71Lz3wwAM6duyYQkNDdccdd2jjxo0KDQ2VJL3yyivy8vJS//79VVZWpqSkJL322mturhoAAHgSjw4777777kXn16lTRzNmzNCMGTOuUkUAAOBac03doAwAAHCpCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWCDsAAMDWPPrjIgAAsKO8Z+LcXYJHaDxx91VZD2d2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArRF2AACArdkm7MyYMUNNmjRRnTp11L59e3355ZfuLgkAAHgAW4Sd9957T+np6Zo0aZK2bdumNm3aKCkpSYWFhe4uDQAAuJktws7UqVM1ZMgQPfzww4qNjdWsWbPk7++vN998092lAQAAN7vmw87p06e1detWdevWzZrm5eWlbt26acOGDW6sDAAAeIJa7i7gcn333XeqqKhQeHi4y/Tw8HDt27fvvMuUlZWprKzMGi8qKpIkFRcXV7uOirIfq72snZyoXeHuEjzC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XGPHjlWDBg20evXqKu97T2ebj4uwqzp16qh79+7q3r27JkyYoEcffVSTJk3S6NGjf3VZLy+vc/7olJeXV3ndtWvXtr52OBySfvpEeemnH96VK1fqpZdeUvPmzeXn56d77733nJszz9fHxfq90n6+7rPrv1rr/i1p0aKFHA6H9u3b96ttL/Y9KSkpUe/evfWXv/zlnOXOBnBJLoGlJlX1Z+hKrR/V82th28fH51f72Llzpw4ePOjyz5EknTp1Srm5uSotLVVubq4GDx6sIUOGWPPPnDlzzqdwX+gfx1atWumJJ57Q0KFDtWLFCnXr1k39+/d3af9Lubm5Ki8vV8eOHa1ptWvX1m233WYF+TvvvFMnTpzQ9u3btX79enXu3FmJiYl6/vnnJUlZWVkaM2bMBWt0OByKiIiw1T+CnNm5xsTGxqq0tFQxMTE6fPiwDh8+bM3bu3evjh8/rtjYWElSaGio8vPzXZbfsWOHy7iPj48qKiouuY5169bpoYce0u9//3vFxcUpIiJC33zzzSX3cz5nzpzRli1brPGcnBwdP37c+m/tfDVXZX/g6gkJCVFSUpJmzJih0tLSc+ZX9emSW265RXv27FGTJk3UvHlzl6EqAWPjxo3njJ89jmJiYrRz506X+tatWycvLy+1bNlS0rk/QxUVFfrqq69+db0tW7bU5s2bXab9chw1r3nz5nI4HBc8C5ydna3Q0FAFBwfL4XBcNMiWlJQoPj5eO3bscBn279+vAQMGqKSkRJI0e/Zsl/lfffXVOcfdxf7Be/TRR/X1119r4MCB2r17t9q1a6fp06df1n4IDg5WmzZtlJmZqaysLCUmJqpTp07avn279u/frwMHDpxzZsfu/wgSdjzUsWPH1LVrV7399tvatWuXDh06pPfff18vvPCC+vTpo27duikuLk4pKSnatm2bvvzySw0aNEidO3e2Tql37dpVW7Zs0bx583TgwAFNmjTpnF/UTZo00aZNm/TNN9/ou+++q/LB3aJFC3300UfasWOHdu7cqQEDBtTYD0bt2rU1fPhwbdq0SVu3btVDDz2kDh06WJcBmjRpokOHDmnHjh367rvvVFZWVqX9gatrxowZqqio0G233aYPP/xQBw4cUHZ2tl599dVzLi9dSFpamr7//ns98MAD2rx5s3Jzc7V8+XI9/PDDVQrp77//vt58803t379f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jlXzuwTglwg7AKrk1KlTxt/f36xfv95l+uDBg80DDzxgBY7PP//cmpeRkWEkmdzcXGvav/3bv5mkpCRrvHPnziYmJsZUVlZa08aOHWtiYmIuWMvmzZuNJCuAnF33xx9/7NLubNhZt26dqVevnnnppZeqvL1z5swxQUFBLtP2799vJJl169ZZ07777jvj5+dn/v73vxtjjHn11VfNjTfeaIwx5uOPPzbt27c3ffr0MTNnzjTGGNOtWzfz1FNPWctLMuPHj7fGS0pKjCSzdOnSKtcK4OK4jAWgSg4ePKiTJ0+qe/fuCgwMtIZ58+YpNzfXate6dWvr6/DwcPn7+6tZs2Yu035+CUqSOnToIIfDYY0nJCTowIED1n03W7duVe/evdW4cWPVrVtXnTt3liTl5eW59NOuXbtz6s7Ly1P37t01ceJEjR49+jL2gJSdna1atWqpffv21rT69eurZcuWys7OliR17txZe/fu1dGjR5WVlaXExEQlJiYqMzNT5eXlWr9+vRITE136/fk+CwgIkNPpPGcfAag+blAGUCUlJSWSpMWLF+u6665zmefr62sFntq1a1vTHQ6Hy/jZaZWVlVVeb2lpqZKSkpSUlKT58+crNDRUeXl5SkpK0unTp13aBgQEnLN8aGioIiMj9c477+iRRx6R0+ms8rqrIy4uTiEhIcrKylJWVpaeffZZRURE6C9/+Ys2b96s8vJy3X777S7LXO4+AnBxnNkBUCWxsbHy9fVVXl6emjdv7jJERUVdVt+bNm1yGd+4caNatGghb29v7du3T8eOHdPzzz+vO++8U61atbqksx5+fn5atGiR6tSpo6SkJJ04caJKy/n4+JzzRFdMTIzOnDnjUu+xY8eUk5Oj2NhYST8FlTvvvFOffPKJ9uzZozvuuEOtW7dWWVmZXn/9dbVr1+68oQzAlUPYAVAldevW1ZNPPqlRo0bprbfeUm5urrZt26bp06frrbfeuqy+8/LylJ6erpycHL3zzjuaPn26RowYIUlq3LixfHx8NH36dH399df69NNPNWXKlEvqPyAgQIsXL1atWrWUnJxsnaW6mCZNmqikpESrVq3Sd999p5MnT6pFixbq06ePhgwZorVr12rnzp168MEHdd1116lPnz7WsomJiXrnnXfUtm1bBQYGysvLS506ddL8+fOtS3AArh7CDoAqmzJliiZMmKCMjAzFxMSoZ8+eWrx4sZo2bXpZ/Q4aNEg//vijbrvtNqWlpWnEiBF67LHHJP10GWru3Ll6//33FRsbq+eff14vvfTSJa8jMDBQS5culTFGvXr1Umlp6UXb33777Xr88cd1//33KzQ0VC+88IIkac6cOYqPj9fvfvc7JSQkyBijJUuWuFyK6ty5syoqKlzuzUlMTDxnGoCrw2HMRV42AQAAcI3jzA4AALA1wg6A36Tk5GSXR+h/Pjz33HPuLg9ADeIyFoDfpP/5n//Rjz/+eN55ISEhCgkJucoVAbhSCDsAAMDWuIwFAABsjbADAABsjbADAABsjbADAABsjbADAABsjbADAABsjbADAABsjbADAABs7f8DEdF68TZuQ9wAAAAASUVORK5CYII=\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**8.Avg fare wwas high for which gender?**"
      ],
      "metadata": {
        "id": "EackfbHrLO3u"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "sns.barplot(data=df,y='fare',x='sex')"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 466
        },
        "id": "qfzPe7QjLJRa",
        "outputId": "d40c998a-c16d-4257-b3fe-38783694003a"
      },
      "execution_count": 17,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "<Axes: xlabel='sex', ylabel='fare'>"
            ]
          },
          "metadata": {},
          "execution_count": 17
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAjIAAAGwCAYAAACzXI8XAAAAOnRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjEwLjAsIGh0dHBzOi8vbWF0cGxvdGxpYi5vcmcvlHJYcgAAAAlwSFlzAAAPYQAAD2EBqD+naQAAIElJREFUeJzt3XtwVPXdx/HPJiEXSHZDgiSkhBgGNbEQxVAhgoWmkUhbGk1aFa2iUq8xQFIfNV5AsHatjHLRgIoIYk2p2FGGWoM2Qhwh3AJYFM3IxSZOLog2CYRmA+Q8fzju45YECQ+bsz94v2bOjOec3ZPvwVl4z9mzG4dlWZYAAAAMFGT3AAAAAKeKkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsULsHsDfOjo6VFdXp6ioKDkcDrvHAQAAJ8GyLB08eFAJCQkKCur6ussZHzJ1dXVKTEy0ewwAAHAKamtrNXDgwC73n/EhExUVJembPwin02nzNAAA4GS0tLQoMTHR++94V874kPn27SSn00nIAABgmO+7LYSbfQEAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADGImQAAICxCBkAAGAsQgYAABiLkAEAAMYiZAAAgLHO+N9+DQAwn2VZam1t9a736dPne38rMs4OhAwAIOC1trYqJyfHu75q1SpFRkbaOBECBW8tAQAAYxEyAADAWIQMAAAwFiEDAACMRcgAAABj2Royjz76qBwOh8+SkpLi3d/W1qb8/HzFxsYqMjJSeXl5amxstHFiAAAQSGy/IvPDH/5Q9fX13uWDDz7w7issLNTq1au1cuVKVVRUqK6uTrm5uTZOCwAAAont3yMTEhKi+Pj447Y3NzdryZIlKi0tVWZmpiRp6dKlSk1N1caNGzVq1KhOj+fxeOTxeLzrLS0t/hkcAADYzvYrMp999pkSEhI0ePBg3XDDDaqpqZEkVVVV6ciRI8rKyvI+NiUlRYMGDVJlZWWXx3O73XK5XN4lMTHR7+cAAADsYWvIjBw5UsuWLVNZWZkWLVqkffv26fLLL9fBgwfV0NCg0NBQRUdH+zwnLi5ODQ0NXR6zuLhYzc3N3qW2ttbPZwEAAOxi61tLEyZM8P53WlqaRo4cqaSkJL322muKiIg4pWOGhYUpLCzsdI0IAAACmO1vLX1XdHS0zj//fO3evVvx8fFqb29XU1OTz2MaGxs7vacGAACcfQIqZA4dOqQ9e/ZowIABSk9PV69evVReXu7dX11drZqaGmVkZNg4JQAACBS2vrV07733auLEiUpKSlJdXZ1mzpyp4OBgTZo0SS6XS1OmTFFRUZFiYmLkdDpVUFCgjIyMLj+xBAAAzi62hswXX3yhSZMm6auvvtI555yjMWPGaOPGjTrnnHMkSXPnzlVQUJDy8vLk8XiUnZ2thQsX2jkyAAAIIA7Lsiy7h/CnlpYWuVwuNTc3y+l02j0OAOAUHDp0SDk5Od71VatWKTIy0saJ4G8n++93QN0jAwAA0B2EDAAAMBYhAwAAjEXIAAAAYxEyAADAWIQMAAAwFiEDAACMRcgAAABjETIAAMBYhAwAADAWIQMAAIxFyAAAAGMRMgAAwFiEDAAAMBYhAwAAjEXIAAAAYxEyAADAWIQMAAAwFiEDAACMRcgAAABjETIAAMBYhAwAADAWIQMAAIxFyAAAAGMRMgAAwFiEDAAAMBYhAwAAjEXIAAAAYxEyAADAWIQMAAAwVojdAwBAoEv/n+V2j3DWcxxtl+s76+MeWSErJNS2eSBVzbnJ7hEkcUUGAAAYjJABAADGImQAAICxCBkAAGAsQgYAABiLkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADGImQAAICxCBkAAGAsQgYAABiLkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADGCpiQeeKJJ+RwODR9+nTvtra2NuXn5ys2NlaRkZHKy8tTY2OjfUMCAICAEhAhs2XLFj3//PNKS0vz2V5YWKjVq1dr5cqVqqioUF1dnXJzc22aEgAABBrbQ+bQoUO64YYbtHjxYvXt29e7vbm5WUuWLNHTTz+tzMxMpaena+nSpdqwYYM2btxo48QAACBQ2B4y+fn5+vnPf66srCyf7VVVVTpy5IjP9pSUFA0aNEiVlZVdHs/j8ailpcVnAQAAZ6YQO3/4ihUrtG3bNm3ZsuW4fQ0NDQoNDVV0dLTP9ri4ODU0NHR5TLfbrVmzZp3uUQEAQACy7YpMbW2tpk2bpldffVXh4eGn7bjFxcVqbm72LrW1taft2AAAILDYFjJVVVXav3+/LrnkEoWEhCgkJEQVFRVasGCBQkJCFBcXp/b2djU1Nfk8r7GxUfHx8V0eNywsTE6n02cBAABnJtveWvrpT3+qnTt3+my75ZZblJKSovvvv1+JiYnq1auXysvLlZeXJ0mqrq5WTU2NMjIy7BgZAAAEGNtCJioqSkOHDvXZ1qdPH8XGxnq3T5kyRUVFRYqJiZHT6VRBQYEyMjI0atQoO0YGAAABxtabfb/P3LlzFRQUpLy8PHk8HmVnZ2vhwoV2jwUAAAJEQIXMunXrfNbDw8NVUlKikpISewYCAAABzfbvkQEAADhVhAwAADAWIQMAAIxFyAAAAGMF1M2+AAB0xgrupea0ST7rgETIAABM4HDICgm1ewoEIN5aAgAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADGImQAAICxCBkAAGAsQgYAABiLkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADGImQAAICxCBkAAGAsQgYAABiLkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADGImQAAICxCBkAAGAsQgYAABiLkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADGImQAAICxCBkAAGAsQgYAABiLkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYy9aQWbRokdLS0uR0OuV0OpWRkaG3337bu7+trU35+fmKjY1VZGSk8vLy1NjYaOPEAAAgkNgaMgMHDtQTTzyhqqoqbd26VZmZmcrJydHHH38sSSosLNTq1au1cuVKVVRUqK6uTrm5uXaODAAAAkiInT984sSJPuuPP/64Fi1apI0bN2rgwIFasmSJSktLlZmZKUlaunSpUlNTtXHjRo0aNcqOkQEAQAAJmHtkjh07phUrVqi1tVUZGRmqqqrSkSNHlJWV5X1MSkqKBg0apMrKyi6P4/F41NLS4rMAAIAzk+0hs3PnTkVGRiosLEx33nmn3njjDV144YVqaGhQaGiooqOjfR4fFxenhoaGLo/ndrvlcrm8S2Jiop/PAAAA2MX2kLngggu0Y8cObdq0SXfddZcmT56sXbt2nfLxiouL1dzc7F1qa2tP47QAACCQ2HqPjCSFhoZqyJAhkqT09HRt2bJF8+fP17XXXqv29nY1NTX5XJVpbGxUfHx8l8cLCwtTWFiYv8cGAAABwPYrMv+to6NDHo9H6enp6tWrl8rLy737qqurVVNTo4yMDBsnRKCyLEuHDh3yLpZl2T0SAMDPbL0iU1xcrAkTJmjQoEE6ePCgSktLtW7dOq1Zs0Yul0tTpkxRUVGRYmJi5HQ6VVBQoIyMDD6xhE61trYqJyfHu75q1SpFRkbaOBEAwN9sDZn9+/frpptuUn19vVwul9LS0rRmzRpdccUVkqS5c+cqKChIeXl58ng8ys7O1sKFC+0cGQAABBBbQ2bJkiUn3B8eHq6SkhKVlJT00EQAAMAkAXePDAAAwMkiZAAAgLEIGQAAYCxCBgAAGOuUQuaVV17R6NGjlZCQoH/961+SpHnz5mnVqlWndTgAAIAT6XbILFq0SEVFRfrZz36mpqYmHTt2TJIUHR2tefPmne75AAAAutTtkHnmmWe0ePFiPfTQQwoODvZuHzFihHbu3HlahwMAADiRbofMvn37NHz48OO2h4WFqbW19bQMBQAAcDK6HTLJycnasWPHcdvLysqUmpp6OmYCAAA4Kd3+Zt+ioiLl5+erra1NlmVp8+bN+vOf/yy3260XX3zRHzMCAAB0qtsh89vf/lYRERF6+OGHdfjwYV1//fVKSEjQ/Pnzdd111/ljRgAAgE51K2SOHj2q0tJSZWdn64YbbtDhw4d16NAh9e/f31/zAQAAdKlb98iEhITozjvvVFtbmySpd+/eRAwAALBNt2/2vfTSS7V9+3Z/zAIAANAt3b5H5u6779bvfvc7ffHFF0pPT1efPn189qelpZ224QAAAE6k2yHz7Q29U6dO9W5zOByyLEsOh8P7Tb8AAAD+1u2Q2bdvnz/mAAAA6LZuh0xSUpI/5gAAAOi2bofMt3bt2qWamhq1t7f7bP/lL3/5/x4KAADgZHQ7ZPbu3aurr75aO3fu9N4bI31zn4wk7pEBAAA9ptsfv542bZqSk5O1f/9+9e7dWx9//LHef/99jRgxQuvWrfPDiAAAAJ3r9hWZyspKvffee+rXr5+CgoIUFBSkMWPGyO12a+rUqXzHDAAA6DHdviJz7NgxRUVFSZL69eunuro6Sd/cBFxdXX16pwMAADiBbl+RGTp0qD788EMlJydr5MiRevLJJxUaGqoXXnhBgwcP9seMRkj/n+V2j3DWcxxtl+s76+MeWSErJNS2eSBVzbnJ7hEAnOFO6orMP//5T3V0dEiSHn74Ye8NvrNnz9a+fft0+eWX6+9//7sWLFjgv0kBAAD+y0ldkRk+fLjq6+vVv39/3XXXXdqyZYskaciQIfr000/19ddfq2/fvt5PLgEAAPSEk7oiEx0d7f1G388//9x7deZbMTExRAwAAOhxJ3VFJi8vT2PHjtWAAQPkcDg0YsQIBQcHd/rYvXv3ntYBAQAAunJSIfPCCy8oNzdXu3fv1tSpU3Xbbbd5P7kEAABgl5P+1NKVV14pSaqqqtK0adMIGQAAYLtuf/x66dKl/pgDAACg27r9hXgAAACBgpABAADGImQAAICxCBkAAGAsQgYAABiLkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADGImQAAICxCBkAAGAsQgYAABgrxO4BgNPFCu6l5rRJPusAgDMbIYMzh8MhKyTU7ikAAD2It5YAAICxCBkAAGAsQgYAABiLkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxrI1ZNxut370ox8pKipK/fv311VXXaXq6mqfx7S1tSk/P1+xsbGKjIxUXl6eGhsbbZoYAAAEEltDpqKiQvn5+dq4caPeffddHTlyROPHj1dra6v3MYWFhVq9erVWrlypiooK1dXVKTc318apAQBAoLD1VxSUlZX5rC9btkz9+/dXVVWVfvzjH6u5uVlLlixRaWmpMjMzJUlLly5VamqqNm7cqFGjRh13TI/HI4/H411vaWnx70kAAADbBNQ9Ms3NzZKkmJgYSVJVVZWOHDmirKws72NSUlI0aNAgVVZWdnoMt9stl8vlXRITE/0/OAAAsEXAhExHR4emT5+u0aNHa+jQoZKkhoYGhYaGKjo62uexcXFxamho6PQ4xcXFam5u9i61tbX+Hh0AANgkYH77dX5+vj766CN98MEH/6/jhIWFKSws7DRNBQAAAllAXJG555579Le//U1r167VwIEDvdvj4+PV3t6upqYmn8c3NjYqPj6+h6cEAACBxtaQsSxL99xzj9544w299957Sk5O9tmfnp6uXr16qby83LuturpaNTU1ysjI6OlxAQBAgLH1raX8/HyVlpZq1apVioqK8t734nK5FBERIZfLpSlTpqioqEgxMTFyOp0qKChQRkZGp59YAgAAZxdbQ2bRokWSpHHjxvlsX7p0qW6++WZJ0ty5cxUUFKS8vDx5PB5lZ2dr4cKFPTwpAAAIRLaGjGVZ3/uY8PBwlZSUqKSkpAcmAgAAJgmIm30BAABOBSEDAACMRcgAAABjETIAAMBYhAwAADAWIQMAAIxFyAAAAGMRMgAAwFiEDAAAMBYhAwAAjEXIAAAAYxEyAADAWIQMAAAwFiEDAACMRcgAAABjETIAAMBYhAwAADAWIQMAAIxFyAAAAGMRMgAAwFiEDAAAMBYhAwAAjEXIAAAAYxEyAADAWIQMAAAwFiEDAACMRcgAAABjETIAAMBYhAwAADAWIQMAAIxFyAAAAGMRMgAAwFiEDAAAMBYhAwAAjEXIAAAAYxEyAADAWIQMAAAwFiEDAACMRcgAAABjETIAAMBYhAwAADAWIQMAAIxFyAAAAGMRMgAAwFiEDAAAMBYhAwAAjEXIAAAAYxEyAADAWIQMAAAwFiEDAACMRcgAAABjETIAAMBYhAwAADAWIQMAAIxFyAAAAGMRMgAAwFiEDAAAMJatIfP+++9r4sSJSkhIkMPh0Jtvvumz37IszZgxQwMGDFBERISysrL02Wef2TMsAAAIOLaGTGtrqy666CKVlJR0uv/JJ5/UggUL9Nxzz2nTpk3q06ePsrOz1dbW1sOTAgCAQBRi5w+fMGGCJkyY0Ok+y7I0b948Pfzww8rJyZEkLV++XHFxcXrzzTd13XXX9eSoAAAgAAXsPTL79u1TQ0ODsrKyvNtcLpdGjhypysrKLp/n8XjU0tLiswAAgDNTwIZMQ0ODJCkuLs5ne1xcnHdfZ9xut1wul3dJTEz065wAAMA+ARsyp6q4uFjNzc3epba21u6RAACAnwRsyMTHx0uSGhsbfbY3NjZ693UmLCxMTqfTZwEAAGemgA2Z5ORkxcfHq7y83LutpaVFmzZtUkZGho2TAQCAQGHrp5YOHTqk3bt3e9f37dunHTt2KCYmRoMGDdL06dP1+9//Xuedd56Sk5P1yCOPKCEhQVdddZV9QwMAgIBha8hs3bpVP/nJT7zrRUVFkqTJkydr2bJluu+++9Ta2qrbb79dTU1NGjNmjMrKyhQeHm7XyAAAIIDYGjLjxo2TZVld7nc4HJo9e7Zmz57dg1MBAABTBOw9MgAAAN+HkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADGImQAAICxCBkAAGAsQgYAABiLkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADGImQAAICxCBkAAGAsQgYAABiLkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADGImQAAICxCBkAAGAsQgYAABiLkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADGImQAAICxCBkAAGAsQgYAABiLkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADGMiJkSkpKdO655yo8PFwjR47U5s2b7R4JAAAEgIAPmb/85S8qKirSzJkztW3bNl100UXKzs7W/v377R4NAADYLOBD5umnn9Ztt92mW265RRdeeKGee+459e7dWy+99JLdowEAAJuF2D3AibS3t6uqqkrFxcXebUFBQcrKylJlZWWnz/F4PPJ4PN715uZmSVJLS4tfZz3m+Y9fjw+YyN+vu57C6xs4nr9f398e37KsEz4uoEPmwIEDOnbsmOLi4ny2x8XF6dNPP+30OW63W7NmzTpue2Jiol9mBNA11zN32j0CAD/pqdf3wYMH5XK5utwf0CFzKoqLi1VUVORd7+jo0Ndff63Y2Fg5HA4bJ0NPaGlpUWJiompra+V0Ou0eB8BpxOv77GJZlg4ePKiEhIQTPi6gQ6Zfv34KDg5WY2Ojz/bGxkbFx8d3+pywsDCFhYX5bIuOjvbXiAhQTqeTv+iAMxSv77PHia7EfCugb/YNDQ1Venq6ysvLvds6OjpUXl6ujIwMGycDAACBIKCvyEhSUVGRJk+erBEjRujSSy/VvHnz1NraqltuucXu0QAAgM0CPmSuvfZaffnll5oxY4YaGhp08cUXq6ys7LgbgAHpm7cWZ86cedzbiwDMx+sbnXFY3/e5JgAAgAAV0PfIAAAAnAghAwAAjEXIAAAAYxEyOCvcfPPNuuqqq+weAzgrWJal22+/XTExMXI4HNqxY4ctc3z++ee2/nz0jID/1BIAwCxlZWVatmyZ1q1bp8GDB6tfv352j4QzGCEDADit9uzZowEDBuiyyy6zexScBXhrCQFn3LhxKigo0PTp09W3b1/FxcVp8eLF3i9CjIqK0pAhQ/T2229Lko4dO6YpU6YoOTlZERERuuCCCzR//vwT/oyOjg653W7vcy666CK9/vrrPXF6wBnt5ptvVkFBgWpqauRwOHTuued+7+tt3bp1cjgcWrNmjYYPH66IiAhlZmZq//79evvtt5Wamiqn06nrr79ehw8f9j6vrKxMY8aMUXR0tGJjY/WLX/xCe/bsOeF8H330kSZMmKDIyEjFxcXpxhtv1IEDB/z25wH/I2QQkF5++WX169dPmzdvVkFBge666y79+te/1mWXXaZt27Zp/PjxuvHGG3X48GF1dHRo4MCBWrlypXbt2qUZM2bowQcf1Guvvdbl8d1ut5YvX67nnntOH3/8sQoLC/Wb3/xGFRUVPXiWwJln/vz5mj17tgYOHKj6+npt2bLlpF9vjz76qJ599llt2LBBtbW1uuaaazRv3jyVlpbqrbfe0jvvvKNnnnnG+/jW1lYVFRVp69atKi8vV1BQkK6++mp1dHR0OltTU5MyMzM1fPhwbd26VWVlZWpsbNQ111zj1z8T+JkFBJixY8daY8aM8a4fPXrU6tOnj3XjjTd6t9XX11uSrMrKyk6PkZ+fb+Xl5XnXJ0+ebOXk5FiWZVltbW1W7969rQ0bNvg8Z8qUKdakSZNO45kAZ6e5c+daSUlJlmWd3Ott7dq1liTrH//4h3e/2+22JFl79uzxbrvjjjus7OzsLn/ul19+aUmydu7caVmWZe3bt8+SZG3fvt2yLMt67LHHrPHjx/s8p7a21pJkVVdXn/L5wl7cI4OAlJaW5v3v4OBgxcbGatiwYd5t3/6Kiv3790uSSkpK9NJLL6mmpkb/+c9/1N7erosvvrjTY+/evVuHDx/WFVdc4bO9vb1dw4cPP81nApzduvN6++7rPi4uTr1799bgwYN9tm3evNm7/tlnn2nGjBnatGmTDhw44L0SU1NTo6FDhx43y4cffqi1a9cqMjLyuH179uzR+eeff2onCVsRMghIvXr18ll3OBw+2xwOh6Rv7nVZsWKF7r33Xj311FPKyMhQVFSU5syZo02bNnV67EOHDkmS3nrrLf3gBz/w2cfvcAFOr+683v77Nd7Z3wPffdto4sSJSkpK0uLFi5WQkKCOjg4NHTpU7e3tXc4yceJE/fGPfzxu34ABA7p3YggYhAyMt379el122WW6++67vdtOdMPfhRdeqLCwMNXU1Gjs2LE9MSJw1vLX6+2rr75SdXW1Fi9erMsvv1yS9MEHH5zwOZdccon++te/6txzz1VICP/8nSn4PwnjnXfeeVq+fLnWrFmj5ORkvfLKK9qyZYuSk5M7fXxUVJTuvfdeFRYWqqOjQ2PGjFFzc7PWr18vp9OpyZMn9/AZAGcuf73e+vbtq9jYWL3wwgsaMGCAampq9MADD5zwOfn5+Vq8eLEmTZqk++67TzExMdq9e7dWrFihF198UcHBwac0C+xFyMB4d9xxh7Zv365rr71WDodDkyZN0t133+39eHZnHnvsMZ1zzjlyu93au3evoqOjdckll+jBBx/swcmBs4M/Xm9BQUFasWKFpk6dqqFDh+qCCy7QggULNG7cuC6fk5CQoPXr1+v+++/X+PHj5fF4lJSUpCuvvFJBQXyI11QOy7Isu4cAAAA4FSQoAAAwFiEDAACMRcgAAABjETIAAMBYhAwAADAWIQMAAIxFyAAAAGMRMgAAwFiEDAAAMBYhAwAAjEXIAAAAYxEyAALS66+/rmHDhikiIkKxsbHKyspSa2urJOnFF19UamqqwsPDlZKSooULF3qfd+uttyotLU0ej0eS1N7eruHDh+umm26y5TwA+BchAyDg1NfXa9KkSbr11lv1ySefaN26dcrNzZVlWXr11Vc1Y8YMPf744/rkk0/0hz/8QY888ohefvllSdKCBQvU2tqqBx54QJL00EMPqampSc8++6ydpwTAT0LsHgAA/lt9fb2OHj2q3NxcJSUlSZKGDRsmSZo5c6aeeuop5ebmSpKSk5O1a9cuPf/885o8ebIiIyP1pz/9SWPHjlVUVJTmzZuntWvXyul02nY+APzHYVmWZfcQAPBdx44dU3Z2tjZv3qzs7GyNHz9ev/rVrxQaGqrIyEhFREQoKOj/LigfPXpULpdLjY2N3m0PPvig3G637r//fj3xxBN2nAaAHsAVGQABJzg4WO+++642bNigd955R88884weeughrV69WpK0ePFijRw58rjnfKujo0Pr169XcHCwdu/e3aOzA+hZ3CMDICA5HA6NHj1as2bN0vbt2xUaGqr169crISFBe/fu1ZAhQ3yW5ORk73PnzJmjTz/9VBUVFSorK9PSpUttPBMA/sQVGQABZ9OmTSovL9f48ePVv39/bdq0SV9++aVSU1M1a9YsTZ06VS6XS1deeaU8Ho+2bt2qf//73yoqKtL27ds1Y8YMvf766xo9erSefvppTZs2TWPHjtXgwYPtPjUApxn3yAAIOJ988okKCwu1bds2tbS0KCkpSQUFBbrnnnskSaWlpZozZ4527dqlPn36aNiwYZo+fbomTJig9PR0jRkzRs8//7z3eDk5OTpw4IDef/99n7egAJiPkAEAAMbiHhkAAGAsQgYAABiLkAEAAMYiZAAAgLEIGQAAYCxCBgAAGIuQAQAAxiJkAACAsQgZAABgLEIGAAAYi5ABAADG+l9NVk0EUJjbeQAAAABJRU5ErkJggg==\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**9. Explore the relationship between fare(ticket price) and survival. Do passengers who paid higher fares have a better chance of survival?**"
      ],
      "metadata": {
        "id": "jsdAv-drNwUw"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "sns.barplot(data=df,y='fare',x='survived',errorbar=('ci',False))"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 466
        },
        "id": "DVnMvyLUNiAW",
        "outputId": "7bd29260-3839-48f2-9760-473a29ba714d"
      },
      "execution_count": 26,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "<Axes: xlabel='survived', ylabel='fare'>"
            ]
          },
          "metadata": {},
          "execution_count": 26
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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zs6dO3PppZdWejTgd7Rjx44899xzPY83btyYp556KqNHj86ECRMqOBnVwNuved34xje+ka997Wtpa2vLW97yltxyyy2ZMWNGpccCfkerVq3K2Wef/Yr1+fPn56677jr8A1FVhAwAUCz3yAAAxRIyAECxhAwAUCwhAwAUS8gAAMUSMgBAsYQMAFAsIQMAFEvIAMU79thjs3jx4n79GqtWrUpNTU22b9/er18H6Bt/awko3uOPP57hw4dXegygAoQMULV2796dIUOG/Nbjxo4deximAaqRl5aAQ+o73/lOTjrppAwbNixjxozJrFmzsnPnzpx11lm55ppreh17wQUX5MMf/nDP42OPPTZf/OIXc8kll6Suri4f+9jH8o53vCOf+cxnej3vhRdeyODBg7NmzZqe57380tLFF1+cCy+8sNfxe/bsyZFHHpm77747SbJv3760tLRk0qRJGTZsWKZOnZrvfOc7vZ7zve99L29605sybNiwnH322fnFL37xu39zgENOyACHzNatW3PRRRflIx/5SJ599tmsWrUqc+bMSV/+Nu1f/dVfZerUqXnyySdz3XXXZd68ebnnnnt6nePee+/N+PHjc8YZZ7zi+fPmzctDDz2UHTt29Kw9/PDDeemll/L+978/SdLS0pK77747t99+e5555pksXLgwf/RHf5TVq1cnSTZv3pw5c+bkvPPOy1NPPZXLL788n/3sZ1/rtwXoR15aAg6ZrVu35je/+U3mzJmTiRMnJklOOumkPp1j5syZ+eQnP9nz+IMf/GCuueaaPProoz3hsnz58lx00UWpqal5xfNnz56d4cOH5/77788f//Ef9xz/vve9LyNHjkxXV1e+/OUv51/+5V/S1NSUJDnuuOPy6KOP5pvf/GbOPPPMLF26NG984xtz4403Jkne/OY35+mnn85f/uVf9v2bAvQrV2SAQ2bq1Kl517velZNOOikf+MAHcscdd+S///u/+3SO6dOn93o8duzYnHPOOfn2t7+dJNm4cWPWrl2befPm7ff5gwYNygc/+MGe43fu3JkHH3yw5/jnnnsuL730Ut797ndnxIgRPdvdd9+dn//850mSZ599NjNmzOh13pejB6gursgAh8zAgQPzyCOP5Ac/+EH++Z//Obfeems+97nPZf369RkwYMArXmLas2fPK86xv3cfzZs3L1dddVVuvfXWLF++PCeddNKrXumZN29ezjzzzGzbti2PPPJIhg0blve85z1J0vOS03e/+9383u/9Xq/n1dbW9vnfDFSWKzLAIVVTU5PTTjstX/jCF/Lkk09myJAhuf/++zN27Nhs3bq157i9e/fmxz/+8UGd8/zzz8+uXbuyYsWKLF++/IBXY172jne8I42Njbn33nvz7W9/Ox/4wAcyePDgJMkJJ5yQ2trabNq0Kccff3yvrbGxMUkyZcqUPPbYY73OuW7dur58G4DDxBUZ4JBZv359Vq5cmXPOOSdHHXVU1q9fnxdeeCFTpkzJ8OHD09zcnO9+97t54xvfmJtuuumgP1xu+PDhueCCC3Ldddfl2WefzUUXXfRbn3PxxRfn9ttvz3/8x3/kX//1X3vWR44cmU996lNZuHBh9u3bl9NPPz0dHR35t3/7t9TV1WX+/Pm54oorcuONN+bTn/50Lr/88rS2tuauu+56jd8VoD8JGeCQqaury5o1a7J48eJ0dnZm4sSJufHGG3Puuedmz549+dGPfpRLLrkkgwYNysKFC3P22Wcf9LnnzZuX9773vXnnO9+ZCRMmHNTxX/rSlzJx4sScdtppvfZ98YtfzNixY9PS0pLnn38+o0aNytve9rb82Z/9WZJkwoQJ+Yd/+IcsXLgwt956a0455ZR8+ctfzkc+8pG+fUOAflfT3Zf3RQIAVBH3yAAAxRIyAECxhAwAUCwhAwAUS8gAAMUSMgBAsYQMAFAsIQMAFEvIAADFEjIAQLGEDABQrP8LLccM+6fWivYAAAAASUVORK5CYII=\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**10. Investigate the relationship between age and survival. Are you younger passengers more likely to survive**"
      ],
      "metadata": {
        "id": "s-FqXRdEPcI_"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "sns.boxplot(data=df,x='survived',y='age')"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 466
        },
        "id": "jcGFNkn-O246",
        "outputId": "55a356a2-cc55-46ad-985b-7515b74bbeb3"
      },
      "execution_count": 30,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "<Axes: xlabel='survived', ylabel='age'>"
            ]
          },
          "metadata": {},
          "execution_count": 30
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAjIAAAGwCAYAAACzXI8XAAAAOnRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjEwLjAsIGh0dHBzOi8vbWF0cGxvdGxpYi5vcmcvlHJYcgAAAAlwSFlzAAAPYQAAD2EBqD+naQAALM5JREFUeJzt3X1UlHXCxvFrQBlYlTF8GSSBsDRtU9u1QswsjWLdNEwOpbFl6T6eimyF2jZK89E0zK3VXlBiD6v5JFnsrpmVusWucmrRjF40K7WVR3zCGWsNRmkZjOH5o+PsTmoZAvf9w+/nnDk1v/uem2s4TXPxu98czc3NzQIAADBQmNUBAAAAWooiAwAAjEWRAQAAxqLIAAAAY1FkAACAsSgyAADAWBQZAABgrE5WB2hrgUBANTU16tatmxwOh9VxAADAKWhubtbhw4cVFxensLCTz7t0+CJTU1Oj+Ph4q2MAAIAW2L9/v/r27XvS5R2+yHTr1k3SN7+I6Ohoi9MAAIBT4fP5FB8fH/weP5kOX2SO7U6Kjo6myAAAYJjvOyyEg30BAICxKDIAAMBYFBkAAGAsigwAADAWRQYAABiLIgMAAIxFkQEAAMaiyAAAAGNRZAAAgLE6/JV9AQDma2pq0vbt23Xo0CHFxMRoyJAhCg8PtzoWbMDSGZmmpibNnj1bSUlJioqK0rnnnquHH35Yzc3NwXWam5v10EMPqU+fPoqKilJqaqr27NljYWoAQHsqLy9XVlaWcnJy9PDDDysnJ0dZWVkqLy+3OhpswNIi8+ijj2rZsmV6+umn9fHHH+vRRx/VokWL9NRTTwXXWbRokZ588kkVFhZq69at6tKli9LS0tTQ0GBhcgBAeygvL9ecOXPUr18/FRQU6LXXXlNBQYH69eunOXPmUGYgR/N/Tn+0s3Hjxsntdqu4uDg4lpGRoaioKD333HNqbm5WXFyc7rnnHt17772SpLq6Orndbq1YsUKTJk363p/h8/nkcrlUV1fHTSMBwCBNTU3KyspSv379NH/+fIWF/ftv70AgoFmzZqmqqkrPPfccu5k6oFP9/rZ0RmbEiBEqKyvT7t27JUkffPCB3nzzTY0dO1aSVFVVJY/Ho9TU1OBrXC6XkpOTVVFRccJt+v1++Xy+kAcAwDzbt2+Xx+NRVlZWSImRpLCwMGVlZenAgQPavn27RQlhB5Ye7Hv//ffL5/Np4MCBCg8PV1NTkxYsWKCsrCxJksfjkSS53e6Q17nd7uCyb8vPz9fcuXPbNjgAoM0dOnRIkpSUlHTC5cfGj62HM5OlMzIvvviiVq1apZKSEr377rt69tln9dhjj+nZZ59t8Tbz8vJUV1cXfOzfv78VEwMA2ktMTIykb2bnT+TY+LH1cGaytMj8+te/1v33369JkyZp8ODBuvnmm5WTk6P8/HxJUmxsrCTJ6/WGvM7r9QaXfZvT6VR0dHTIAwBgniFDhig2NlarVq1SIBAIWRYIBLRq1Sr16dNHQ4YMsSgh7MDSIvPVV18dt98zPDw8+B9sUlKSYmNjVVZWFlzu8/m0detWpaSktGtWAED7Cg8P15133qmKigrNmjVLO3fu1FdffaWdO3dq1qxZqqio0B133MGBvmc4S4+RGT9+vBYsWKCEhAT9+Mc/1nvvvaff/e53mjp1qiTJ4XBo5syZmj9/vvr376+kpCTNnj1bcXFxmjBhgpXRAQDtYNSoUZo7d66WLl2q7Ozs4HifPn00d+5cjRo1ysJ0sANLT78+fPiwZs+erTVr1ujgwYOKi4vT5MmT9dBDDykiIkLSNxfEmzNnjoqKilRbW6uRI0dq6dKlGjBgwCn9DE6/BgDzcWXfM8+pfn9bWmTaA0UGAADzGHEdGQAAgNNBkQEAAMaiyAAAAGNRZAAAgLEoMgAAwFgUGQAAYCyKDAAAMBZFBgAAGIsiAwAAjEWRAQAAxqLIAAAAY1FkAACAsSgyAADAWJ2sDgC0lqamJm3fvl2HDh1STEyMhgwZovDwcKtjAQDaEEUGHUJ5ebmWLl0qj8cTHIuNjdWdd96pUaNGWZgMANCW2LUE45WXl2vOnDnq16+fCgoK9Nprr6mgoED9+vXTnDlzVF5ebnVEAEAbcTQ3NzdbHaIt+Xw+uVwu1dXVKTo62uo4aGVNTU3KyspSv379NH/+fIWF/bubBwIBzZo1S1VVVXruuefYzQQABjnV729mZGC07du3y+PxKCsrK6TESFJYWJiysrJ04MABbd++3aKEAIC2RJGB0Q4dOiRJSkpKOuHyY+PH1gMAdCwUGRgtJiZGklRVVXXC5cfGj60HAOhYKDIw2pAhQxQbG6tVq1YpEAiELAsEAlq1apX69OmjIUOGWJQQANCWKDIwWnh4uO68805VVFRo1qxZ2rlzp7766ivt3LlTs2bNUkVFhe644w4O9AWADoqzltAhnOg6Mn369NEdd9zBdWQAwECn+v1NkUGHwZV9AaDjONXvb67siw4jPDxcP/nJT6yOAQBoRxwjAwAAjMWMDDqMxsZGrV27VjU1NYqLi1N6eroiIiKsjgUAaEMUGXQIhYWFKi0tVVNTU8hYZmambr/9dguTAQDaEkUGxissLNTq1at11lln6eqrr1ZcXJxqamr0+uuva/Xq1ZJEmQGADoqzlmC0xsZGjR07VpGRkeratau8Xm9wmdvt1pEjR9TQ0KD169ezmwkADMJZSzgjrF27Vk1NTaqvr9fgwYM1cuRI+f1+OZ1OffbZZ9qyZUtwvczMTIvTAgBaG0UGRvvss88kfTP7sm3btmBxkb45Hdvtdsvr9QbXAwB0LJaefn3OOefI4XAc98jOzpYkNTQ0KDs7Wz169FDXrl2VkZERsusAOMbr9So6Olr33nuv/vSnP+nee+9VdHQ0/70AQAdnaZHZtm2bDhw4EHy8/vrrkhTcBZCTk6N169aptLRUmzdvVk1NjSZOnGhlZNhM//79JUkOh0PPP/+8xo0bpx49emjcuHF6/vnn5XA4QtYDAHQslu5a6tWrV8jzhQsX6txzz9UVV1yhuro6FRcXq6SkRGPGjJEkLV++XIMGDdKWLVs0fPjwE27T7/fL7/cHn/t8vrZ7A7Dcnj17JEnNzc2aPHmypk6dqpSUFFVUVOgPf/iDjh3Lfmw9AEDHYptjZBobG/Xcc88pNzdXDodDlZWVOnr0qFJTU4PrDBw4UAkJCaqoqDhpkcnPz9fcuXPbKzZsonfv3vriiy/0+OOPB8fCw8PVu3dvHTx40MJkAIC2ZJsi89JLL6m2tla33nqrJMnj8SgiIkLdu3cPWc/tdofc4fjb8vLylJubG3zu8/kUHx/fFpFhA2effbYk6eDBgxo+fLjOPvvsE561dGw9AEDHYpsiU1xcrLFjxyouLu60tuN0OuV0OlspFewuPT1dhYWFioyM1N69e0POWnK73erSpYsaGhqUnp5uYUoAQFuxRZHZt2+f3njjDf35z38OjsXGxqqxsVG1tbUhszJer1exsbEWpIQdRUREKDMzU6tXr1ZERIRuuOEG9enTJ3jweH19vSZNmsTF8ACgg7JFkVm+fLl69+6ta6+9Njg2bNgwde7cWWVlZcrIyJAk7dq1S9XV1UpJSbEqKmzo2O0HSktL9eKLLwbHw8PDNWnSJG5PAAAdmOW3KAgEAkpKStLkyZO1cOHCkGV33HGHXnvtNa1YsULR0dGaMWOGJOnvf//7KW+fWxScObj7NQB0HMbcouCNN95QdXW1pk6detyyxYsXKywsTBkZGfL7/UpLS9PSpUstSAkTHNvNBAA4c1g+I9PWmJEBAMA8p/r9bemVfQEAAE4HRQYAABiLIgMAAIxFkQEAAMaiyAAAAGNRZAAAgLEoMgAAwFgUGQAAYCzLr+wLe2hoaFB1dbXVMfAtCQkJioyMtDoGANgWRQaSpOrqak2fPt3qGPiWoqIiDRgwwOoYAGBbFBlI+uYv/6KiIqtjnLZ9+/ZpwYIFevDBB5WYmGh1nNOWkJBgdQQAsDWKDCRJkZGRHeov/8TExA71fgAAJ8bBvgAAwFgUGQAAYCyKDAAAMBZFBgAAGIsiAwAAjMVZSwAA22tsbNTatWtVU1OjuLg4paenKyIiwupYsAGKDADA1goLC1VaWqqmpqaQsczMTN1+++0WJoMdUGQAALZVWFio1atX66yzztK0adOUkpKiiooKFRcXa/Xq1ZJEmTnDcYwMAMCWGhsbVVpaqrPOOkulpaUaN26cevTooXHjxoWMNzY2Wh0VFqLIAABsae3atWpqatK0adMUCARUWlqqJ554QqWlpQoEApo6daqampq0du1aq6PCQuxaAgDYUk1NjSRpz549Wrx48XHHyFx77bUh6+HMRJEBANhSXFycpG9mZk50jMzLL78csh7OTOxaAgDY0tixYyVJDodDzz//fMgxMs8//7wcDkfIejgzUWQAALa0fv16SVJzc7MmT56sdevW6YsvvtC6des0efJkNTc3h6yHMxO7lgAAtnTs2Jf09HS98sorevzxx4PLwsPDdd111+nll1/mGJkzHEUGAGBLx4596d+/v9avX3/clX03btwYsh7OTBQZAIAtpaenq7CwUMXFxfrZz36mzMzM4LKvv/5af/jDHxQeHq709HQLU8JqHCMDALCliIgIZWZm6ssvv1RmZmbIMTL/Oc49l85szMgAAGzr2O0HSktLjztGZtKkSdyeANbPyHz22Wf6xS9+oR49eigqKkqDBw/WO++8E1ze3Nyshx56SH369FFUVJRSU1O1Z88eCxMDANrT7bffrvXr1ys7O1vXX3+9srOztX79ekoMJFk8I/Pll1/qsssu0+jRo7V+/Xr16tVLe/bs0VlnnRVcZ9GiRXryySf17LPPKikpSbNnz1ZaWpo++ugjRUZGWpgeANBeju1mAr7N0iLz6KOPKj4+XsuXLw+OJSUlBf+9ublZS5Ys0axZs4IHc61cuVJut1svvfSSJk2adNw2/X6//H5/8LnP52vDdwAA9tfQ0KDq6mqrY+BbEhIS+IO8FVhaZF5++WWlpaUpMzNTmzdv1tlnn60777xT//Vf/yVJqqqqksfjUWpqavA1LpdLycnJqqioOGGRyc/P19y5c9vtPQCA3VVXV2v69OlWx8C3FBUVacCAAVbHMJ6lRWbv3r1atmyZcnNz9cADD2jbtm26++67FRERoSlTpsjj8UiS3G53yOvcbndw2bfl5eUpNzc3+Nzn8yk+Pr7t3gQA2FxCQoKKioqsjnHa9u3bpwULFujBBx9UYmKi1XFOW0JCgtUROgRLi0wgENDFF1+sRx55RJL0k5/8RB9++KEKCws1ZcqUFm3T6XTK6XS2ZkwAMFpkZGSH+ss/MTGxQ70fnB5Lz1rq06ePLrjggpCxQYMGBfflxsbGSpK8Xm/IOl6vN7gMAACcuSwtMpdddpl27doVMrZ79+7glGFSUpJiY2NVVlYWXO7z+bR161alpKS0a1YAAGA/lu5aysnJ0YgRI/TII4/ohhtu0Ntvv62ioqLgvlyHw6GZM2dq/vz56t+/f/D067i4OE2YMMHK6AAAwAYsLTKXXHKJ1qxZo7y8PM2bN09JSUlasmSJsrKyguvcd999qq+v1/Tp01VbW6uRI0dqw4YNnLIGAACsv0XBuHHjNG7cuJMudzgcmjdvnubNm9eOqQAAgAksv0UBAABAS1FkAACAsSgyAADAWBQZAABgLIoMAAAwFkUGAAAYiyIDAACMRZEBAADGosgAAABjUWQAAICxKDIAAMBYFBkAAGAsigwAADAWRQYAABiLIgMAAIxFkQEAAMaiyAAAAGNRZAAAgLEoMgAAwFgUGQAAYCyKDAAAMBZFBgAAGIsiAwAAjEWRAQAAxqLIAAAAY1FkAACAsSgyAADAWBQZAABgLIoMAAAwFkUGAAAYiyIDAACMZWmR+e///m85HI6Qx8CBA4PLGxoalJ2drR49eqhr167KyMiQ1+u1MDEAALATy2dkfvzjH+vAgQPBx5tvvhlclpOTo3Xr1qm0tFSbN29WTU2NJk6caGFaAABgJ50sD9Cpk2JjY48br6urU3FxsUpKSjRmzBhJ0vLlyzVo0CBt2bJFw4cPb++oAADAZiyfkdmzZ4/i4uLUr18/ZWVlqbq6WpJUWVmpo0ePKjU1NbjuwIEDlZCQoIqKipNuz+/3y+fzhTwAAEDHZGmRSU5O1ooVK7RhwwYtW7ZMVVVVuvzyy3X48GF5PB5FRESoe/fuIa9xu93yeDwn3WZ+fr5cLlfwER8f38bvAgAAWMXSXUtjx44N/vuQIUOUnJysxMREvfjii4qKimrRNvPy8pSbmxt87vP5KDMAAHRQlu9a+k/du3fXgAED9Omnnyo2NlaNjY2qra0NWcfr9Z7wmJpjnE6noqOjQx4AAKBjslWROXLkiP7xj3+oT58+GjZsmDp37qyysrLg8l27dqm6ulopKSkWpgQAAHZh6a6le++9V+PHj1diYqJqamo0Z84chYeHa/LkyXK5XJo2bZpyc3MVExOj6OhozZgxQykpKZyxBAAAJFlcZP7v//5PkydP1j//+U/16tVLI0eO1JYtW9SrVy9J0uLFixUWFqaMjAz5/X6lpaVp6dKlVkYGAAA2YmmRWb169Xcuj4yMVEFBgQoKCtopEQAAMImtjpEBAAD4ISgyAADAWBQZAABgLIoMAAAwFkUGAAAYiyIDAACMRZEBAADGosgAAABjUWQAAICxKDIAAMBYFBkAAGAsigwAADAWRQYAABiLIgMAAIxFkQEAAMaiyAAAAGNRZAAAgLEoMgAAwFgUGQAAYCyKDAAAMBZFBgAAGIsiAwAAjEWRAQAAxqLIAAAAY51Wkfn000+1ceNG/etf/5IkNTc3t0ooAACAU9GiIvPPf/5TqampGjBggH7+85/rwIEDkqRp06bpnnvuadWAAAAAJ9OiIpOTk6NOnTqpurpaP/rRj4LjN954ozZs2NBq4QAAAL5Lp5a86C9/+Ys2btyovn37hoz3799f+/bta5VgAAAA36dFMzL19fUhMzHHHDp0SE6n87RDAQAAnIoWFZnLL79cK1euDD53OBwKBAJatGiRRo8e3WrhAAAAvkuLdi0tWrRIV111ld555x01Njbqvvvu086dO3Xo0CG99dZbrZ0RAADghFo0I3PhhRdq9+7dGjlypNLT01VfX6+JEyfqvffe07nnntuiIAsXLpTD4dDMmTODYw0NDcrOzlaPHj3UtWtXZWRkyOv1tmj7AACg42nRjIwkuVwuPfjgg60SYtu2bXrmmWc0ZMiQkPGcnBy9+uqrKi0tlcvl0l133aWJEycy6wMAACS1sMhs3779hOMOh0ORkZFKSEg45YN+jxw5oqysLP3+97/X/Pnzg+N1dXUqLi5WSUmJxowZI0lavny5Bg0apC1btmj48OEtiQ4AADqQFhWZiy66SA6HQ9K/r+Z77Lkkde7cWTfeeKOeeeYZRUZGfue2srOzde211yo1NTWkyFRWVuro0aNKTU0Njg0cOFAJCQmqqKg4aZHx+/3y+/3B5z6f74e/QQAAYIQWHSOzZs0a9e/fX0VFRfrggw/0wQcfqKioSOeff75KSkpUXFysv/71r5o1a9Z3bmf16tV69913lZ+ff9wyj8ejiIgIde/ePWTc7XbL4/GcdJv5+flyuVzBR3x8fEveIgAAMECLZmQWLFigJ554QmlpacGxwYMHq2/fvpo9e7befvttdenSRffcc48ee+yxE25j//79+tWvfqXXX3/9e2dtfoi8vDzl5uYGn/t8PsoMAAAdVItmZHbs2KHExMTjxhMTE7Vjxw5J3+x+OnYPphOprKzUwYMH9dOf/lSdOnVSp06dtHnzZj355JPq1KmT3G63GhsbVVtbG/I6r9er2NjYk27X6XQqOjo65AEAADqmFs3IDBw4UAsXLlRRUZEiIiIkSUePHtXChQs1cOBASdJnn30mt9t90m1cddVVwdJzzG233aaBAwfqN7/5jeLj49W5c2eVlZUpIyNDkrRr1y5VV1crJSWlJbHblNfrVV1dndUxznjHbpHBrTLsweVyfef/BwDgdLWoyBQUFOi6665T3759g6dM79ixQ01NTXrllVckSXv37tWdd9550m1069ZNF154YchYly5d1KNHj+D4tGnTlJubq5iYGEVHR2vGjBlKSUmx3RlLXq9Xv7j5Fh1t9H//ymgXCxYssDoCJHWOcOq5/1lJmQHQZlpUZEaMGKGqqiqtWrVKu3fvliRlZmbqpptuUrdu3SRJN99882mHW7x4scLCwpSRkSG/36+0tDQtXbr0tLfb2urq6nS00a9/9btCgUiX1XEAWwhrqJP2blZdXR1FBkCbafEF8bp166ZRo0bpnHPOUWNjoyTpb3/7myTpuuuua9E2N23aFPI8MjJSBQUFKigoaGnMdhWIdCnQpafVMQAAOGO0qMjs3btX119/vXbs2CGHw6Hm5uaQ68g0NTW1WkAAAICTadFZS7/61a+UlJSkgwcP6kc/+pE+/PBDbd68WRdffPFxsyoAAABtpUUzMhUVFfrrX/+qnj17KiwsTOHh4Ro5cqTy8/N1991367333mvtnAAAAMdp0YxMU1NT8KDenj17qqamRtI315HZtWtX66UDAAD4Di2akbnwwgv1wQcfKCkpScnJyVq0aJEiIiJUVFSkfv36tXZGAACAE2pRkZk1a5bq6+slSfPmzdO4ceN0+eWXq0ePHnrhhRdaNSAAAMDJtKjI/Oc9ls477zx98sknOnTokM4666yQs5cAAADaUouvI/NtMTExrbUpAACAU9Kig30BAADsoNVmZACgo+KmsPbATWHtxS43haXIAMB34Kaw9sNNYe3BLjeFpcgAwHfgprDA8ex0U1iKDACcAm4KC9gTB/sCAABjUWQAAICxKDIAAMBYFBkAAGAsigwAADAWRQYAABiLIgMAAIxFkQEAAMaiyAAAAGNRZAAAgLEoMgAAwFgUGQAAYCyKDAAAMBZFBgAAGIsiAwAAjEWRAQAAxqLIAAAAY1FkAACAsSwtMsuWLdOQIUMUHR2t6OhopaSkaP369cHlDQ0Nys7OVo8ePdS1a1dlZGTI6/VamBgAANiJpUWmb9++WrhwoSorK/XOO+9ozJgxSk9P186dOyVJOTk5WrdunUpLS7V582bV1NRo4sSJVkYGAAA20snKHz5+/PiQ5wsWLNCyZcu0ZcsW9e3bV8XFxSopKdGYMWMkScuXL9egQYO0ZcsWDR8+3IrIAADARmxzjExTU5NWr16t+vp6paSkqLKyUkePHlVqampwnYEDByohIUEVFRUn3Y7f75fP5wt5AACAjsnyIrNjxw517dpVTqdTt99+u9asWaMLLrhAHo9HERER6t69e8j6brdbHo/npNvLz8+Xy+UKPuLj49v4HQAAAKtYXmTOP/98vf/++9q6davuuOMOTZkyRR999FGLt5eXl6e6urrgY//+/a2YFgAA2Imlx8hIUkREhM477zxJ0rBhw7Rt2zY98cQTuvHGG9XY2Kja2tqQWRmv16vY2NiTbs/pdMrpdLZ1bAAAYAOWz8h8WyAQkN/v17Bhw9S5c2eVlZUFl+3atUvV1dVKSUmxMCEAALALS2dk8vLyNHbsWCUkJOjw4cMqKSnRpk2btHHjRrlcLk2bNk25ubmKiYlRdHS0ZsyYoZSUFM5YAgAAkiwuMgcPHtQtt9yiAwcOyOVyaciQIdq4caOuvvpqSdLixYsVFhamjIwM+f1+paWlaenSpVZGBgAANmJpkSkuLv7O5ZGRkSooKFBBQUE7JQIAACax/GDfjiTsX7VWRwBso6N9Hjra+wFOh50+DxSZVhRVVW51BABthM83YE8UmVb0r6RRCkR1tzoGYAth/6rtUF/+fL6Bf7PT55si04oCUd0V6NLT6hgA2gCfb8CebHcdGQAAgFNFkQEAAMaiyAAAAGNRZAAAgLEoMgAAwFgUGQAAYCyKDAAAMBZFBgAAGIsiAwAAjEWRAQAAxqLIAAAAY1FkAACAsSgyAADAWBQZAABgLIoMAAAwFkUGAAAYiyIDAACMRZEBAADGosgAAABjUWQAAICxKDIAAMBYFBkAAGAsigwAADAWRQYAABiLIgMAAIxFkQEAAMbqZHWAjiSsoc7qCIBt8HkA0B4oMq3A5XKpc4RT2rvZ6iiArXSOcMrlclkdA0AHZmmRyc/P15///Gd98sknioqK0ogRI/Too4/q/PPPD67T0NCge+65R6tXr5bf71daWpqWLl0qt9ttYfJQbrdbz/3PStXV8Reo1fbt26cFCxbowQcfVGJiotVxzngul8tWn1UAHY+lRWbz5s3Kzs7WJZdcoq+//loPPPCArrnmGn300Ufq0qWLJCknJ0evvvqqSktL5XK5dNddd2nixIl66623rIx+HLfbzf+wbSQxMVEDBgywOgYAoI1ZWmQ2bNgQ8nzFihXq3bu3KisrNWrUKNXV1am4uFglJSUaM2aMJGn58uUaNGiQtmzZouHDhx+3Tb/fL7/fH3zu8/na9k0AAADL2OqspWO7ZmJiYiRJlZWVOnr0qFJTU4PrDBw4UAkJCaqoqDjhNvLz8+VyuYKP+Pj4tg8OAAAsYZsiEwgENHPmTF122WW68MILJUkej0cRERHq3r17yLput1sej+eE28nLy1NdXV3wsX///raODgAALGKbs5ays7P14Ycf6s033zyt7TidTjmdzlZKBQAA7MwWReauu+7SK6+8ovLycvXt2zc4Hhsbq8bGRtXW1obMyni9XsXGxlqQFMCZiuviAP9mp8+DpUWmublZM2bM0Jo1a7Rp0yYlJSWFLB82bJg6d+6ssrIyZWRkSJJ27dql6upqpaSkWBEZwBmG60QBJ2aX60RZWmSys7NVUlKitWvXqlu3bsHjXlwul6KiouRyuTRt2jTl5uYqJiZG0dHRmjFjhlJSUk54xhIAtDauE2UfXCfKXuxynShLi8yyZcskSVdeeWXI+PLly3XrrbdKkhYvXqywsDBlZGSEXBAPANoL14myF64Thf9k+a6l7xMZGamCggIVFBS0QyIAAGAS25x+DQAA8ENRZAAAgLEoMgAAwFgUGQAAYCyKDAAAMBZFBgAAGIsiAwAAjEWRAQAAxqLIAAAAY1FkAACAsSgyAADAWBQZAABgLIoMAAAwFkUGAAAYiyIDAACMRZEBAADGosgAAABjUWQAAICxKDIAAMBYFBkAAGAsigwAADAWRQYAABiLIgMAAIxFkQEAAMaiyAAAAGNRZAAAgLEoMgAAwFgUGQAAYCyKDAAAMBZFBgAAGIsiAwAAjGVpkSkvL9f48eMVFxcnh8Ohl156KWR5c3OzHnroIfXp00dRUVFKTU3Vnj17rAkLAABsx9IiU19fr6FDh6qgoOCEyxctWqQnn3xShYWF2rp1q7p06aK0tDQ1NDS0c1IAAGBHnaz84WPHjtXYsWNPuKy5uVlLlizRrFmzlJ6eLklauXKl3G63XnrpJU2aNOmEr/P7/fL7/cHnPp+v9YMDAABbsO0xMlVVVfJ4PEpNTQ2OuVwuJScnq6Ki4qSvy8/Pl8vlCj7i4+PbIy4AALCAbYuMx+ORJLnd7pBxt9sdXHYieXl5qqurCz7279/fpjkBAIB1LN211BacTqecTqfVMQAAQDuw7YxMbGysJMnr9YaMe73e4DIAAHBms22RSUpKUmxsrMrKyoJjPp9PW7duVUpKioXJAACAXVi6a+nIkSP69NNPg8+rqqr0/vvvKyYmRgkJCZo5c6bmz5+v/v37KykpSbNnz1ZcXJwmTJhgXWgAAGAblhaZd955R6NHjw4+z83NlSRNmTJFK1as0H333af6+npNnz5dtbW1GjlypDZs2KDIyEirIgMAABuxtMhceeWVam5uPulyh8OhefPmad68ee2YCgAAmMK2x8gAAAB8H4oMAAAwFkUGAAAYiyIDAACMRZEBAADGosgAAABjUWQAAICxKDIAAMBYFBkAAGAsigwAADAWRQYAABiLIgMAAIxFkQEAAMaiyAAAAGNRZAAAgLEoMgAAwFgUGQAAYCyKDAAAMBZFBgAAGIsiAwAAjEWRAQAAxqLIAAAAY1FkAACAsSgyAADAWBQZAABgLIoMAAAwFkUGAAAYiyIDAACMRZEBAADG6mR1ANhDQ0ODqqurrY5x2vbt2xfyT9MlJCQoMjLS6hgAYFsUGUiSqqurNX36dKtjtJoFCxZYHaFVFBUVacCAAVbHAADbMqLIFBQU6Le//a08Ho+GDh2qp556SpdeeqnVsTqUhIQEFRUVWR0D35KQkGB1BACwNdsXmRdeeEG5ubkqLCxUcnKylixZorS0NO3atUu9e/e2Ol6HERkZyV/+QAfFrmN7Ytdx63A0Nzc3Wx3iuyQnJ+uSSy7R008/LUkKBAKKj4/XjBkzdP/993/v630+n1wul+rq6hQdHd3WcQHAdnbv3t2hdh13FOw6/m6n+v1t6xmZxsZGVVZWKi8vLzgWFham1NRUVVRUnPA1fr9ffr8/+Nzn87V5TgCwM3Yd2xO7jluHrYvMF198oaamJrnd7pBxt9utTz755ISvyc/P19y5c9sjHgAYgV3H6Mg63HVk8vLyVFdXF3zs37/f6kgAAKCN2HpGpmfPngoPD5fX6w0Z93q9io2NPeFrnE6nnE5ne8QDAAAWs/WMTEREhIYNG6aysrLgWCAQUFlZmVJSUixMBgAA7MDWMzKSlJubqylTpujiiy/WpZdeqiVLlqi+vl633Xab1dEAAIDFbF9kbrzxRn3++ed66KGH5PF4dNFFF2nDhg3HHQAMAADOPLa/jszp4joyAACY51S/v219jAwAAMB3ocgAAABjUWQAAICxKDIAAMBYFBkAAGAsigwAADAWRQYAABjL9hfEO13HLpPj8/ksTgIAAE7Vse/t77vcXYcvMocPH5YkxcfHW5wEAAD8UIcPH5bL5Trp8g5/Zd9AIKCamhp169ZNDofD6jhoYz6fT/Hx8dq/fz9XcgY6GD7fZ5bm5mYdPnxYcXFxCgs7+ZEwHX5GJiwsTH379rU6BtpZdHQ0/6MDOig+32eO75qJOYaDfQEAgLEoMgAAwFgUGXQoTqdTc+bMkdPptDoKgFbG5xsn0uEP9gUAAB0XMzIAAMBYFBkAAGAsigwAADAWRQYAABiLIoMOo6CgQOecc44iIyOVnJyst99+2+pIAFpBeXm5xo8fr7i4ODkcDr300ktWR4KNUGTQIbzwwgvKzc3VnDlz9O6772ro0KFKS0vTwYMHrY4G4DTV19dr6NChKigosDoKbIjTr9EhJCcn65JLLtHTTz8t6Zt7bMXHx2vGjBm6//77LU4HoLU4HA6tWbNGEyZMsDoKbIIZGRivsbFRlZWVSk1NDY6FhYUpNTVVFRUVFiYDALQ1igyM98UXX6ipqUlutztk3O12y+PxWJQKANAeKDIAAMBYFBkYr2fPngoPD5fX6w0Z93q9io2NtSgVAKA9UGRgvIiICA0bNkxlZWXBsUAgoLKyMqWkpFiYDADQ1jpZHQBoDbm5uZoyZYouvvhiXXrppVqyZInq6+t12223WR0NwGk6cuSIPv300+Dzqqoqvf/++4qJiVFCQoKFyWAHnH6NDuPpp5/Wb3/7W3k8Hl100UV68sknlZycbHUsAKdp06ZNGj169HHjU6ZM0YoVK9o/EGyFIgMAAIzFMTIAAMBYFBkAAGAsigwAADAWRQYAABiLIgMAAIxFkQEAAMaiyAAAAGNRZAAAgLEoMgCMd84552jJkiVt+jM2bdokh8Oh2traNv05AH4Y7rUEwHjbtm1Tly5drI4BwAIUGQC21djYqIiIiO9dr1evXu2QBoAdsWsJQKv64x//qMGDBysqKko9evRQamqq6uvrdeWVV2rmzJkh606YMEG33npr8Pk555yjhx9+WLfccouio6M1ffp0jRgxQr/5zW9CXvf555+rc+fOKi8vD77u2K6lm266STfeeGPI+kePHlXPnj21cuVKSVIgEFB+fr6SkpIUFRWloUOH6o9//GPIa1577TUNGDBAUVFRGj16tP73f//39H85AFodRQZAqzlw4IAmT56sqVOn6uOPP9amTZs0ceJE/ZB70z722GMaOnSo3nvvPc2ePVtZWVlavXp1yDZeeOEFxcXF6fLLLz/u9VlZWVq3bp2OHDkSHNu4caO++uorXX/99ZKk/Px8rVy5UoWFhdq5c6dycnL0i1/8Qps3b5Yk7d+/XxMnTtT48eP1/vvv65e//KXuv//+lv5aALQhdi0BaDUHDhzQ119/rYkTJyoxMVGSNHjw4B+0jTFjxuiee+4JPr/hhhs0c+ZMvfnmm8HiUlJSosmTJ8vhcBz3+rS0NHXp0kVr1qzRzTffHFz/uuuuU7du3eT3+/XII4/ojTfeUEpKiiSpX79+evPNN/XMM8/oiiuu0LJly3Tuuefq8ccflySdf/752rFjhx599NEf/ksB0KaYkQHQaoYOHaqrrrpKgwcPVmZmpn7/+9/ryy+//EHbuPjii0Oe9+rVS9dcc41WrVolSaqqqlJFRYWysrJO+PpOnTrphhtuCK5fX1+vtWvXBtf/9NNP9dVXX+nqq69W165dg4+VK1fqH//4hyTp448/VnJycsh2j5UeAPbCjAyAVhMeHq7XX39df//73/WXv/xFTz31lB588EFt3bpVYWFhx+1iOnr06HHbONHZR1lZWbr77rv11FNPqaSkRIMHD/7OmZ6srCxdccUVOnjwoF5//XVFRUXpZz/7mSQFdzm9+uqrOvvss0Ne53Q6f/B7BmAtZmQAtCqHw6HLLrtMc+fO1XvvvaeIiAitWbNGvXr10oEDB4LrNTU16cMPPzylbaanp6uhoUEbNmxQSUnJSWdjjhkxYoTi4+P1wgsvaNWqVcrMzFTnzp0lSRdccIGcTqeqq6t13nnnhTzi4+MlSYMGDdLbb78dss0tW7b8kF8DgHbCjAyAVrN161aVlZXpmmuuUe/evbV161Z9/vnnGjRokLp06aLc3Fy9+uqrOvfcc/W73/3ulC8u16VLF02YMEGzZ8/Wxx9/rMmTJ3/va2666SYVFhZq9+7d+tvf/hYc79atm+69917l5OQoEAho5MiRqqur01tvvaXo6GhNmTJFt99+ux5//HH9+te/1i9/+UtVVlZqxYoVLfytAGhLFBkArSY6Olrl5eVasmSJfD6fEhMT9fjjj2vs2LE6evSoPvjgA91yyy3q1KmTcnJyNHr06FPedlZWln7+859r1KhRSkhIOKX1FyxYoMTERF122WUhyx5++GH16tVL+fn52rt3r7p3766f/vSneuCBByRJCQkJ+tOf/qScnBw99dRTuvTSS/XII49o6tSpP+wXAqDNOZp/yHmRAAAANsIxMgAAwFgUGQAAYCyKDAAAMBZFBgAAGIsiAwAAjEWRAQAAxqLIAAAAY1FkAACAsSgyAADAWBQZAABgLIoMAAAw1v8D+2YjIfI1MDEAAAAASUVORK5CYII=\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [],
      "metadata": {
        "id": "CoLhDgmnQL7Q"
      },
      "execution_count": null,
      "outputs": []
    }
  ]
}
