---
title: "方法 : 分離ストレージでストアを取得する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb0b877aa0f4cee36bd1f8c1cea624cf9368fbaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>方法 : 分離ストレージでストアを取得する
分離ストアは、データ コンパートメント内の仮想ファイル システムを公開します。 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>クラスがいくつかの分離ストアと対話するためのメソッドを提供します。 作成し、ストアを取得する<xref:System.IO.IsolatedStorage.IsolatedStorageFile>3 つの静的メソッドを提供します。  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>ユーザーおよびアセンブリによる分離ストレージを返します。  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>ドメインとアセンブリが分離される記憶域を返します。  
  
     両方のメソッドが呼び出されるコードに属しているストアを取得します。  
  
-   静的メソッド<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>スコープ パラメーターの組み合わせに渡すことで指定されている分離ストアを返します。  
  
 次のコードでは、ユーザー、アセンブリ、およびドメイン別に分離されたストアを返します。  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 使用することができます、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>ローミング ユーザー プロファイルを使用して、ストアを移動することを指定します。 これを設定する方法の詳細については、次を参照してください。[分離のタイプ](../../../docs/standard/io/types-of-isolation.md)です。  
  
 別のアセンブリ内から取得される分離ストアは、既定では、異なるストアです。 パラメーターのアセンブリまたはドメインの証拠を渡すことで、別のアセンブリまたはドメインのストアにアクセスすることができます、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>メソッドです。 これには、アプリケーション ドメインの id を使用して分離ストレージにアクセスする権限が必要です。 詳細については、次を参照してください。、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>メソッドのオーバー ロードします。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>、および<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>を返し、<xref:System.IO.IsolatedStorage.IsolatedStorageFile>オブジェクト。 状況に最適などの分離タイプを決定するために、次を参照してください。[分離のタイプ](../../../docs/standard/io/types-of-isolation.md)です。 分離ストレージ ファイル オブジェクトがある場合を読み取り、書き込み、作成、分離ストレージのメソッドを使用して、ファイルおよびディレクトリを削除します。  
  
 コードに渡すことを防止するためのメカニズムがない、<xref:System.IO.IsolatedStorage.IsolatedStorageFile>されるコードをオブジェクトには、ストア自体を取得するための十分なアクセスにないです。 参照時にのみドメインとアセンブリの id と分離ストレージのアクセス許可がチェックされて、<xref:System.IO.IsolatedStorage.IsolatedStorage>オブジェクトは、取得したでは通常、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>、または<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>メソッドです。 参照を保護する<xref:System.IO.IsolatedStorage.IsolatedStorageFile>オブジェクトは、そのため、これらの参照を使用するコードの責任です。  
  
## <a name="example"></a>例  
 次のコードでは、ユーザーおよびアセンブリ別に分離されたストアを取得するクラスの単純な例を提供します。 追加することでユーザー、ドメイン、およびアセンブリ別に分離されたストアを取得するコードを変更することができます<xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType>引数にする、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>メソッドのパス。  
  
 コードを実行した後、」と入力して、ストアが作成されたことを確認できます**StoreAdm/LIST**コマンドライン。 これにより、実行、[分離ストレージ ツール (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md)し、ユーザーの現在の分離を格納すべて一覧表示します。  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)  
 [分離のタイプ](../../../docs/standard/io/types-of-isolation.md)  
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
