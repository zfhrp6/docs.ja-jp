---
title: "Constructor &#39;&lt;name&gt;&#39; cannot call itself | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30298"
  - "vbc30298"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30298"
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Constructor &#39;&lt;name&gt;&#39; cannot call itself
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

クラスまたは構造体の `Sub New` プロシージャがそれ自体を呼び出しています。  
  
 コンストラクターの目的は、クラスまたは構造体を最初に作成するとき、それを初期化することです。  クラスまたは構造体には、複数のコンストラクターを作成できます。ただし、すべてのコンストラクターでパラメーター リストが同じでないことが必要です。  コンストラクターから別のコンストラクターを呼び出して、それ自体の機能に加えて別の機能も実行することが可能です。  しかし、コンストラクターが自分を呼び出すことには意味がなく、実際これが許可されると、無限再帰が起きてしまいます。  
  
 **Error ID:** BC30298  
  
### このエラーを解決するには  
  
1.  呼び出されるコンストラクターのパラメーター リストを調べます。  このパラメーター リストは、呼び出しを行っているコンストラクターのものと異なっている必要があります。  
  
2.  別のコンストラクターを呼び出すつもりでない場合は、`Sub New` 呼び出し全体を削除してください。  
  
## 参照  
 [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)