---
title: '&#39;&lt;属性&gt;&#39;ために適用することはできません、GUID の形式&#39;&lt;数&gt;&#39;が正しくありません'
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 93b208b2119942f939a3af223c2f562c6097f7a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587561"
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>&#39;&lt;属性&gt;&#39;ために適用することはできません、GUID の形式&#39;&lt;数&gt;&#39;が正しくありません
A`COMClassAttribute`属性ブロックは、GUID の適切な形式に準拠していないグローバル一意識別子 (GUID) を指定します。 `COMClassAttribute` クラス、インターフェイス、および作成イベントを一意に識別するのに Guid を使用します。  
  
 GUID は、16 バイトで構成されます。前半の 8 バイトは数値、後半の 8 バイトはバイナリです。 Uuidgen.exe などの Microsoft ユーティリティによって生成され、領域と時間で一意であることが保証されます。  
  
 **エラー ID:** BC32500  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  正しい GUID または COM オブジェクトを識別するために必要な Guid を決定します。  
  
2.  `COMClassAttribute` 属性ブロックに表示される GUID 文字列が正しくコピーされていることを確認します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Guid>  
[属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)

