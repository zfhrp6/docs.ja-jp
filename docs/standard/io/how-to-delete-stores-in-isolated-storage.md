---
title: "方法 : 分離ストレージでストアを削除する | Microsoft Docs"
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
  - "ストア、削除"
  - "データ ストア、削除"
  - "削除 (ストアを)"
  - "削除 (ストアを)"
  - "分離ストレージ、削除 (ストアを)"
  - "格納 (分離ストレージを使用したデータの)、削除 (ストアを)"
  - "データ ストレージ (分離ストレージを使用した)、削除 (ストアを)"
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 分離ストレージでストアを削除する
分離ストレージ ファイルを削除するため、<xref:System.IO.IsolatedStorage.IsolatedStorageFile> クラスは 2 つのメソッドを提供します。  
  
-   インスタンス メソッド <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> は引数を使わず、そのインスタンス メソッドを呼び出すストアを削除します。 この操作にアクセス許可は必要ありません。 ストアにアクセスできるすべてのコードは、その内部の一部のデータやすべてのデータを削除できます。  
  
-   静的メソッド <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> は <xref:System.IO.IsolatedStorage.IsolatedStorageScope> 列挙値を使い、コードを実行するユーザーのすべてのストアを削除します。 この操作を実行するには、<xref:System.Security.Permissions.IsolatedStorageContainment> の値に対する <xref:System.Security.Permissions.IsolatedStorageFilePermission> アクセス許可が必要です。  
  
## 例  
 静的 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> メソッドとインスタンス <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> メソッドの使い方を次のコード例に示します。 クラスは、次の 2 つのストアを取得します。1 つは、ユーザーとアセンブリで使うように分離して、もう 1 つは、ユーザー、ドメイン、アセンブリで使うように分離します。 次に、分離ストレージ ファイル `isoStore1` の <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> メソッドを呼び出すことにより、ユーザー、ドメイン、アセンブリのストアが削除されます。 その後、静的メソッド <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> を呼び出すことによって、ユーザーの残りのストアすべてを削除します。  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## 参照  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)