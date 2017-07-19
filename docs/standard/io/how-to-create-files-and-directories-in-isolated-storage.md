---
title: "方法 : 分離ストレージでファイルおよびディレクトリを作成する | Microsoft Docs"
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
  - "ディレクトリ [.NET Framework]、分離ストレージ"
  - "ファイル [.NET Framework]、分離ストレージ"
  - "分離ストレージ、作成 (ファイルとディレクトリを)"
  - "データ ストア、作成 (ファイルとディレクトリを)"
  - "データ ストレージ (分離ストレージを使用した)、作成 (ファイルとディレクトリを)"
  - "ストア、作成 (ファイルとディレクトリを)"
  - "格納 (分離ストレージを使用したデータの)、作成 (ファイルとディレクトリを)"
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : 分離ストレージでファイルおよびディレクトリを作成する
分離ストアを取得した後で、データを格納するためのディレクトリおよびファイルを作成できます。  ストア内では、ファイル名およびディレクトリ名が、仮想ファイル システムのルートからのパスを使用して指定されています。  
  
 ディレクトリを作成するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=fullName> のインスタンス メソッドを使用します。  存在しないディレクトリのサブディレクトリを指定すると、ディレクトリとサブディレクトリの両方が作成されます。  既存のディレクトリを指定すると、ディレクトリを作成せずにメソッドは、例外はスローされません。  ただし、無効な文字が含まれているディレクトリ名を指定した場合、<xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外がスローされます。  
  
 ファイルを作成するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=fullName> のメソッドを使用します。  
  
 Windows オペレーティング システムでは、分離ストレージ ファイル名やディレクトリ名は大文字と小文字を区別しないです。  つまり、`ThisFile.txt`という名前のファイルを作成し、1 個のファイルのみが作成されると、`THISFILE.TXT`という名前のファイルを作成します。  表示目的では、ファイル名の元の大文字\/小文字が維持されます。  
  
## 例  
 分離ストア内にファイルおよびディレクトリを作成する方法を次のコード例で示します。  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## 参照  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>   
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)