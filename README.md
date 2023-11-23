# LIGHTCAM
 A FAST AND LIGHT IMPLEMENTATION OF CONTEXT-AWARE MASKING  BASED D-TDNN FOR SPEAKER VERIFICATION
# Result  
  * Setup:F-bank80,num_frms300,epoch150, CrossEntropyLoss, aug_prob0.2, shuffle(2500)，MarginScheduler
  * Scoring: cosine similarity scoring
  * Metric: EER(%),MinDCF  
  
  Table 1 shows the experimental results of the proposed and baseline models. For fair comparison, all baseline models involved in the experiment are retrained using the same experimental setups. By comparing with ECAPA-TDNN and Res-Net34, it can be found that the proposed LightCAM has achieved slight performance improvements in EER and MinDCF on the O, E, and H test sets of VoxCeleb1. Mean-while, LightCAM has smaller number of parameters comparing with ECAPA-TDNN. This indicates that, with the goal of model lightweighting, LightCAM retains a slight advantage over mainstream speaker verification systems in terms of performance at a small parameter cost. Compared to CAM++, LightCAM achieves a further 5.7% improvement in EER for VoxCeleb1-O at the cost of 13.5% of the parameter set, demonstrating the effectiveness of the proposed DSM and MFA methods in improving model performance.  
  
<p align="center">Table1 Performance comparison of different network structures on VoxCeleb1 dataset</p>  

<center>  
  
Architecture  |Params(M)  |VoxCeleb1-O EER(%)/MinDCF  |VoxCeleb1-E EER(%)/MinDCF  |VoxCeleb1-H EER(%)/MinDCF  
| :----: | :-----: | :------: | :-------: | :--------: |   
ECAPA-TDNN  |14.65  |0.86/0.0921  |1.07/0.1185  |2.06/0.1956  
ResNet34  |6.63  |0.86/0.0912  |1.05/0.1214  |1.96/0.1921  
CAM++  |7.18  |0.88/0.0935  |0.97/0.1183  |1.89/0.1971  
**LightCAM**  |8.15  |**0.83/0.0891**  |**0.95/0.1114**  |**1.86/0.1922**  
  
</center>    

Table 2 shows that LightCAM has 55.6% parameters and 34.6% FLOPs compared to ECAPA-TDNN. LightCAM has slightly more parameters compared to ResNet34 but significant fewer FLOPs and RTF. Moreover, LightCAM also reduces FLOPs by 20.8% and RTF by 34.6% compared to CAM++. It is worth noting that LightCAM achieves the fastest inference speed among all mainstream methods. The computational complexity of the proposed model has been greatly improved, making it more suitable for practical applications.  
  
<p align="center">Table2 Complexity comparison of the model</p>  

<div class="center">  
  
Model  |Params(M)  |FLOPs(G)  |RTF  
| :----: | :-----: | :------: | :-------: |   
ECAPA-TDNN  |14.65  |3.96  |0.042  
ResNet34  |6.63  |6.84  |0.057  
CAM++  |7.18  |1.73  |0.026  
**LightCAM**  |8.15  |**1.37**  |**0.017**  
  
</div>  
  
<p align="center">Table3 Ablation study of LightCAM modules. With DSM and MFA applied on CAM++, we get LightCAM</p>  

Method  |Params(M)  |FLOPs(G)  |VoxCeleb1-O EER(%)/MinDCF  |VoxCeleb1-E EER(%)/MinDCF  |VoxCeleb1-H EER(%)/MinDCF  
| :----: | :-----: | :------: | :-------: | :--------: | :---------: |   
CAM++  |7.18  |1.73  |0.88/0.0935  |0.97/0.1183  |1.89/0.1971  
+DSM  |7.36  |1.36  |0.83/0.1091  |1.01/0.1184  |1.94/0.2044  
++MFA  |8.15  |1.37  |0.83/0.0891  |0.95/0.1114  |1.86/0.1922  
