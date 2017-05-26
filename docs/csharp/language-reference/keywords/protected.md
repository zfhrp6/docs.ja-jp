---
title: "protected (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- protected
- protected_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
caps.latest.revision: 20
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 81791f38f277a4b61cc8eb96f1ee3b509a808f6a
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="protected-c-reference"></a>protected (C# リファレンス)
`protected` キーワードはメンバー アクセス修飾子です。 protected メンバーは、そのクラス内部と、派生クラスのインスタンスからアクセスできます。 `protected` と他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」を参照してください。  
  
## <a name="example"></a>例  
 派生クラス内で基底クラスの protected メンバーにアクセスできるのは、派生クラスの型を通してアクセスした場合のみです。 たとえば、次のコード セグメントを考えてみます。  
  
 [!code-cs[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 ステートメント `a.x = 10` でエラーが発生します。これは、クラス B のインスタンスではなく、静的メソッド Main 内にあるためです。  
  
 構造体は継承できないため、構造体のメンバーを protected にすることはできません。  
  
## <a name="example"></a>例  
 この例では、`DerivedPoint` クラスは `Point` から派生しています。 そのため、基底クラスの protected メンバーに、派生クラスから直接アクセスできます。  
  
 [!code-cs[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 `x` と `y` のアクセス レベルを [private](../../../csharp/language-reference/keywords/private.md) に変更すると、コンパイラによってエラー メッセージが生成されます。  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)
