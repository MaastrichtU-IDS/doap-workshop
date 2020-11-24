### Descriptors DOAP

A critical component of project reusability is providing standard metadata descriptors. Thus, adding DOAP descriptors will greatly improve the reusability of the project. We hope that adopting DOAP schema will lead search engines and other applications to give users direct access to the project, and thus increase visibility.

Each project's owner provides a DOAP with a list of "descriptors" to categorize each release, describing who it's for, what systems it can run on, and how mature it is. It is noteworthy that some of the descriptors could be not useful for you and thereby, they can be empty.



## Example 1: [Fairsharing Metrics](https://github.com/MaastrichtU-IDS/fairsharing-metrics)

---

#### 📋 Project information

The selection of project type strictly depends on the project content. In this case, the project is categorized in "*Research*" type.

| 🗂️ Type of project | `doap: category`                                             |
| ----------------- | ------------------------------------------------------------ |
| 🧪 Research        | A folder that contains all your "*Research*" related project's file |

The descriptor for project type is `category` and will look like the following:

```turtle
doap:category "Research" ;
```

---

The next step is to select the status of your project. The table below shows the current definition for each status.

| ✔️ Status of the project | `bibo:status`                                                |
| :---------------------- | ------------------------------------------------------------ |
| 🚀 Active                | The project is being actively developed since the first commit. <img src="https://www.repostatus.org/badges/latest/active.svg" alt="Project Status: Active - A IDS project is a publicly available code concerning IDS grants in varying state of usability, development and support.."> |
| 🗑️ Inactive              | The project is no longer being actively developed, support/maintenance. <img src="https://www.repostatus.org/badges/latest/inactive.svg" alt="Project Status: Inactive- A IDS project is a publicly available code concerning IDS grants in varying state of usability, development and support.."> |
| 🚧 Work in Progress*     | Initial development is in progress, but there has not yet been a stable, usable release suitable for the public. <img src="https://www.repostatus.org/badges/latest/wip.svg" alt="Project Status: WIP- Initial development is in progress, but there has not yet been a stable, usable release suitable for the public."> |

> *🚧not yet available in the list (TBD)

The status of a project has been gathered from [bibo ontology](http://purl.org/ontology/bibo/) and will look like this:

```turtle
bibo:status "Active" ;
```

From this point onward, the necessary information can be directly gathered from the Github repository.

| 🎬 Project name | Typically the title of the `README.md` |
| -------------- | -------------------------------------- |
| `doap: name`   | `doap:name "Fairsharing Metrics" ;`    |

| 🔖 Project description | Typically the title of the Github `About` repository details |
| --------------------- | ------------------------------------------------------------ |
| `doap: description`   | `doap:description "A Dockerization of the Fairsharing metrics as a module for Data Quality Analysis."` |



| ⚖️ License URL   | Add a license of the `LICENSE.md` repository details. Or chose a popular license [here]( https://choosealicense.com/) |
| --------------- | ------------------------------------------------------------ |
| `doap: license` | `doap:license <https://github.com/MaastrichtU-IDS/fairsharing-metrics> ;` |

| ☕ Programming languages          | A full list of programming languages we accept is available in the [form](https://maastrichtu-ids.github.io/projects/create-doap). Feel free to customize your doap file as best your convenience |
| -------------------------------- | ------------------------------------------------------------ |
| ```doap: programming-language``` | ```doap:programming-language "Python" ;```                   |



---

### 🔗 Project links

| 💾 Git repository URL (GitHub/GitLab) | URL location of your repository                              |
| ------------------------------------ | ------------------------------------------------------------ |
| `doap: repository`                   | `doap:location <https://github.com/MaastrichtU-IDS/fairsharing-metrics> ;` |

| 🚧 Issue tracker URL | URL location of your issue tracker                           |
| ------------------- | ------------------------------------------------------------ |
| `doap:bug-database` | `doap:bug-database <https://github.com/MaastrichtU-IDS/fairsharing-metrics/issues> ;` |

| 🏠 Project homepage URL | URL location of your website                                 |
| ---------------------- | ------------------------------------------------------------ |
| `doap: homepage`       | `doap:homepage <https://github.com/MaastrichtU-IDS/fairsharing-metrics> ;` |

| 🏠📖 Project wiki | URL location of your project wiki                            |
| --------------- | ------------------------------------------------------------ |
| `doap: wiki`    | `doap: wiki <https://github.com/MaastrichtU-IDS/fairsharing-metrics/wiki>` |

| 📥 Project download page | URL location of your downloadable package |
| ----------------------- | ----------------------------------------- |
| `doap: download-page`   |                                           |

| 🛩️ Service endpoint URL   | URL location of your endpoint service |
| ------------------------ | ------------------------------------- |
| `doap: service-endpoint` |                                       |

| 💬 Mailing list or community chat URL | URL location of your chat channel and communication |
| ------------------------------------ | --------------------------------------------------- |
| `doap:mailing-list`                  |                                                     |

---

### 👤 Contact details

| 🏷️ Contributor name | Name and Surname of the project owner |
| ------------------ | ------------------------------------- |
| `foaf:name`        | `foaf:name "Vincent Emonet" ;`        |

| 📬 Contributor email | Email of the project owner                                  |
| ------------------- | ----------------------------------------------------------- |
| `foaf:mbox`         | `foaf:mbox <mailto:vincent.emonet@maastrichtuniversity.nl>` |

Feel free to manually add more [DOAP project properties](https://vemonet.github.io/doap/class-doapproject.html) or contributors after downloading the turtle file.