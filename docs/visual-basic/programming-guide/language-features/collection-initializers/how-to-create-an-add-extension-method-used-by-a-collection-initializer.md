---
title: "How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic) | Microsoft Docs"
ms.custom: ""
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
  - "collection initializers [Visual Basic]"
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コレクションの作成のためにコレクション初期化子を使用する場合、Visual Basic コンパイラでは、`Add` メソッドのパラメーターがコレクション初期化子内の値の型と一致するコレクション型の `Add` メソッドを検索します。  この `Add` メソッドは、コレクション初期化子からの値を使用してコレクションを作成するために使用されます。  
  
 一致する `Add` メソッドがなく、コレクションのコードを変更できない場合、コレクション初期化子に必要なパラメーターを取得する `Add` という拡張メソッドを追加できます。  通常この処理は、ジェネリック コレクションに対してコレクション初期化子を使用する場合に必要になります。  
  
## 使用例  
 拡張メソッドを <xref:System.Collections.Generic.List%601> ジェネリック型に追加することで、`Employee` 型のオブジェクトの追加にコレクション初期化子を使用できるようにする方法を次の例に示します。  拡張メソッドを使用することで、簡略化されたコレクション初期化子構文を使用できます。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/visualbasic/how-to-create-an-add-ext_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/visualbasic/how-to-create-an-add-ext_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/visualbasic/how-to-create-an-add-ext_3.vb)]  
  
## 参照  
 [Collection Initializers](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [How to: Create a Collection Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)