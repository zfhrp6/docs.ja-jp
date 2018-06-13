---
title: override (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 8f692dfdf8bd34ddb62623d86ec3dadd2b8dead3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280154"
---
# <a name="override-c-reference"></a>override (C# リファレンス)
`override` 修飾子は、継承したメソッド、プロパティ、インデクサー、またはイベントの抽象実装または仮想実装を拡張したり修飾したりする際に必要です。  
  
## <a name="example"></a>例  
 この例では、`Square` クラスが `Area` のオーバーライドされる実装を提供する必要があります。これは、`Area` が抽象 `ShapesClass` から継承されているためです。  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 `override` メソッドは、基底クラスから継承されるメンバーの新しい実装を提供します。 `override` 宣言によってオーバーライドされるメソッドを、オーバーライドされる基本メソッドと言います。 オーバーライドされる基本メソッドには、`override` メソッドと同じシグネチャが必要です。 継承については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。  
  
 非仮想メソッドまたは静的メソッドをオーバーライドすることはできません。 オーバーライドされる基本メソッドは、`virtual`、`abstract`、`override` のいずれかである必要があります。  
  
 `override` 宣言は、`virtual` メソッドのアクセシビリティを変更できません。 `override` メソッドと `virtual` メソッドの両方に、同じ[アクセス レベル修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)が必要です。  
  
 `override` メソッドの修飾に、修飾子 `new`、`static`、または `virtual` は使用できません。  
  
 オーバーライドするプロパティの宣言では、継承されるプロパティとまったく同じアクセス修飾子、型、および名前を指定する必要があります。オーバーライドされるプロパティは、`virtual`、`abstract`、または `override` である必要があります。  
  
 `override` キーワードの使い方の詳細については、「[Override キーワードと New キーワードによるバージョン管理](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)」および「[Override キーワードと New キーワードを使用する場合について](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)」を参照してください。  
  
## <a name="example"></a>例  
 この例では、`Employee` という基底クラスと、`SalesEmployee` という派生クラスを定義します。 `SalesEmployee` クラスには追加のプロパティ `salesbonus` があり、このプロパティを処理に含めるために、`CalculatePay` メソッドをオーバーライドします。  
  
 [!code-csharp[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)
