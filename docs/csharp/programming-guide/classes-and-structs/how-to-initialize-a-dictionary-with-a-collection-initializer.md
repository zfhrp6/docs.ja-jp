---
title: '方法 : コレクション初期化子を使用してディクショナリを初期化する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: b8c44ebbdc89d72398c3380d708b45d0b7dfdad3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>方法 : コレクション初期化子を使用してディクショナリを初期化する (C# プログラミング ガイド)
<xref:System.Collections.Generic.Dictionary`2> にはキーと値のペアのコレクションが含まれています。 その <xref:System.Collections.Generic.Dictionary`2.Add*> メソッドは、それぞれキーと値に対する 2 つのパラメーターを受け取ります。 `Add` メソッドが複数のパラメーターを受け取る <xref:System.Collections.Generic.Dictionary`2> またはコレクションを初期化するには、次の例に示すように、各パラメーターのセットを中かっこで囲みます。  
  
## <a name="example"></a>例  
 次のコード例では、<xref:System.Collections.Generic.Dictionary`2> が型 `StudentName` のインスタンスで初期化されています。  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 コレクションの各要素の中かっこの 2 つのペアに注目してください。 最も内側の中かっこは `StudentName` のオブジェクト初期化子を囲み、最も外側の中かっこは、`students`<xref:System.Collections.Generic.Dictionary`2> に追加されるキーと値のペアの初期化子を囲んでいます。 最後に、ディクショナリのコレクション初期化子全体が中かっこで囲まれています。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコードを実行するには、クラスをコピーし、Visual Studio で作成した Visual C# コンソール アプリケーション プロジェクトに貼り付けます。 既定では、このプロジェクトは、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のバージョン 3.5 を対象としており、System.Core.dll への参照と System.Linq の using ディレクティブが含まれます。 これらの要件のうち 1 つまたは複数がプロジェクトから欠落している場合は、手動で追加することができます。  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
