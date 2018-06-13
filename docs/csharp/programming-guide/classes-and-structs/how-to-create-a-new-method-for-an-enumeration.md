---
title: '方法 : 列挙型対応の新しいメソッドを作成する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 8de44cbddf26af45245709d0e28d2d157256ce59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313034"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>方法 : 列挙型対応の新しいメソッドを作成する (C# プログラミング ガイド)
拡張メソッドを使用して、特定の列挙型に固有の機能を追加することができます。  
  
## <a name="example"></a>例  
 次の例では、`Grades` 列挙型は学生が授業で受け取る成績評価を表わしています。 `Passing` という名前の拡張機能メソッドが `Grades` 型に追加されていて、この型の各インスタンスが合格点を表しているかどうかを自ら "認識" できるようになっています。  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 `Extensions` クラスには動的に更新される静的変数も含まれていて、拡張メソッドの戻り値はその変数の現在の値を反映していることに注意してください。 背後では、拡張メソッドが自分が定義されている静的クラスに直接呼び出されることを、この例は示しています。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコードを実行するには、Visual Studio で作成した Visual C# コンソール アプリケーション プロジェクトに、そのコードをコピーして貼り付けます。 既定では、このプロジェクトは、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のバージョン 3.5 を対象としており、System.Core.dll への参照と System.Linq の `using` ディレクティブが含まれます。 これらの要件のうち、1 つ以上がプロジェクトから欠落している場合、手動で追加できます。  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [拡張メソッド](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
