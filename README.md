# Kaggle:Jigsaw Rate Severity of Toxic Comments

## 比赛介绍:

本次竞赛中，一对评论被提交给专家评分员，他们在两条评论中标出一 个更有害的评论。而参赛者将对一组大约14000条评论进行 评分。 当参赛者为评论提供分数时，它们将与几十万个（专家给出的）排名进行比较。你与专家的平均一致意见将决定你的 个人得分。

竞赛类型：本次竞赛属于深度学习/自然语言处理，所以推荐使用的模型或者库：Bert/Roberta/TF-IDF<br>
赛题数据：本次比赛官方没有提供训练集，参赛者可以用往届比赛的文本数据。虽然不包括训练数据，但提供了一组大约14000条评论的成对的毒性排名。<br>
评估标准：对于ground truth测试数据中的大约20万对评级，主办方使用选手预测的毒性分数对评论对进行排名。如果这个 排名与注释者的排名相符，则该对评论获得1分，如果不相符则获得0分。最后的分数是所有评论的平均值。<br>

## 数据说明：

本次比赛官方没有提供训练集，参赛者可以用往届比赛的文本数据。虽然不包括训练数据，但提供了一组大约14000条评论的成对的毒性排名。<br>

官方数据页面：https://www.kaggle.com/c/jigsaw-toxic-severity-rating/data<br>

comments_to_score.csv：<br>
对于这个文件中的每个评论文本，你的任务是预测一个分数，代表该评论的相对毒性严重程度。与毒性程度较低的评论相比，毒性程度较高的评论应该得到较高的数 值；分数是相对的，不受限于某个数值范围。注意：这个文件有~14000条评论，将由你提交的 模型来评分。

sample_submission.csv:<br>
一个正确格式的提交样本文件

validation_data.csv:<br>
可用于验证模型的配对排名；该数据包括注释者的工作者ID，以及该注释者对给定的一对注释的排名；注意，该数据包含comments_to_score中所没有的注释。<br>

## 解决方案思路
本次竞赛我们的方案采用了Bert + Roberta的形式，由于不清楚往届的训练数据和本次比赛的验证数据是否存在分布偏差的问题，我们只考虑了在验证数据上建立Bert和Roberta模型。<br>
在文本数据的处理上，我们将max_len设置在了64。并且只截取每个句子正中间的部分。之后我们对数据做了5Fold的标准切分。<br>
模型上我们选择了Bert和Roberta的base版本，在之后接了一个Dropout层和Linear层。<br>

## Введение в конкурс：
В этом конкурсе пара отзывов отправляется экспертам-оценщикам, которые выигрывают торги за более вредную рецензию из двух обзоров. Конкурсанты, с другой стороны, оценят набор из примерно 14 000 отзывов. Когда участники предоставляют оценки для отзывов, они сравниваются с сотнями тысяч рейтингов (предоставленных экспертами). Ваше среднее соглашение с экспертами определит ваш личный балл.

Тип конкурса: Этот конкурс относится к глубокому обучению / обработке естественного языка, поэтому рекомендуемая модель или библиотека: Bert / Roberta / TF-IDF<br>
Данные соревнований: для этого соревнования нет официального набора тренировочных данных, и участники могут использовать текстовые данные предыдущих соревнований. Хотя данные о тренировках не включены, приводится рейтинг парной токсичности около 14 000 комментариев.<br>
Критерии оценки: примерно для 200 000 пар оценок в данных теста достоверности на местах организатор ранжирует пары отзывов, используя прогнозируемые участниками оценки токсичности. Если этот рейтинг совпадает с рейтингом аннотатора, пара отзывов получает 1 балл, а если нет - 0 баллов. Окончательная оценка - это среднее значение всех отзывов.<br>


## Описание данных:

Для этого соревнования нет официального набора тренировочных данных, и участники могут использовать текстовые данные предыдущих соревнований. Хотя данные о тренировках не включены, приводится рейтинг парной токсичности примерно 14 000 комментариев. < br >

Официальная страница данных: https://www.kaggle.com/c/jigsaw-toxic-severity-rating/data < br >

comments_to_score.csv: < br >
Для каждого текста обзора в этом файле ваша задача - предсказать оценку, отражающую относительную токсичность этого обзора. Отзывы с более высокой токсичностью должны получать более высокие значения, чем обзоры с более низкой токсичностью; оценки относительны и не ограничиваются определенным диапазоном значений. Примечание. Этот файл содержит ~ 14 000 комментариев, которые будут оцениваться по модели, которую вы отправляете.

sample_submission.csv: < br >
Правильно отформатированный пример файла для отправки

validation_data.csv: < br >
Сопряжение рейтингов, которые можно использовать для проверки модели; эти данные включают идентификатор работника аннотатора и рейтинг аннотатора для данной пары аннотаций; обратите внимание, что эти данные содержит аннотации, которых нет в комментариях _ to _ score. < br >

## Идеи решения
Наша схема в этом конкурсе принимает форму Берт + Роберта. Поскольку неясно, существует ли смещение в распределении между данными предыдущих тренировок и данными проверки этого соревнования, мы рассматриваем только установление моделей Берта и Роберты на проверочные данные. < br >
Для обработки текстовых данных мы устанавливаем max _ len в 64. И усекается только средняя часть каждого предложения. Затем делаем 5Fold стандартную сегментацию данных. < br >
Для модели мы выбрали базовую версию Bert и Roberta, затем слой Dropout и линейный слой. < br >

