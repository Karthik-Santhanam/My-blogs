# Mainframe Modernization - A perspective

## "What" do we mean by Mainframe modernization?

> Most of the thoughts here are my own and out of my experiences. Please feel free to disagree/comment/share your thoughts.

Before I answer the question as to what is mainframe modernization, allow me to pose a few more questions. Have we heard of any of the following?
- IIS Modernization
- WAS modernization
- Liberty server moderniztion

I don't think any one of us have heard of it. Because, by default we know that these are server software and hardware and they are modernized whenever there is a need to modernize them and there is continuous work happening there. 

### Prelude to the Mainframe world

So, to answer the original question here goes another question. Do we have to modernize mainframe?  Or the applications running on it? Just so that we are aware, the latest z15 Mainframe (Linux One III) was launched in first quarter of 2020.

> Fact check: z13 released in 2015 as far as clocking is concerned is as fast as or faster than the 2021 Intel Xeon (Tiger lake family) at its Max Turbo frequency (5GHz). z15 released in 2019 is way faster than most of x86 servers available in the market. 

While we are at it, let us talk a bit more about other innovations in this space. In the early 90s, there was this famous alliance called AIM - short for Apple, IBM and Motorola who created PCs using RISC (Reduced Instruction Set Computing) while most computers, including Mainframe and x86 machines (majorly Microsoft) used CISC (Complex Instruction Set Computing). In 2000s, mobile technologist thought; for a small battery size, we need to use ARM processors (basically RISC based chips manufactured originally by Acron) and we have seen the fast hand held computers these days. Apple used their first home grown chip A6 on iPhone 5 (I had one of those and loved it. I still have it in my garage... :sad:). Still they statyed with Intel on their PCs. They still believed in CISC. Now, fast forward to 2020, Apple announced M1 chip which is based on their A12 Bionic chip (basically that runs on iPhones) to run their PCs and laptops. A breakthrough in innovation. They claim it is 5x faster. I am yet to lay my hand on one of those Macbook beauties. What goes around comes around, I suppose!

> Fact check: IBM annonced a breakthrough innovation in lithography space in 2021. They created a 2nm chip in their labs. It is true! 

A lot of workloads that run the x86 distributed servers can run on z13, z14 and specially z15 mainframes. A zServer can have zOS and Linux (Ubuntu, SuSE, RHEL and debian are the knwon ones) running on the same server. There are speciality processors for running Linux workload - IFLs (Integrated Facility for Linux).

Excerpt from https://www.ibm.com/downloads/cas/K9XD9V1Q

Dense consolidation of workloads is made possible by z15 workload management capabilities. z15 is designed to support 80% or higher sustained utilization rates. Based on IT Economics assessments of customer environments running a total of 13,800 x86 cores, average measured peak utilization is 16%. Lower sustained x86 utilization rates require the use of more physical x86 servers and cores, associated software and datacenter costs. IBM internal tests show that when running mixed workloads consisting of both open source and IBM proprietary software, IBM z15 requires 23 times fewer cores than the compared x86 servers and delivers a 27% lower overall TCO over 5 years. IBM Z sustained utilization rates can enable IT organizations to consolidate distributed workloads from many commodity servers to just a few servers, enabling IT efficiencies and lower datacenter costs. IBM z15 performance and server design are intended to help organizations run more workloads efficiently and securely with fewer resources.

z15 has increased cost-efficiencies for IBM Z pervasive encryption by introducing on-chip compression
and encryption capabilities for CPs for z/OS workloads and IFL workloads. Compression within the chip can help not only to reduce latency but also to eliminate the need and associated expense for encryption cards. z15 Integrated Accelerator for zEnterprise Data Compression can reduce transmission costs of daily back-ups for disaster recovery13 and help reduce MIPS costs.


### So, "why" mainframe application modernization then?

Mainframes have been around for a long time now. The mostly commonly used programming language on mainframe, COBOL has been around since 1959. Most applications that are running strongly on mainframes can be older than most of the people reading this blog. 

> Fact check: COBOL stands for COmmon Business Oriented Language. It was written to easily convert business problems to code. Therefore, most early COBOL programmers were people with strong domain knowledge. Which also says why COBOL is very English-like. Ironically! After many years, we are talking about DDD!

