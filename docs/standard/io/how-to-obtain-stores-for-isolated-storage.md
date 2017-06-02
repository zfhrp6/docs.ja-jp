---
title: "方法 : 分離ストレージでストアを取得する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ストア、取得"
  - "格納 (分離ストレージを使用したデータの)、取得 (ストアを)"
  - "分離ストレージ、取得 (ストアを)"
  - "データ ストア、取得"
  - "データ ストレージ (分離ストレージを使用した)、取得 (ストアを)"
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
caps.latest.revision: 19
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : 分離ストレージでストアを取得する
分離ストアは、データ コンパートメント内の仮想ファイル システムを公開します。  <xref:System.IO.IsolatedStorage.IsolatedStorageFile> クラスは分離ストアと対話するためのメソッドを提供します。  ストアの作成および取得するために、<xref:System.IO.IsolatedStorage.IsolatedStorageFile> は 3 個の静的メソッドを提供し、T:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> は、ユーザーおよびアセンブリ別に分離されたストレージが返されます。  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>、ドメイン、およびアセンブリ別に分離されたストレージが返されます。  
  
     メソッドは両方とも、呼び出しコードに属するストアを取得します。  
  
-   静的メソッド <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> は、スコープ パラメーターの組み合わせを渡すことによって指定される分離ストアを返します。  
  
 次のコードは、ユーザー、ドメイン、およびアセンブリ別に分離されたストアを返します。  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 ローミング ストアは、ローミング ユーザー プロファイルを行う必要があることを指定するために <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> のメソッドを使用できます。  このプロパティを設定する方法の詳細については [分離のタイプ](../../../docs/standard/io/types-of-isolation.md)を参照してください。  
  
 既定では、異なるアセンブリから取得される分離ストアは、異なるストアです。  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> のメソッドのパラメーターのアセンブリまたはドメインの証拠を渡すことにより、異なるアセンブリまたはドメインのストアにアクセスできます。  別のアセンブリまたはドメインのストアにアクセスするには、アプリケーション ドメイン ID 別の分離ストレージにアクセスするためのアクセス許可が必要です。  詳細については、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッド オーバーロードを参照します。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>と <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> のメソッドは <xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクトを返します。  場面に応じてどの分離タイプを使用するのが適切かを判断するには、「[分離のタイプ](../../../docs/standard/io/types-of-isolation.md)」を参照してください。  分離ストレージ ファイル オブジェクトがある場合は、分離ストレージのメソッドを使用して、ファイルやディレクトリの読み取り、書き込み、作成、および削除を行うことができます。  
  
 コードはコードにストアを取得するための十分なアクセス権がない <xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクトを渡すことを防ぐ機構はありません。  ドメインおよびアセンブリの ID や分離ストレージのアクセス許可の確認は、<xref:System.IO.IsolatedStorage.IsolatedStorage> オブジェクトへの参照が取得されたとき、つまり、通常は <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> メソッド、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> メソッド、または <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドでしか実行されません。  したがって、<xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクトへの参照の保護は、その参照を使用するコードで行う必要があります。  
  
## 例  
 次のコードは、ユーザーおよびアセンブリ別に分離されたストアを取得するクラスの簡単な例を示します。  コードは <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> のメソッドに渡す引数に <xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=fullName> に追加することによって、ユーザー、ドメイン、およびアセンブリ別に分離されたストアを取得するように変更できます。  
  
 コードを実行すると、ストアは、コマンド ラインに" **StoreAdm \/LIST** の入力によって作成されたことを確認できます。  これは [分離ストレージ ツール \(Storeadm.exe\)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) を実行し、ユーザーの現在の分離ストアが一覧表示されます。  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## 参照  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>   
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)   
 [分離のタイプ](../../../docs/standard/io/types-of-isolation.md)   
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)