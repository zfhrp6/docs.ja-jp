---
title: "式の型が &quot;&lt;typename&gt;&quot; は制限付きの型と &quot;Object&quot; または &quot;ValueType&quot; から継承されたメンバーにアクセスするために使用できない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
dev_langs:
- VB
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: aaedfd825889498159f92cbd1d615cc0064973d3
ms.lasthandoff: 03/13/2017

---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>式の型が '&lt;typename&gt;' は制限付きの型と 'Object' または 'ValueType' から継承したメンバーのアクセスに使用することはできません
式では、共通言語ランタイム (CLR) でボックス化できない型に評価が、ボックス化を必要とするメンバーにアクセスします。  
  
 *ボックス化*を型に変換するために必要な処理を指します`Object`または<xref:System.ValueType>.</xref:System.ValueType>に場合によっては、 共通言語ランタイムでは、特定の構造体の型を次に例をボックスことはできません<xref:System.ArgIterator>、 <xref:System.RuntimeArgumentHandle>、 <xref:System.TypedReference>.</xref:System.TypedReference> </xref:System.RuntimeArgumentHandle> </xref:System.ArgIterator>  
  
 この式が制限付きの型を使用して、継承されたメソッドを呼び出すしよう<xref:System.Object>または<xref:System.ValueType>、<xref:System.Object.GetHashCode%2A>または<xref:System.Object.ToString%2A>.</xref:System.Object.ToString%2A></xref:System.Object.GetHashCode%2A>など</xref:System.ValueType></xref:System.Object> このメソッドにアクセスする[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]このエラーが発生する暗黙的なボックス化変換しようとしました。  
  
 **エラー ID:** BC31393  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  問題の型に評価される式を探します。  
  
2.  <xref:System.Object>または<xref:System.ValueType>.</xref:System.ValueType></xref:System.Object>から継承されたメソッドを呼び出そうとすると、ステートメントの一部を検索します。  
  
3.  メソッドの呼び出しを回避するステートメントを書き直してください。  
  
## <a name="see-also"></a>関連項目  
 [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
