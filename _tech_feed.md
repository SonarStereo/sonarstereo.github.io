
# Техноблог

## AutoML

Неплохая вводная статья по AutML. В конце - направления развития этого направления
[Как AutoML помогает создавать модели композитного ИИ — говорим о структурном обучении и фреймворке FEDOT](https://habr.com/ru/companies/spbifmo/articles/558450/)



## Техноблоги

Camera basics (блог компании Opto Engineering)
https://www.opto-e.com/en/basics/camera-basics

Блог Железный пепелац 
https://lead-pepelats.ru/blog/calculate-obscura-for-solarography

Блог компании Lucid Vision Labs
https://thinklucid.com/tech-briefs/understanding-digital-image-sensors

Блог компании Dewesoft
https://dewesoft.com/blog/how-aerospace-telemetry-works

Блог ThinkAutonomous
https://www.thinkautonomous.ai/blog/ransac-algorithm/


## Алгоритм ICP

Salient Preprocessing: Robotic ICP Pose Estimation Based on SIFT Features
https://www.mdpi.com/2075-1702/11/2/157

обзорные слайды
Iterative Closest Point: Point Cloud Alignment 
https://www.ipb.uni-bonn.de/html/teaching/msr2-2020/sse2-03-icp.pdf

ICP Algorithm: Theory, Practice And Its SLAM-oriented Taxonomy
https://arxiv.org/pdf/2206.06435

LIDAR Odometry with ICP
http://andrewjkramer.net/blog/


## Обзор по трёхмерному зрению (2022) 
[Трехмерное распознавание:текущее состояние и тенденции](https://sciencejournals.ru/issues/auttel/2022/vol_2022/iss_4/AutTel_2204002Orlova/AutTel_2204002Orlova-site.html)

свойства, присущие облакам точек: 
* нерегулярность - неравномерное распределение плотностей точек в объеме облака); 
* неструктурированность - отсутствие какой-либо сетки, на которой лежат точки;
* неупорядоченность - точки хранятся в каком-либо списке, и порядок их распо-ложения в этом списке не имеет значения.

глубокое обучение на облаках точек:
* на решётке
  * воксельные (разрешение обычно низкое, проблема разреженности)
  * многоракурсные (multiview)
  * высокоразмерные решётки
* сырые облака точек
  * PointNet
  * без локальных корреляций
  * с локальными корреляциями (среди них - графовые)


## RANSAC и варианты

[RANSAC for Robotic Applications: A Survey (картинка с эпиполярной геометрией)]
https://www.mdpi.com/1424-8220/23/1/327

[Efficient Ransac]https://www.hinkali.com/Education/PointCloud.pdf

[MLESAC: A new robust estimator with application
 to estimating image geometry](https://www.robots.ox.ac.uk/~vgg/publications/2000/Torr00/torr00.pdf)

[RANSAC Traditional Approaches](https://cmp.felk.cvut.cz/cvpr2020-ransac-tutorial/presentations/RANSAC-CVPR20-Chum.pdf) 

[Random Sample Consensus Explained](https://www.baeldung.com/cs/ransac)



## Животные и восприятие окружающего

4 необычных органа чувств в природе, которых нет у человека

https://dzen.ru/a/Zydjl7KvZDxs99jw

## Курс по проективной геометрии и SLAM

[Vorlesung Computer Vision](https://www.ismll.uni-hildesheim.de/lehre/cv-17s/script/)

  	01. Projective Geometry	
   	02. Projective Geometry in 3D		
   	03. Estimating 2D Transformations	
   	04. Interest Points	
   	05. Simultaneous Localization and Mapping 
    
## Прямая и обратная кинематика

📅 30.08.2025

🛰️ Термины:
* The **forward kinematics** (FK) problem uses the kinematic equations to determine the pose given
the joint angles and bones lengths.
* The **inverse kinematics** (IK) problem computes the joint angles for a desired pose
of the articulated body. 

📚 Статья про кинематику плюс ICP:
[ICPIK: Inverse Kinematics based Articulated-ICP](https://openaccess.thecvf.com/content_cvpr_workshops_2015/W15/papers/Fleishman_ICPIK_Inverse_Kinematics_2015_CVPR_paper.pdf)

In this paper we address the problem of matching a kinematic model of an articulated (составной) body to a point cloud ob
tained from a consumer grade 3D sensor. Используют **ICP**. 

📚 Для начала хорошо почитать вот это
[Инверсная кинематика в двухмерном пространстве](https://habr.com/ru/articles/358798/)

##  Arjan Westerdiep о вокселях

📅 30.08.2025

🛰️ Воксели для отрисовки многоугольников и рендеринга, а также ЛЕГО 😃
[читать здесь](https://www.drububu.com/tutorial/voxels.html)

У Арджана на сайте много всего интересного, например, 
[Real-time 3D on an ATmega328](https://drububu.com/miscellaneous/tiny_devices/index.html)

## Лазерные сканеры для сварки

📅 30.08.2025

🛰️ На сварочной горелке монтируется интеллектуальный лазерный сенсор,  который отслеживает 
положение сварных соединений и помогает сохранить правильное положение электрода относительно шва.
Пример такого сварочного сканера - по 
[ссылке](https://www.robowizard.ru/products/datchiki/datchiki-dlya-svarki/meta-laser-vision-system)

## VA imaging: словарь терминов по машинному зрению

📅 29.08.2025

🛰️ Много полезной информации

https://va-imaging.com/pages/wiki-machine-vision

## ИИ инструменты: n8n, Ollama

📅 29.08.2025

🛰️ Эти инструменты увязываются с помощью REST API 

n8n: flexible AI workflow automation
[https://n8n.io/](https://n8n.io/)

ollama: chat & build with open models
[https://ollama.com/](https://ollama.com/)

## Роботы и квантовые вычисления

📅 29.08.2025

🛰️ Когда робот двигается, его система должна просчитать, как именно изгибать каждый сустав, чтобы конечность оказалась в нужной точке. Эта задача невероятно сложна для человекоподобных роботов с большим количеством суставов. Традиционные компьютеры тратят на это массу времени, перебирая варианты методом проб и ошибок.

Японские ученые предложили радикально новый подход: использовать кубиты для представления положения частей робота и квантовую запутанность, которая моделирует взаимное влияние суставов друг на друга. При этом расчет прямой кинематики выполняется квантовыми схемами, а обратной — классическими компьютерами. Такой гибридный метод объединяет скорость квантовых вычислений со стабильностью традиционных систем.

На практике это позволило добиться впечатляющих результатов. На квантовом симуляторе Fujitsu и 64-кубитном квантовом компьютере, созданном в сотрудничестве с RIKEN, ученые показали, что расчет движений человекоподобного робота с 17 суставами стал не только быстрее, но и гораздо точнее. Если раньше подобные вычисления занимали около получаса и требовали упрощения модели, теперь робот может двигаться более реалистично и плавно.

💡 *т.е внешний вычислитель можно привлечь для расчёта движения робота-гуманоида*
# Ссылки
