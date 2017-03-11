---
title: "Early and Late Binding (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "02/25/2017"
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
  - "early binding"
  - "objects [Visual Basic], late-bound"
  - "objects [Visual Basic], early-bound"
  - "objects [Visual Basic], late bound"
  - "early binding, Visual Basic compiler"
  - "binding, late and early"
  - "objects [Visual Basic], early bound"
  - "Visual Basic compiler, early and late binding"
  - "late binding"
  - "late binding, Visual Basic compiler"
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Early and Late Binding (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラは、オブジェクトがオブジェクト変数に代入されるときに `binding` と呼ばれる処理を実行します。  オブジェクトが特定のオブジェクト型として宣言された変数に代入される場合、オブジェクトは*事前バインディング*されます。  事前バインディングされたオブジェクトでは、アプリケーションが実行される前に、コンパイラによってメモリの割り当てとその他の最適化が実行されます。  たとえば、次のコード例では <xref:System.IO.FileStream> 型の変数を宣言しています。  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#90)]  
  
 <xref:System.IO.FileStream>は特定のオブジェクト型であるため、`FS` に代入されるインスタンスは事前バインディングされます。  
  
 対照的に、オブジェクトが `Object` 型として宣言された変数に代入される場合は、*遅延バインディング*されます。  この型のオブジェクトは、任意のオブジェクトへの参照を保持できますが、事前バインディングされたオブジェクトの利点をほとんど持ちません。  たとえば、次のコード例では、`CreateObject` 関数で返されたオブジェクトを保持するオブジェクト変数を宣言しています。  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/LateBinding.vb#91)]  
  
## 事前バインディングの利点  
 可能な場合は、事前バインディングされたオブジェクトを使用してください。これによって、コンパイラは、アプリケーションをより効率的にする重要な最適化を実行できます。  事前バインディングされたオブジェクトは遅延バインディングされたオブジェクトよりも処理が高速です。また、使用されているオブジェクトの種類が明確になるため、コードがより読みやすくなり、保守も簡単になります。  事前バインディングのその他の利点として、自動コード補完やダイナミック ヘルプなどの便利な機能が有効になります。これは、[!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs-md.md)] の統合開発環境 \(IDE\) により、コードの編集中に作業しているオブジェクトの種類が正確に判断されるためです。  事前バインディングを使用すると、プログラムのコンパイル時にコンパイラがエラーを報告できるため、ランタイム エラーの数が減少し、エラーの重大性も低下します。  
  
> [!NOTE]
>  遅延バインディングを使用できるのは、`Public` として宣言されている型メンバーにアクセスするときだけです。  `Friend` または `Protected Friend` として宣言されたメンバーにアクセスすると、ランタイム エラーになります。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>   
 [Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)