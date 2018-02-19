# Parametric RBAC Maintenance via Max-SAT

This web site contains the dataset and experimental results partially illustrated within the manuscript "Paramtric RBAC Maintenance via Max-SAT" which is currently under review to SACMAT Conference 2018. 

# Datasets

## SmallComp

Dataset generated by simplyfing the paper working example to obtain optimal solution with a wide range of B values thus enabling the comparison with sub-otpimal solvers


|Input| Link|  	   
|:-:	           |:---:	|
|Permission-to-User | [UPA](dataset/SC/UPA.txt)|
|User-to-role      |[UA](dataset/SC/UA.txt)  |
|Permission-to-Role | [PA](dataset/SC/PA.txt) |
|Exception List           | [excs](dataset/SC/excs.txt)| 


## Domino

Dataset benchmark used in Role-mining literature obtained from the user access profiles of the Lotus Domino Server.


|Input| Link|  	   
|:-:	           |:---:	|
|Permission-to-User | [UPA](dataset/D/UPA.txt)|
|User-to-role      |[UA](dataset/D/UA.txt)  |
|Permission-to-Role | [PA](dataset/D/PA.txt) |
|Exception List           | [excs](dataset/D/excs.txt)| 


## University

Dataset benchmark used in Role-ming literature generated from a template at the Stony Brook University.


|Input| Link|  	   
|:-:	           |:---:	|
|Permission-to-User | [UPA](dataset/U/UPA.txt)|
|User-to-role      |[UA](dataset/U/UA.txt)  |
|Permission-to-Role | [PA](dataset/U/PA.txt) |
|Exception List           | [excs](dataset/U/excs.txt)| 


## Firewall1

Dataset benchmark used in Role-ming literature representing policies implemented though firewalls used to provide external users access to internal resources. 


|Input| Link|  	   
|:-:	           |:---:	|
|Permission-to-User | [UPA](dataset/F/UPA.txt)|
|User-to-role      |[UA](dataset/F/UA.txt)  |
|Permission-to-Role | [PA](dataset/F/PA.txt) |
|Exception List           | [excs](dataset/F/excs.txt)| 





# Selection of a Max-SAT solver

## Complete Solvers

|Solver  	       |SmallComp  |Domino   	 |University   	|Firewall1   	|   	
|:-:	           |:---:	|:---:	|:---:	|:---:	|	
|_Maximo_   	   |[B<=0.5](complete/SC/maximo/Results.txt)   	   |[B=0](complete/D/maximo/Results.txt)    	  |[B=0](complete/U/maximo/Results.txt)   	| [B=0](complete/F/maximo/Results.txt)   	|   	
|_MaxHS_   	     |[B<=0.4](complete/SC/maxHS/Results.txt)     	   |[B=0](complete/D/maxHS/Results.txt)   	      |[B=0](complete/U/maxHS/Results.txt)    	|  -  	|   	
|_LMHS_ |[B<=0.3](complete/SC/lmhs/Results.txt) | [B=0](complete/D/lmhs/Results.txt)   |  [B=0](complete/D/lmhs/Results.txt)  	|  - 	|   
|_Ahmaxsat_   	 |[B<=0.25](complete/SC/ahmaxsat/Results.txt)   	 |- | -  	|  - 	|   	







## Incomplete Solvers

### Time complexity based on Firewall1 variant

90 online fixing instances of increasing size have been generated from _Firewall1_ by selecting more and more of its users (i.e., rows); each instance is associated with a single exception to incorporate and generates a Max-SAT encoding of growing size. 


|Number of users (CNF formula size)|UA|PA|exc|
|:---:|:---:|:---:|:---:|
|5 users (0.3 MB)|[UA](dataset/complexity/89/UA.txt)|[PA](dataset/complexity/89/PA.txt)|[exc](dataset/complexity/89/excs.txt)|
|21 users (5.1 MB)|[UA](dataset/complexity/85/UA.txt)|[PA](dataset/complexity/85/PA.txt)|[exc](dataset/complexity/85/excs.txt)|
|37 users (11.3 MB)|[UA](dataset/complexity/81/UA.txt)|[PA](dataset/complexity/81/PA.txt)|[exc](dataset/complexity/81/excs.txt)|
|53 users (27.5 MB)|[UA](dataset/complexity/77/UA.txt)|[PA](dataset/complexity/77/PA.txt)|[exc](dataset/complexity/77/excs.txt)|
|69 users (54.9 MB)|[UA](dataset/complexity/73/UA.txt)|[PA](dataset/complexity/73/PA.txt)|[exc](dataset/complexity/73/excs.txt)|
|85 users (79.6 MB)|[UA](dataset/complexity/69/UA.txt)|[PA](dataset/complexity/69/PA.txt)|[exc](dataset/complexity/69/excs.txt)|
|101 users (120.1 MB)|[UA](dataset/complexity/65/UA.txt)|[PA](dataset/complexity/65/PA.txt)|[exc](dataset/complexity/65/excs.txt)|
|117 users (162.4 MB)|[UA](dataset/complexity/61/UA.txt)|[PA](dataset/complexity/61/PA.txt)|[exc](dataset/complexity/61/excs.txt)|
|133 users (231.7 MB)|[UA](dataset/complexity/57/UA.txt)|[PA](dataset/complexity/57/PA.txt)|[exc](dataset/complexity/57/excs.txt)|
|149 users (300.9 MB)|[UA](dataset/complexity/53/UA.txt)|[PA](dataset/complexity/53/PA.txt)|[exc](dataset/complexity/53/excs.txt)|
|165 users (337.2 MB)|[UA](dataset/complexity/49/UA.txt)|[PA](dataset/complexity/49/PA.txt)|[exc](dataset/complexity/49/excs.txt)|
|181 users (380.7 MB)|[UA](dataset/complexity/45/UA.txt)|[PA](dataset/complexity/45/PA.txt)|[exc](dataset/complexity/45/excs.txt)|
|197 users (519.1 MB)|[UA](dataset/complexity/41/UA.txt)|[PA](dataset/complexity/41/PA.txt)|[exc](dataset/complexity/41/excs.txt)|


