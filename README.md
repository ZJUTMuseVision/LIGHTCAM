# LIGHTCAM
 A FAST AND LIGHT IMPLEMENTATION OF CONTEXT-AWARE MASKING  BASED D-TDNN FOR SPEAKER VERIFICATION
# Result  
  * Setup:F-bank80,num_frms300,epoch150, CrossEntropyLoss, aug_prob0.2, shuffle(2500)，MarginScheduler
  * Scoring: cosine similarity scoring
  * Metric: EER(%),MinDCF
Performance comparison of different network structures on VoxCeleb1 dataset   
  
Architecture  |Params(M)  |VoxCeleb1-O EER(%)/MinDCF  |VoxCeleb1-E EER(%)/MinDCF  |VoxCeleb1-H EER(%)/MinDCF  
 ---- | ----- | ------ | ------- | --------  
ECAPA-TDNN  |14.65  |0.86/0.0921  |1.07/0.1185  |2.06/0.1956  
ResNet34  |6.63  |0.86/0.0912  |1.05/0.1214  |1.96/0.1921  
CAM++  |7.18  |0.88/0.0935  |0.97/0.1183  |1.89/0.1971  
**LightCAM**  |  8.15  |**0.83/0.0891**  |**0.95/0.1114**  |**1.86/0.1922**  

Complexity comparison of the model  

Model  |Params(M)  |FLOPs(G)  |RTF  
 ---- | ----- | ------ | -------  
ECAPA-TDNN  |14.65  |3.96  |0.042  
ResNet34  |6.63  |6.84  |0.057  
CAM++  |7.18  |1.73  |0.026  
**LightCAM**  |  8.15  |**1.37**  |**0.017**  
  
Ablation study of LightCAM modules. With DSM and MFA applied on CAM++, we get LightCAM  

Method  |Params(M)  |FLOPs(G)  |VoxCeleb1-O EER(%)/MinDCF  |VoxCeleb1-E EER(%)/MinDCF  |VoxCeleb1-H EER(%)/MinDCF  
 ---- | ----- | ------ | ------- | -------- | ---------  
CAM++  |7.18  |1.73  |0.88/0.0935  |0.97/0.1183  |1.89/0.1971  
+DSM  |7.36  |1.36  |0.83/0.1091  |1.01/0.1184  |1.94/0.2044  
++MFA  |8.15  |1.37  |0.83/0.0891  |0.95/0.1114  |1.86/0.1922  
