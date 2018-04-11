---
title: アクセシビリティ ドメイン (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 127bacda4bf8363fccff3dd3ef6770ad50984cfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-domain-c-reference"></a>アクセシビリティ ドメイン (C# リファレンス)
メンバーのアクセシビリティ ドメインとは、どのプログラム セクションをメンバーから参照できるかを規定するものです。 そのメンバーが他の型の入れ子になっている場合、そのアクセシビリティ ドメインは、そのメンバーの[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)と、その直接のコンテナーである型のアクセシビリティ ドメインとの両方によって決定されます。  
  
 トップレベルの型のアクセシビリティ ドメインは、それが宣言されているプロジェクトのプログラム テキストと同じかそれ以上になります。 つまり、そのプロジェクトのすべてのソース ファイルがアクセシビリティ ドメインに含まれます。 入れ子にされた型のアクセシビリティ ドメインは、それが宣言されている型のプログラム テキストと同じかそれ以上になります。 つまり、アクセシビリティ ドメインは型の本体 (入れ子にされたすべての型のコンテナー) です。 入れ子にされた型のアクセシビリティ ドメインが、その型を含んでいる型のアクセシビリティ ドメインを超えることはありません。 次の例では、以上の概念を説明します。  
  
## <a name="example"></a>例  
 この例には、トップレベルの型 `T1` があり、そこに `M1` と `M2` の 2 つのクラスが入れ子にされています。 これらのクラスには、それぞれ異なるアクセシビリティが宣言されたいくつかのフィールドがあります。 `Main` メソッドの各ステートメントには、それぞれのメンバーのアクセシビリティ ドメインを示したコメントが記述されています。 アクセスできないメンバーを参照するステートメントがコメント アウトされていることに注目してください。アクセスできないメンバーを参照したことが原因で発生するコンパイラ エラーを確認したい場合は、1 つずつコメントを解除してください。  
  
 [!code-csharp[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [アクセシビリティ レベルの使用に関する制限事項](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
