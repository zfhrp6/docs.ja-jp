---
title: 式の型&#39; &lt;typename&gt; &#39;は制限付きの型とから継承されたメンバーのアクセスに使用することはできません&#39;オブジェクト&#39;または&#39;ValueType&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab4e48c93a6a3c645bf9b5cc6c536d418022ae86
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>式の型&#39; &lt;typename&gt; &#39;は制限付きの型とから継承されたメンバーのアクセスに使用することはできません&#39;オブジェクト&#39;または&#39;ValueType&#39;
式は、共通言語ランタイム (CLR) でボックス化できない型に評価が、ボックス化を必要とするメンバーにアクセスします。  
  
 *ボックス化* とは、型を `Object` (場合によっては <xref:System.ValueType>) に変換するために不可欠な処理です。 共通言語ランタイムでは、特定の構造体の型をたとえばボックスことはできません<xref:System.ArgIterator>、 <xref:System.RuntimeArgumentHandle>、および<xref:System.TypedReference>です。  
  
 この式から継承されたメソッドの呼び出しに制限付きの型を使用しようとしました。<xref:System.Object>または<xref:System.ValueType>、など<xref:System.Object.GetHashCode%2A>または<xref:System.Object.ToString%2A>です。 このメソッドにアクセスするには、Visual Basic はこのエラーが発生する暗黙的なボックス化変換をしようとしました。  
  
 **エラー ID:** BC31393  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  問題の型に評価される式を探します。  
  
2.  継承されたメソッドを呼び出そうとすると、ステートメントの一部を検索<xref:System.Object>または<xref:System.ValueType>です。  
  
3.  メソッドの呼び出しを避けるために、ステートメントを書き直してください。  
  
## <a name="see-also"></a>関連項目  
 [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
