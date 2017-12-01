---
title: "既定の値式 (C# プログラミング ガイド)"
description: "既定の値式は、あらゆる参照型または値型の既定値を生成します"
ms.date: 08/23/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2bb1c269e5347d615c47ab828506aef538c4761
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="default-value-expressions-c-programming-guide"></a>既定の値式 (C# プログラミング ガイド)

既定の値式は、型の既定値を生成します。 既定の値式は、ジェネリック クラスおよびメソッドで特に役立ちます。 ジェネリックの使用で発生する問題の 1 つは、次のことがあらかじめわかっていない場合に、パラメーター化された型 `T` に既定値を割り当てる方法です。

- `T` が参照型または値型のどちらか。
- `T` が値型の場合、T は数値かユーザー定義の構造体か。

 パラメーター化された型 `T` の変数 `t` が指定されている場合、ステートメント `t = null` は `T` が参照型の場合にのみ有効です。 割り当て `t = 0` は数値型でのみ機能し、構造体では機能しません。 これは、参照型 (クラスの型およびインターフェイスの型) に対して `null` を、数値型に対しては 0 を返す既定の値式を使用すると解決します。 ユーザー定義の構造体の場合は、0 ビット パターンに初期化された構造体を返します。これにより、そのメンバーが値型か参照型に応じて、各メンバーに 0 または `null` が生成されます。 null 許容値型の場合は、`default` は構造体と同様に初期化される <xref:System.Nullable%601?displayProperty=nameWithType> を返します。

`default(T)` 式は、ジェネリック クラスやメソッドに制限されません。 既定の値式は、任意のマネージ型で使用できます。 次の式のいずれかが有効です。

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 `GenericList<T>` クラスの次の例は、ジェネリック クラスに `default(T)` 演算子を使う方法を示します。 詳しくは、「[ジェネリックの概要](../generics/introduction-to-generics.md)」をご覧ください。

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a>既定のリテラルと型推論

C# 7.1 より、コンパイラが式の型を推定できる場合、`default` リテラルを既定の値式に使用することができます。 `default` リテラルは同等の `default(T)` (`T` は推定型) と同じ値を生成します。 これにより、型を複数回宣言する冗長さが低減され、コードが簡潔になります。 `default` リテラルは、次の場所のいずれかで使用できます。

- 変数初期化子
- 変数の代入
- オプションのパラメーターの既定値の宣言
- メソッド呼び出しの引数の値の提供
- return ステートメント (または式のようなメンバー内の式)

次の例は、既定の値式の `default` リテラルの多くの使用法を示しています。

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a>関連項目

 <xref:System.Collections.Generic>[C# プログラミング ガイド](../index.md)  
 [ジェネリック](../generics/index.md)  
 [ジェネリック メソッド](../generics/generic-methods.md)  
 [ジェネリック](~/docs/standard/generics/index.md)  
