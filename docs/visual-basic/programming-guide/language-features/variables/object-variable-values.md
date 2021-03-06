---
title: 对象变量值 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 28307cc477f661c3046e125f297c1519485ad797
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="object-variable-values-visual-basic"></a>对象变量值 (Visual Basic)
变量[Object 数据类型](../../../../visual-basic/language-reference/data-types/object-data-type.md)可以指任何类型的数据。 在中存储的值`Object`变量被保存别处在内存中，而变量本身的数据指针。  
  
## <a name="object-classifier-functions"></a>对象分类器函数  
 Visual Basic 提供返回有关新增功能的信息的函数`Object`变量所引用下, 表中所示。  
  
|函数|如果对象变量引用的则返回 True|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|一个值，而不是单个值的数组|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|A[日期数据类型](../../../../visual-basic/language-reference/data-types/date-data-type.md)值或可以解释为日期和时间值的字符串|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|类型的对象<xref:System.DBNull>，它表示缺失或不存在的数据|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|一个异常对象，它派生自 <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[执行任何操作](../../../../visual-basic/language-reference/nothing.md)，也就是说，没有任何对象当前分配给变量|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|一个数字或可以解释为数字的字符串|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|引用类型 （如字符串、 数组、 委托或类类型）|  
  
 这些函数可用于避免提交向操作或过程的无效值。  
  
## <a name="typeof-operator"></a>TypeOf 运算符  
 你还可以使用[TypeOf 运算符](../../../../visual-basic/language-reference/operators/typeof-operator.md)来确定是否为特定数据类型中当前引用的对象变量。 `TypeOf`...`Is`表达式计算结果为`True`如果操作数的运行时类型派生自或实现指定的类型。  
  
 下面的示例使用`TypeOf`引用值和引用类型的对象变量上。  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 前面的示例将以下行**调试**窗口：  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 对象变量`num`类型的数据是指`Integer`，和`frm`类的对象是指<xref:System.Windows.Forms.Form>。  
  
## <a name="object-arrays"></a>对象数组  
 你可以声明并使用的数组`Object`变量。 当你需要处理各种数据类型和对象类时，这非常有用。 数组中的所有元素必须都具有相同的声明的数据类型。 声明此数据类型作为`Object`可用于存储对象和类以及数组中的其他数据类型的实例。  
  
## <a name="see-also"></a>请参阅  
 [对象变量](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [对象变量声明](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [对象变量赋值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [如何：引用对象的当前实例](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [如何：确定对象变量引用的类型](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [如何：确定两个对象是否相关](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [如何：确定两个对象是否相同](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)  
 [数据类型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
