---
title: "方法 : コレクション初期化子を使用してディクショナリを初期化する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 41d6a9934daaa1274901e20de58cfd480c904bfa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/25/2017

---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>方法 : コレクション初期化子を使用してディクショナリを初期化する (C# プログラミング ガイド)
<xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> メソッドは、キー用と値用の 2 つのパラメーターを受け取ります。 複数のパラメーターを受け取る <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add` メソッドを初期化するには、次の例に示すように、各パラメーターのセットを中かっこで囲みます。  
  
## <a name="example"></a>例  
 次のコード例では、<xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName`。  
  
 [!code-cs[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 コレクションの各要素の中かっこの 2 つのペアに注目してください。 最も内側の中かっこは `StudentName` のオブジェクト初期化子を囲み、最も外側の中かっこは、`students`<xref:System.Collections.Generic.Dictionary`2> に追加されるキーと値のペアの初期化子を囲んでいます。 最後に、ディクショナリのコレクション初期化子全体が中かっこで囲まれています。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコードを実行するには、クラスをコピーし、[!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)] で作成した Visual C# コンソール アプリケーション プロジェクトに貼り付けます。 既定では、このプロジェクトは、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のバージョン 3.5 を対象としており、System.Core.dll への参照と System.Linq の using ディレクティブが含まれます。 これらの要件のうち 1 つまたは複数がプロジェクトから欠落している場合は、手動で追加することができます。   
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

