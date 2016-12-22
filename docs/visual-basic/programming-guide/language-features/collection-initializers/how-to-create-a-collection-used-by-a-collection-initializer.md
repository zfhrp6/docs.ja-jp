---
title: "How to: Create a Collection Used by a Collection Initializer (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "collection initializers [Visual Basic]"
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create a Collection Used by a Collection Initializer (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

コレクションの作成のためにコレクション初期化子を使用する場合、Visual Basic コンパイラでは、`Add` メソッドのパラメーターがコレクション初期化子内の値の型と一致するコレクション型の `Add` メソッドを検索します。  この `Add` メソッドは、コレクション初期化子からの値を使用してコレクションを作成するために使用されます。  
  
## 使用例  
 `Order` 型のオブジェクトを追加するためにコレクション初期化子が使用できるパブリックの `Add` メソッドが、`OrderCollection` コレクションに含まれるコード例を次に示します。  `Add` メソッドを使用することで、簡略化されたコレクション初期化子構文を使用できます。  
  
 [!CODE [VbVbalrCollectionInitializersHowTo2#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2#4)]  
  
 [!CODE [VbVbalrCollectionInitializersHowTo2#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2#1)]  
  
 [!CODE [VbVbalrCollectionInitializersHowTo2#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2#2)]  
  
 [!CODE [VbVbalrCollectionInitializersHowTo2#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2#3)]  
  
## 参照  
 [Collection Initializers](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [How to: Create an Add Extension Method Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)