The following figure shows the minimum timeout needed (y axis) to obtain a feasible solution for these inputs as a function of their size (x axis) with [B=0.8](complexity/Results.txt).
![H_ResponseTime](imgMaintenance/H_responseTime.png)




### Quality of incomplete solutions

Experiment based on _SmallComp_ dataset to measure the ability of the incomplete solver adopted to satisfy the soft constraints. In particular, this is computed as the average weight of satisfied soft constraints over the total sum of weights for the 12 exceptions. 

Average percentage of satisfied soft clauses (y axis) as a function of the balance B (x_axis) in the _SmallComp_ dataset:
![rateSoft](imgMaintenance/rateSoft.png)


Results are also available in plain text in [rate.txt](qualityIncompleteMaintenance/rate.txt) which are based on the evalaution of the three configurations:
- complete solver [Results.txt](qualityIncompleteMaintenance/Results.txt)
- incomplete solver (timeout 2 sec) [Results.txt](qualityIncompleteMaintenance/2/Results.txt)
- incomplete solver (timeout 180 sec) [Results.txt](qualityIncompleteMaintenance//180/Results.txt)


# Experimental Results 

## Impact of Beta

By adopting CCEHC Max-SAT solver we asses experimentally the impact of balance B to **sim** (similarity) and **opt** (simplicity) for three dataset.

- [SmallComp](preferencesImpact/optsim/SmallCompSimplicity180.dat) 
- [Domino](preferencesImpact/optsim/DominoSimplicity180.dat)
- [University](preferencesImpact/optsim/UniversitySimplicity360.dat)

Average similarity and simplicity (y axis) as a function of the balance B (x axis) with 21 values of B sampled at regular intervals:
![A_sim](preferencesImpact/optsim/A_Sim.png)

Average number of roles after incorporating exceptions (y axis) as a function of the balance B (x axis) for different dataset:
![A_RoleAssA_sim](preferencesImpact/optsim/A_RoleAss.png)

Average number of assignments per role (y axis) depending on the balance B (x axis):
![A_AssPerRole](preferencesImpact/AssPerRole_SatRate/A_AssPerRole.png)

Average percentage of satisfied weights (y axis) depending on the balance B (x axis):
![A_SatRate.png](preferencesImpact/AssPerRole_SatRate/A_SatRate.png)




## Impact of timeout

Results collected in the following are obtained starting from _Domino_ to show the impact of the timeout with three different balance configurations:

- [B = 0.15](timeImpact/Semplicity_w0.15_paper.dat) 
- [B = 0.4](timeImpact/Semplicity_w0.4_paper.dat) 
- [B = 0.65](timeImpact/Semplicity_w0.65_paper.dat) 
- [B = 0.9](timeImpact/Semplicity_w0.9_paper.dat) 


Average similarity in Domino (y axis) as a function of the timeout (x axis, secs) at different balance points B.
![C_timeoutSim](timeImpact/C_timeoutSim.png)

Average number of roles in Domino (y axis) as a function of the timeout (x axis, secs) at different balance points B.
![C_timeoutRole](timeImpact/C_timeoutRole.png) 

Average number of assignments in Domino (y axis) as a function of the timeout (x axis, secs) at different balance points B.
![C_timeoutAss](timeImpact/C_timeoutAss.png)







## The order of exceptions with a variant of _Domino_ dataset

We picked a string of 5 exceptions to be incorporated.

|Input| Link|  	   
|:-:	           |:---:	|
|Permission-to-User | [UPA](dataset/permutations/UPA.txt)|
|User-to-role      |[UA](dataset/permutations/UA.txt)  |
|Permission-to-Role | [PA](dataset/permutations/PA.txt) |
|Exception List           | [excs](dataset/permutations/excs.txt)| 

We generated all the  120 permutations as possibly different incorporating sequences. We fix each sequence and collected at each our metrics. 

In the following is reported the distribution of the final number of roles obtained at different B values.

![F](permutations/F.png)
