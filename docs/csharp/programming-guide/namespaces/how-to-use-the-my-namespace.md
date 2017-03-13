---
title: "方法 : My 名前空間を使用する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, My 名前空間アクセス"
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# 方法 : My 名前空間を使用する (C# プログラミング ガイド)
<xref:Microsoft.VisualBasic.MyServices> 名前空間 \(Visual Basic では `My`\) を使用すると、いくつもの .NET Framework クラスに簡単かつ直感的にアクセスできるため、コンピューター、アプリケーション、設定、リソースなどと対話するコードを記述できます。  `MyServices` 名前空間は、もともとは Visual Basic で使用するものとして設計されましたが、C\# アプリケーションでも使用できます。  
  
 Visual Basic で `MyServices` 名前空間を使用する方法の詳細については、「[Development with My](../../../visual-basic/developing-apps/development-with-my/index.md)」を参照してください。  
  
## 参照の追加  
 `MyServices` クラスをソリューションで使用する前に、Visual Basic ライブラリへの参照を追加する必要があります。  
  
#### Visual Basic ライブラリへの参照を追加するには  
  
1.  **ソリューション エクスプローラー**で、**\[参照設定\]** ノードを右クリックし、**\[参照の追加\]** をクリックします。  
  
2.  **\[参照の追加\]** ダイアログ ボックスが表示されたら、一覧を下にスクロールし、Microsoft.VisualBasic.dll を選択します。  
  
     プログラムの先頭の `using` セクションに次の行を追加することもできます。  
  
     [!code-cs[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]  
  
## 使用例  
 次の例では、`MyServices` 名前空間に含まれているさまざまな静的メソッドを呼び出します。  このコードをコンパイルするには、Microsoft.VisualBasic.DLL への参照をプロジェクトに追加する必要があります。  
  
 [!code-cs[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]  
  
 `MyServices` 名前空間のクラスの中には C\# アプリケーションから呼び出すことができないクラスもあります。たとえば、<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> クラスは、C\# と互換性がありません。  そのような場合は、同様に VisualBasic.dll に含まれている <xref:Microsoft.VisualBasic.FileIO.FileSystem> を構成する静的メソッドを代わりに使用できます。  このようなメソッドを使用してディレクトリを複製する方法を次に示します。  
  
 [!code-cs[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [名前空間](../../../csharp/programming-guide/namespaces/index.md)   
 [名前空間の使用](../../../csharp/programming-guide/namespaces/using-namespaces.md)