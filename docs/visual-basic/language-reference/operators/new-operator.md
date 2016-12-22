---
title: "New Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.new"
  - "vb.NewConstraint"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "constraints, Visual Basic generic types"
  - "generics [Visual Basic], constraints"
  - "constraints, New keyword"
  - "New constraint"
  - "New keyword"
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# New Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`New` 句を開始して新しいオブジェクト インスタンスを作成するか、型パラメーターにコンストラクター制約を指定するか、または `Sub` プロシージャをクラス コンストラクターとして識別します。  
  
## 解説  
 代入ステートメントの宣言で、`New` 句は、インスタンスを作成する定義済みのクラスを指定する必要があります。  つまり、クラスは呼び出し元のコードがアクセスできる 1 つ以上のコンストラクターを公開する必要があります。  
  
 `New` 句は、宣言ステートメントまたは代入ステートメントの中で使用できます。  ステートメントが実行されると、指定したクラスの適切なコンストラクターが呼び出されて、指定した引数が渡されます。  次に例を示します。この例では、2 つのコントラクターを持つ `Customer` クラスのインスタンスを作成します。一方はパラメーターを受け取らず、もう一方は文字列パラメーターを受け取ります。  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 配列はクラスであることから、`New` は次のとおり、新しい配列のインスタンスを作成できます。  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 新しいインスタンスを作成するためのメモリが不足している場合、共通言語ランタイム \(CLR\) は <xref:System.OutOfMemoryException> エラーをスローします。  
  
> [!NOTE]
>  `New` キーワードは、アクセス可能なパラメーターなしのコンストラクターを渡された型が公開する必要があることを示すために、型パラメーター リストでも使用されます。  型パラメーターと制約の詳細については、「[Type List](../../../visual-basic/language-reference/statements/type-list.md)」を参照してください。  
  
 クラスのコンストラクターのプロシージャを作成するには、`Sub` プロシージャの名前を `New` キーワードにします。  詳細については、「[Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)」を参照してください。  
  
 キーワード `New` は、次の構文で使用します。  
  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 参照  
 <xref:System.OutOfMemoryException>   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)   
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)