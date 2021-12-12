# Alliance Auth Grafana Dashboards!

## Installation

### Important
These dashboards are used from data gaterhed from Alliance Auth. If you don't have Alliance Auth running already,
please install it first before proceeding. (see the official
[AA installation guide](https://allianceauth.readthedocs.io/en/latest/installation/allianceauth.html)
for details)

### Step 1 - Install Grafana

Install as per grafana docs based on on youryour server reqruirmnets. [Source](https://grafana.com/docs/grafana/latest/installation/)

### Step 2 - Create Read only user in the database

Open up a SQLKL Shell with ``mysql -u root -p`` and then create a read only user for the Alliance Auth database and give it privileges on, replacing ``PASSWORD`` with a secure password

```bash
CREATE USER 'alliancegrafana'@'localhost' IDENTIFIED BY 'PASSWORD';
GRANT SELECT, SHOW VIEW ON alliance_auth . * TO 'alliancegrafana'@'localhost';
```
### Step 3 - Add Datasource to Grafana
Before you can import the dashboards, you need to add your data source.

Add a data source in grafana using the read only user created

* Move your cursor to the cog icon on the side menu which will show the configuration options.
![Data Source](/docs/images/datasource.png "Data Source")
* Click on Data sources. The data sources page opens showing a list of previously configured data sources for the Grafana instance.
* Click Add data source to see a list of all supported data sources.
* Move the curse over the MySQL data source and click on select
![Data Source](/docs/images/selectsource.png "Select Source")
* Configure the data source settings with the details we created in step 2

### Step 4 - Import Dashbnoards

* To import a dashboard click the + icon in the left side menu, and then click Import.
* Copy and paste in the contents of the JSON files for the Dashboard you require

## Avaliable Dashboards

There are a number of dashboards located within this repo - Some do require pre req mods to be isntalled along side your Alliance Auth Instalation which are highlighted below

Drop into each folder to see previews of each dashboard
#### Assets

| Name                             | Description                                                     | Modules Required        |
|:---------------------------------|:----------------------------------------------------------------|:------------------------|
| Assets / Location Search         | Will list all Capital Ships by Pilot and location               | Corp Tools |
| Assets / Overview                | Will display a list of all Capital ships in total               | Corp Tools |
| Assets / Assets Playgrond        | Will show assets by class of selected characters                | Corp Tools |


#### Capitals

| Name                             | Description                                                     | Modules Required        |
|:---------------------------------|:----------------------------------------------------------------|:------------------------|
| Capitals / Capitals              | Will give a break down of all total capital ships in group by location       | Corp Tools |

#### Clones

| Name                             | Description                                                     | Modules Required        |
|:---------------------------------|:----------------------------------------------------------------|:------------------------|
| Clones / Clones              | Will give a break down of where clones are located        | Corp Tools |

#### Tasks

| Name                             | Description                                                     | Modules Required        |
|:---------------------------------|:----------------------------------------------------------------|:------------------------|
| Task / Task             | Will show you how and when tasks are running and give overview on number of tasks ran        | Corp Tools / Celery |

Active Devs:
 * [MillerUk](https://github.com/milleruk)