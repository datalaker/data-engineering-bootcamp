# Klodars Datalake Design

## Problem Statement

Klodars Corporation is a fictitious organization that sells umbrellas and rain gear in Seattle, Washington (cliche much?). In addition to website sales, Klodars employs salespeople to reach out to retailers to sell its umbrellas as a bulk distribution in the Seattle area. It has a small software development team that writes applications to manage inventory and sales, leveraging SQL server as the operational database running on servers that are maintained in its offices. It also leverages Salesforce to manage its customer profiles and interactions.

Because of the quality of its rain gear and excellent sales channels, Klodars Corporation is rapidly expanding across the state of Washington as well as in the neighboring states of Oregon and Idaho. Its direct-to-consumer business is taking off through its website, and its marketing department is running excellent campaigns on social media. In addition, Klodars wants to expand its business to sell winter gear based on customer demand. So it plans to acquire another business that sells winter gear. While this is amazing news for the business, it is at that inflection point where its database technology doesn’t quite scale to its increasing needs, and it is evaluating a move to the cloud.

## Why Klodars Corporation Moves to the Cloud

Klodars Corporation is a thriving company that sells rain gear and other supplies in the Pacific Northwest region. The rapid growth in its business is driving its move to the cloud for the following reasons:

- The databases running on the on-premises systems do not scale anymore to the rapid growth of the business.
- As the business grows, the team is growing too. Both the sales and marketing teams are observing that their applications are getting a lot slower and even timing out sometimes because of the increasing number of users concurrently using the system.
- The marketing department wants more input into how it can best target its campaigns on social media and is exploring the idea of leveraging influencers but doesn’t know how or where to start.
- The sales department cannot rapidly expand work with customers distributed across three states, so it is struggling to prioritize the kinds of retail customers and wholesale distributors it wants to engage first.
- The investors love the growth of the business and are asking the CEO how Klodars Corporation can expand beyond winter gear. The CEO needs to figure out the expansion strategy.

Alice, a motivated leader from the software development team, pitches to the CEO and CTO of Klodars Corporation the idea of looking into the cloud and seeing how other business are leveraging a data lake approach to solve the challenges they are experiencing. She also gathers data points that show the opportunities that a cloud data lake approach can present, including the following:
- The cloud can scale elastically to the company’s growing needs, and given that it pays for consumption, it doesn’t need to overprovision its hardware to budget for peak seasons and have the hardware sit around at other times.
- Cloud-based data lakes and data warehouses can scale to support the growing number of concurrent users.
- The cloud data lake has tools and services to process data from various sources, such as website clickstreams, retail analytics, social media feeds, and even the weather, so the company can have a better understanding of its marketing campaigns.
- Klodars Corporation can hire data analysts and data scientists to process trends from the market to help provide valuable signals to help with its expansion strategy.

The CEO is completely sold on this approach and wants to try out the cloud data lake solution. At this point in its journey, it’s important for Klodars Corporation to keep its existing business running while it starts experimenting with the cloud approach. Let’s take a look at how different cloud architectures can bring unique strengths to Klodars while also helping meet its needs arising from rapid growth and expansion.

## Use Case for a Modern Data Warehouse Architecture

Klodars will leverage the modern data warehouse architecture and start loading data from its operational databases into the data lake. Instead of continuing to store its backups on its on-premises systems, it can now create daily backups and store up to one year’s worth of backups (or more if it wants to) in its data lake. Klodars can do this while the operational databases on its servers continue to serve their existing applications, thereby ensuring the continuity of the company’s operations. In addition, Klodars will plan to load data from social media feeds that relate to rain gear and winter gear to analyze patterns. This architecture will also enable the company to load other data, such as its clickstream, into the data lake storage in real time using real-time ingestion techniques like Apache Kafka.

