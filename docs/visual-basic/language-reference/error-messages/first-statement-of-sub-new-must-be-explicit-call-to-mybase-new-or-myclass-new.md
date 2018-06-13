---
title: "この最初のステートメント&#39;Sub New&#39;を明示的に呼び出す必要があります&#39;トラクター&#39;または&#39;'mybase.new'&#39;ため、 &#39;&lt;古い形式&gt;&#39; 、基底クラスで&#39;&lt;baseclassname&gt; &#39;の&#39; &lt;derivedclassname&gt; &#39;旧式とマークされて: &#39; &lt;errormessage&gt;&#39;"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: dbce2a9edcc38ff137cb7ec0c97e5c259c0a0979
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589894"
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>この最初のステートメント&#39;Sub New&#39;を明示的に呼び出す必要があります&#39;トラクター&#39;または&#39;'mybase.new'&#39;ため、 &#39;&lt;古い形式&gt;&#39; 、基底クラスで&#39;&lt;baseclassname&gt; &#39;の&#39; &lt;derivedclassname&gt; &#39;旧式とマークされて: &#39; &lt;errormessage&gt;&#39;
クラス コンストラクターが基底クラスのコンストラクターを明示的に呼び出さず、暗黙的な基底クラスのコンストラクターが <xref:System.ObsoleteAttribute> 属性およびエラーとして扱うことを示すディレクティブでマークされています。  
  
 派生クラスのコンス トラクターが基底クラスのコンス トラクターを呼び出さない場合、Visual Basic はパラメーターなしの基底クラスのコンス トラクターの暗黙的な呼び出しを生成しようとします。 引数を指定せずに呼び出すことができる基底クラスにアクセス可能なコンス トラクターがない場合、Visual Basic は、暗黙的な呼び出しを生成できません。 この場合、必要なコンス トラクターでマークされている、<xref:System.ObsoleteAttribute>属性があるため、Visual Basic から呼び出すことができません。  
  
 どのプログラミング要素でも、 <xref:System.ObsoleteAttribute> を適用すれば、もう使用しなくなったものとしてマークを付けることができます。 これを行う場合、この属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False`のどちらかに設定できます。 `True`に設定した場合、この要素を使用しようとすると、コンパイラはエラーとして処理します。 `False`に設定した場合、または既定値の `False`を使用した場合、コンパイラはこの要素の使用が試行されると、警告を発行します。  
  
 **エラー ID:** BC30920  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを確認し、適切な処理を行います。  
  
2.  `MyBase.New()` または `MyClass.New()` の呼び出しを `Sub New` の最初のステートメントとして派生クラスに含めます。  
  
## <a name="see-also"></a>関連項目  
 [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
