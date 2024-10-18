# Help Section

## Help Flow

* Every page in the plant operator's screen has a help button on the top right.
* Clicking on it takes the user to the help screen which shows a list of videos.  Each video has a title and a description.
* Clicking on a video runs it in a media player.
* Flows in the app can be stored in a video and it can be shown in this screen.
* This page is fully configurable through MDMS.
* Refer to the following MDMS file to configure the list of videos:&#x20;

{% embed url="https://github.com/egovernments/egov-mdms-data/blob/b7c8f264c6005b030f694ada754f0d7a52a85640/data/pg/common-masters/howItWorks.json" %}

* Multiple languages can be configured. Currently, English and Hindi are the two options available.&#x20;

<figure><img src="../../../../.gitbook/assets/image (165).png" alt="" width="310"><figcaption><p>Help Section UI</p></figcaption></figure>

* Sample configuration object:&#x20;

```json
{
          "TQM": {
              "moduleCode" : "TQM",
              "videosJson":  [
                  {
                      "headerLabel": "TQM_HELP_Q1",
                      "description": "TQM_HELP_Q1_DESC",
                      "en_IN": "https://media.w3.org/2010/05/sintel/trailer.mp4",
                      "hi_IN": "https://media.w3.org/2010/05/sintel/trailer.mp4"
                  },
                  {
                    "headerLabel": "TQM_HELP_Q2",
                    "description": "TQM_HELP_Q2_DESC",
                    "en_IN": "https://media.w3.org/2010/05/sintel/trailer.mp4",
                    "hi_IN": "https://media.w3.org/2010/05/sintel/trailer.mp4"
                  },
                  {
                    "headerLabel": "TQM_HELP_Q3",
                    "description": "TQM_HELP_Q4_DESC",
                    "en_IN": "https://media.w3.org/2010/05/sintel/trailer.mp4",
                    "hi_IN": "https://media.w3.org/2010/05/sintel/trailer.mp4"
                  },
                  {
                    "headerLabel": "TQM_HELP_Q4",
                    "description": "TQM_HELP_Q4_DESC",
                    "en_IN": "https://media.w3.org/2010/05/sintel/trailer.mp4",
                    "hi_IN": "https://media.w3.org/2010/05/sintel/trailer.mp4"
                  },
                  {
                    "headerLabel": "TQM_HELP_Q5",
                    "description": "TQM_HELP_Q5_DESC",
                    "en_IN": "https://media.w3.org/2010/05/sintel/trailer.mp4",
                    "hi_IN": "https://media.w3.org/2010/05/sintel/trailer.mp4"
                  },
                  {
                    "headerLabel": "TQM_HELP_Q6",
                    "description": "TQM_HELP_Q6_DESC",
                    "en_IN": "https://media.w3.org/2010/05/sintel/trailer.mp4",
                    "hi_IN": "https://media.w3.org/2010/05/sintel/trailer.mp4"
                  }
              ],
              "screenHeader":"TQM_HELP_SECTION"
          }
      }
      
```

* The above configuration object is used to render the screen. It has a video level header and description along with URLs for Hindi and English videos. The page level header is also present.
* The module name can be configured. For example, here we have added the module name as TQM.&#x20;
