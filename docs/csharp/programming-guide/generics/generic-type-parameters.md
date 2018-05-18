---
title: ジェネリック型の型パラメーター (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 35029b90fb7b905a87055596cf8dcd6a84ef9d36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="generic-type-parameters-c-programming-guide"></a>ジェネリック型の型パラメーター (C# プログラミング ガイド)
ジェネリック型またはメソッド定義で、型パラメーターは、ジェネリック型の変数をインスタンス化するときにクライアントが指定する特定の型のためのプレースホルダーになります。 「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」に記載されている `GenericList<T>` などのジェネリック クラスは、実際は型でないため、そのままでは使用できません。これは型の設計図のようなものです。 `GenericList<T>` を使用するには、クライアント コードで構築された型を宣言し、インスタンス化する必要があります。山かっこ内に型引数を指定します。 この特定のクラスの型引数は、コンパイラで認識されるあらゆる型にすることができます。 構築された型インスタンスは、次のようにさまざまな型引数を利用し、いくつでも作成できます。  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 `GenericList<T>` の各インスタンスでは、クラス内のすべての `T` は実行時に型引数に置換されます。 この置換を使用し、単一クラス定義を使用してタイプ セーフで効率的なオブジェクトを 3 つ作成しました。 この置換が CLR で実行されるしくみについては、「[ランタイムのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)」を参照してください。  
  
## <a name="type-parameter-naming-guidelines"></a>型パラメーターの名前付けガイドライン  
  
-   1 文字の名前でも完全に説明され、説明的な名前を付けることに意味がない場合を除き、ジェネリック型パラメーターには**説明的な名前を付けてください**。  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   1 文字の型パラメーターを持つ型の型パラメーター名として T を利用することを**検討してください**。  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   型パラメーターの説明的な名前には "T" という**接頭辞を付けてください**。  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   型パラメーターに与えられた制約をパラメーターの名前で示唆することを**検討してください**。 たとえば、`ISession` に制約されているパラメーターの名前を `TSession` にします。  
  
## <a name="see-also"></a>参照  
 <xref:System.Collections.Generic>  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ジェネリック](../../../csharp/programming-guide/generics/index.md)  
 [C++ テンプレートと C# ジェネリックの違い](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
