# Introduction: Integrating Cloud ERP with OIC (INTERNAL ONLY)

<!-- Comment out table of contents
## Table of Contents
[Introduction](#introduction)
-->

![](./images/intro.png " ")

## Introduction

*In addition to the workshop*, feel free to watch the walk-through companion video by clicking on the following link:
[Integration lab Walkthrough Video](<INSERT LINK HERE>)

In this lab, you will use Oracle Integration to make a connection to your Cloud ERP instance. From there, you will build a basic application integration that creates an Order. After that, you will create a Process that allows for human approval. You will create a process form that allows you to enter order information. The process allows you to define workflow approval and call an integration to create an Order within ERP.

![](./images/notionalarch.png " ")

### Objectives
- Make connection to ERP instance
- Build application integration
- Learn process basics
- Create an order
- See end-to-end history of entire process

### Required Artifacts

- Oracle Integration Cloud Instance.
- Oracle ERP Cloud Instance.
- Autonomous Data Warehouse Instance. 
- Postman

### Extra Resources
-   To learn more about Oracle Integration, feel free to explore the capabilities by clicking on this link: [OIC Documentation](https://docs.oracle.com/en/cloud/paas/integration-cloud/index.html)
-   To learn more about , Oracle ERP Cloud feel free to explore the capabilities by clicking on this link: [ERP Cloud](https://go.oracle.com/LP=85331?elqCampaignId=48423&src1=ad:pas:go:dg:erp&src2=wwmk160606p00030c0001&SC=sckw=WWMK160606P00030C0001&mkwid=%7cpmt%7ce%7cpdv%7cc%7c&GOOGLE&oracle+erp+cloud&Cj0KCQjw7qn1BRDqARIsAKMbHDaSJX4r2woRQrLHIFTCk3imWrf6ORbhp3f1czxUvvxVTsz8Votd7TQaAhggEALw_wcB&gclid=Cj0KCQjw7qn1BRDqARIsAKMbHDaSJX4r2woRQrLHIFTCk3imWrf6ORbhp3f1czxUvvxVTsz8Votd7TQaAhggEALw_wcB&gclsrc=aw.ds)
