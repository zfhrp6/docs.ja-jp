---
title: '方法 : My 名前空間を使用する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: ceab0dbb2ded070fc7de4f5a59d778be2a54f9cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>方法 : My 名前空間を使用する (C# プログラミング ガイド)
<xref:Microsoft.VisualBasic.MyServices> 名前空間 (Visual Basic では `My`) を使用すると、いくつもの .NET Framework クラスに簡単かつ直感的にアクセスでき、コンピューター、アプリケーション、設定、リソースなどと対話するコードを記述できます。 `MyServices` 名前空間は、もともとは Visual Basic で使用するものとして設計されましたが、C# アプリケーションでも使用できます。  
  
 Visual Basic で `MyServices` 名前空間を使用する方法の詳細については、「[Development with My](../../../visual-basic/developing-apps/development-with-my/index.md)」 (My を使用した開発) を参照してください。  
  
## <a name="adding-a-reference"></a>参照の追加  
 `MyServices` クラスをソリューションで使用する前に、Visual Basic ライブラリへの参照を追加する必要があります。  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Visual Basic ライブラリへの参照を追加するには  
  
1.  **ソリューション エクスプローラー**で、**[参照設定]** ノードを右クリックし、**[参照の追加]** をクリックします。  
  
2.  **[参照設定]** ダイアログ ボックスが表示されたら、一覧を下にスクロールし、Microsoft.VisualBasic.dll を選択します。  
  
     プログラムの先頭の `using` セクションに次の行を追加することもできます。  
  
     [!code-csharp[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]  
  
## <a name="example"></a>例  
 次の例では、`MyServices` 名前空間に含まれているさまざまな静的メソッドを呼び出します。 このコードをコンパイルするには、Microsoft.VisualBasic.DLL への参照をプロジェクトに追加する必要があります。  
  
 [!code-csharp[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]  
  
 `MyServices` 名前空間のクラスの中には C# アプリケーションから呼び出すことができないクラスもあります。たとえば、<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> クラスは、C# と互換性がありません。 そのような場合は、同様に VisualBasic.dll に含まれている <xref:Microsoft.VisualBasic.FileIO.FileSystem> を構成する静的メソッドを代わりに使用できます。 このようなメソッドを使用してディレクトリを複製する方法を次に示します。  
  
 [!code-csharp[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [名前空間](../../../csharp/programming-guide/namespaces/index.md)  
 [名前空間の使用](../../../csharp/programming-guide/namespaces/using-namespaces.md)
