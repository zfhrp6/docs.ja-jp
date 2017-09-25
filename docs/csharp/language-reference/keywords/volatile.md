---
title: "volatile (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- volatile_CSharpKeyword
- volatile
dev_langs:
- CSharp
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c8f9fba15991197be885a973435089098a57db87
ms.contentlocale: ja-jp
ms.lasthandoff: 09/25/2017

---
# <a name="volatile-c-reference"></a>volatile (C# リファレンス)
`volatile` キーワードは、同時に実行されている複数のスレッドによって、フィールドが変更される可能性があることを示します。 `volatile` と宣言されているフィールドは、シングル スレッドによるアクセスを前提とする、コンパイラの最適化の対象にはなりません。 このため、フィールドには常に最新の値が含まれます。  
  
 `volatile` 修飾子は、通常、アクセスをシリアル化する [lock](../../../csharp/language-reference/keywords/lock-statement.md) ステートメントが使用されない場合に、複数のスレッドからアクセスされるフィールドに対して使用します。  
  
 `volatile` キーワードは次の型のフィールドに使用できます。  
  
-   参照型。  
  
-   ポインター型 (unsafe コンテキスト内)。 ポインター自体は volatile にできますが、ポインターが指しているオブジェクトは volatile にできません。 つまり、"volatile を指すポインター" は宣言できません。  
  
-   sbyte、byte、short、ushort、int、uint、char、float、bool などの型。  
  
-   基本データ型 byte、sbyte、short、ushort、int、または uint のいずれかが含まれる列挙型。  
  
-   参照型であることが判明しているジェネリック型パラメーター。  
  
-   <xref:System.IntPtr> および <xref:System.UIntPtr>。  
  
 volatile キーワードは、クラスまたは構造体のフィールドにのみ適用できます。 ローカル変数を `volatile` として宣言することはできません。  
  
## <a name="example"></a>例  
 次の例は、public のフィールド変数を `volatile` として宣言する方法を示しています。  
  
 [!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a>例  
 次の例は、補助スレッドつまりワーカー スレッドを作成および使用して、プライマリ スレッドとの並行処理を実行する方法を示しています。 マルチスレッドの背景情報については、[スレッド化](../../../standard/threading/index.md)に関するページと「[スレッド処理](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)」を参照してください。  
  
 [!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)