Can you get back to the question KS? :joy:
Oh! sorry. Yes, so why modernize? As said earlier, we have applications that are written decades ago and have had many changes/additions over the years. 
Now, that is going to be a normal thing. Still, why modernize? Mainframe applications are monolithic and have complex code. 
So, what? :sleep:
Now, think of a scenario here: I have a simple part of my application where I have a UI to get customer information from an underlying database and provide all the linked accounts. Ideally, when I speak to a modern day developer, the scenario would entail a UI side of things, a simple html/css/js or a SPA using Angular/React/Vue, then a middleware, a server component for the backend where I can have the business logic, then a data layer where there would DAO to access customer and account databases. This is a typical n-tier architecture (Note: I am not talking microservices here). Now, how would it be, if I were to do most part of the n-tier architecture where I have the logic for serving the UI, access to middleware, any required business logic and accessing the database in a single module. This is what how a single-tier architecture looks like. 
In the single-tier architecture, as features are added, inter-module communications are mostly a direct communication. i.e., we don't have interfaces, jars, dlls, dependencies in package.json etc. We have interface in the form of copybooks which are used as address spaces to send and receive data between programs. Now, that is tight-coupling you would say. Yes, it is!

> Note: There are sites where mainframe applications are built/converted as 3-tier applications. But, that's not the most common pattern. There is a lot that can be discussed as to why and how of this. It requires a while blog to say why it was done the way it was done.

Mainframe z/OS typically have a lot of batch processing. Batch processing is mostly done during the non-peak processing hours to distribute the load on the system for better CPU utilization. Again, this has a lot of historic importance and older pricing models in the world of mainframes. While, most mainframers and lot more of non-mainframers speak volumes about MIPS reduction (overly abused concept), not many understand the relevance and how pricing models have evolved over the decades.  I am no expert in z/OS performance and capacity planning either. But, have spoken to a few of the experts over the last couple of decades.

As time progressed and people with the domain knowledge kept moving/retiring, these applications became harder to discover and analyze. The very nature of these applications being monolithic and single-tiered with high complexity and high criticality, has made organizations to be more risk-averse to changes. This has increased the amount of reviews and testing over the years, thereby making release cycles longer. 
Now, with the agile ways of working across the enterprises, leaders' expections from the mainframe have also increased and want shorter release cycles with better quality and efficiency. 
Here comes the whole new thought process of application modernization. We will specifically talk about ways to modernize and pitfalls in the next section.
> Note: We should be aware that, application/legacy modernization is not limited to mainframe and COBOL/PL1. 

> Fact check: I did mention z/OS more than once here. I wanted to mention that Mainframes are not limited to z/OS. z/TPF on the other hand is a high availability system typically used in airline ticketing. z/VSE is another which is mainly used for smaller mainframes. Something more like a DOS on Z. VSE stands for Virtual Storage Extended.

Excerpt from https://www.ibm.com/docs/en/zos-basic-skills?topic=systems-mainframe-operating-system-ztpf
z/TPF can use multiple mainframes in a loosely coupled environment to routinely handle tens of thousands of transactions per second, while experiencing uninterrupted availability that is measured in years. Very large terminal networks, including special-protocol networks used by portions of the reservation industry, are common.

## "How" part of the modernization journey

Firstly, there is no silver bullet for modernizing applications. Each application in an enterprise has to go through a journey based on the current state, planned future state and the cost of modernization. The emphasis should be on the word 'journey'. Any modern applications in the next decade will be a legacy. There is always a scope to improve the current state; call it modernization or just continuous improvement.

In a general philosophy of Application migration to cloud, we talk about 6R strategy: Rehost, Replatform, Retain, Retire/Remove, Replace/Repurchase and Refactor. Ideally, every application within the mainframe estate has to be looked at individually and multiple strategies may have to be applied for the modernization. 

Before we start applying the 6Rs and start talking the cloud terminologies, we have to look at the current state of the application. Doing a deep discovery along with the impacts to all the interfacing applications gives a good idea of the data model, complexity of the application, and the coupling factor. These are good inputs that will be required to make an informed decision. There are many Business Rules Extraction software that can help in the BRE. But, there have been very few which one could really benefit from. An application build over decades of code would need just more than that to help.

