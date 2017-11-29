---
title: "派生クラスで基本クラスのイベントを発生させることはできません。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords: BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70dde8b96980adfd618e38b9ce142cdec56a6b13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>派生クラスで基本クラスのイベントを発生させることはできません。
宣言されている宣言領域からのみイベントを発生させることができます。 そのため、クラスは、その他のクラス、1 つでも派生元からイベントを発生させることはできません。  
  
 **エラー ID:** BC30029  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   移動、`Event`ステートメントまたは`RaiseEvent`もように、同じクラス内のステートメント。  
  
## <a name="see-also"></a>関連項目  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
 [RaiseEvent ステートメント](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
