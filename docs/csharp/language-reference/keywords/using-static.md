---
title: "using static ディレクティブ (C# リファレンス)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5838bede475cf2ad1b72518770241e86206a06bb
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="using-static-directive-c-reference"></a>using static ディレクティブ (C# リファレンス)

`using static` ディレクティブは、型名を指定せずにアクセスできる静的メンバーの型を指定します。 構文は次のとおりです。

```csharp
using static <fully-qualified-type-name>
```

*fully-qualified-type-name* は、型名を指定せずに参照できる静的メンバーの型の名前です。 完全修飾型名 (完全な名前空間名と型名) を指定しないと、C# によってコンパイラ エラー CS0246 "型または名前空間の名前 '<type-name>' が見つかりませんでした" が生成されます。

`using static` ディレクティブは、インスタンス メンバーがある場合でも、静的メンバーがあるすべての型に適用されます。 ただし、インスタンス メンバーは、型のインスタンスを通してのみ呼び出すことができます。

`using static` ディレクティブは、C# 6 で導入されました。

## <a name="remarks"></a>コメント
 
通常は、静的メンバーを呼び出すときに、型名とメンバー名を指定します。 同じ型名を繰り返し入力してその型のメンバーを呼び出すと、コードが冗長でわかりにくくなる可能性があります。 たとえば、次の `Circle` クラスの定義は、<xref:System.Math> クラスのメンバー数を参照します。
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

メンバーが参照されるたびに <xref:System.Math> クラスを明示的に参照する必要がなくなれば、`using static` ディレクティブによって生成されるコードがより簡潔になります。

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static` は、指定した型で宣言されているアクセス可能な静的メンバーおよび入れ子になった型のみをインポートします。  継承されたメンバーはインポートされません。  using static ディレクティブを使用して、Visual Basic モジュールを含む、名前付きの型からインポートすることができます。  F# の最上位の関数が、有効な C# 識別子を名前に持つ名前付きの型の静的メンバーとしてメタデータに存在する場合は、その F# 関数をインポートできます。  
  
 `using static` を使用すると、指定した型で宣言された拡張メソッドを拡張メソッドの参照で使用できるようになります。  ただし、コード内で修飾なしで参照している場合は、拡張メソッドの名前はスコープにインポートされません。  
  
 同じコンパイル単位または名前空間の多様な `using static` ディレクティブによってさまざまな型からインポートされた同じ名前を持つメソッドが、メソッド グループを形成します。  これらのメソッド グループ内のオーバーロードの解決方法は、C# の通常の規則に従います。  
  
## <a name="example"></a>例

次の例では、`using static` ディレクティブを使用して、<xref:System.Console> クラス、<xref:System.Math> クラス、および <xref:System.String> クラスの静的メンバーを、型名を指定せずに使用できるようにしています。

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

上の例では、`using static` ディレクティブを <xref:System.Double> 型に適用することもできます。 これは必要を呼び出すこと、<xref:System.Double.TryParse(System.String,System.Double@)>型名を指定せずメソッドです。 ただし、どの数値型の `TryParse` メソッドが呼び出されたかを判断するために `using static` ステートメントを確認する必要が出てくるため、コードが読みにくくなります。

## <a name="see-also"></a>関連項目

[using ディレクティブ](using-directive.md)   
[C# リファレンス](../../../csharp/language-reference/index.md)   
[C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
[名前空間の使用](../../../csharp/programming-guide/namespaces/using-namespaces.md)   
[名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md)   
[名前空間](../../../csharp/programming-guide/namespaces/index.md)   