In most mainframe application cases, we are talking about single-tier architecture with complex business logic and multiple application coupled tightly either by P2P message transfers, file transfer or in many cases application program calls (these are not API calls. But, actual program to program call). 

Unless the strategy is to replace existing with COTS applications, we should be looking for refactoring as the first step and then trying to hollow-out the application. Note: Hollowing-out is very commonly done using what is called as the Strangler pattern. By the way, if you are in software design and architecture, you would for sure know Martin Fowler and here is his talk on strangler pattern if you would love to read more about it :smile: https://martinfowler.com/bliki/StranglerFigApplication.html

Okay! Before we get on to this, identify the technical debts in your application. Spend time working out what would cause more technical debt and eliminate those processes. Communicate it to the wider team and ensure that the team is working together in resolving the existing tech debts. There is a belief that project takes away life and we cannot go on clearing the technical debt. Common KS, talk some sense. Okay - I used to think so too. But, have a quick look at this one from Martin Fowler as well if you please https://martinfowler.com/bliki/TechnicalDebt.html 

### Replace/Repurchase

Oh! This sounds like the easiest option. Right? Actually, if it was so easy, you would have seen every vendor line up in front of companies fighting it out with their SaaS project. But, what could be the problem. I know you already know the answer :smile: Customization! Customization! Customization! Almost any business in the automotive section, financial sector, airlines, Healthcare have what they call it as their differentiator. We are just not like others, you see! We provide xx better than them, although they may provide yy services better than us. 

So, whatever COTS product one buys, it has to be customized for the enterprise. Although, this is much simpler than building an application bottom-up, it takes quite some time depending on the size and complexity of the customization in the application in question. We should also consider the in-flight changes i.e., ongoing projects and maintenance during the migration, data migration and ETL requirements, operations and maintenance of the new application, operational user training to name a few things. 

Ideally, we would use smaller COTS applications for specific functionalities of application and migrate them making it easier to maintain. This of course will lead to a lot more applications in the portfolio. But, loose coupling would make it easier to build new features.

### Refactoring 

Disclaimer: I am considering in-place modernization as part of Refactoring as I am not specifically talking about 6Rs of application migration to cloud. Many may disagree. I definitely welcome all comments and thoughts and love to have the discussion/debate and learn in the process. Also, for me, Retain of 6Rs will need some bit of Refactoring for better throughput and time-to-market. Therefore, will not talk about retain separately.

A good way to refactor an application is to start looking for number of inter-application calls, bulky code, code with high degree of cyclomatic & heuristic complexity, low-performing or expensive code/database calls. Work on things which are more of low-hanging fruits i.e., pick the ones that can be easily transformed within a set timeframe. 

Optimization strategies like usage of latest compilers, identification of low-performing or high CPU consuming code/queries and refactoring them helps in a lot of cost reduction. Strategy to spread out the batch workload as the real-time workload on mainframes are constantly increasing and slowly reaching 24/7 mode helps is better utilization of procesing power of the Big-Iron. Also, where there are opportunities, convert some of the batch workloads to real-time thereby aiding for 24/7 availability. These are common strategies that are applied in most Mainframe sites. However, the direction has been swayed in many sites as leaders and engineers were looking for cloud as the primary source of modernization - A strategy that needs much clarity in thought with a good exercise on Cost/Benefit analysis.

Mainframe COBOL/PL1 programs typically run into hundreds or more commonly, a few thousand lines. As much as I love to talk about the why bit of it, the primary purpose of this blog is not that. As discussed earlier, this is mostly because, we look at single-tiers in most of the applications. A screen functionality (read it as UI if you are not comfortable with 3270 terminology) is more often than not is completely handled by a single module or a set of simple modules where there is no clear segregation of concerns. 
These are good candidates for refactoring. At every opportunity, when these code can be looked at and refactored, we have simple segregated code.
Oh KS! you seem to be in a dreamland, how do you expect me to segregate code that has been running fine for 40 years and has 8000 lines? Apologies! I didn't mean that you have change every bit of code. But, wherever possible, we can do that. We can always change the database calls in a code to a single Data Access layer. We can simplify bulky code with 100s of lines of business logic into multiple smaller modules if we do it right. Very similar to the Strangler pattern. But, applied to code instead of application.
Ah! won't there be a performance impact? Slight unnoticable change for sure. But, the advantages overweigh. 

