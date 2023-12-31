[](#anchor_1)

[](#anchor_2)1\. 什么是缺陷报告，缺陷报告的作用，缺陷报告的要点
----------------------------------------

1.  缺陷报告是描述软件缺陷现象和重现步骤的集合。软件缺陷报告 Software Bug Report(SBR) 或软件问题报告 software Problem Report(SPR)。
2.  缺陷报告是软件测试人员的工作成果之一，体现软件测试的价值缺陷报告可以把软件存在的缺陷准 确的描述出来，便于开发人员修正缺陷报告可以反映项目 / 产品当前的质量状态，便于项目整体进度和 质量控制软件测试缺陷报告是软件测试的输出成果之一，可以衡量测试人员的工作能力。
3.  标题 (Title) 简洁、准确、完整、反映缺陷本质、方便查询前缀 + 标题正文，标题正文采用结果和动作， 或者现象和位置的方式表达；步骤 (Steps) 可复现、完整、简洁、准确按数字编号；实际结果 (Actual results) 准确、详细描述软件的现象和特征；期望结果 (Expected results) 准确、丰富、有理有据；平台 (Platforms) 准确；截图 (Sereenshots) 准确反映缺陷特征；注释 (Notes) 关于缺陷的辅助说明

[](#anchor_3)2\. 缺陷报告的优先级别
--------------------------

*   最高优先级：立即修复，停止进一步测试
*   次高优先级：在产品发布之前必须修复
*   中等优先级：如果时间允许应该修复
*   最低优先级：可能会修复，但是也能发布

[](#anchor_4)3\. 简单概述缺陷报告
-------------------------

现在缺陷报告一般不再使用纸质档文档编写，而是专用测试管理工具（如 TestDirector、禅道），这样便于缺陷管理。在这些工具中，每个缺陷作为一条记录输入指定的缺陷管理系统中。

[](#anchor_5)4\. 缺陷报告包括哪些项？
---------------------------

缺陷报告包括：软件名称、版本号、功能模块、缺陷编号、对应的用例编号、编写时间、编写人、 测试员、预期结果、实际结果、缺陷描述、严重级别、优先级别

[](#anchor_6)5\. 软件测试缺陷报告的 5C 原则
--------------------------------

*   Correct（准确）：每个组成部分的描述准确，不会引起误解； Clear（清晰）：每个组成部分的描述清晰，易于理解；
*   Concise（简洁）：只包含必不可少的信息，不包括任何多余的内容；
*   Complete（完整）：包含复现该缺陷的完整步骤和其他本质信息；
*   Consistent（一致）：按照一致的格式书写全部缺陷报告。

[](#anchor_7)6\. 软件缺陷的生命周期？
---------------------------

测试人员提交新的 Bug 入库，错误状态为 New。

高级测试人员验证错误，如果确认是错误，分配给相应的开发人员，设置状态为 Open。

如果不是错误， 则拒绝， 设置为 Declined（拒绝）状态。

开发人员查询状态为 Open 的 Bug，如果不是错误，则置状态为 Declined；如果是 Bug 则修复并置状态为 Fixed。

不能解决的 Bug，要留下文字说明及保持 Bug 为 Open 状态。

对于不能解决和延期解决的 Bug，不能由开发人员自己决定， 一般要通过某种会议（评审会）通过才能认可。

测试人员查询状态为 Fixed 的 Bug， 然后验证 Bug 是否已解决，如解决置 Bug 的状态为 Closed，如没有解决置状态为 Reopen。

[](#anchor_8)7\. 缺陷描述（报告单）中应该包括哪些内容？
------------------------------------

缺陷的标题，简要描述。缺陷的类型。缺陷的详细步骤描述。缺陷的实际结果。期望结果。有的缺陷需要上传截图，日志信息。缺陷的等级。缺陷指派给开发同事。

[](#anchor_9)8\. 如何提高缺陷的记录质量？
-----------------------------

通用 UI 要统一、准确；尽量使用业界惯用的表达术语和表达方法；使用业界惯用的表达术语和表达方法，保证表达准确，体现专业化；每条缺陷报告只包括一个缺陷；不可重现的缺陷也要报告；明确 指明缺陷类型；明确指明缺陷严重等级和优先等级；描述 (Description) ，简洁、准确，完整，揭示缺

陷实质，记录缺陷或缺陷出现的位置；短行之间使用自动数字序号，使用相同的字体、字号、行间距；每一个步骤尽量只记录一个操作；确认步骤完整，准确，简短；根据缺陷，可选择是否进行图象捕捉；检查拼写和语法缺陷；尽量使用短语和短句，避免复杂句型句式；缺陷描述内容。

[](#anchor_10)9\. 如果一个缺陷被提交后，开发人员认为不是问题，怎么处理？
---------------------------------------------

1.  首先，将问题提交到缺陷管理库里面进行备案。
    
2.  然后，要获取判断的依据和标准：
    
    *   根据需求说明书、产品说明、设计文档等，确认实际结果是否与计划有不一致的地方，提供 缺陷是否确认的直接依据；
    *   如果没有文档依据，可以根据类似软件的一般特性来说明是否存在不一致的地方，来确认是 否是缺陷；
    *   根据用户的一般使用习惯，来确认是否是缺陷；
    *   与设计人员、开发人员和客户代表等相关人员探讨，确认是否是缺陷；
3.  合理的论述，向测试经理说明自己的判断的理由，注意客观、严谨，不掺杂个人情绪。
    
4.  等待测试经理做出最终决定，如果仍然存在争议，可以通过公司政策所提供的渠道，向上级反映， 并有上级做出决定。
    

[](#anchor_11)10\. 软件缺陷的原则
--------------------------

1.  软件缺陷区别于软件 bug, 它是在测试过程中出现的对系统有影响的，但是在设计中没有的或者对修改后的 bug 测试和开发人员有不同意见等
2.  软件未达到产品说明书标明的功能。
3.  软件出现了产品说明书指明不会出现的错误。
4.  软件功能超出产品说明书指明范围。
5.  软件未达到产品说明书虽未指出但应达到的目标。
6.  软件测试员认为软件难以理解、不易使用、运行速度缓慢，或者最终用户认为不好。

[](#anchor_12)11\. 软件缺陷的特征
--------------------------

1.  “看不到”
2.  ——软件的特殊性决定了缺陷不易看到
3.  “看到但是抓不到”
4.  ——发现了缺陷，但不易找到问题发生的原因所在

[](#anchor_13)12\. 软件缺陷产生的原因
----------------------------

1.  软件产品说明书（需求）——56%
2.  设计——27%
3.  编写代码——7%
4.  其他——10%

[](#anchor_14)13\. 什么是 Bug？
---------------------------

软件的 Bug 指的是软件中（包括程序和文档）不符合用户需求的问题。

常见的软件 Bug 分为以下三类：

1.  没有实现的功能
2.  完成了用户需求的功能，但是运行时会出现一些功能或性能上的问题
3.  实现了用户不需要的多余的功能

[](#anchor_15)14\. 缺陷处理流程
-------------------------

测试人员提交新的 Bug 入库，错误状态为 New。

高级测试人员验证错误，如果确认是错误，分配给相应的开发人员，设置状态为 Open。如果不是错误，则拒绝，设置为 Declined（拒绝）状态。

开发人员查询状态为 Open 的 Bug，如果不是错误，则置状态为 Declined； 如果是 Bug 则修复并置状态为 Fixed。

不能解决的 Bug，要留下文字说明及保持 Bug 为 Open 状态。

对于不能解决和延期解决的 Bug，不能由开发人员自己决定，一般要通过某种会议（评审会）通过才能认可。

测试人员查询状态为 Fixed 的 Bug，然后验证 Bug 是否已解决，如解决置 Bug 的状态为 Closed， 如没有解决置状态为 Reopen。

[](#anchor_16)15\. 缺陷的等级划分
--------------------------

*   严重： 系统崩溃、数据丢失、数据毁坏
*   较严重：操作性失误、错误结果、遗漏功能
*   一般：小问题、错别字、UI 布局、罕见故障
*   建议：不影响使用的瑕疵或更好的实现

[](#anchor_17)16\. 开发人员修复缺陷后，如何保证不影响其他功能？
-----------------------------------------

重新执行用例、看是否出现错误结果。并对周围的一些相关功能点追加新的测试用例。

[](#anchor_18)17\. 状态为已修改的缺陷，实际没有修改怎么办？
---------------------------------------

加强项目质量管理，提高项目执行能力。如果测试人员发现了这样的问题，首先要弄清楚是什么 原因导致这种情况，最终还是要督促开发人员，修改掉这些问题。如果是不能重现的问题或者是老版 本中遗留下来的问题不能修改的 要做好标示。

[](#anchor_19)18\. 生产软件的最终目的是为了满足客户需求，我们以客户需求作为评判软件质量的标准，认为软件缺陷（ Software Bug ）的具体含义包括哪些几个因素？
---------------------------------------------------------------------------------------------

1.  软件未达到客户需求的功能和性能；
2.  软件超出客户需求的范围；
3.  软件出现客户需求不能容忍的错误；
4.  软件的使用未能符合客户的习惯和工作环境。

[](#anchor_20)19\. 如何进行缺陷评估
---------------------------

评估软件质量的重要指标，通常评估模型假设缺陷的发现是呈泊松分布的；严格的缺陷评估要考察在 测试过程中发现缺陷的间隔时间长短。评估要估计软件当前的可靠性并预测随着测试的继续进行，软 件可靠性会怎样提高。

SQA Suite 提供四种形式进行缺陷评估：

1.  缺陷分布报告可以生成缺陷数量与缺陷属性的函数。如测试需求和状态。
2.  缺陷趋势报告可以看出缺陷增长和减少的趋势；
3.  缺陷年龄报告展示一个缺陷处于某种状态的时间长短
4.  测试结果进度报告展示测试过程在被测应用的几个版本中的执行结果以
5.  测试周期。

具体步骤

1.  回顾测试日记
2.  评估测试需求的覆盖率
3.  分析缺陷
4.  决定是否达到完成测试的标准，没有满足标准时
5.  再测试
6.  降低标准
7.  确定软件的一个满足标准的子集，看是否可以发布。
