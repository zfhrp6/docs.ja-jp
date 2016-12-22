---
title: "&#39;&lt;expression&gt;&#39; cannot be used as a type constraint | Microsoft Docs"
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
  - "bc32061"
  - "vbc32061"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32061"
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;expression&gt;&#39; cannot be used as a type constraint
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

型パラメーターに対する有効な制約を表さない式が、制約リストに含まれています。  
  
 制約リストには、型パラメーターに渡される型引数に対する要件を設定します。  次の要件を任意に組み合わせて指定できます。  
  
-   型引数は、1 つまたは複数のインターフェイスを実装する。  
  
-   型引数は、最大で 1 つのクラスを継承する必要があります。  
  
-   型引数は、作成側のコードがアクセスできるパラメーターなしのコンストラクターを公開する必要があります \(`New` 制約を含む\)。  
  
 特定のクラスまたはインターフェイスを制約リストに含めない場合は、次のいずれかを指定することで、より汎用的な要件を設定できます。  
  
-   型引数は、値型である必要があります \(`Structure` 制約を含む\)。  
  
-   型引数は、参照型である必要があります \(`Class` 制約を含む\)。  
  
 同じ型パラメーターに対して `Structure` と `Class` の両方を指定することはできません。また、これらを複数回指定することもできません。  
  
 **Error ID:** BC32061  
  
### このエラーを解決するには  
  
-   式と各要素のスペルが正しいかどうかを確認します。  
  
-   式が上記の要件を満たしていない場合は、制約リストから式を削除します。  
  
-   式がインターフェイスまたはクラスを参照する場合は、コンパイラがそのインターフェイスまたはクラスにアクセスできることを確認します。  場合によっては、有効な名前かどうかを確認することや、プロジェクトに参照を追加することが必要です。  詳細については、「[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」の「プロジェクトへの参照」を参照してください。  
  
## 参照  
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Value Types and Reference Types](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)