Reduce inter-application and inter-module calls. Covert them to some sort of interfaces i.e., APIs where possible. 

Some hate it some love it when I say APIs! 
A simple question! If I ask you to check your bank accounts, statements etc using a unique userid and password on a 3270 screen, how comfortable would you be? Even better, let us say you can use your payment wallets with an app on your mobile which will be an emulator to 3270 screen. Not good. Right? Then, why do we expect business users, operators, new-age developers to use 3270 screens? All I am trying to say is expose the functionalities required by business users so that these can be used by enterprise middleware and web/thick-client front-end to make better UI. The point here is not to have REST APIs alone. You can use CWS (CICS Web Support), CTG, IMS SOAP Gateway, Cics Web Services, IBM Websphere MQ or any other means. Ofcourse, REST APIs exposed via z/OS Connect or OpenLegacy has its own advantage with respect to ease of use and speed of delivery.
IBM and most ISVs these days provide a gamut of mainframe operation functionalities via REST APIs. RSE APIs and z/OSMF APIs are commonly used by open source projects like Zowe https://openmainframeproject.org/projects/zowe. z/OSMF comes with a web interface and a gamut of APIs for use by mainframe operators and developers alike. CA SYSVIEW provides APIs for DB2 management. BMC CRA (Common REST API) provides a great set of APIs for system maintenance. These are just a few to name.


Now, for those cloud enthusiasts! Refactoring also enables us to easily and safely port bit by bit into distributed application stack if that is what we intend to. This way the core is hollowed-out and simplified in a cloud-native environment. One can use DDD and strangler pattern to dish out microservices if that is intended to be done.


### Rehosting

A strategy that is least preferred from my perspective. But, there are customers and sites with a smaller footprint on mainframe who would still prefer this. 
Azure cloud provides a lot of options for rehosting the mainframe. Seriously??? Yes, seriously! Micro Focus alongside Azure provides a Micro Focus Enterprise Server on Azure. This can not only move your batch-worloads. But, your entire mainframe workload with some changes to Azure. From a Development cycle standpoint, the benefits are very little to go with the strategy. 
There are other options where IBM zD&T can be used and be placed in Azure or AWS. There is also TmaxSoft OpenFrame for rehosting of mainframes. You can get a good deal of information on microsoft docs https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/mainframe-rehosting/overview


### Replatform

Replatforming is mainly about converting a mainframe based tech-stack to another distributed tech-stack either via automated conversion and refactoring or by refactoring existing stack to cloud-native and moving it to distributed platforms. 
There are a lot of software vendors providing replatforming solutions from COBOL/PL1 to Java/C# etc. Any automated conversion can only do so much. Remember, we are converting procedural language code to Object-Oriented code. The patterns will be affected on automated conversion. In most cases, automated conversion may not be sufficient and will require further manual refactoring.
Smaller/peripheral applications or applications which have are refactored to a acceptable extent are much suitable for replatforming. 

Some vendor softwares provided below:
1. Heirloom computing helps automated replatform to Java stack - https://www.heirloomcomputing.com/
2. Raincode helps automated replatform to .Net stack - https://www.raincode.com/
3. Other vendors like Modern systems (Now, OneAdvanced) provide solutions on rehosting and replatforming - https://modernsystems.com/legacy-modernization-services-2/mainframe-rehosting/

## Next Steps

Identify your pain points with your Mainframe. Work on those pain points. Mainframes are still used by more than 90% of Fortune 500 companies for a reason. There is a lot of possibilities within the Big Iron. All it needs, is a bit of pragmatic thinking and some exploring.

Things that need to be looked at next in our future blogs:
1. DevOps on Mainframe - A pragmatic approach
2. Measuring, Monitoring and Analytics 
3. z/OSMF and RSE APIs - Usage and Benefits