With the dataset up and ready to go, the data engineering team will use tools like Apache Spark to process the structured data from its database dumps and from the website clickstream to generate high-value data that shows the shopping and sales trends over time. The team will also process the social media feeds and extract data that pertains to rain gear and winter gear as well as any associated purchases that the same feeds indicate. This architecture will enable the data engineering team to generate high-value data on a scheduled basis (e.g., daily) on sales trends, inventory and supply, website-browsing trends, and social media trends around rain and winter gear. This data will then be loaded into the data warehouse and refreshed on a periodic basis (e.g., daily).

The data stored in the data warehouse is very high-value structured data. The business analysts will use this high-value data to build dashboards that show the sales trends quarter over quarter or month over month, so the sales teams can understand the trend of their sales and set projections for the upcoming time period. The business analysts can also slice and dice the data by factors like region, salespeople coverage, partners, and other attributes, so the leadership team can understand the growth drivers and make data-informed decisions about the company’s expansion strategy. The marketing team consumes the social media and website-browsing trends by running interactive queries on the data warehouse to understand the next set of targeted marketing campaigns to develop. The team can also understand the impact of its marketing campaigns by correlating the campaigns with the sales results.

The impact doesn’t stop there. Klodars now has formed a data science team that can build on the existing datasets, such as sales, social media trends, and website-browsing trends, to find interesting correlations and effects of influencers that are not straightforward to process with manual analysis. The team can bring additional datasets to the data lake, such as weather data, data about winter activities like skiing, and so on, to surface interesting insights to the leadership team. This data can be fed back to the data engineering team to be loaded into the warehouse to be consumed by the leadership, marketing, and sales teams.

Figure below provides a representation of the modern data warehouse architecture at Klodars Corporation.

