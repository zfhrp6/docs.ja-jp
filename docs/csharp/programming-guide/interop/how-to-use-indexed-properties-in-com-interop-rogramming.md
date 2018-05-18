---
title: '方法: COM 相互運用機能を使用したプログラミングでインデックス付きプロパティを使用する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 5856ef871f865b2af0ab9ea637c26242cf99fb34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>方法: COM 相互運用機能を使用したプログラミングでインデックス付きプロパティを使用する (C# プログラミング ガイド)
"*インデックス付きプロパティ*" により、パラメーターを持つ COM プロパティが C# プログラミングでいっそう使いやすくなります。 インデックス付きプロパティは、[名前付き引数と省略可能な引数](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)、新しい型 ([dynamic](../../../csharp/language-reference/keywords/dynamic.md))、[埋め込み型情報](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)などの Visual C# の他の機能と連携して、Microsoft Office プログラミングをいっそう強力なものにします。  
  
 以前のバージョンの C# では、プロパティとしてメソッドにアクセスできるのは、`get` メソッドがパラメーターを持たず、`set` メソッドが 1 つだけ値パラメーターを持つ場合に限られました。 しかし、すべての COM プロパティがこのような制限を満たしているわけではありません。 たとえば、Excel の [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.range.aspx) プロパティには、範囲の名前のパラメーターを必要とする `get` アクセサーがあります。 これまでは、このような `Range` プロパティに直接アクセスすることはできず、次の例に示すように、`get_Range` メソッドを代わりに使う必要がありました。  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 インデックス付きプロパティを使うと、次のようなコードを記述できます。  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  また、前の例では、[省略可能な引数](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)機能も使われており、`Type.Missing` を省略できます。  
  
 同様に、Visual C# 2008 以前では、[Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) オブジェクトの `Value` プロパティの値を設定するには、2 つの引数が必要です。 1 つのパラメーターでは、範囲の値の型を指定する省略可能なパラメーターの引数を渡します。 そしてもう 1 つのパラメーターで、`Value` プロパティの値を渡します。 次の例は、これらの方法を示したものです。 どちらも、セル A1 の値を `Name` に設定しています。
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 インデックス付きプロパティを使うと、次のようなコードを記述できます。  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 独自のインデックス付きプロパティを作成することはできません。 この機能では、既存のインデックス付きプロパティの使用のみがサポートされます。  
  
## <a name="example"></a>例  
 次に完全なコードの例を示します。 Office API にアクセスするプロジェクトを設定する方法について詳しくは、「[方法: Visual C# の機能を使用して Office 相互運用オブジェクトにアクセスする](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)」をご覧ください。  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a>参照  
 [名前付き引数と省略可能な引数](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [dynamic 型の使用](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [方法: Office プログラミングで名前付き引数と省略可能な引数を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [方法: Visual C# の機能を使用して Office 相互運用オブジェクトにアクセスする](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 [チュートリアル: Office のプログラミング](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
