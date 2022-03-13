# Text-Classification-Toxic-Comments
Kaggle比赛链接：https://www.kaggle.com/c/jigsaw-toxic-severity-rating.

比赛介绍:.
本次竞赛中，一对评论被提交给专家评分员，他们在两条评论中标出一 个更有害的评论。而参赛者将对一组大约14000条评论进行 评分。 当参赛者为评论提供分数时，它们将与几十万个（专家给出的）排名进行比较。你与专家的平均一致意见将决定你的 个人得分。.

竞赛类型：本次竞赛属于深度学习/自然语言处理，所以推荐使用的模型或者库：Bert/Roberta/TF-IDF.
赛题数据：本次比赛官方没有提供训练集，参赛者可以用往届比赛的文本数据。虽然不包括训练数据，但提供了一组大约14000条评论的成对的毒性排名。.
评估标准：对于ground truth测试数据中的大约20万对评级，主办方使用选手预测的毒性分数对评论对进行排名。如果这个 排名与注释者的排名相符，则该对评论获得1分，如果不相符则获得0分。最后的分数是所有评论的平均值。 详见：Jigsaw Rate Severity of Toxic Comments | Kaggle.
推荐阅读 Kaggle 内的一篇 EDA（探索数据分析）来获取一些预备知识：[Pytorch + W&B] Jigsaw Starter | Kaggle.
