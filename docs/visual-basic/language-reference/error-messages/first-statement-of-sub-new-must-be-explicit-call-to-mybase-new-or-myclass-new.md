---
title: "この &#39; の最初のステートメント新しいサブ &#39;明示的に呼び出す &#39; にする必要があります。指定されて &#39;または &#39;です。'Mybase.new' &#39;&#39;です。&lt;古い形式&gt;&#39;以外の場合は、基本クラス &#39; で&lt;baseclassname&gt;&#39; の &#39;&lt;derivedclassname&gt;&#39; 旧式とマークされて: &#39;&lt;errormessage&gt;&#39;です。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords: BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8882acd947251d85804fbefd54267ce078e31b95
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>この &#39; の最初のステートメント新しいサブ &#39;明示的に呼び出す &#39; にする必要があります。指定されて &#39;または &#39;です。'Mybase.new' &#39;&#39;です。&lt;古い形式&gt;&#39;以外の場合は、基本クラス &#39; で&lt;baseclassname&gt;&#39; の &#39;&lt;derivedclassname&gt;&#39; 旧式とマークされて: &#39;&lt;errormessage&gt;&#39;です。
クラス コンストラクターが基底クラスのコンストラクターを明示的に呼び出さず、暗黙的な基底クラスのコンストラクターが <xref:System.ObsoleteAttribute> 属性およびエラーとして扱うことを示すディレクティブでマークされています。  
  
 派生クラスのコンストラクターが基底クラスのコンストラクターを呼び出さない場合、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] では、パラメーターなしの基底クラスのコンストラクターの暗黙的な呼び出しを生成しようとします。 引数を指定せずに呼び出すことができるアクセス可能なコンストラクターが基底クラスにない場合、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] では暗黙的な呼び出しを生成できません。 この場合、必要なコンストラクターが <xref:System.ObsoleteAttribute> 属性でマークされるため、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] では呼び出すことができません。  
  
 <xref:System.ObsoleteAttribute> を適用することで、使用されなくなった要素としてすべてのプログラミング要素にマークを付けることができます。 これを行う場合、この属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False`のどちらかに設定できます。 `True`に設定した場合、この要素を使用しようとすると、コンパイラはエラーとして処理します。 `False`に設定するか、または既定の `False`にする場合、この要素を使用しようとすると、コンパイラは警告を発行します。  
  
 **エラー ID:** BC30920  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを確認し、適切な処理を行います。  
  
2.  `MyBase.New()` または `MyClass.New()` の呼び出しを `Sub New` の最初のステートメントとして派生クラスに含めます。  
  
## <a name="see-also"></a>関連項目  
 [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