![How Klodars Corporation leverages the modern data warehouse architecture](https://user-images.githubusercontent.com/62965911/215307132-e0e906b1-3491-4b12-afa9-bfbe063f1674.png)

With the data lake strategy relying on a modern data warehouse architecture, Klodars Corporation is able to scale to its growing customer needs by prioritizing the right set of focus areas informed by data. Its modern data warehouse strategy enables the company to work on innovations while simultaneously keeping its existing business running. The phased movement of its existing applications to the modernized cloud architectures gives the team time to thoughtfully design and implement this transition.

## Use Case for Data Lakehouse Architecture

Klodars Corporation will leverage the data lake by loading data from its operational data bases into the data lake storage, similar to what we saw in the modern data warehouse architecture. Let’s take a closer look at how this architecture affects the business.

The data engineering team will now use tools like Apache Spark to process the structured data from its database dump and from the website clickstream to generate high-value data that shows the shopping and sales trends over time. The team will also process the social media feeds and extract data that pertains to rain and winter gear as well as any associated purchases the same feeds indicate.

Let’s now move on to how this extracted data will be processed. The data engineering team will generate high-value data on a scheduled basis (e.g., daily) on sales trends, inventory and supply, website-browsing trends, and social media trends around rain and winter gear. Now, instead of loading data into the warehouse, the business analysts can start querying this data using their familiar tool of choice based on SQL, as well as modern querying tools like Presto, without having to move the data. Similar to the modern data warehouse pattern, the data scientists can bring their own datasets, such as the weather data, as well as explore data that is already in the data lake.

The lakehouse provides a key advantage over the modern data warehouse by eliminating the need to have two places to store the same data. Let’s say that the data science team leveraged its new datasets, such as the weather data, and built a new dataset that correlates sales with the weather. The business analysts have this data ready to go for their deeper analysis since everyone is using the same data store, and possibly the same data formats. Similarly, if the business analysis generated a specific filtered dataset, the data scientists can start using this for their analysis.

Take a moment to think about what this means and what the impact is. This completely explodes the scenarios, promoting the cross-pollination of insights between the different classes of consumers of the data platform. A shared platform with no silos implies that the data generated by the BI analysts and the data scientists is available for both to further innovate on, thereby increasing the value of data multifold for Klodars Corporation. A representation of the data lakehouse architecture at Klodars Corporation is presented below:

![How Klodars Corporation leverages the data lakehouse architecture](https://user-images.githubusercontent.com/62965911/215307131-fbaf5406-5863-4a22-9230-53553dd1d05f.png)

## Use Case for a Data Mesh Architecture

Klodars Corporation was running fine as long as its software products and teams were smaller. However, as the business grew and launched in more regions, the teams and organization grew significantly, and the central data platform was no longer able to scale to the needs. Further, as Klodars Corporation acquired other companies on different technology stacks, it was hard for them to integrate as one unit. Alice and her team on the central data platform decided to implement a data mesh architecture.

The central data platform team at Klodars Corporation publishes the architecture, along with deployment and configuration scripts to automate the domain setup, and they set up data governance, compliance, and the data sharing infrastructure. Klodars Corporation has sales, marketing, and customer success teams that implement their domains and share their insights with other organizations. The sales team finds that the modern data warehouse architecture suits its needs, given that it has a prolific usage of operational databases, and the customer success team finds the lakehouse architecture better for its needs, given the diversity of data sources that can benefit both its BI and data science teams. The data mesh pattern enables Klodars Corporation to give this freedom of choice to its domains while promoting the sharing of data, maintaining the proposition of a unified data platform. Further, the companies that Klodars Corporation acquired were able to retain their existing data lakes with minor tweaks. When Klodars Corporation wants to expand to winter gear, it can effectively share its insights with the ski corporations it partners with to promote a better partnership, extending the data mesh architecture. Klodars Corporation is growing rapidly and wants to expand its business to Europe, which has unique data residency and other compliance requirements. It can set up domains specific to the European Union (EU) that also respect EU-specific requirements without incurring a huge development or rearchitecture effort. Further down the road, when Klodars Corporation acquires other companies, it can onboard the data platforms of the companies they acquired as domains to its existing data mesh. A representation of the data mesh architecture at Klodars Corporation is depicted below:

![How Klodars Corporation leverages the data mesh architecture](https://user-images.githubusercontent.com/62965911/215307128-c17a4143-8a37-435c-8058-7c7f0d5327d8.png)

![Data Governance](https://user-images.githubusercontent.com/62965911/215307120-e8c13cc2-d629-4848-a876-7092c261cde8.png)

## Setting Up the Cloud Data Lake Infrastructure

![Decision framework for the cloud data lake](https://user-images.githubusercontent.com/62965911/215307129-43364063-0283-45e1-af6c-d49014fd500b.png)

### Step 1: Identify the Goals

Klodars Corporation currently has legacy applications leveraging operational databases (SQL server) to manage its inventory and sales, and customer relationship management (CRM) software (such as Salesforce) to manage its customer profile and interactions. When Klodars Corporation hits growing pains as it rapidly expands across the state of Washington and neighboring states, along with the growth of its online business, its software development leader, Alice, pitches the idea of developing a data lake to her executives, and they are eager to invest in the approach.

The rubber has hit the road, and Alice begins planning the data lake implementation project. The very first step she takes is to inventory the problems across the organization, and she comes up with the list outlined in table below:

| **Customer** | **Problem**                                                                                           | **Severity of problem** | **Helpfulness of data lake** | **How cloud data lake can help**                                                                                                                                           |
| ------------ | ----------------------------------------------------------------------------------------------------- | ----------------------- | ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Engineering  | Database is not scaling to growth of business.                                                        | High                    | High                         | Cloud infrastructure can elastically scale.                                                                                                                                |
| Sales        | Sales queries are painstakingly slow.                                                                 | Medium                  | High                         | Cloud infrastructure scaling can support a growing number of concurrent users.                                                                                             |
| Sales        | I can’t prioritize which retailer or wholesale distributor to engage outside the state of Washington. | High                    | Medium                       | While we can explore retail datasets to identify the sales, this would be more experimental and takes time to mature.                                                      |
| Marketing    | Queries are taking a really long time to run; complex queries are timing out.                         | High                    | High                         | Cloud infrastructure scaling can support a growing number of concurrent users.                                                                                             |
| Marketing    | I am spending a lot of time running targeted campaigns.                                               | High                    | High                         | Cloud data lakes can support data science scenarios that help with personalized and targeted campaigns.                                                                    |
| Marketing    | I need to find the right influencers for our product.                                                 | High                    | Medium                       | While data science and machine learning can identify insights from social media, the specific influencers are determined with more one-to-one connections and engagements. |
| Exec team    | I need to understand what product offerings we can start expanding to beyond winter gear.             | Medium                  | High                         | We can run data science models on retail datasets to understand the behavior of customers buying winter gear to come up with useful product recommendations.               |

Based on this inventory, Alice defined the goals of her data lake implementation as follows and reviews it with her stakeholders to finalize the goals:

- (Must have) Support better scale and performance for existing sales and marketing dashboards as measured by a 50% increase in query performance at the 75th percentile.
- (Must have) Support data science models on the data lake as measured by a pilot engagement on product offering recommendations to the executive team.
- (Nice to have) Support more data science models on the data lake as measured by the next set of scenarios on partnership identification for sales and by influencer recommendation for marketing.

### Step 2: Plan the Architecture and Deliverables

Based on the goals defined for the cloud data lake implementation, Alice and her team then investigate different architecture choices using the following guiding principles:

- There is minimal/no disruption to the existing dashboards that sales and marketing teams consume.
- The dashboards need to scale to the growth of the data and address the performance issues faced by customers.
- The data science scenarios need to be addressed as part of the new platform. This includes product recommendations for the executive team, distributor/retailer recommendations to sales teams, and influencer recommendations to marketing teams.
- Given the criticality of the dashboards to the business and the projected future growth that needs to be factored in, the new architecture needs to be rolled out in the next six months.

They evaluate the following architecture patterns on the cloud (this is fairly agnostic of the specific provider):

- Cloud data warehouse: In this architecture pattern, there is no cloud data lake involved, and the primary component would be a cloud data warehouse. If you would like a refresher on cloud data warehouses, refer to “Cloud Data Warehouses”. While this would take the least time to implement and be a seamless experience for the business analysts from sales and marketing teams, the data science capabilities are limited. As a result, this could serve as a pilot, but there might be roadblocks when the scenarios get more advanced, such as bringing in more diverse datasets.
- Modern data warehouse: As we saw in “Modern Data Warehouse Architecture”, this involves leveraging cloud data lake storage for the data collection and processing and a cloud data warehouse for BI scenarios. This would take a bit longer to implement than the cloud data warehouse. However, the rich set of data science capabilities on the data lake would help the team focus on the pilots while also supporting the data analysts through the data warehouse. Additionally, the data lake offers cheaper storage to preserve multiple snapshots of historical data of the on-premises databases.
- Data lakehouse: As we saw in “Data Lakehouse Architecture”, this involves leveraging a cloud data lake storage for the end-to-end implementation without requiring a cloud data warehouse component. This is very attractive for the team given the support for both data science and data analyst scenarios; however, they soon realize that upskilling is required for the tooling support and automation end to end.

The team did not evaluate the data mesh architecture because it wanted to focus on maintaining central control of the end-to-end implementation. They will evaluate the data mesh during the next phase of the project.

The team settled on a modern data warehouse architecture, because it provided a smoother transition from the current architecture while offering support for data science. The team also plans to investigate data lakehouse and data mesh architectures in the next phase of the project once they are up and running on the cloud.

As shown in figure below, the modern data warehouse architecture for Klodars Corporation consists of the following components:

- A cloud data lake storage that acts as a central repository of the data
- Ingestion systems that upload data from existing sources, such as the operational data store, as well as new data sources, such as social media, into the cloud data lake
- Data processing engines that process data from the cloud data lake storage with complex data transformations to generate high-value data
- Data science and machine learning solutions that are leveraged by data scientists for ad hoc exploratory analysis
- A cloud data warehouse that serves this high-value data to BI use cases and data analysts

![Proposed Cloud Data Lake Architecture for Klodars Corporation](https://user-images.githubusercontent.com/62965911/215307136-b2c4e5ff-6334-4c33-a614-5402fb3a04e7.png)

The deliverable for their project consists of the following phases:

- Phase 1: Ingestion - Load data into the data lake. Set up automated pipelines to take daily backups of the operational databases and CRM system in the data lake. Store data for the past 90 days.
- Phase 2: Processing - This consists of two phases that can run in parallel:
    - Process BI data: Run processing pipelines to refresh data daily into the cloud data warehouse. Validate with feedback from data analysts on sales and marketing teams.
    - Advanced scenarios: Develop product recommendation models based on data from the operational databases and CRM system, leveraging data scientists.
- Phase 3: Limited release - This phase involves the release of the data lake platform to select customers from the sales, marketing, and executive teams while the on-premises implementation is still running. This helps catch issues early and iterate based on customer feedback.
- Phase 4: Release to production - This involves the release of the data lake to all customers at the Klodars Corporation. At this point, both the on-premises and the cloud platforms are running in parallel.
- Phase 5: Turn off on-premises dashboards - Once the data lake implementation is successful on the cloud, the dashboards running on premises for the analysis will be turned off.

After completing the plan (step 2), next step would be 1) Implementing the Cloud Data Lake, and 2) Release and Operationalize.

## Data Governance at Klodars Corporation

Alice and her team understand the importance of data governance for their data platform architecture and set out to make the following changes:

- They leverage a data catalog based on the open source Apache Atlas to curate and publish the metadata for data in their enriched and curated zones.
- They classify data in the Sales and Customer tables with the right classes—PII, financial information, and so on—and data types and ensure that the data catalog has information about this data classification.
- Given that they don’t require the actual PII information for their scenarios, they write a PII scrubber to ensure that the PII data is masked (a unique hash for the value is stored instead of the value in plain text). The result is that the data analysts can still look at information for unique users without seeing their personal information.
- From a security and access control perspective, they do the following:
    - They implement data lake storage security so that access to raw data is locked down to just the platform team and access to enriched data and curated datasets is read-only for the business analysts and data scientists in their organizations. The data scientists and business analysts have read and write access to the workspaces provisioned for them but can’t see other users’ workspaces unless they choose to share explicitly.
    - They ensure that the product and executive teams have access to the dashboards and that the data scientists have access to all of the data science computational frameworks. The ingest pipeline and data-prep pipeline are strictly locked down to the data engineering team.
    - They implement a data governance solution that has the data catalog as well as policy and access management across both the data lake and the data warehouse data.

The below figure shows the implementation of data governance by Klodars Corporation.

![Data governance at Klodars Corporation](https://user-images.githubusercontent.com/62965911/215307136-b2c4e5ff-6334-4c33-a614-5402fb3a04e7.png)

## Implementing the Cloud Data Lake

Klodars Corporation planned to implement its solution as a hybrid solution, with its legacy component running on premises and its data analytics components running on the cloud. It picked PaaS for its big data cluster and data lake storage, running Apache Spark, and leveraged a SaaS solution for its data warehouse and dashboarding component. Klodars understood the impact of networking resources between its on-premises solution and its cloud provider on the performance of its solution and planned for the right capacity with the cloud provider. It also ran a PoC of the data processing workload of one of its data- and compute-intensive scenarios—product recommendation and sales projections—and ensured that it had picked a big data cluster with the right set of resources.

Klodars also segmented their clusters—one for sales scenarios, one for marketing scenarios, and one for product scenarios—to ensure that a peak workload on one did not affect the performance of the others. To promote sharing of data and insights, the data scientists had access to all of the data from product, sales, and marketing for their exploratory analysis. However, Klodars also provisioned separate clusters for the data scientists and set a limit for the resources so that there were guardrails against spurious jobs that could hog resources. You can find an overview of this implementation in figure below:

![Data lake implementation at Klodars Corporation](https://user-images.githubusercontent.com/62965911/215307127-df8c4688-d100-4cb4-bf72-7e9a673c62dd.png)

## How Klodars Corporation Managed Its SLAs, SLOs, and SLIs

Klodars Corporation has a daily executive briefing at 9 A.M. where they look at the daily sales data for their products; this data helps the team strategize about the plans and allocations for the day and is time used for inventory planning. This requirement defines the needs for the SLA. The sales team and the data team agree on a contract that the sales dashboards will be refreshed with the new data by 9 A.M. This becomes the SLA that the data team promises the sales team.

The data team then works backward from this SLA and defines the requirements for their copy jobs and Spark jobs. The data team knows that the latest data lands in their sales databases by 3 A.M., and a dump of that data needs to be copied over to the data lake storage to serve as input for the Spark jobs. The Spark jobs crunch the data from this sales database with other data to produce the datasets that power the sales dashboard. This understanding helps the data team set goals for their copy job and Spark job appropriately. The Spark job needs to be completed by 8 A.M. to give a one-hour buffer for any unforeseen issues. So the data team has a window between 3 A.M. and 8 A.M. to meet its SLAs. The team runs a few PoCs and defines the goals as three hours or less for the copy job and two hours or less for the Spark job. These become the SLOs.

The team then builds metrics dashboards about the copy job progress tracking as well as the Spark job progress tracking, along with the finer granular details pertaining to both jobs. These metrics serve as the SLIs. These concepts are illustrated in Figure below.

![Klodars Corporation working on SLAs, SLOs, and SLIs](https://user-images.githubusercontent.com/62965911/215307135-6e83797e-0e77-4c45-b93a-78b8c56b6e57.png)

A pictorial representation of how these metrics align with the architecture of Klodars Corporation is shown in Figure below.

![Klodars Corporation’s data lake architecture and SLAs, SLOs, and SLIs](https://user-images.githubusercontent.com/62965911/215307133-c97cfca7-5c5f-4d09-9082-84a7b64a3f22.png)

These become the defining requirements for deciding what kind of architecture and technical components serve as the best choices to meet the SLAs while optimizing for cost and operational burden on the data team.

## How Klodars Corporation picked their data formats

Alice and her team understood the importance of data formats in their organization and ensured that their data preparation jobs stored the enriched and curated data in Apache Parquet. Based on analyzing their use cases, the time values (e.g., dates of sales, inventory dates) and regional information were most commonly used for queries and dashboards, so they optimized their Parquet files in a way that they were organized based on the dates and regions. This greatly improved the query performance for their dashboards, and their business analysts were more productive. Since the format offered a very high degree of compression, they were able to demonstrate savings in data storage costs that were well appreciated by the finance teams and executive leadership. Alice and her team are also evaluating the use of Delta Lake or Apache Iceberg as the first step to running the data lakehouse pattern they are going to explore.

## Optimal data organization strategy for Klodars Corporation

Alice and her team wanted to explore various ways to partition their data. They took a closer look at their sales data, which most of their customers queried on, and brainstormed various options to organize it, as shown in Figure 5-10:

- Option 1: Organize data by regions followed by salesperson; this option is optimized for queries where regional sales patterns are most commonly used, followed by individual performance.
- Option 2: Organize data by time, followed by regions; this option is optimized for queries where trend over time is most commonly used, followed by regional pivots.
- Option 3: Organize data by regions, followed by time; this option is optimized for queries where regional sales patterns are most commonly used, followed by trends over time.

![Data partitioning options at Klodars Corporation](https://user-images.githubusercontent.com/62965911/215307124-3af89ecb-3c0c-405d-a22d-f9524a884595.png)

They interviewed the consumers and looked at the query trends on the data lake and data warehouse. They determined that the most common query pattern was regional, followed by trends over time, so they chose Option 2 as their partitioning strategy. They repeated this analysis for their other datasets and ensured that the partitioning strategy met their usage patterns.