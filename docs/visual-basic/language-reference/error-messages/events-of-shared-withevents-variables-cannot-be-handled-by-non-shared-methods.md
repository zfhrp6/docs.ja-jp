---
title: 共有 WithEvents 変数のイベントを、非共有メソッドで処理できません。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53372927b88df3946583564492df42170f302739
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>共有 WithEvents 変数のイベントを、非共有メソッドで処理できません。
宣言された変数、`Shared`修飾子は、共有変数。 共有変数は、1 つだけの記憶域の場所を識別します。 宣言された変数、`WithEvents`修飾子は、変数が属する型が変数で発生させるイベントのセットを処理することをアサートします。 プロパティがによって作成された値が変数に割り当てられている場合、`WithEvents`宣言を既存のイベント ハンドラーをアンフックし、使用して、新しいイベント ハンドラーをフック、、`Add`メソッドです。  
  
 **エラー ID:** BC30594  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   イベント ハンドラーを宣言`Shared`です。  
  
## <a name="see-also"></a>関連項目  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
