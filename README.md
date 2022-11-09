# Efficient adversarial training

### Problem Statement

Adversarial attacks have posed serious security concerns for DNN applications in critical sectors. At the same time, adversarial training (AT) is the most effective method to defend against adversarial attacks empirically. Additionally, the adversarially trained robust models show better transferability to downstream tasks [1], improve generalizations on clean samples [2], and align with human perceptions [3]. These intriguing properties of the robust model motivate studies in AT. However, AT is also known to be time-consuming. In each optimization step, the model needs to generate an adversarial example by performing several forward and backward passes. This becomes a major bottleneck. However, although there are attempts to accelerate the AT [4, 5], efficient AT on large-scale datasets still needs to be solved. 

### Project Goals  

- **Efficient adversarial training at scale:** An important aspect of efficient AT is to generate adversarial examples using the fewest steps. The gradient information or trajectory from the original inputs could also be leveraged to train the model [4, 5]. Recent advances in VisionTransformer (ViT) exhibit that it can improve the robustness of the architecture itself. However, training ViT itself is time-consuming. In this project, we encourage you to develop an efficient AT method that can scale on ImageNet using ViT. 

- **Adversarial robust pre-training:** Recent advances in self-supervised learning (SSL) have drawn a lot of attention [6, 7]. The significant advantage of SSL is that it does not require human supervision. This makes it suitable for large-scale pre-training, and the ultimate goal is for the learner to understand visual images or natural languages. The evaluation is the performance of fine-tuning downstream tasks. Pretrained models have demonstrated it's the capability to outperform the model only trained on the downstream task significantly. However, current pre-training methods do not consider adversarial robustness. When fine-tuning a pre-trained model with adversarial training, there is no difference with training on a randomly initialized model. This indicates that the features learned by self-supervised learners are not adversarially robust. The robust and non-robust features have been extensively studied in the adversarial robustness field [3], and the adversarially trained model learns robust features that align with human perception [3], robust feature transfer better [2, 8] that could improve the learner's capability when fine-tuning on downstream task. These benefits and advantages encourage exploring an SSL strategy that is able to learn robust features. Masked Image Modeling (MIM) is one of the popular SSL strategies. It masks out parts of the image, and the model learns to reconstruct the image. The current approach [7] uses black pixels to replace the masked part of the image. Although this demonstrated it is quite effective, this pre-trained model does not help adversarial training on downstream tasks. It could suggest that features learned by MIM are not robust features. MIM may encourage the model to use features that help reconstruct the image, e.g., pixels surrounding the masked-out regions are more important than other parts of the image. One possible way to improve MIM is by adding perturbations on either the masked or unmasked regions. This will create challenges during training that encourage the model to learn semantically meaningful features rather than spurious features that only help to reconstruct the image. 
In this project, we encourage you to develop pre-training methods that can learn the robust features in the pre-training phase. The model should be able to efficiently finetuned on downstream tasks using standard training or adversarial training with few epochs while maintaining the properties associated with robust features. 

`Note：` Consider the challenge of the task above. You can choose one of the topics or other closely related topics in which you are interested.

`Code:` You may follow the following as an example
  - [RobustWRN](https://github.com/HanxunH/RobustWRN)
  - [Masked Autoencoder [7]](https://github.com/facebookresearch/mae)
  - [RobustBench](https://github.com/RobustBench/robustbench)
  - [Fast AT [4]](https://github.com/locuslab/fast_adversarial)
  - [Free AT [5]](https://github.com/mahyarnajibi/FreeAdversarialTraining)

### Reference 

[1] Salman, H., Ilyas, A., Engstrom, L., Kapoor, A., & Madry, A. Do adversarially robust imagenet models transfer better?. NeurIPS 2022\
[2]  Xie, Cihang, and Alan Yuille. "Intriguing Properties of Adversarial Training at Scale." ICLR 2020\
[3] Tsipras, D., Santurkar, S., Engstrom, L., Turner, A., & Madry, A.  Robustness May Be at Odds with Accuracy. ICLR 2019.\
[4] Wong, E., Rice, L., & Kolter, J. Z. Fast is better than free: Revisiting adversarial training. ICLR 2020.\
[5] Shafahi, A., Najibi, M., Ghiasi, M. A., Xu, Z., Dickerson, J., Studer, C., ... & Goldstein, T. Adversarial training for free!. NeurIPS 2019.\
[6] Ting Chen, Simon Kornblith, Mohammad Norouzi, and Geoffrey Hinton. A simple framework for contrastive learning of visual representations. In ICML, 2020.\
[7] Kaiming He, Xinlei Chen, Saining Xie, Yanghao Li, Piotr Dollár, and Ross Girshick. Masked autoencoders are scalable vision learners. In CVPR, 2022.\
[8] Wu, Zuxuan, et al. "That: Two head adversarial training for improving robustness at scale." arXiv preprint arXiv:2103.13612 (2021).
