---
title: "&quot;&lt;属性&gt;&quot; ために、適用できません GUID の形式 &quot;&lt;数&gt;&quot; が正しくない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32500
- bc32500
dev_langs:
- VB
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
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
ms.openlocfilehash: f22f9ecd63582e2a346702919cf9154819b8eb0e
ms.lasthandoff: 03/13/2017

---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>'&lt;属性&gt;' ために、適用できません GUID の形式 '&lt;数&gt;' が正しくありません
A`COMClassAttribute`属性ブロックは、GUID を適切な形式に準拠しないグローバル一意識別子 (GUID) を指定します。 `COMClassAttribute`クラス、インターフェイス、および作成イベントを一意に識別するのに Guid を使用します。  
  
 GUID は、16 バイトで構成されます。前半の 8 バイトは数値、後半の 8 バイトはバイナリです。 Uuidgen.exe などのマイクロソフト ユーティリティによって生成され、領域と時間で一意であることが保証されます。  
  
 **エラー ID:** BC32500  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  正しい GUID または COM オブジェクトを識別するために必要な Guid を確認します。  
  
2.  `COMClassAttribute` 属性ブロックに表示される GUID 文字列が正しくコピーされていることを確認します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Guid></xref:System.Guid>   
[属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)


