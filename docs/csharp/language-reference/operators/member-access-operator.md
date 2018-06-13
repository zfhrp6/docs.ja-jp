---
title: である必要があります。 演算子 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 088f1991cafa92a69e11ca14bd2d983b36c0e3ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271030"
---
# <a name="-operator-c-reference"></a>である必要があります。 演算子 (C# リファレンス)
ドット演算子 (`.`) は、メンバー アクセスに使用されます。 ドット演算子は、型または名前空間のメンバーを指定します。 たとえば、ドット演算子は、.NET Framework クラス ライブラリ内の特定のメソッドにアクセスするために使用されます。  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 たとえば、次のクラスを考えてみます。  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 `s` 変数には 2 つのメンバー (`a` と `b`) があり、それらにアクセスするために、ドット演算子を使用します。  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 ドットは、修飾名を形成するためにも使用されます。この修飾名は、たとえば、属している名前空間やインターフェイスを指定する名前です。  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 using ディレクティブを使用すると、名前の修飾をオプションにすることができます。  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 ただし、識別子があいまいな場合は、修飾する必要があります。  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)
