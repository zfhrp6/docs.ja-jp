---
title: '&#39;です。&lt;属性&gt;&#39; ために、適用できません GUID &#39; の形式&lt;数&gt;&#39; が正しくありません'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ead07d12064dbe18a1e23d4d1343b1efba1b533
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>&#39;です。&lt;属性&gt;&#39; ために、適用できません GUID &#39; の形式&lt;数&gt;&#39; が正しくありません
A`COMClassAttribute`属性ブロックは、GUID の適切な形式に準拠していないグローバル一意識別子 (GUID) を指定します。 `COMClassAttribute`クラス、インターフェイス、および作成イベントを一意に識別するのに Guid を使用します。  
  
 GUID は、16 バイトで構成されます。前半の 8 バイトは数値、後半の 8 バイトはバイナリです。 Uuidgen.exe などの Microsoft ユーティリティによって生成され、領域と時間で一意であることが保証されます。  
  
 **エラー ID:** BC32500  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  正しい GUID または COM オブジェクトを識別するために必要な Guid を決定します。  
  
2.  `COMClassAttribute` 属性ブロックに表示される GUID 文字列が正しくコピーされていることを確認します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Guid>  
[属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)

