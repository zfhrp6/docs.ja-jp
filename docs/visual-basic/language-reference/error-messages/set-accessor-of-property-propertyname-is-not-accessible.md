---
title: "&#39;Set&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31102"
  - "bc31102"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31102"
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &#39;Set&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ステートメントがプロパティの値を格納しようとしましたが、プロパティの `Set` プロシージャへのアクセス許可がありません。  
  
 [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) が [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)よりも制限の高いアクセス レベルでマーク付けされている場合にプロパティ値の設定を試みると、次のケースでエラーになります。  
  
-   `Set` ステートメントが [Private](../../../visual-basic/language-reference/modifiers/private.md) でマーク付けされており、呼び出し元のコードがプロパティが定義されたクラスまたは構造体の外側にある場合。  
  
-   `Set` ステートメントが [Protected](../../../visual-basic/language-reference/modifiers/protected.md) でマーク付けされており、呼び出し元のコードがプロパティが定義されたクラスまたは構造体の内部にも、派生クラスの内部にもない場合。  
  
-   `Set` ステートメントが [Friend](../../../visual-basic/language-reference/modifiers/friend.md) でマーク付けされており、呼び出し元のコードがプロパティが定義されたのと同じアセンブリにない場合。  
  
 **Error ID:** BC31102  
  
### このエラーを解決するには  
  
-   プロパティが定義されたソース コードを変更できる場合は、`Set` プロシージャをプロパティ自体と同じアクセス レベルで宣言できないか検討してください。  
  
-   プロパティが定義されたソース コードを変更できない場合、または `Set` プロシージャをプロパティ自体よりも高いアクセス レベルで制限する必要がある場合は、プロパティ値を設定するステートメントをプロパティへのアクセスが可能なコード領域に移動することを検討します。  
  
## 参照  
 [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)