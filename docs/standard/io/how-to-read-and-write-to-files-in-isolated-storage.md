---
title: "方法 : 分離ストレージ内でファイルの読み取りと書き込みを行う | Microsoft Docs"
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
  - "データ ストレージ (分離ストレージを使用した), 読み取りと書き込み (ファイルの)"
  - "データ ストア, 読み取りと書き込み (ファイルの)"
  - "ファイル, 分離ストレージ"
  - "分離ストレージ, 読み取りと書き込み (ファイルの)"
  - "読み取り (データを)"
  - "読み取り (ストア内のファイルを)"
  - "ストア, 読み取りと書き込み (ファイルの)"
  - "格納 (分離ストレージを使用したデータの), 読み取りと書き込み (ファイルの)"
  - "書き込み (ストア内のファイルへの)"
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : 分離ストレージ内でファイルの読み取りと書き込みを行う
から読み取ったり、またはファイルに、分離ストアに書き込むには、ストリーム リーダー \(<xref:System.IO.StreamReader> オブジェクト\) またはストリーム ライター \(<xref:System.IO.StreamWriter> オブジェクト\) を持つ <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> オブジェクトを使用します。  
  
## 例  
 次のコード例は TestStore.txt という名前のストアにファイルがあるかどうかを分離ストアをチェックします。  存在しない場合は、ファイルを作成して「Hello Isolated Storage」と書き込みます。  TestStore.txt が既に存在する場合は、このコード例では、ファイルから読み込みます。  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## 参照  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>   
 <xref:System.IO.FileMode?displayProperty=fullName>   
 <xref:System.IO.FileAccess?displayProperty=fullName>   
 <xref:System.IO.StreamReader?displayProperty=fullName>   
 <xref:System.IO.StreamWriter?displayProperty=fullName>   
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)   
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)