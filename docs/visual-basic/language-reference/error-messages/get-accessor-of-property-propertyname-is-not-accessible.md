---
title: "&#39;Get&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31103"
  - "bc31103"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31103"
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &#39;Get&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ステートメントがプロパティの値を取得しようとしましたが、プロパティの `Get` プロシージャへのアクセス許可がありません。  
  
 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)が [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)よりも制限の高いアクセス レベルでマーク付けされている場合、プロパティ値の読み取りは次のケースでエラーになります。  
  
-   `Get` ステートメントが [Private](../../../visual-basic/language-reference/modifiers/private.md) でマーク付けされており、呼び出し元のコードがプロパティが定義されたクラスまたは構造体の外側にある場合。  
  
-   `Get` ステートメントが [Protected](../../../visual-basic/language-reference/modifiers/protected.md) でマーク付けされており、呼び出し元のコードがプロパティが定義されたクラスまたは構造体の内部にも、派生クラスの内部にもない場合。  
  
-   `Get` ステートメントが [Friend](../../../visual-basic/language-reference/modifiers/friend.md) でマーク付けされており、呼び出し元のコードがプロパティが定義されたのと同じアセンブリにない場合。  
  
 **Error ID:** BC31103  
  
### このエラーを解決するには  
  
-   プロパティが定義されたソース コードを変更できる場合は、`Get` プロシージャをプロパティ自体と同じアクセス レベルで宣言することを検討してください。  
  
-   プロパティが定義されたソース コードを変更できない場合、または `Get` プロシージャをプロパティ自体よりも厳しいアクセス レベルで制限する必要がある場合は、プロパティ値を読み取るステートメントをプロパティへのアクセスが可能なコード領域に移動することを検討してください。  
  
## 参照  
 [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)