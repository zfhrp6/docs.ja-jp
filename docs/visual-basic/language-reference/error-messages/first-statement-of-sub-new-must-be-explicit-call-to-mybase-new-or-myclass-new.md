---
title: "この &quot;Sub New&quot; の最初のステートメントは &quot;MyBase.New&quot; &quot;mybase.new&quot; または &quot;myclass.new&quot; への明示的な呼び出しをする必要がありますので、&quot;&lt;constructorname&gt;&quot;の基本クラス&quot;&lt;baseclassname&gt;&quot;の&quot;&lt;derivedclassname&gt;&quot; 不使用とマークされた: &quot;&lt;errormessage&gt;&quot; |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
dev_langs:
- VB
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: feb04d426b7e050b7ad05cdfd4d481172dda3a49
ms.lasthandoff: 03/13/2017

---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>この 'Sub New' の最初のステートメントは 'MyBase.New' 'mybase.new' または 'myclass.new' への明示的な呼び出しをする必要がありますので、'&lt;constructorname&gt;'の基本クラス'&lt;baseclassname&gt;'の'&lt;derivedclassname&gt;' 不使用とマークされた: '&lt;errormessage&gt;'
クラスのコンス トラクターが基本クラスのコンス トラクターを明示的に呼び出していないと、暗黙の型の基本クラス コンス トラクターが付いて、<xref:System.ObsoleteAttribute>属性と、エラーとして扱うディレクティブ</xref:System.ObsoleteAttribute>。  
  
 派生クラスのコンス トラクターは、基本クラスのコンス トラクターを呼び出していない[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]パラメーターなしの基本クラス コンス トラクターへの暗黙の呼び出しを生成しようとします。 引数を指定せずに呼び出すことができる基本クラスでアクセス可能なコンス トラクターがない場合[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]暗黙の呼び出しを生成することはできません。 この場合、必要なコンス トラクターがでマークされた、<xref:System.ObsoleteAttribute>ため属性[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]それを呼び出すことはできません</xref:System.ObsoleteAttribute>  
  
 使用中と不要になった<xref:System.ObsoleteAttribute>を</xref:System.ObsoleteAttribute>適用することで任意のプログラミング要素をマークすることができます。 これを行う場合は、属性を設定することができます<xref:System.ObsoleteAttribute.IsError%2A>プロパティを`True`または`False`</xref:System.ObsoleteAttribute.IsError%2A>。 `True`に設定した場合、コンパイラは、この要素を使用する試行をエラーとして処理します。 `False`に設定するか、または既定の `False`にする場合、この要素の使用が試行されると、コンパイラは警告を発行します。  
  
 **エラー ID:** BC30920  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを確認し、適切な処理を行います。  
  
2.  `MyBase.New()` または `MyClass.New()` の呼び出しを `Sub New` の最初のステートメントとして派生クラスに含めます。  
  
## <a name="see-also"></a>関連項目  
 [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
