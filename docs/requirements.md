# IBM Application Navigator requirements

IBM Application Navigator installs on top of Red Hat OpenShift as part of the IBM Cloud Pak for Applications.
For full details on the system requirements for Cloud Pak for Applications, see [Preparing for installation](https://www.ibm.com/support/knowledgecenter/SSCSJL_4.1.x/install-prerequisites.html).

Application Navigator requires the following minimum scheduling capacity.
As the number of applications increase in the environment, additional resources are required.

| Applications | CPU (cores) | Memory (GB) | Disk (GB) |
|---|---|---|---|
| 0 -2500 | 1 | 1 | 3 |
| 2501 - 5000 | 2 | 2 | 3 |
| 5001 - 7500 | 3 | 3 | 3 |
| 7501 - 10000 | 4 | 4 | 3 |

The scaling formula is 1 CPU per 2500 applications, 1 GB memory per 2500 applications, and 3 GB storage.

#### Background

The system requirement numbers were determined by running a full system load in the IBM development lab.
The test scenario covered 10,000 applications, with approximately 60,000 application components.
The test workload added and deleted applications non-stop for 7 days, which resulted in approximately
3 GB memory usage, and a CPU utilization of 35% across two 4-CPU worker nodes.
