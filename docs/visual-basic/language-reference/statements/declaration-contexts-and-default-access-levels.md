---
title: "Declaration Contexts and Default Access Levels (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "module level, defined"
  - "declaration contexts, Visual Basic"
  - "procedure level, defined"
  - "namespace level, defined"
  - "access levels, Visual Basic"
  - "access levels, default levels"
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Declaration Contexts and Default Access Levels (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このトピックでは、Visual Basic のどのデータ型がどのデータ型の中で宣言できるかについて説明します。また、指定がない場合の各データ型の既定のアクセス レベルを示します。  
  
## 宣言コンテキストのレベル  
 *宣言コンテキスト*とは、プログラミング要素が宣言されるコードの領域のことです。  別のプログラミング要素の中であることも多く、この場合このプログラミング要素は "*コンテナー要素*" と呼ばれます。  
  
 宣言コンテキストのレベルは次のとおりです。  
  
-   *名前空間レベル*: 同じソース ファイルまたは名前空間内にあるが、クラス、構造体、モジュール、インターフェイスは異なる  
  
-   *モジュール レベル*: 同じクラス、構造体、モジュール、インターフェイス内にあるが、プロシージャやブロックは異なる  
  
-   *プロシージャ レベル*: 同じプロシージャまたはブロック \(`If` や `For` など\) 内にある  
  
 次の表に、宣言されたさまざまなプログラミング要素の既定のアクセス レベルを、宣言コンテキスト別に示します。  
  
|宣言された要素|名前空間レベル|モジュール レベル|プロシージャ レベル|  
|-------------|-------------|---------------|----------------|  
|変数 \([Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)\)|不可|`Private` \(`Structure` では `Public`、`Interface` では不可\)|`Public`|  
|定数 \([Const Statement](../../../visual-basic/language-reference/statements/const-statement.md)\)|不可|`Private` \(`Structure` では `Public`、`Interface` では不可\)|`Public`|  
|列挙型 \([Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)\)|`Friend`|`Public`|不可|  
|クラス \([Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)\)|`Friend`|`Public`|不可|  
|構造体 \([Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)\)|`Friend`|`Public`|不可|  
|モジュール \([Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)\)|`Friend`|不可|不可|  
|インターフェイス \([Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)\)|`Friend`|`Public`|不可|  
|プロシージャ \([Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)、[Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)\)|不可|`Public`|不可|  
|外部参照 \([Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)\)|不可|`Public` \(`Interface` では不可\)|不可|  
|演算子 \([Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)\)|不可|`Public` \(`Interface` または `Module` では不可\)|不可|  
|プロパティ \([Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)\)|不可|`Public`|不可|  
|既定のプロパティ \([Default](../../../visual-basic/language-reference/modifiers/default.md)\)|不可|`Public` \(`Module` では不可\)|不可|  
|イベント \([Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)\)|不可|`Public`|不可|  
|デリゲート \([Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md)\)|`Friend`|`Public`|不可|  
  
 詳細については、「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
## 参照  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)