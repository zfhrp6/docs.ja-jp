---
title: "方法: 分離ストレージの領域不足状態に備える | Microsoft Docs"
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
  - "データ ストア、クォータ"
  - "分離ストレージ、クォータ"
  - "量 (使用する分離ストレージの)"
  - "制限 (使用する分離ストレージに対する)"
  - "ストア、クォータ"
  - "ストア、領域不足の状態"
  - "データ ストレージ (分離ストレージを使用した)、クォータ"
  - "格納 (分離ストレージを使用したデータの)、クォータ"
  - "領域 (分離ストレージの残りの)"
  - "データ ストア、領域不足の状態"
  - "格納 (分離ストレージを使用したデータの)、領域不足の状態"
  - "クォータ (分離ストレージの)"
  - "分離ストレージ、領域不足の状態"
  - "データ ストレージ (分離ストレージを使用した)、領域不足の状態"
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法: 分離ストレージの領域不足状態に備える
分離ストレージを使用するコードは、分離ストレージ ファイルおよびディレクトリが格納されているデータ コンパートメントの最大サイズを指定する[クォータ](../../../docs/standard/io/isolated-storage.md#quotas)によって制約されます。  クォータは、セキュリティ ポリシーによって定義され、管理者が構成できます。  データを書き込むときに最大許容サイズを超えると <xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外がスローされ、操作は失敗します。  これにより、データ ストレージがいっぱいになると、アプリケーションに要求を拒否させる不当なサービス拒否攻撃を防止できます。  
  
 指定した書き込みがこのような理由で失敗する可能性があるかどうかを判断できるように、<xref:System.IO.IsolatedStorage.IsolatedStorage> クラスには、<xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>、および <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> の 3 つの読み取り専用プロパティが用意されています。  ストアへの書き込みがストアの最大許容サイズを超過するかどうかを判断するためにこれらのプロパティを使用できます。  分離ストレージは同時にアクセスできることに注意してください。; したがって、残りのストレージの量を計算するときに、も、そのストアに書き込むまでに使用できます。  ただし、使用できるメモリの上限に達するとしているかどうかを確認するには、ストアの最大サイズを使用できます。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> のプロパティはアセンブリの証拠によって正しく機能します。  したがって、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>、または <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> のメソッドを使用して作成された <xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクトにのみこのプロパティを取得する必要があります。   他の方法で作成された<xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクト \(たとえば、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> のメソッドから返されるオブジェクト\) 正確な最大サイズを返します。  
  
## 例  
 分離されたストアを取得し、いくつかのファイルを作成して、<xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> プロパティを取得するコード例を次に示します。  残りの容量は、バイト数で報告されます。  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## 参照  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)   
 [方法 : 分離ストレージでストアを取得する](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)