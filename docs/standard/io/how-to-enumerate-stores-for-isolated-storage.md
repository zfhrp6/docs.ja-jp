---
title: "方法 : 分離ストレージでストアを列挙する | Microsoft Docs"
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
  - "列挙 (ストアを)"
  - "データ ストレージ (分離ストレージを使用した)、列挙 (ストアを)"
  - "格納 (分離ストレージを使用したデータの)、列挙 (ストアを)"
  - "ストア、列挙"
  - "分離ストレージ、列挙 (ストアを)"
  - "データ ストア、列挙"
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : 分離ストレージでストアを列挙する
<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=fullName> の静的メソッドを使用して、現在のユーザーのすべての分離ストアを列挙できます。  このメソッドは <xref:System.IO.IsolatedStorage.IsolatedStorageScope> 値を受け取り、<xref:System.IO.IsolatedStorage.IsolatedStorageFile> 列挙子を返します。  ストアを列挙するには、<xref:System.Security.Permissions.IsolatedStorageContainment> 値を指定する <xref:System.Security.Permissions.IsolatedStorageFilePermission> のアクセス許可が必要です。  <xref:System.IO.IsolatedStorage.IsolatedStorageScope> 値の <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> のメソッドを呼び出すと、現在のユーザーに対して定義されている <xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクトの配列を返します。  
  
## 例  
 次のコード例は、ユーザーおよびアセンブリ別に分離されたストアを作成し、いくつかのファイルを、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> のメソッドを使用して取得しますそれらのファイルを取得します。  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## 参照  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)