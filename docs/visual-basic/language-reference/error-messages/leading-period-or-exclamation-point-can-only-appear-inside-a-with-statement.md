---
title: "トップ &#39;。&#39;です。または &#39; です。&#39;です。内でのみ表示できます、&#39;です。&#39;です。ステートメント"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords: BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 961f2d737123ab68b200d5fc7658cb81291a5de6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>トップ &#39;。&#39;です。または &#39; です。&#39;です。内でのみ表示できます、&#39;です。&#39;です。ステートメント
ピリオド (.) または感嘆符 (!) 外にある内部、`With`左の式がブロックされます。 メンバー アクセス (`.`) およびディクショナリ メンバー アクセス (`!`) メンバーを含む要素を指定する式が必要です。 またはの対象として、アクセサーの左側にすぐにこの表示する必要があります、`With`メンバー アクセスを含むブロックします。  
  
 **エラー ID:** BC30157  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  いることを確認、`With`ブロックが正しく書式設定されています。  
  
2.  ある場合ありません`With`ブロックは、メンバーを含む定義の要素に評価されるアクセサーの左側に式を追加します。  
  
## <a name="see-also"></a>関連項目  
 [コード内の特殊文字](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [With...End With ステートメント](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
